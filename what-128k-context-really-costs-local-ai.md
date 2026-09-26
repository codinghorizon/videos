---
layout: default
title: "Your 128K local AI setting has a hidden memory bill"
permalink: /what-128k-context-really-costs-local-ai/
date: 2026-09-26
---

# Your 128K local AI setting has a hidden memory bill

{% raw %}
Checked 2026-09-26. Primary sources only: vendor model cards and config.json files,
vendor announcements, official documentation and arXiv. KV cache arithmetic uses the standard formula
`2 (K and V) x layers-with-KV x kv_heads x head_dim x bytes-per-element x tokens`, and
1 GiB = 2^30 bytes, 1 MiB = 2^20 bytes.

---

## 1. RTX 3090 has 24GB of video memory

- Source: https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090-3090ti/
- Text: "The GeForce RTX(TM) 3090 Ti and 3090 are powered by Ampere ... and a staggering 24 GB of G6X memory". Specs table: "24 GB GDDR6X".
- Photograph (beat 008): https://commons.wikimedia.org/wiki/File:RTX_3090_Founders_Edition.jpg, "RTX 3090 Founders Edition", by Adam Kapetanakis (Kaptainvet), CC BY-SA 4.0. It shows the non-Ti card. It is credited on screen under the photo, and the file is at public/<slug>/photo/rtx3090-fe.jpg, downscaled to 2016x1512. NVIDIA's own page photo was not used because it shows the 3090 Ti.
- Status: confirmed

## 2. Qwen3-8B: 128K (131,072) via YaRN, native 32,768, YaRN needs supported configuration

- Source: https://huggingface.co/Qwen/Qwen3-8B (model card)
- Text: "Context Length: 32,768 natively and 131,072 tokens with YaRN."
- Text: "Qwen3 natively supports context lengths of up to 32,768 tokens. ... We have validated the model's performance on context lengths of up to 131,072 tokens using the YaRN method."
- Text: "YaRN is currently supported by several inference frameworks, e.g., transformers and llama.cpp for local use, vllm and sglang for deployment. In general, there are two approaches to enabling YaRN for supported frameworks: Modifying the model files: In the config.json file, add the rope_scaling fields ... Passing command line arguments" (e.g. `vllm serve ... --rope-scaling '{"rope_type":"yarn","factor":4.0,"original_max_position_embeddings":32768}' --max-model-len 131072`, `llama-server ... --rope-scaling yarn --rope-scale 4 --yarn-orig-ctx 32768`).
- Text: "The default max_position_embeddings in config.json is set to 40,960." Shipped config has `"rope_scaling": null`.
- Status: confirmed

## 3. Qwen3-8B KV cache: 18 GiB at 131,072, 4.5 GiB at 32,768 (fp16)

- Source: https://huggingface.co/Qwen/Qwen3-8B/blob/main/config.json
- Values: `num_hidden_layers: 36`, `num_key_value_heads: 8`, `head_dim: 128` (all layers full attention; `use_sliding_window: false`).
- Per token: 2 x 36 x 8 x 128 x 2 B = 147,456 B
- 131,072 tokens: 19,327,352,832 B = **18.00 GiB**
- 32,768 tokens: 4,831,838,208 B = **4.50 GiB**
- Linear in tokens (4x tokens = 4x cache): correct for this all-full-attention design.
- Status: confirmed

## 4. Devstral Small 2: 24B, 256K, repo work with tools, 68% SWE-bench Verified; KV 20 GiB @128K fp16, ~2.5 GiB @32K 8-bit

- Announcement: https://mistral.ai/news/devstral-2-vibe-cli (Dec 9, 2025)
  - "Devstral Small 2 (24B)" ... "Devstral Small 2 scores 68.0% on SWE-bench Verified, and places firmly among models up to five times its size while being capable of running locally on consumer hardware."
  - "Devstral Small 2, a 24B-parameter model with the same 256K context window and released under Apache 2.0"
- Model card: https://huggingface.co/mistralai/Devstral-Small-2-24B-Instruct-2512
  - "Devstral is an agentic LLM for software engineering tasks. Devstral Small 2 excels at using tools to explore codebases, editing multiple files and power software engineering agents."
  - "Lightweight: with its compact size of just 24 billion parameters" / "Context Window: A 256k context window."
  - Benchmark table: "Devstral Small 2 | 24 | 68.0% (SWE Bench Verified)"
- Config: https://huggingface.co/mistralai/Devstral-Small-2-24B-Instruct-2512/blob/main/config.json
  - `text_config`: `num_hidden_layers: 40`, `num_key_value_heads: 8`, `head_dim: 128`, `sliding_window: null`, rope `yarn`, `max_position_embeddings: 393216`.
- Per token fp16: 2 x 40 x 8 x 128 x 2 B = 163,840 B
- 131,072 tokens fp16: 21,474,836,480 B = **20.00 GiB**
- 32,768 tokens at 1 byte/element (ideal 8-bit): 2,684,354,560 B = **2.50 GiB**
- Chapter 5 derivations: 128K at ideal 8-bit = 10.00 GiB; at ideal 4-bit = 5.00 GiB (before format overhead).
- Status: confirmed (all parts)

## 5. Qwen3.6-35B-A3B: hybrid, mostly recurrent-state layers; 35B total / ~3B active; full-attention KV 2.5 GiB @131,072; 4-bit weights + KV = 18.8 GiB

- Model card: https://huggingface.co/Qwen/Qwen3.6-35B-A3B
  - "Number of Parameters: 35B in total and 3B activated"
  - "Number of Layers: 40"
  - "Hidden Layout: 10 x (3 x (Gated DeltaNet -> MoE) -> 1 x (Gated Attention -> MoE))"
  - Gated DeltaNet: 32 linear-attention heads for V, 16 for QK, head dim 128. Gated Attention: 16 Q heads, 2 KV heads, head dim 256.
  - "Context Length: 262,144 natively and extensible up to 1,010,000 tokens."
- Config: https://huggingface.co/Qwen/Qwen3.6-35B-A3B/blob/main/config.json
  - `text_config`: `full_attention_interval: 4`, `layer_types` = 30 x `linear_attention` + 10 x `full_attention`, `num_hidden_layers: 40`, `num_key_value_heads: 2`, `head_dim: 256`, `mamba_ssm_dtype: float32`.
- Full-attention KV per token fp16: 2 x 10 x 2 x 256 x 2 B = 20,480 B
- 131,072 tokens: 2,684,354,560 B = **2.50 GiB**
- 4-bit weights: 35e9 x 0.5 B = 17.5e9 B = 16.30 GiB; + 2.50 = **18.80 GiB** (excludes Gated DeltaNet recurrent state and runtime buffers, as stated in the video). Note the HF safetensors widget lists 36B params (includes the vision encoder); using 36e9 gives 16.76 + 2.5 = 19.26 GiB.
- "Most of its layers carry forward a compact recurrent state": 30 of 40 layers are Gated DeltaNet (linear attention with fixed-size recurrent state).
- Status: confirmed

## 6. Qwen3.8-27B: released August 2026, dense, hybrid attention, native window > 128K; full-attention KV 8 GiB @131,072; SWE-bench Pro 61.7 vs 53.5

- Model card: https://huggingface.co/Qwen/Qwen3.8-27B
  - "Qwen3.8-27B brings these advances to a compact, deployment-friendly dense model: a native vision-language model"
  - "Number of Parameters: 27B"; "Hidden Layout: 16 x (3 x (Gated DeltaNet -> FFN) -> 1 x (Gated Attention -> FFN))"
  - "Context Length: 262,144 natively and extensible up to 1,000,000 tokens."
  - Citation block: `title = {Qwen3.8-Max}: A New Bar for Coding and Cowork`, `month = {August}, year = {2026}`. HF API `createdAt` for the repo: 2026-08-05.
  - Benchmark table (Text Performance, Coding): "Agentic coding / SWE-bench Pro: Qwen3.8-27B 61.7 | Qwen3.6-27B 53.5 | Qwen3.7-Plus 57.6 | Muse Glimmer-30B 51.2 | Opus4.6 Max 53.4"
  - Footnote: "SWE-bench Pro: Except for Opus4.6 Max, which uses the officially reported score, all models are evaluated with the Claude Code harness at temp=1.0, top_p=0.95, and a 256K context window. Problematic tasks were corrected, and all baseline models were re-evaluated on the refined benchmark." (i.e. Qwen's own refined SWE-bench Pro, not the stock public set)
- Config: https://huggingface.co/Qwen/Qwen3.8-27B/blob/main/config.json
  - `text_config`: `full_attention_interval: 4`, 64 layers = 48 `linear_attention` + 16 `full_attention`, `num_key_value_heads: 4`, `head_dim: 256`.
- Full-attention KV per token fp16: 2 x 16 x 4 x 256 x 2 B = 65,536 B
- 131,072 tokens: 8,589,934,592 B = **8.00 GiB**
- vs Qwen3.6-35B-A3B 2.50 GiB: ratio 3.2x ("more than three times"): correct. 27B < 35B total params: correct.
- Status: confirmed. Nuance: the exact public release day within August is not stated on the card; the repo was created 2026-08-05 and third-party coverage says it landed on HF on 14 August 2026. "August 2026" is safe.

## 7. NVIDIA Nemotron 3 Nano 30B A3B: hybrid Mamba + attention + sparse MoE; up to 1M tokens, smaller default for memory reasons

- Model card: https://huggingface.co/nvidia/NVIDIA-Nemotron-3-Nano-30B-A3B-BF16
  - "The model employs a hybrid Mixture-of-Experts (MoE) architecture, consisting of 23 Mamba-2 and MoE layers, along with 6 Attention layers. Each MoE layer includes 128 experts plus 1 shared expert, with 6 experts activated per token. The model has 3.5B active parameters and 30B parameters in total."
  - "Architecture Type: Mamba2-Transformer Hybrid Mixture of Experts (MoE)"
  - "Maximum input size: 1M tokens"
  - "Please note that the model supports up to a 1M context size, although the default context size in the Hugging Face configuration is 256k due to higher VRAM requirements."
- Config: https://huggingface.co/nvidia/NVIDIA-Nemotron-3-Nano-30B-A3B-BF16/blob/main/config.json: `max_position_embeddings: 262144`, `hybrid_override_pattern` with 6 `*` attention layers, `num_key_value_heads: 2`, `head_dim: 128`.
- Status: confirmed (Active params are stated as 3.5B despite the "A3B" name; the video does not state an active count.)

## 8. DeepSeek V4.1 Flash: 890 bytes/token global KV (compressed design + 4-bit cache); 552B backbone + separate large conditional memory; 890 x 131,072 = ~111 MiB

- Model card: https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash
- Tech report: https://arxiv.org/abs/2609.19969 ("DeepSeek-V4.1-Flash: Pushing the Limits of KV Cache Compression")
  - "We introduce DeepSeek-V4.1-Flash, a multimodal Mixture-of-Experts (MoE) model with 552B backbone parameters and support for contexts of up to one million tokens."
  - "Compressed Sparse Attention 2 (CSA2) ... Combined with FP4 main KV caching (E2M1 format, one E4M3 scale per 16 channels), these designs reduce the global KV cache footprint to 890 bytes per token, roughly 1/4 of DeepSeek-V4-Flash."
  - "Additional architectural components include ... Engram conditional memory (196B parameters, sparsely accessed via token-based lookup)"
  - Table row: "# Backbone Params | - | 284B | 1.6T | 552B"
  - Also: SWA Bounded Replay handles the sliding-window (local) KV separately, which is outside the "global" figure (consistent with "Local attention state ... outside that number").
- Arithmetic: 890 x 131,072 = 116,654,080 B = **111.25 MiB** = 0.109 GiB ("just over a tenth of a gibibyte": correct).
- Status: confirmed (Conditional memory = 196B params; HF safetensors widget shows 763B total stored params.)

## 9. DeepSeek-R1-Distill-Qwen models are built on Qwen base architectures

- Source: https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Qwen-7B
  - "We open-source distilled 1.5B, 7B, 8B, 14B, 32B, and 70B checkpoints based on Qwen2.5 and Llama3 series to the community."
  - Table: DeepSeek-R1-Distill-Qwen-1.5B -> Qwen2.5-Math-1.5B; -Qwen-7B -> Qwen2.5-Math-7B; -Qwen-14B -> Qwen2.5-14B; -Qwen-32B -> Qwen2.5-32B.
  - "DeepSeek-R1-Distill models are fine-tuned based on open-source models, using samples generated by DeepSeek-R1."
- Status: confirmed (base is Qwen2.5, so they carry Qwen2.5 attention, not V4.1's CSA2/FP4 cache).

## 10. Ollama: q8_0 about 1/2 of f16, q4_0 about 1/4; q4_0 precision loss more noticeable at higher context; support depends on model/backend

- Source: https://docs.ollama.com/faq ("How can I set the quantization type for the K/V cache?")
  - "The K/V context cache can be quantized to significantly reduce memory usage when Flash Attention is enabled."
  - "q8_0 - 8-bit quantization, uses approximately 1/2 the memory of f16 with a very small loss in precision, this usually has no noticeable impact on the model's quality (recommended if not using f16)."
  - "q4_0 - 4-bit quantization, uses approximately 1/4 the memory of f16 with a small-medium loss in precision that may be more noticeable at higher context sizes."
  - "How much the cache quantization impacts the model's response quality will depend on the model and the task."
  - Flash Attention section: "Ollama uses Flash Attention automatically when the selected backend and devices support it."
  - "Currently this is a global option - meaning all models will run with the specified quantization type."
- Status: confirmed (support dependency is expressed via the Flash Attention requirement and backend/device support; model dependence is stated for quality impact).

## 11. llama-bench separates prompt processing (pp) from text generation (tg)

- Source: https://github.com/ggml-org/llama.cpp/blob/master/tools/llama-bench/README.md
  - "llama-bench can perform three types of tests: Prompt processing (pp): processing a prompt in batches (-p); Text generation (tg): generating a sequence of tokens (-n); Prompt processing + text generation (pg)"
  - Example output rows `pp512` and `tg128` reported separately in tokens/s.
- Status: confirmed

## 12. vLLM automatic prefix caching: reuses shared-prefix KV, saves prefill, does not speed up decoding

- Source: https://docs.vllm.ai/en/stable/features/automatic_prefix_caching/
  - "Automatic Prefix Caching (APC in short) caches the KV cache of existing queries, so that a new query can directly reuse the KV cache if it shares the same prefix with one of the existing queries, allowing the new query to skip the computation of the shared part."
  - "APC only reduces the time of processing the queries (the prefilling phase) and does not reduce the time of generating new tokens (the decoding phase)."
- Status: confirmed

## 13. RULER: tests beyond needle-in-a-haystack, including multi-hop tracing and aggregation

- Source: https://arxiv.org/abs/2404.06654
  - Title: "RULER: What's the Real Context Size of Your Long-Context Language Models?"
  - "However, this simple retrieval-based test is indicative of only a superficial form of long-context understanding."
  - "RULER expands upon the vanilla NIAH test to encompass variations with diverse types and quantities of needles. Moreover, RULER introduces new task categories multi-hop tracing and aggregation to test behaviors beyond searching from context."
- Status: confirmed

## 14. A gibibyte is 2^30 bytes

- Source: https://physics.nist.gov/cuu/Units/binary.html (NIST, IEC binary prefixes): gibi, symbol Gi, 2^30 (= 1,073,741,824). One gibibyte = 1 GiB = 2^30 B.
- Status: confirmed

## 15. 24e9 params at 4 bits = 11.18 GiB

- 24e9 x 0.5 B = 12,000,000,000 B / 1,073,741,824 = **11.176 GiB** ("about 11.2")
- Chapter 8 total: 11.18 + 2.50 (8-bit KV at 32K) = 13.68 GiB before quantization overhead and buffers.
- Status: confirmed

---

## Notes

All figures shown are confirmed by the primary sources above. Context worth knowing:
- Qwen3.8-27B SWE-bench Pro figures are from Qwen's refined version of SWE-bench Pro run in the Claude Code harness (card footnote), so "Qwen's own evaluation" is the right framing.
- Nemotron 3 Nano's card states 3.5B active parameters.
- Qwen3.6-35B-A3B's stored checkpoint is listed as 36B params on HF (vision encoder included); the 18.8 GiB figure uses the card's 35B.
- DeepSeek V4.1 Flash's conditional memory (Engram) is 196B parameters.

---

## Figures derived for the picture

The same arithmetic as above, applied to published parameter counts and configs. Weights at
an ideal 4 bits are parameters x 0.5 bytes; KV is 2 x attention layers x KV heads x head
dimension x 2 bytes x 131,072 tokens. Neither includes quantization overhead, runtime
buffers or recurrent state.

- Qwen3-8B, 8.2B parameters (huggingface.co/Qwen/Qwen3-8B, "Number of Parameters: 8.2B"):
  4.1e9 bytes = **3.8 GiB** of weights at 4 bit; with its 18 GiB cache, 21.8 GiB at 128K.
- Qwen3.8-27B, 27B parameters: 13.5e9 bytes = **12.6 GiB** at 4 bit; with its 8 GiB cache,
  20.6 GiB at 128K, or 16.6 GiB with the cache at 8 bit.
- NVIDIA Nemotron 3 Nano 30B A3B, 6 attention layers, 2 KV heads, head dimension 128 (its
  config.json): 2 x 6 x 2 x 128 x 2 x 131,072 = 805,306,368 bytes = **0.75 GiB** at 128K.
- DeepSeek V4.1 Flash, 552B backbone parameters: 276e9 bytes = **257 GiB** at 4 bit; the
  196B parameter Engram conditional memory would add **91 GiB** at 4 bit.
- Devstral Small 2 at 128K: 11.2 GiB of weights + 20 GiB of 16 bit cache = 31.2 GiB; with
  an 8 bit cache, 21.2 GiB; with a 4 bit cache, 16.2 GiB.
- The prefill example: 100,000 tokens / 1,000 tokens per second = 100 s; / 5,000 = 20 s.
  These are arithmetic, not measured rates.
{% endraw %}

---
layout: default
title: "The Four Bit Setting That Makes Huge AI Models Fit"
permalink: /quantization-explained/
date: 2026-09-26
---

# The Four Bit Setting That Makes Huge AI Models Fit

{% raw %}
Sources checked September 2026. Where a figure is plain arithmetic rather than a
measurement, it is marked as arithmetic. Memory sizes in arithmetic are decimal gigabytes
(1 GB = 10^9 bytes) unless marked GiB (2^30 bytes).


## 140 gigabytes down to 35

**A 70B model in half precision needs about 140 GB for its weights.** Arithmetic:
parameters × bits per weight ÷ 8 = bytes. 70 × 10^9 × 16 ÷ 8 = 140 × 10^9 bytes = 140 GB.
Half precision (FP16 or BF16) is 16 bits per value.
- FP16 and BF16 are both listed as 16 bit types in the GGUF type table:
  https://huggingface.co/docs/hub/gguf

**At four bits the raw weight arithmetic is about 35 GB.** Arithmetic: 70 × 10^9 × 4 ÷ 8 =
35 × 10^9 bytes. That is a 75% reduction of the raw weight figure (4 ÷ 16 = 1/4).

**Real files are larger than the raw arithmetic.** llama.cpp's own quantize documentation
lists Llama 3.1 70B at 43.1 GB in Q4_K_M, against 280.9 GB for the original (the "original"
column there is 32 bit float, which is why it is double 140 GB).
- https://github.com/ggml-org/llama.cpp/blob/master/tools/quantize/README.md
  ("Memory/Disk Requirements" table: 8B 32.1 GB → 4.9 GB; 70B 280.9 GB → 43.1 GB;
  405B 1,625.1 GB → 249.1 GB, Q4_K_M)

**Quantized models now run on phones.** The PyTorch torchao project reports a quantized
Qwen3-4B (int8 activations, int4 weights) "running with 14.8 tokens/s with 3379 MB memory
usage on iPhone 15 Pro through ExecuTorch".
- https://github.com/pytorch/ao (README, Inference section)
- https://huggingface.co/pytorch/Qwen3-4B-INT8-INT4


## The numbers inside a model

**Four bits encode 16 values; sixteen bits encode 65,536.** Arithmetic: 2^4 = 16,
2^16 = 65,536.

**The 70B → 140 GB and 35 GB figures:** see the previous chapter (arithmetic).

**Quantizers split weights into groups (blocks), each with its own scale, and some add an
offset (zero point / minimum).** llama.cpp's formats are defined this way:
- Q4_0: "Each block has 32 weights. Weight formula: `w = q * block_scale`" (scale only,
  symmetric).
- Q4_1: "Each block has 32 weights. Weight formula: `w = q * block_scale + block_minimum`"
  (scale plus offset).
- Q4_K: "Super-blocks with 8 blocks, each block has 32 weights. Weight formula:
  `w = q * block_scale(6-bit) + block_min(6-bit)`, resulting in 4.5 bits-per-weight."
- https://huggingface.co/docs/hub/gguf ("Quantization Types" table)

**PyTorch documents the same scale and zero point pattern:**
`x_q = (x_float / scale + zp).round().clamp(qmin, qmax)`, where "scale and zero point (zp)
refer to parameters used to quantize x_float".
- https://pytorch.org/blog/quantization-aware-training/

**Outliers are the reason one global scale fails.** The LLM.int8() paper describes
"emergent features in transformer language models that dominate attention and transformer
predictive performance", handled with vector wise quantization (separate normalisation
constants) and by keeping outlier dimensions in 16 bit while "more than 99.9% of values are
multiplied in 8-bit".
- https://arxiv.org/abs/2208.07339
- The Transformers bitsandbytes docs add that hidden state values are "usually normally
  distributed ([-3.5, 3.5])" but for large models can be "[-60, 6] or [6, 60]", and that
  8 bit quantization "works well for values ~5, but beyond that, there is a significant
  performance penalty": https://huggingface.co/docs/transformers/main/en/quantization/bitsandbytes

**Quantization keeps the parameter count; it changes storage precision.** The PyTorch QAT
table shows a Llama3-8B model quantized to int4 weights at 3.881 GB, which is still an 8B
parameter model (the parameter count of an 8B model at 16 bit would be about 16 GB).
- https://pytorch.org/blog/quantization-aware-training/ (Table 1)


## Four bit is not the file size

**8B model: about 16 GB at 16 bit, about 4 GB at 4 bit.** Arithmetic: 8 × 10^9 × 2 bytes =
16 GB; 8 × 10^9 × 0.5 bytes = 4 GB.

**Real download sizes for one coding model (Qwen2.5-Coder-7B-Instruct GGUF, bartowski).**
The page lists the model size as "8B params". Files as listed:

| Quant | File size | Page description |
|---|---|---|
| f16 | 15.24 GB | Full F16 weights |
| Q8_0 | 8.10 GB | "Extremely high quality, generally unneeded but max available quant" |
| Q5_K_M | 5.44 GB | "High quality, recommended" |
| Q4_K_M | 4.68 GB | "Good quality, default size for must use cases" |
| Q2_K | 3.02 GB | "Very low quality but surprisingly usable" |

- https://huggingface.co/bartowski/Qwen2.5-Coder-7B-Instruct-GGUF (made with llama.cpp
  release b3772)
- Qwen's own model card gives the exact count: "Number of Parameters: 7.61B"
  (6.53B non-embedding), 28 layers, 28 query heads and 4 KV heads.
  https://huggingface.co/Qwen/Qwen2.5-Coder-7B-Instruct
- Arithmetic check: 7.61B × 0.5 bytes = 3.8 GB raw at 4 bits, yet the Q4_K_M file is
  4.68 GB. 7.61B × 2 bytes = 15.2 GB, matching the f16 file.

**Effective bits per weight are higher than the name.** llama.cpp measures, on Llama 3.1 8B:
Q4_K_M 4.8944 bits/weight (4.58 GiB), Q5_K_M 5.7036 (5.33 GiB), Q8_0 8.5008 (7.95 GiB),
Q2_K 3.1593 (2.95 GiB), F16 16.0005 (14.96 GiB).
- https://github.com/ggml-org/llama.cpp/blob/master/tools/quantize/README.md

**Real files carry scales, offsets and metadata.** GGUF "encodes both the tensors and a
standardized set of metadata", unlike tensor only formats such as safetensors.
- https://huggingface.co/docs/hub/gguf

**The KV cache stores keys and values so earlier tokens are not recomputed, and it grows
with context.** Hugging Face: "to predict token number 1000 in the generation, you need
information from the previous 999 tokens". Size formula given:
`2 * 2 * num_layers * num_key_value_heads * head_dim * sequence_length` bytes at 16 bit.
Their example: Llama 2 7B with a 10,000 token input needs about 5 GB of KV cache, "roughly
one-third of the model's parameter memory".
- https://huggingface.co/blog/kv-cache-quantization (16 May 2024)

**KV cache for a typical 8B model.** Llama 3 8B config: `num_hidden_layers` 32,
`num_attention_heads` 32, `num_key_value_heads` 8, `hidden_size` 4096 (so head dim
4096 ÷ 32 = 128), `max_position_embeddings` 8192, `torch_dtype` bfloat16.
- https://huggingface.co/unsloth/llama-3-8b/raw/main/config.json (public mirror of
  meta-llama/Meta-Llama-3-8B, which is gated)
- Arithmetic at 16 bit: 2 (K and V) × 32 layers × 8 heads × 128 × 2 bytes = 131,072 bytes =
  128 KiB per token. At 8,192 tokens: 1 GiB. At 131,072 tokens (128K): 16 GiB.

**Blocks and mixed precision inside "four bit".** In llama.cpp's k-quants, Q4_K_M "uses
GGML_TYPE_Q6_K for half of the attention.wv and feed_forward.w2 tensors, else
GGML_TYPE_Q4_K", while Q4_K_S "uses GGML_TYPE_Q4_K for all tensors". Q3_K_M uses Q4_K for
attention.wv, attention.wo and feed_forward.w2.
- https://github.com/ggml-org/llama.cpp/pull/1684
- The quantize tool's `--pure` flag will "disable k-quant mixtures and quantizes all tensors
  to the same type", confirming the default K types are mixtures.
  https://github.com/ggml-org/llama.cpp/blob/master/tools/quantize/README.md
- The S, M and L suffixes are small, medium and large variants of the mix. The docs do not
  formally expand the letter K; the family is referred to as "k-quants".

**Two "4 bit" files differ in size and quality.** llama.cpp's Llama 3 8B scoreboard:
Q4_K_S 4.37 GiB (+0.2689 perplexity vs FP16) and Q4_K_M 4.58 GiB (+0.1754 perplexity).
- https://github.com/ggml-org/llama.cpp/blob/master/tools/quantize/quantize.cpp
  (built in type descriptions)
- https://github.com/ggml-org/llama.cpp/blob/master/tools/perplexity/README.md

**Q4_K_M is a llama.cpp / GGUF type.** The quantize tool is run as
`llama-quantize <in>.gguf <out>.gguf Q4_K_M`; it takes a GGUF file and converts it.
- https://github.com/ggml-org/llama.cpp/blob/master/tools/quantize/README.md

**AWQ, GPTQ, bitsandbytes and GGUF are separate formats and loaders.** GGUF is "a file
format for storing models for inference with GGML and executors based on GGML"
(https://github.com/ggml-org/ggml/blob/master/docs/gguf.md). bitsandbytes quantizes at load
time by passing a `BitsAndBytesConfig` to `from_pretrained()`
(https://huggingface.co/docs/transformers/main/en/quantization/bitsandbytes). GPTQ and AWQ
checkpoints are produced by their own algorithms and loaded by GPU serving engines such as
vLLM (https://docs.vllm.ai/projects/llm-compressor/en/latest/).


## How the approximation is chosen

**More bits, more steps.** Arithmetic: a 2 bit code has 4 levels, 4 bit 16, 5 bit 32,
8 bit 256. For a fixed range, the step size halves with each extra bit.

**Group size is a trade off.** llama.cpp blocks are 32 weights (Q4_0, Q8_0) or 16 to 32
weights inside 256 weight super-blocks (k-quants); scales in k-quants are themselves stored
at 6 or 4 bits to save overhead.
- https://huggingface.co/docs/hub/gguf
- PyTorch used "a group size of 256 for weights" for 4 bit and moved to "a group size of 32
  ... for finer-grained quantization" at 2 and 3 bits because "Quantization degradation is
  more severe at lower bit-widths". https://pytorch.org/blog/quantization-aware-training/

**Symmetric vs asymmetric.** Q4_0 / Q8_0 use `w = q * block_scale` (symmetric about zero);
Q4_1 / Q4_K / Q5_K add a block minimum (an offset).
- https://huggingface.co/docs/hub/gguf

**Calibration with representative inputs.** AWQ's scale "is determined by collecting the
activation statistics offline" (https://arxiv.org/abs/2306.00978). llama.cpp's
`--imatrix file_name` will "use data in file_name as importance matrix for quant
optimizations" (https://github.com/ggml-org/llama.cpp/blob/master/tools/quantize/README.md).
On the Llama 3 8B scoreboard, Q4_K_M with a Wikitext importance matrix scores perplexity
6.3829 versus 6.4071 without one (FP16: 6.2332)
(https://github.com/ggml-org/llama.cpp/blob/master/tools/perplexity/README.md).


## Why there are so many methods

**GPTQ (post training).** "a new one-shot weight quantization method based on approximate
second-order information, that is both highly-accurate and highly-efficient." Quantizes
GPT models with 175 billion parameters "in approximately four GPU hours", to "3 or 4 bits
per weight, with negligible accuracy degradation", with end to end speedups over FP16 "of
around 3.25x when using high-end GPUs (NVIDIA A100) and 4.5x when using more cost-effective
ones (NVIDIA A6000)". GPTQ quantizes weights in sequence and updates the weights not yet
quantized to compensate for the error of those already quantized.
- https://arxiv.org/abs/2210.17323

**AWQ (activation aware).** "not all weights in an LLM are equally important. Protecting
only 1% salient weights can greatly reduce quantization error." "To identify salient weight
channels, we should refer to the activation distribution, not weights." Reports "more than
3x speedup over the Huggingface FP16 implementation on both desktop and mobile GPUs".
- https://arxiv.org/abs/2306.00978

**SmoothQuant.** Enables "8-bit weight, 8-bit activation (W8A8) quantization for LLMs" by
"offline migrating the quantization difficulty from activations to weights"; "up to 1.56x
speedup and 2x memory reduction for LLMs with negligible loss in accuracy"; training free.
- https://arxiv.org/abs/2211.10438

**QAT.** "simulating quantization numerics during training while keeping the weights
and/or activations in the original data type ... effectively 'fake quantizing' the
values", "effectively allowing the model to adjust for quantization noise during the
training process". Results on Llama3-8B (int8 dynamic activations + int4 grouped weights):
recovers "96% of the accuracy degradation on hellaswag and 68% of the perplexity
degradation on wikitext" compared with PTQ. At 2 bits, PTQ wikitext perplexity "explode[d]"
(603,336; 6,766 after skipping sensitive layers) and QAT brought it to 30. Cost: QAT
fine-tuning measured "~34% slower than regular full fine-tuning".
- https://pytorch.org/blog/quantization-aware-training/
- The torchao README separately reports QAT recovering "67% of quantized accuracy
  degradation on Gemma3-4B": https://github.com/pytorch/ao

**QLoRA.** Backpropagates "through a frozen, 4-bit quantized pretrained language model into
Low Rank Adapters (LoRA)"; introduces NF4 ("information theoretically optimal for normally
distributed weights"), double quantization ("quantizing the quantization constants") and
paged optimizers; "reduces memory usage enough to finetune a 65B parameter model on a
single 48GB GPU".
- https://arxiv.org/abs/2305.14314
- Transformers: "8 and 4-bit training is only supported for training *extra* parameters."
  https://huggingface.co/docs/transformers/main/en/quantization/bitsandbytes


## Weights are only one target

**Weights dominate memory traffic for single user generation.** AWQ: "weight access
dominates the memory traffic for on-device LLMs."
- https://arxiv.org/html/2306.00978

**W4A16 and W8A8.** vLLM's LLM Compressor lists W4A16 / W8A16 as weight only schemes
("Optimize for latency on older hardware"), W8A8-INT8 as weights and activations
("Balanced performance and compatibility"), and W8A8-FP8 as weights and activations
requiring compute capability 8.9 ("High throughput on modern GPUs").
- https://docs.vllm.ai/projects/llm-compressor/en/latest/

**Weight only needs dequantization during compute.** AWQ's kernels avoid "writing
dequantized weights into DRAM by fusing dequantization kernels with the matrix
multiplication kernel."
- https://arxiv.org/html/2306.00978
- torchao: "Sometimes quantizing a layer can make it slower because of overhead", and its
  API separates options for "Memory bound models" (int4 / int8 weight only) from "Compute
  bound models" (int8 dynamic activation). https://pytorch.org/blog/pytorch-native-architecture-optimization/

**KV cache quantization is a separate option.** vLLM: "Quantizing the KV (Key-Value) cache
to FP8 format can significantly reduce its memory footprint", allowing more tokens,
higher throughput and longer context; set with `kv_cache_dtype="fp8"` (fp8_e4m3 or
fp8_e5m2). Without calibrated scales all scales default to 1.0, which can cost accuracy.
- https://docs.vllm.ai/en/latest/features/quantization/quantized_kvcache.html

**Hugging Face KV cache quantization results.** int4 KV cache gives about 2.5x memory
saving with quality comparable to fp16; int2 degrades. Quantized cache allowed up to 128K
tokens on an 80 GB A100 versus about 40K at half precision.
- https://huggingface.co/blog/kv-cache-quantization

**In llama.cpp the cache defaults to 16 bit regardless of weight type.** `--cache-type-k`
and `--cache-type-v` both "(default: f16)"; allowed values include q8_0, q4_0, q4_1,
iq4_nl, q5_0, q5_1.
- https://github.com/ggml-org/llama.cpp/blob/master/tools/server/README.md

**FP8.** Two encodings: E4M3 (4 exponent bits, 3 mantissa) and E5M2 (5 exponent, 2
mantissa); matched 16 bit training quality on models up to 175B parameters.
- https://arxiv.org/abs/2209.05433
- NVIDIA Transformer Engine: E4M3 "can store values up to +/-448", E5M2 "up to +/-57344";
  E4M3 is used in the forward pass (more precision), E5M2 for gradients (more range).
  https://docs.nvidia.com/deeplearning/transformer-engine-releases/release-2.14/user-guide/examples/fp8_primer.html
- FP8 compute needs compute capability 8.9 or newer (Ada Lovelace, Hopper and later):
  https://docs.vllm.ai/projects/llm-compressor/en/latest/


## When smaller becomes faster

**Single user decoding is memory bound.** AWQ: "the generation stage for on-device LLMs has
arithmetic intensity≈1. This underscores the memory-bound nature of the workload." "Since
the FLOPs of a given model is fixed, the only way to improve the peak performance is to
reduce the total amount of memory traffic." 4 bit weights raise arithmetic intensity to
about "4 FLOPs/Byte".
- https://arxiv.org/html/2306.00978

**Measured on llama.cpp (Llama 3.1 8B, text generation, tokens/s at 128 tokens):**
F16 29.17, Q8_0 50.93, Q5_K_M 67.23, Q4_K_M 71.93, Q2_K 79.85. The README does not state
the hardware.
- https://github.com/ggml-org/llama.cpp/blob/master/tools/quantize/README.md

**torchao's published cases (named models and accelerators):**
- Llama 3 8B, int4 weight only (autoquant + HQQ): "97% speedup" (baseline bf16, A100 80GB).
- Llama 3.1 8B at 128K context with a quantized KV cache: "73% peak VRAM reduction";
  int4 weights plus int8 KV cache run the full 128K context "in under 18.9GB of VRAM".
- https://pytorch.org/blog/pytorch-native-architecture-optimization/
- Gemma3-12b-it, int4 weight only: "1.73x speedup with 65% less memory" on H100.
- gemma-3-27b-it, float8 dynamic quantization: "1.5-1.6x speedup" on H100.
- Llama-3-8B int4: "1.89x faster inference with 58% less memory".
- https://github.com/pytorch/ao (README)

**Different hardware, different results.** GPTQ reported 3.25x on A100 and 4.5x on A6000
for the same method (https://arxiv.org/abs/2210.17323). llm-compressor recommends
different schemes for latency on older hardware versus high throughput on modern GPUs
(https://docs.vllm.ai/projects/llm-compressor/en/latest/).


## What quality loss looks like

**Perplexity as a measure, and its limits.** "Perplexity measures how well the model can
predict the next token with lower values being better." "Within llama.cpp the perplexity of
base models is used primarily to judge the quality loss from e.g. quantized models vs.
FP16." It is "not directly comparable between models", and "finetunes typically result in
a higher perplexity value even though the human-rated quality of outputs increases."
The tool also reports KL divergence and "Same top p", how often both models pick the same
top token.
- https://github.com/ggml-org/llama.cpp/blob/master/tools/perplexity/README.md

**Higher precision keeps more of the original; careful low bit stays close.** Llama 3 8B
Wikitext perplexity (FP16 6.2332): Q8_0 6.2343, Q5_K_M 6.2886, Q4_K_M 6.4071 (6.3829 with an
importance matrix). Size 14.97 GiB → 7.96 → 5.33 → 4.58.
- https://github.com/ggml-org/llama.cpp/blob/master/tools/perplexity/README.md
- quantize.cpp's built in descriptions: Q8_0 "+0.0026 ppl", Q5_K_M "+0.0569 ppl", Q4_K_M
  "+0.1754 ppl", Q2_K "+3.5199 ppl" @ Llama-3-8B.
  https://github.com/ggml-org/llama.cpp/blob/master/tools/quantize/quantize.cpp

**Two bit and codebook methods exist.**
- AQLM: "the first scheme that is Pareto optimal in terms of accuracy-vs-model-size when
  compressing to less than 3 bits per parameter"; learned additive quantization with
  codebooks. https://arxiv.org/abs/2401.06118
- QuIP#: randomized Hadamard incoherence plus vector quantization with codebooks based on
  the E8 lattice; "state-of-the-art results in extreme compression regimes (≤ 4 bits per
  weight)". https://arxiv.org/abs/2402.04396
- llama.cpp i-quants use an importance matrix, down to IQ1_S (1.56 bits per weight).
  https://huggingface.co/docs/hub/gguf

**Errors have less room at very low bits.** PyTorch: "Quantization degradation is more
severe at lower bit-widths"; 2 bit PTQ "saw wikitext perplexity explode".
- https://pytorch.org/blog/quantization-aware-training/


## Choose the file, not the number

**GGUF can hold different tensor types in one file.** Each tensor records its own type,
and the Hub viewer shows each tensor's "name, shape, precision".
- https://github.com/ggml-org/ggml/blob/master/docs/gguf.md
- https://huggingface.co/docs/hub/gguf

**bitsandbytes quantizes while loading, including the 4 bit QLoRA options.**
`BitsAndBytesConfig(load_in_4bit=True)`, `bnb_4bit_quant_type="nf4"` ("You should use NF4
for training 4-bit base models"), `bnb_4bit_use_double_quant=True` (saves "an additional
0.4 bits/parameter"). "Quantizing a model in 4-bit reduces your memory-usage by 4x".
Hardware: NVIDIA GPUs (CUDA), Intel XPU, Intel Gaudi and CPU.
- https://huggingface.co/docs/transformers/main/en/quantization/bitsandbytes

**Q5 vs Q4 in one GGUF family.** Llama 3 8B: Q5_K_M 5.33 GiB, perplexity 6.2886;
Q4_K_M 4.58 GiB, perplexity 6.4071. Q5_K_M generates more slowly in llama.cpp's own table
(67.23 vs 71.93 tokens/s on Llama 3.1 8B).
- https://github.com/ggml-org/llama.cpp/blob/master/tools/perplexity/README.md
- https://github.com/ggml-org/llama.cpp/blob/master/tools/quantize/README.md

**Q4_K_M allocates bits differently from a plain Q4.** Q4_K_M uses Q6_K for half of the
attention.wv and feed_forward.w2 tensors; Q4_0 uses one 4 bit type with a per-block scale.
- https://github.com/ggml-org/llama.cpp/pull/1684
- https://huggingface.co/docs/hub/gguf


## Testing without fooling yourself

**Perplexity is not a task test.** See the perplexity documentation above: it measures
next token prediction on a corpus (Wikitext-2 by convention), not task success.
- https://github.com/ggml-org/llama.cpp/blob/master/tools/perplexity/README.md

**Long prompts: check the cache options.** llama.cpp exposes `--cache-type-k` and
`--cache-type-v` (default f16); vLLM exposes `kv_cache_dtype`.
- https://github.com/ggml-org/llama.cpp/blob/master/tools/server/README.md
- https://docs.vllm.ai/en/latest/features/quantization/quantized_kvcache.html

**More requests on one GPU.** vLLM: FP8 KV cache enables storing more tokens, "enhancing
throughput".
- https://docs.vllm.ai/en/latest/features/quantization/quantized_kvcache.html


## The decision

**Roughly three quarters off the raw weight figure.** Arithmetic: 16 bit → 4 bit is 1/4 the
bits, a 75% reduction. Real files are larger: the Qwen2.5-Coder-7B f16 file is 15.24 GB and
its Q4_K_M file is 4.68 GB, a 69% reduction.
- https://huggingface.co/bartowski/Qwen2.5-Coder-7B-Instruct-GGUF

**Five and eight bit options.** For the same model: Q5_K_M 5.44 GB, Q8_0 8.10 GB.
- https://huggingface.co/bartowski/Qwen2.5-Coder-7B-Instruct-GGUF
{% endraw %}

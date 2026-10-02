---
layout: default
title: "7 Qwen 3.8 models, and the biggest is not the best"
permalink: /qwen-3-8-models-tier-list/
date: 2026-10-02
---

# 7 Qwen 3.8 models, and the biggest is not the best

{% raw %}
Sources checked on 2 October 2026. Every benchmark figure below is a score Qwen or Alibaba
published about its own models, in its own tables, with its own harnesses. None of them
was measured independently.

## Qwen3.8 27B

- Dense causal language model with a vision encoder; 27B parameters; image and video
  input; native context 262,144 tokens, "extensible up to 1,000,000 tokens".
  [huggingface.co/Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B)
- Text performance table, Coding rows (Qwen3.8-27B · Qwen3.6-27B · Qwen3.7-Plus ·
  Muse Glimmer-30B · Opus4.6 Max):
  - Terminal Bench 2.1 (Terminus): 73.0 · 63.4 · 64.0 · 51.7 · **78.2**
  - SWE-bench Pro: **61.7** · 53.5 · 57.6 · 51.2 · 53.4
  - DeepSWE 1.1: **42.2** · 13.3 · 14.2 · -- · --
- Footnote: "Except for Opus4.6 Max, which uses the officially reported score, all models
  are evaluated with the Claude Code harness at temp=1.0, top_p=0.95, and a 256K context
  window. Problematic tasks were corrected, and all baseline models were re-evaluated on
  the refined benchmark."
- Quantized downloads: Unsloth's GGUF repository lists UD-Q4_K_M at 16.5 GB, Q4_1 at
  17.5 GB and UD-Q4_K_XL at 17.6 GB. Ollama's `qwen3.8:27b` package is listed at 18 GB.
  [huggingface.co/unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) ·
  [ollama.com/library/qwen3.8/tags](https://ollama.com/library/qwen3.8/tags)
- The 2.4T flagship against 27B: 2,400 / 27 = 88.9, so "almost ninety times" the parameters.

## Qwen3.8 Flash Next

- "125B with 6B activated, plus 51B n-gram embedding and 4B MTP"; Gated DeltaNet and Qwen
  Sparse Attention; native context 262,144, extensible to 1,000,000; text, image and
  video input. Hugging Face lists the model size as 180B params.
  [huggingface.co/Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next)
- "a multimodal MoE model that also serves as an early preview of the architecture used
  in Qwen4", carrying forward "the hybrid Gated DeltaNet + Gated Attention design";
  "three out of every four layers use Gated DeltaNet"; N-gram Embedding "performs lookups
  using the local context formed by the current token and several preceding tokens",
  "effectively adding a large-scale local-pattern memory"; the MTP module is trained for
  multi step speculative decoding. Published 26 August 2026.
  [qwen.ai/blog?id=qwen3.8-flash-next](https://qwen.ai/blog?id=qwen3.8-flash-next)
- "Qwen3.8-Flash is the official version based on Qwen3.8-Flash-Next with more production
  features, e.g., 1M context length by default, official built-in tools."
  [huggingface.co/Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next)
- Coding rows (Flash Next · 27B · Qwen3.7-Plus · DeepSeek-V4-Flash-0731 · Claude Opus 4.6
  Max): DeepSWE 1.1 58.7 · 42.2 · 16.5 · 54.4 · --; SWE-bench Pro 62.5 · 61.7 · 55.8 ·
  56.0 · 53.4. Also CoWorkBench 73.9 and NL2Repo-Bench 48.1 for Flash Next.

## Qwen3.8 Max

- Open checkpoint Qwen3.8-2.4T-A95B: "2.4T in total and 95B activated", 512 experts with 10
  routed and 1 shared active; native context 262,144, extensible to 1,010,000; "a text-only
  model that requires thinking mode for all interactions".
  [huggingface.co/Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B)
- "Qwen3.8-Max is the official version based on Qwen3.8-2.4T-A95B with more features, such
  as vision input & non-thinking support, 1M context length by default, official built-in
  tools."
- Full benchmark table (Opus4.8 · Fable5 · GPT5.6 Sol (max) · Qwen3.7-Max · Qwen3.8-Max):
  Terminal Bench 2.1 84.6 · 84.6 · 88.8 · 74.5 · 86.6; SWE-bench Pro 69.2 · 80.0 · 64.6 ·
  60.6 · 67.7; PaperBench 80.3 · 88.8 · 90.5 · 64.8 · 93.0.
  [qwen.ai/blog?id=qwen3.8](https://qwen.ai/blog?id=qwen3.8) (3 August 2026)
- "As of July 30, 2026, after approximately 16 days of fully autonomous AI operation, the
  repository had accumulated 265 commits, 127 PRs, and 151 issues." The project is the
  oh-my-cli command line harness, run by Qwen3.8-Max. Same page.
- Serving recipe: the NVFP4 W4A4 build is 1.32 TiB of weights and fits on 8 B300 GPUs.
  [recipes.vllm.ai/Qwen/Qwen3.8-2.4T-A95B](https://recipes.vllm.ai/Qwen/Qwen3.8-2.4T-A95B)
- NVIDIA DGX B300: eight B300 GPUs in one system.
  [nvidia.com/en-us/data-center/dgx-b300](https://www.nvidia.com/en-us/data-center/dgx-b300/)

## Prices

- Alibaba Cloud Model Studio, per million tokens, 2 October 2026:
  qwen3.8-max, International deployment, $2 input and $6 output;
  qwen3.8-flash, Global deployment, $0.113 input and $0.382 output (International $0.15
  and $0.47). Prices differ by region, deployment scope, batch and caching discounts.
  [alibabacloud.com/help/en/model-studio/model-pricing](https://www.alibabacloud.com/help/en/model-studio/model-pricing)

## Qwen3.8 Omni Flash and Omni Flash Realtime

- "Text, image, audio, and video inputs with a 1M-token context window"; workflows such as
  video editing, translation and building reports from meetings; across 29 evaluations its
  average score improves by more than 25% over Qwen3.5-Omni-Plus.
  [qwen.ai/blog?id=qwen3.8-omni-flash](https://qwen.ai/blog?id=qwen3.8-omni-flash) (18 September 2026)
- UniClawBench 69.6 (Qwen3.5-Omni-Plus 67.1). LVBench 76.9. AndroidWorld: Omni Flash 87.1,
  Flash 84.5, 27B 81.9, Qwen3.7-Plus 81.0, Claude Opus 4.6 (Max) 62.0; 87.1 minus 62.0 is
  25.1 points. ClawEval-MM: pass@3 60.4, average 61.9.
- Text table: SWE-bench Pro Omni Flash 63.3, Flash 62.5, 27B 61.7, Qwen3.7-Plus 55.8,
  DeepSeek-V4-Flash-0731 56.0, Opus 4.6 Max 53.4; DeepSWE 1.1 Omni Flash 57.8, Flash 58.7.
- Realtime: "It perceives and responds while receiving live audio-visual streams";
  "supports connections over WebSocket and WebRTC". Same page.

## Qwen3.8 LiveTranslate

- "Average lagging (LAAL) drops from 2.8 seconds to 2.3 seconds"; an Interleave
  architecture "improving faithfulness, fluency, and conciseness"; real time speaker
  separation; synchronized source and translation output; 60 languages. On FLEURS across
  70 language directions it "leads both the previous generation and current mainstream
  real-time interpretation systems".
  [qwen.ai/blog?id=qwen3.8-livetranslate](https://qwen.ai/blog?id=qwen3.8-livetranslate) (18 September 2026)

## A discrepancy

- The narration says Qwen3.7 Plus scores 78.2 on Terminal Bench 2.1, ahead of 27B's 73.0.
  In Qwen's 27B model card, 78.2 is Claude Opus 4.6 Max's score; Qwen3.7-Plus is listed at
  64.0, below the 27B. The picture shows the table as published.
{% endraw %}

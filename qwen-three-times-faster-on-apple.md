---
layout: default
title: "Qwen is 3x faster on apple, but should you switch?"
permalink: /qwen-three-times-faster-on-apple/
date: 2026-09-29
---

# Qwen is 3x faster on apple, but should you switch?

{% raw %}
Every figure, version, price and benchmark stated in the video, with the primary source it
comes from. Checked 27 to 28 September 2026.

## Splash and Inco AI

- **Splash** is an open source local inference engine for Apple silicon from **Inco AI**,
  announced 17 September 2026. It "combines DFlash 2 speculative decoding, specialized Metal
  kernels, and automatic memory planning".
  [Inco AI, "Splash: A Local Engine Built Around the Model"](https://inco.ai/blog/splash/) ·
  [github.com/incoai/splash](https://github.com/incoai/splash)
- **The three times figure is against Ollama.** On Qwen3.8-27B with short prompts, Inco's
  Figure 2 reports 74 tokens per second for Splash, 38 for oMLX and 24 for Ollama: 74 ÷ 24 is
  3.1 times Ollama, and 74 ÷ 38 is 1.9 times oMLX. Inco's own headline is "2× the decode speed
  of the next-fastest engine", and its launch post on X reads "Up to 3× the decode speed of
  Ollama, 2× oMLX". [Inco AI launch post, Figure 2](https://inco.ai/blog/splash/) ·
  [README, Performance](https://github.com/incoai/splash#performance) ·
  [Inco AI on X](https://x.com/inco_ai/status/2101100749623341513)
- **Test setup:** "All engines ran on the same 48 GB M5 Pro ... The prompts are a fixed set of
  coding tasks from NVIDIA's SPEED-Bench, up to 32K tokens, with a 1,024-token output limit.
  Reasoning was on for both models, the 27B at its medium level, and decode figures include
  reasoning tokens." The README gives the machine as "M5 Pro (16-core GPU, 48 GB)".
  [Inco AI launch post](https://inco.ai/blog/splash/) ·
  [docs/performance.md](https://github.com/incoai/splash/blob/main/docs/performance.md)
- **Time to first token, Qwen3.8-27B, 32K prompt:** 96 seconds uncached; 282 milliseconds on
  an exact replay with the prompt cached (oMLX: 2,049 ms on the same replay). Inco notes the
  replay "isolates the cached path. A real agent turn appends new tokens to the prefix and pays
  for those as well."
  [Inco AI launch post, Figure 4](https://inco.ai/blog/splash/) ·
  [incoai/Qwen3.8-27B-Splash, Performance](https://huggingface.co/incoai/Qwen3.8-27B-Splash)
- **Four concurrent short prompts, Qwen3.8-27B:** 170 tokens per second combined for Splash,
  43 for oMLX, "timed from the first streamed token to the last across all four requests".
  Per request figures are not reported. [Inco AI launch post, Figure 5](https://inco.ai/blog/splash/)
- **Kernels and weights:** "Each gets its own 4-bit matrix multiplication and attention
  kernels, written for that workload and for the model's exact dimensions ... Everything ships
  precompiled." Weight preparation "reorders an MLX target's codes, scales and biases into
  256-row tiles without requantization" and "repacks GGUF blocks".
  [Inco AI launch post](https://inco.ai/blog/splash/) ·
  [DEVELOPMENT.md, Weight preparation](https://github.com/incoai/splash/blob/main/DEVELOPMENT.md)
- **API:** "OpenAI Chat Completions and Responses, and Anthropic Messages, with streaming, tool
  calls, JSON Schema output, images, and inline PDFs."
  [README, Use the API](https://github.com/incoai/splash#use-the-api)
- **Batching and cache:** "Splash batches requests as they arrive ... a request that shares a
  prefix with an earlier one reuses those pages instead of recomputing them."
  [Inco AI launch post, Scheduling and Memory](https://inco.ai/blog/splash/)
- **Hardware support:** "Apple M3 or newer, macOS 26.4 or later ... The 4-bit examples need at
  least 36 GB of unified memory (48 GB recommended); 24 GB Macs can use smaller GGUF variants."
  Smaller variants were measured separately, on a 24 GB M6 (12-core GPU).
  [README, Quick start](https://github.com/incoai/splash#quick-start) ·
  [docs/performance.md, Smaller GGUFs on 24 GB Macs](https://github.com/incoai/splash/blob/main/docs/performance.md)
- **Package size:** the incoai/Qwen3.8-27B-Splash package lists 14.1 GiB for the 4-bit target,
  1.2 GiB for the DFlash 2 draft and 0.9 GiB for the vision encoder, 16.2 GiB in all.
  [incoai/Qwen3.8-27B-Splash](https://huggingface.co/incoai/Qwen3.8-27B-Splash)
- **Supported models now:** Unsloth GGUF variants from 1 to 8 bits, MLX 4-bit checkpoints, and
  Prism ML Ternary Bonsai 2. At launch Splash shipped "two supported models" as prepared
  packages. [README, Models](https://github.com/incoai/splash#models) ·
  [Inco AI launch post, The Bottom Line](https://inco.ai/blog/splash/)
- **LM Studio:** LM Studio Bionic 1.1.5 or newer lists "Splash (Metal)" under Settings ·
  Runtime · Experimental backends; the Splash models are then picked from the model list.
  [LM Studio, "Splash Engine"](https://lmstudio.ai/blog/splash-engine)

## Speculative decoding and DFlash

- **DFlash:** Chen, Liang and Liu, "DFlash: Block Diffusion for Flash Speculative Decoding",
  a lightweight block diffusion draft that generates the draft tokens "in a single forward
  pass". [arXiv:2602.06036](https://arxiv.org/abs/2602.06036)
- **DFlash 2:** "DFlash predicts every position independently ... nothing makes them fit
  together ... DFlash 2 keeps each position's top candidates, and the selector traces one
  coherent path through them." [Inco AI, "DFlash 2: Keep Drafting Parallel"](https://inco.ai/blog/dflash2/)
- **Other engines run DFlash drafts:** "DFlash draft models run in SGLang, vLLM, TensorRT-LLM,
  and llama.cpp." [Inco AI launch post, The Bottom Line](https://inco.ai/blog/splash/)

## The models

- **Qwen3.8-27B, Terminal Bench 2.1 (Terminus):** 73.0, against 51.7 for Muse Glimmer-30B and
  78.2 for Opus4.6 Max, in Qwen's own Text Performance table.
  [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B)
- **Qwen3.6-35B-A3B:** "Number of Parameters: 35B in total and 3B activated."
  [Qwen/Qwen3.6-35B-A3B model card](https://huggingface.co/Qwen/Qwen3.6-35B-A3B)
- **Muse Glimmer:** "a 30-billion-parameter causal language model", from Meta Superintelligence
  Lab, Apache 2.0. [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B)
- **Gemma 4:** a local model family that "processes text, image ... (all models)".
  [Gemma 4 model overview](https://ai.google.dev/gemma/docs/core)

## The other engines

- **oMLX:** "LLM inference, optimized for your Mac. Continuous batching and tiered KV caching";
  multi-model serving. Its experimental DFlash integration lists draft checkpoints for Gemma 4
  and Muse Glimmer-30B as well as Qwen.
  [github.com/jundot/omlx](https://github.com/jundot/omlx) ·
  [DFlash-MLX integration report](https://github.com/jundot/omlx/blob/main/docs/experimental/dflash_mlx_integration.md)
- **Ollama:** downloads for macOS, Windows and Linux; a public model library.
  [github.com/ollama/ollama](https://github.com/ollama/ollama) · [ollama.com/library](https://ollama.com/library)
- **Lily (Perplexity):** "A small Metal inference server for one checkpoint: Qwen3.6-35B-A3B."
  Perplexity reports it averages 1.35 times MLX-LM's decode throughput (170.0 against 126.4
  tokens per second) across ten context lengths from 256 to 128K, measured on an M5 Max with a
  40-core GPU and 128 GB. That comparison uses a different model, machine and baseline from
  Inco's charts. [Lily README](https://github.com/perplexityai/pplx-garden/tree/main/lily) ·
  [Perplexity, "Optimizing on-device inference for Apple silicon"](https://www.perplexity.ai/hub/blog/optimizing-on-device-inference-for-apple-silicon)

## The machine

- **Price:** "The 14-inch MacBook Pro with M5 Pro starts at $2,199 (U.S.)", announced 3 March
  2026. [Apple Newsroom](https://www.apple.com/newsroom/2026/03/apple-introduces-macbook-pro-with-all-new-m5-pro-and-m5-max/)
- **Memory:** the M5 Pro 14-inch starts at 24 GB of unified memory, configurable to 48 GB; the
  base M5 Pro has a 16-core GPU. [MacBook Pro tech specs](https://www.apple.com/macbook-pro/specs/)

## Arithmetic in the video

- 1,000 generated tokens at 74 tokens per second is 13.5 seconds; at 24 it is 41.7 seconds.
- 170 ÷ 43 = 3.95, reported by Inco as 3.9 times.
{% endraw %}

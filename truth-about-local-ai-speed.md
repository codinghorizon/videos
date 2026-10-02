---
layout: default
title: "Local AI Hit 150 Tok/s. So Why Does It Still Feel Slow?"
permalink: /truth-about-local-ai-speed/
date: 2026-10-02
---

# Local AI Hit 150 Tok/s. So Why Does It Still Feel Slow?

{% raw %}
Every figure this video states, and where it comes from. Pages were checked on 2 October 2026.

## RTX 4090, Llama 3 8B, about 150 tokens per second

- NVIDIA Technical Blog, "Accelerating LLMs with llama.cpp on NVIDIA RTX Systems", 2 October 2024.
  https://developer.nvidia.com/blog/accelerating-llms-with-llama-cpp-on-nvidia-rtx-systems/
  - "On the NVIDIA RTX 4090 GPU, users can expect ~150 tokens per second, with an input sequence length of 100 tokens and an output sequence length of 100 tokens."
  - The figure is described as "NVIDIA internal measurements" of a Llama 3 8B model on llama.cpp (Figure 1).
  - NVIDIA lists its llama.cpp contributions as "Implementing CUDA Graphs in llama.cpp to reduce overheads and gaps between kernel execution times to generate tokens" and "Reducing CPU overheads when preparing ggml graphs."
  - The body text does not say in so many words that the 150 figure was measured on the build with those changes; the page's summary box makes that connection.

## Arc B580, Qwen3 8B, prompt and generation rates

- llama.cpp discussion #12570, "Current status of Intel Arc GPUs for llama.cpp", comment by KenBlasse, 13 July 2026: "Arc B580 (Battlemage / BMG G21) — Vulkan status report + Qwen3-8B numbers". A community report, not an Intel or llama.cpp result.
  https://github.com/ggml-org/llama.cpp/discussions/12570
  - Setup: Intel Arc B580, 12 GB; Mesa (ANV) 25.0.7, Vulkan 1.4; llama.cpp master 6eddde0 built with `-DGGML_VULKAN=ON`; `llama-bench -fa 1 -p 512 -n 128 -r 3`; Qwen3-8B from the official Qwen/Qwen3-8B-GGUF.
  - Qwen3-8B Q4_K_M, 4.68 GiB: pp512 504.72 ± 3.54 t/s; tg128 30.39 ± 0.35 t/s.
  - Qwen3-8B Q8_0, 8.11 GiB: pp512 517.55 ± 4.01 t/s; tg128 14.03 ± 0.01 t/s.
  - The prompt (pp512) and generation (tg128) figures are separate tests, as the video says.

## Prompt processing and generation, as the tools name them

- llama.cpp, `tools/llama-bench/README.md`: "Prompt processing (pp): processing a prompt in batches (`-p`)" and "Text generation (tg): generating a sequence of tokens (`-n`)".
  https://github.com/ggml-org/llama.cpp/blob/master/tools/llama-bench/README.md
- Ollama, `docs/api.md`: the response reports `load_duration` ("time spent in nanoseconds loading the model"), `prompt_eval_count`, `prompt_eval_duration` ("time spent in nanoseconds evaluating uncached prompt tokens"), `eval_count`, `eval_duration` ("time in nanoseconds spent generating the response") and `total_duration`.
  https://github.com/ollama/ollama/blob/main/docs/api.md

## Memory bandwidth and capacity

- Intel Arc B580 specifications: Memory 12 GB GDDR6; Graphics Memory Interface 192 bit; Graphics Memory Bandwidth 456 GB/s.
  https://www.intel.com/content/www/us/en/products/sku/241598/intel-arc-b580-graphics/specifications.html
- NVIDIA Ada GPU Architecture whitepaper (v2.02), specification table: GeForce RTX 4090 memory bandwidth 1008 GB/sec.
  https://images.nvidia.com/aem-dam/Solutions/geforce/ada/nvidia-ada-gpu-architecture.pdf
- NVIDIA GeForce RTX 4090 product page: 24 GB GDDR6X, 384-bit memory interface.
  https://www.nvidia.com/en-us/geforce/graphics-cards/40-series/rtx-4090/
- 1,008 ÷ 456 = 2.21, the "about 2.2 times" gap on paper.
- NVIDIA GeForce RTX 5060 family page: RTX 5060 Ti with 16 GB or 8 GB GDDR7, 128-bit.
  https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5060-family/

## Qwen3.5

- Qwen3.5-9B model card: "Context Length: 262,144 natively and extensible up to 1,010,000 tokens"; "Qwen3.5 models operate in thinking mode by default"; image input examples; a "Reasoning & Coding" evaluation table including LiveCodeBench v6 and OJBench; serving examples with `--reasoning-parser qwen3` and tool calling via `--tool-call-parser qwen3_coder`.
  https://huggingface.co/Qwen/Qwen3.5-9B
- Qwen3.5-4B and Qwen3.5-27B model cards exist with the same native context.
  https://huggingface.co/Qwen/Qwen3.5-4B · https://huggingface.co/Qwen/Qwen3.5-27B
- Ollama library, qwen3.5: 4b 3.4GB, 9b 6.6GB (also `latest`), 27b 17GB, all listed at 256K context with text and image input.
  https://ollama.com/library/qwen3.5/tags

## Ministral 3 8B

- Mistral AI, Ministral-3-8B-Instruct-2512 model card: "Supports a 256k context window"; "Vision: Enables the model to analyze images"; "Ministral 3 8B can even be deployed locally, capable of fitting in 12GB of VRAM in FP8, and less if further quantized."
  https://huggingface.co/mistralai/Ministral-3-8B-Instruct-2512

## Speculative decoding

- llama.cpp, `docs/speculative.md`: "A much smaller model (called the _draft model_) generates drafts. A draft model is the most used approach in speculative decoding."
  https://github.com/ggml-org/llama.cpp/blob/master/docs/speculative.md

## Arithmetic in the video

These follow from the figures above or from the video's own stated examples:

- 100 tokens at 150 tok/s = 0.67 s; 1,000 tokens at 150 tok/s = 6.7 s.
- 1,500 tokens at 150 tok/s = 10 s; at 30 tok/s = 50 s, five times longer.
- 1,000 prompt tokens at 1,000 tok/s = 1 s; 200 tokens at 50 tok/s = 4 s. The ratio of those two rates is 20 to 1.
- 512 tokens at 504.72 tok/s = 1.01 s; 128 tokens at 30.39 tok/s = 4.21 s; together about 5.2 s, as an illustration only, because the two rates come from separate tests.
- 120 tokens at 30 tok/s = 4 s; 2,000 tokens at 30 tok/s = 67 s.
- 9 billion weights at 4 bits = 4.5 GB.
- 100 tok/s shared evenly by four replies = 25 tok/s each.
{% endraw %}

---
layout: default
title: "128GB Local AI Has One Model That Makes It Worth It"
permalink: /best-local-ai-128gb-vram/
date: 2026-10-04
---

# 128GB Local AI Has One Model That Makes It Worth It

{% raw %}
Every figure the video states or shows, with where it comes from. Pages were read on 4 October 2026.

## The community benchmark (Strix Halo, 128 GB)

visorcraft, strix-halo-llm-perf, BENCHMARKS.md. All tests on a GMKtec EVO-X2 with a Ryzen AI Max+ 395 and 128 GB of LPDDR5X-8000, llama.cpp with the Vulkan RADV backend, 120 W.
https://github.com/visorcraft/strix-halo-llm-perf/blob/main/BENCHMARKS.md

- Qwen3-235B-A22B, Q3_K_M: 104.72 GiB package, 17.21 tokens per second generation on Vulkan RADV (14.32 on ROCm 7.2 HIP). The page calls it "the largest model we can fit in 128 GB", leaving about 18 GB for KV cache and the OS, with 121 to 122 GB used of 123 GB and a 32K context in its summary table.
- GPT-OSS 120B, Q4_K_M: 58.5 GiB, 53.4 tokens per second in llama-server, 131K context. The page notes the run used a shorter generation than the llama-bench rows.
- Qwen3-Coder-Next 80B-A3B, Q4_K_M: 45.17 GiB, 42.70 tokens per second (tg128), 531 tokens per second prompt processing (pp512); 39.5 tokens per second on ROCm HIP.
- Llama 3.1 70B, Q4_K_M: 39.59 GiB, 5.10 tokens per second at 120 W (5.06 at 85 W).

## The models

- GPT-OSS 120B: about 117B total parameters and 5.1B active per token, open weight, Apache 2.0 licence, 128K context.
  https://huggingface.co/openai/gpt-oss-120b
  https://arxiv.org/abs/2508.10925
- Qwen3-235B-A22B: 235B total, 22B activated, 128 experts with 8 activated, 32,768 tokens of context natively and 131,072 with YaRN.
  https://huggingface.co/Qwen/Qwen3-235B-A22B
- Qwen3-Coder-Next: 80B total, 3B activated, built for coding agents and local development, 256K context; its card carries Qwen's own coding agent benchmark chart.
  https://huggingface.co/Qwen/Qwen3-Coder-Next
- Llama 3.1 70B: a dense model with 128K context.
  https://huggingface.co/meta-llama/Llama-3.1-70B

## The napkin floor

Four bit weights are about half a byte per parameter: 70B is about 35 GB, 120B about 60 GB, 235B about 118 GB, before quantization overhead, the context cache and the runtime. This is arithmetic, not a measured file size; the measured packages above are what the video uses for fit. The narration says "forty bit estimate" in chapter one; the estimate it refers to is the four bit one.

## The machines

- AMD Ryzen AI Max+ 395 (Strix Halo): memory bandwidth 256 GB/s, 128 GB LPDDR5X in the Ryzen AI Halo developer platform.
  https://www.amd.com/en/products/processors/desktops/ryzen/ryzen-ai-halo/ryzen-ai-max-plus-395.html
- AMD says up to 96 GB of a 128 GB system can be assigned to graphics.
  https://www.amd.com/en/blogs/2025/amd-ryzen-ai-max-395-processor-breakthrough-ai-.html
- Mac Studio with M5 Max: configurable to 128 GB of unified memory and 614 GB/s of memory bandwidth; the base Mac Studio starts at $2,499 with 36 GB.
  https://www.apple.com/mac-studio/specs/
- MLX, Apple's array framework for Apple silicon, built around unified memory.
  https://github.com/ml-explore/mlx
- Nvidia DGX Spark: 128 GB of LPDDR5x unified memory, 273 GB/s.
  https://www.nvidia.com/en-us/products/workstations/dgx-spark/
- Framework Desktop: Ryzen AI Max+ 395 with 128 GB LPDDR5x-8000.
  https://frame.work/desktop?tab=specs

## Prices

- AMD Ryzen AI Halo developer platform: $3,999 in the United States (Tom's Hardware, 13 June 2026).
  https://www.tomshardware.com/desktops/mini-pcs/amd-challenges-nvidias-dgx-spark-with-usd3-999-ryzen-ai-halo-with-windows-11-support-strix-halo-desktop-undercuts-nvidia-by-usd700-packs-128gb-of-unified-memory
- GMKtec EVO-X3, 128 GB and 2 TB: $3,600 at launch (Liliputing, 6 July 2026); later listed at $3,799.99 on GMKtec's store.
  https://liliputing.com/gmk-evo-x3-with-ryzen-ai-max-395-and-128gb-ram-now-available-for-3600-and-up/

## The independent comparison

Tom's Hardware tested a 128 GB M4 Max Mac Studio against Nvidia GB10 and Strix Halo (30 July 2026). The M4 Max has 546 GB/s against 273 GB/s for GB10 and 256 GB/s for Strix Halo, led on decode throughput, and generated 27% to 82% more tokens per second than GB10 depending on the model: well short of what the bandwidth ratio alone would suggest.
https://www.tomshardware.com/desktops/exploring-apple-silicons-local-ai-performance-with-the-mac-studio-and-m4-max-m4-max-beats-gb10-and-strix-halo-in-decode-throughput-but-memory-bandwidth-isnt-everything

## Arithmetic in the video

- 300 tokens at 5.06 tokens per second is about 59 seconds; at 42.7 tokens per second it is about 7 seconds. Generation only, before prompt processing.
- Free memory on the fit map is 128 GB less the measured package, and where a context cache is drawn it is labelled as illustrative except for the 235B case, which uses the benchmark's own figure of 121 to 122 GB used.
{% endraw %}

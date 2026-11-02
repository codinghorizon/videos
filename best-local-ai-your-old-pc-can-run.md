---
layout: default
title: "The Best Local AI Your Old PC Can Run"
permalink: /best-local-ai-your-old-pc-can-run/
date: 2026-11-02
---

# The Best Local AI Your Old PC Can Run

{% raw %}
Every figure the shots put on screen, with the page it comes from. Prices were read on
2026-11-01 (PRICES.md). Speeds are other people's published runs; we ran nothing ourselves.

## Why an old PC can run AI: memory speed sets the ceiling

- **2.74 GB**: Qwen3.5 4B at 4 bits (Q4_K_M), Unsloth's GGUF file list.
  https://huggingface.co/unsloth/Qwen3.5-4B-GGUF
- **25.6 GB/s**: Core i5-5200U (Q1 2015), two channels of DDR3L-1600, Intel ARK.
  https://www.intel.com/content/www/us/en/products/sku/85212/intel-core-i55200u-processor-3m-cache-up-to-2-70-ghz/specifications.html
- **9.3 tok/s ceiling**: our arithmetic, 25.6 / 2.74 = 9.34. A ceiling, not a measured speed.
- **A token is about three quarters of a word, ~7 words a second**: 9.3 x 0.75 = 7.0, our arithmetic.
- **19x**: GTX 1080 Ti memory bandwidth 484 GB/s (Wikipedia, GeForce 10 series) / 25.6 = 18.9.
  https://en.wikipedia.org/wiki/GeForce_10_series

## 2015 laptop

- **AVX2 on the 5th gen Core i5**: Intel ARK above. **LM Studio requires AVX2 on x64**:
  https://lmstudio.ai/docs/app/system-requirements
- **Gemma 4 E2B at 9.9 tok/s on an i5 laptop with 12 GB, in Ollama**: It's FOSS.
  https://itsfoss.com/testing-local-llms-without-gpu
- **Qwen3.5 4B at 4 bits under 3 GB**: Unsloth, as above (2.74 GB).

## 2017 office desktop

- **7th gen Core i5, DDR4-2400**: Core i5-7500, Intel ARK. "Half again as quick" is 38.4 GB/s
  (our arithmetic for two channels of DDR4-2400) against 25.6 GB/s.
  https://www.intel.com/content/www/us/en/products/sku/97123/intel-core-i57500-processor-6m-cache-up-to-3-80-ghz/specifications.html
- **Qwen3.5 9B at 4 bits under 6 GB**: Unsloth. https://huggingface.co/unsloth/Qwen3.5-9B-GGUF
- **6.8 tok/s ceiling**: our arithmetic, 38.4 / 5.68.
- **Qwen3 4B at 10 tok/s on a Core i5-8500T (DDR4-2666)**: r/LocalLLaMA.
  https://reddit.com/r/LocalLLaMA/comments/1rznt50/running_local_llm_on_i3_4th_gen_cpu/
- **Qwen3.6 35B-A3B is a 22 GB file at Q4_K_M**: Unsloth. https://huggingface.co/unsloth/Qwen3.6-35B-A3B-GGUF

## A viewer's question

- **Core i5-3450 is Ivy Bridge (2012), AVX but no AVX2** (AVX2 arrived with Haswell):
  https://en.wikipedia.org/wiki/Ivy_Bridge_(microarchitecture)
- **Ollama ships plain cpu, cpu_avx and cpu_avx2 builds**: https://docs.ollama.com/troubleshooting

## GTX 970

- **Released September 2014, 4 GB with 3.5 GB fast**: Wikipedia, GeForce 900 series.
  https://en.wikipedia.org/wiki/GeForce_900_series
- **Gemma 4 E2B (Google's QAT Q4_0) at 47.6 tok/s in llama.cpp CUDA**: ai-muninn, June 2026.
  https://ai-muninn.com/en/blog/gtx-970-gemma4-e2b-quantization-benchmark
- **$44 used**: https://resaleprices.com/gpu/nvidia-gtx-970
- **The scoreboard's standard model (Llama 2 7B Q4_0) only ran on the 970 at Q3_K_S**:
  https://github.com/ggml-org/llama.cpp/discussions/15013

## Driver 580 and CUDA 13

- **580 is the last driver branch for Maxwell and Pascal**: NVIDIA forums.
  https://forums.developer.nvidia.com/t/unix-graphics-feature-deprecation-schedule/60588
- **CUDA 13 drops Maxwell, Pascal and Volta**: https://docs.nvidia.com/cuda/cuda-features-archive/index.html
  and https://developer.nvidia.com/blog/navigating-gpu-architecture-support-a-guide-for-nvidia-cuda-developers
- **Ollama supports compute capability 5.0+, needs driver 570+ for 5.0 to 6.2; Vulkan**: https://docs.ollama.com/gpu
- **llama.cpp releases ship CUDA 12 and Vulkan builds**: https://github.com/ggml-org/llama.cpp/releases
- **Security updates through October 2028**, as Nvidia told Windows Central:
  https://www.windowscentral.com/hardware/nvidia/nvidia-end-of-life-pascal-maxwell-volta-windows-10
  (also Tom's Hardware: https://www.tomshardware.com/pc-components/gpu-drivers/nvidia-to-axe-maxwell-pascal-and-volta-gpus-with-end-of-driver-support-580-series-drivers-will-be-the-last-to-support-gtx-900-and-1000-cards)

## GTX 1070 and GTX 1080

- **Qwen3.5 9B Q4_K_M at 35.7 tok/s on a GTX 1080 in Ollama**: llm-bench. https://llm-bench.io/hardware/gtx-1080
- **Qwen3.6 35B-A3B at 24 tok/s on a GTX 1080, 128K context, --n-cpu-moe 30, 32 GB RAM, a tuned fork**:
  r/LocalLLaMA. https://reddit.com/r/LocalLLaMA/comments/1tcc7h5
- **$91 (1070) and $114 (1080) used**: https://resaleprices.com/gpu/nvidia-gtx-1070 and
  https://resaleprices.com/gpu/nvidia-gtx-1080

## RX 580

- **ROCm does not list the RX 580**: Ollama's ROCm card list, https://docs.ollama.com/gpu
- **Vulkan scoreboard, same test: RX 580 39.32, GTX 1070 41.48 tok/s** (2.16 behind):
  https://github.com/ggml-org/llama.cpp/discussions/10879
- **Qwen3.5 4B at about 16 tok/s on Vulkan, one owner**: https://reddit.com/r/LocalLLaMA/comments/1rtab9m
- **$77 used; 77 / 8 = $9.63 a GB**: https://resaleprices.com/gpu/amd-rx-580-8gb
- **More than twice the speed on Linux (about 35 tok/s) as on Windows (15 to 17)**:
  https://github.com/aivisionslab-studios/rx580-local-ai-guide

## GTX 1080 Ti

- **March 2017, 11 GB**: Wikipedia, GeForce 10 series.
- **$176 (1080 Ti) and $423 (RTX 3080 10GB) used; $16 and $42 a GB**: ResalePrices.
  https://resaleprices.com/gpu/nvidia-gtx-1080-ti and https://resaleprices.com/gpu/nvidia-rtx-3080
- **Gemma 4 12B at 4 bits is a 7 GB file**: Unsloth. https://huggingface.co/unsloth/gemma-4-12b-it-GGUF
- **Qwen3.6 35B-A3B at 16.8 tok/s on one 1080 Ti in plain Ollama 0.30.2**: dev.to.
  https://dev.to/sysoft/running-a-35b-moe-qwen36-35b-a3b-on-2x-gtx-1080-ti-in-2026-real-benchmarks-and-does-the-56on

## RTX 2070 Super

- **Turing, still supported by CUDA 13**: NVIDIA's CUDA 13 notes above.
- **41% faster than the 1080 Ti** on the llama.cpp CUDA scoreboard: 88.06 against 62.49 tok/s.
  https://github.com/ggml-org/llama.cpp/discussions/15013
- **Qwen3.5 9B at 55 tok/s in Ollama with a 116K context**: llm-bench. https://llm-bench.io/hardware/rtx-2070-super
- **$199 used**: https://resaleprices.com/gpu/nvidia-rtx-2070-super. **$2.26 and $2.82 per tok/s**:
  199 / 88.06 and 176 / 62.49, our arithmetic on the scoreboard speeds.

## RTX 3080 and RTX 3090

- **"I have a 3080 at 10G. I'm so sad."**: a viewer comment under one of our videos, found at verify.
- **More than double the 1080 Ti**: 139.65 against 62.49 tok/s on the CUDA scoreboard.
- **RTX 3070 8GB, Qwen3.6 35B-A3B at 27 tok/s with --n-cpu-moe 27, 32 GB RAM**: llamaperf.
  https://llamaperf.com/report/4625fcbf-c1e0-43a5-a14f-8d6512eba63d
- **$3.03 per tok/s**: 423 / 139.65, our arithmetic.
- **RTX 3090, Qwen 3.8 27B fully on the card at 40.9 tok/s**: llamaperf. https://llamaperf.com/gpu/rtx-3090
- **$1,796 used**: https://rigprice.com/gpu/rtx-3090/ (launch price $1,499).

## The RAM upgrade

- **32 GB (2x16GB) DDR4-3200 at $249.99 on Newegg, late October**:
  https://www.newegg.com/p/pl?d=32gb+ddr4+3200+2x16gb+desktop&Order=1

### Not checked

- The Newegg $249.99 was read in late October; Newegg refused automated reads on 2026-11-01, so
  it was not re-read on the day of recording.
- The laptop and office desktop speeds are from different apps and files than the card runs,
  so the 47.6 against 9.9 comparison is not a like for like test (the narration says so).
- The "10 tok/s" office desktop run is an 8th gen Core i5, one generation newer than the
  desktop the chapter describes (the narration says "from the year after").
- No clean RTX 3080 run on the 35B model was found (the narration says so).
{% endraw %}

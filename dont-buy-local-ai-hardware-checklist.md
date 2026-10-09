---
layout: default
title: "The RTX 3090 Trap That Costs Local AI Buyers $1,600"
permalink: /dont-buy-local-ai-hardware-checklist/
date: 2026-10-09
---

# The RTX 3090 Trap That Costs Local AI Buyers $1,600

{% raw %}
Every figure the video puts on screen, with its primary source. Prices are US prices checked on 9 October 2026.

## Prices

| figure | what | source |
|---|---|---|
| about $1,600 | Used RTX 3090 24GB, going rate (median of 84 screened eBay asking prices, range $1,550 to $1,799; $1,623 on 9 Oct 2026). Asking prices, not completed sales. | [RigPrice RTX 3090](https://rigprice.com/gpu/rtx-3090/) |
| about $3,200 | Two used RTX 3090s at about $1,600 each (1,600 × 2) | derived |
| $8,422 | MSI RTX 5090 32G Ventus 3X OC on Newegg ($8,419.00 main offer and $8,420.00 from a second seller on 9 Oct 2026; $8,422 on 7 Oct) | [Newegg listing](https://www.newegg.com/p/N82E16814137920) |
| $3,499.99 | GMKtec EVO-X2, Ryzen AI Max+ 395 (Strix Halo), 128GB RAM + 1TB SSD, US | [GMKtec EVO-X2](https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc) |
| $5,499 | Mac Studio with M5 Ultra (30-core CPU, 64-core GPU), 96GB unified memory, 1TB, the 96GB starting configuration | [Apple Store, Mac Studio](https://www.apple.com/shop/buy-mac/mac-studio) |

## Our calculations

| figure | formula |
|---|---|
| about $38 per token per second, used RTX 3090 | $1,600 ÷ 41.93 tok/s = $38.16 |
| about $111 per token per second, RTX 5090 listing | $8,422 ÷ 75.74 tok/s = $111.20 |
| about $92 a year, RTX 3090 | 0.350 kW × 4 h × 365 days × $0.18 per kWh = $91.98 |
| about $151 a year, RTX 5090 | 0.575 kW × 4 h × 365 days × $0.18 per kWh = $151.11 |
| about 1.8 times faster | 75.74 ÷ 41.93 = 1.81 |

The power estimate uses each card's rated board power at full load for four hours a day; real inference draw varies, and the rest of the system adds to it.

## Memory capacity

- RTX 3090: 24GB GDDR6X. RTX 5090: 32GB GDDR7. [NVIDIA RTX 3090](https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090/), [NVIDIA RTX 5090](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/)
- Mac Studio: up to 512GB unified memory with M5 Ultra; M5 Max up to 128GB. [Apple Mac Studio specs](https://www.apple.com/mac-studio/specs/)
- DGX Spark: 128GB of coherent unified system memory. [NVIDIA developer blog](https://developer.nvidia.com/blog/how-nvidia-dgx-sparks-performance-enables-intensive-ai-tasks)
- Ryzen AI Max+ 395 (Strix Halo): up to 128GB unified LPDDR5X. [AMD](https://www.amd.com/en/products/processors/desktops/ryzen/ryzen-ai-halo/ryzen-ai-max-plus-395.html)
- A 70 billion parameter model at about 4 bits per weight needs roughly 35 to 40GB for the weights alone (70e9 × ~4 to 4.5 bits ÷ 8), before the context cache and the runtime.

## Memory bandwidth

| machine | bandwidth | source |
|---|---|---|
| RTX 3090 | 936 GB/s | [TechPowerUp RTX 3090](https://www.techpowerup.com/gpu-specs/geforce-rtx-3090.c3622) |
| RTX 5090 | 1,792 GB/s | [TechPowerUp RTX 5090](https://www.techpowerup.com/gpu-specs/geforce-rtx-5090.c4216) |
| Strix Halo (Ryzen AI Max+ 395) | 256 GB/s (256-bit LPDDR5X-8000) | [AMD](https://www.amd.com/en/products/processors/desktops/ryzen/ryzen-ai-halo/ryzen-ai-max-plus-395.html) |
| DGX Spark | 273 GB/s | [NVIDIA developer blog](https://developer.nvidia.com/blog/how-nvidia-dgx-sparks-performance-enables-intensive-ai-tasks) |
| Mac Studio, M4 Max (40-core GPU) | 546 GB/s | [Apple, Mac Studio (2025) tech specs](https://support.apple.com/en-us/122211) |

## Published speed results

- Qwen 3.8 27B Q4_K_M, llama.cpp llama-bench, 512 token prompt, 128 generated tokens, full GPU offload, three runs after a warmup: RTX 3090 41.93 tok/s, RTX 5090 75.74 tok/s. [GPU Battle](https://gpubattle.com/guides/qwen3-8-27b-gpu-benchmarks) (updated October 2026)
- DGX Spark: Qwen3 235B in NVFP4 on TRT-LLM, two DGX Spark systems linked through ConnectX-7, input 2,048 tokens, output 128, batch 1: 11.73 tok/s decode. [NVIDIA developer blog](https://developer.nvidia.com/blog/how-nvidia-dgx-sparks-performance-enables-intensive-ai-tasks)
- Strix Halo, GPT-OSS 120B MXFP4, llama.cpp tg128: 51.0 to 56.6 tok/s across ROCm and Vulkan builds in the AMD Strix Halo Toolboxes project's results. The video quotes 53.7 to 53.8 tok/s from published results, which sits inside that range. [kyuz0 AMD Strix Halo Toolboxes](https://kyuz0.github.io/amd-strix-halo-toolboxes/)
- Prompt processing (reading the input) and token generation (writing the reply) are reported separately by llama-bench (pp and tg); prompt rates are many times the generation rates on the same hardware.

## Power

- RTX 5090: 575 W total graphics power; 1000 W required system power. [NVIDIA RTX 5090](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/)
- RTX 3090: 350 W graphics card power. [NVIDIA RTX 3090](https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090/)
- Ryzen AI Max+ 395: configurable TDP of 45 to 120 W; mini PCs built on it run the chip above 100 W under sustained load. [AMD](https://www.amd.com/en/products/processors/desktops/ryzen/ryzen-ai-halo/ryzen-ai-max-plus-395.html)

## Software backends

- llama.cpp documents CUDA for NVIDIA GPUs, HIP for AMD GPUs, SYCL for Intel GPUs, Metal for Apple Silicon, plus Vulkan and others. [llama.cpp README](https://github.com/ggml-org/llama.cpp/blob/master/README.md), [build docs](https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md)
- OpenVINO is Intel's inference toolkit for Intel CPUs, GPUs and NPUs. [OpenVINO](https://github.com/openvinotoolkit/openvino)
- MLX is Apple's array framework designed for Apple Silicon and its unified memory. [MLX](https://github.com/ml-explore/mlx)

## Cloud rental

- Hourly GPU rental for short tests. [Vast.ai](https://vast.ai/), [RunPod pricing](https://www.runpod.io/gpu-instance/pricing)

## Not checked

- The exact 53.7 to 53.8 tok/s Strix Halo figure for GPT-OSS 120B MXFP4 was not located; the closest primary results (kyuz0 toolboxes, tg128) span 51.0 to 56.6 tok/s by backend.
- "Over one hundred watts in published testing" for Strix Halo rests on reviews of specific mini PCs, not on one cited test.
- Mac Studio M5 Ultra is listed by Apple as "coming late October"; the $5,499 price is Apple's listed price, not a shipping unit.
- Resale prices next year are not knowable; RigPrice reports asks, not completed sales.
{% endraw %}

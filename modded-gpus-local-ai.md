---
layout: default
title: "RTX 4090 48GB Mods Have One Expensive Catch For Buyers"
permalink: /modded-gpus-local-ai/
date: 2026-10-08
---

# RTX 4090 48GB Mods Have One Expensive Catch For Buyers

{% raw %}
Every figure the video puts on screen, with its source. Prices were checked on 2026-10-07 and are US asking prices, not completed sales.

## Prices and price per gigabyte

- **Used RTX 3090 24GB: $1,600.** RigPrice used price today (https://rigprice.com/gpu/rtx-3090/), checked 2026-10-07. $1,600 / 24 GB = $67 per GB. Two cards: $3,200, before a host computer.
- **Intel Arc Pro B60 24GB: $649.99.** ASRock B60 CT 24G on Newegg (https://www.newegg.com/p/N82E16814930148), checked 2026-10-07. $650 / 24 GB = $27 per GB.
- **RTX 5090 32GB: $8,422.00.** MSI RTX 5090 32G Ventus 3X OC on Newegg (https://www.newegg.com/msi-rtx-5090-32g-ventus-3x-oc-geforce-rtx-5090-32gb-graphics-card/p/N82E16814137920?Item=9SIAYB7M5P4014), checked 2026-10-07. $8,422 / 32 GB = $263 per GB.
- **Modified RTX 2080 Ti 22GB: $610 + $10 shipping.** MSI RTX 2080 Ti Aero Magic 22GB, eBay Buy It Now (https://www.ebay.com/itm/227476657350), the cheapest 22GB listing with $10 shipping on 2026-10-07. ($610 + $10) / 22 GB = $28 per GB.
- **Modified RTX 3080 20GB: $979.00.** "OEM NVIDIA GeForce RTX 3080 20GB Turbo", eBay (https://www.ebay.com/itm/377005379375), checked 2026-10-07. $979 / 20 GB = $49 per GB.
- **Modified RTX 4090 48GB: US $5,468.99.** "[USA Made] 48GB RTX 4090 (Not D) Nvidia for Ai/LLM/HighDensity - 90 day warranty", eBay (https://www.ebay.com/itm/397973376248), checked 2026-10-07. $5,469 / 48 GB = $114 per GB. The listing title states a 90 day warranty.
- **128GB Strix Halo: $3,499.99.** GMKtec EVO-X2, AMD Ryzen AI Max+ 395, 128GB RAM + 1TB SSD (https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc), checked 2026-10-07. $3,500 / 128 GB = $27 per GB.
- **Mac Studio M5 Ultra: from $5,499.** Apple store (https://www.apple.com/shop/buy-mac/mac-studio), checked 2026-10-07; the M5 Ultra configuration starts at 96GB of unified memory. $5,499 / 96 GB = $57 per GB.

## Benchmarks

- **RTX 3090: 41.93 tok/s; RTX 5090: 75.74 tok/s** on Qwen 3.8 27B Q4_K_M, same guide and setup (llama.cpp llama-bench). 75.74 / 41.93 = 1.8. Source: GPU Battle, Qwen3.8 27B GPU benchmarks (https://gpubattle.com/guides/qwen3-8-27b-gpu-benchmarks).
- **RTX 4090 48GB: 88.63 tok/s** decode, concurrent-decode workload, qwen2.5-coder 14.8B, Q4_K_M, ollama 0.31.1. Source: LLM-Speed (https://llm-speed.com/hw/rtx-4090-48gb). A different model from GPU Battle's, so not a direct ranking.
- **RTX 2080 Ti 22GB: 23.7 tok/s** decode at 4096 prompt / 128 generated tokens, and 16.3 tok/s at 64K / 512, llama.cpp. Source: weicj/2080Ti-LLM-Toolbox (https://github.com/weicj/2080Ti-LLM-Toolbox/blob/main/engines/llamacpp/README.md).
- **Two RTX 3090s on 70B Q4: 16 to 21 tok/s** (Llama 3.3 70B Q4_K_M, 4K to 8K context). Source: InsiderLLM, Running 70B models locally (https://insiderllm.com/pdfs/running-70b-models-locally-vram-guide.pdf).
- **Intel Arc Pro B60: 51 tok/s** with OpenVINO GenAI on Qwen 3.6-27B-A3B-Coder (int4), the project's own model and runtime. Source: srmiles/local-llm-benchmarks (https://github.com/srmiles/local-llm-benchmarks).
- **128GB Strix Halo: 53.7 to 53.8 tok/s** on gpt-oss-120b MXFP4 (llama.cpp, Vulkan), **5.6 tok/s** on llama3.1:70b (Ollama, a 43 GB file, which the video also shows as a real 70B Q4 file size). Source: huppiflupp/strix-halo-llm-speeds (https://github.com/huppiflupp/strix-halo-llm-speeds).

## Specifications

- **Intel Arc Pro B60:** 24GB GDDR6, up to 456 GB/s, 120 to 200 W total board power depending on the partner board. Source: Intel Arc Pro B60 datasheet (https://cdrdv2-public.intel.com/855693/Datasheet-Intel%C2%AE%20Arc%E2%84%A2%20Pro%20B60%20Graphics.pdf).
- **Rated power:** RTX 3090 350 W (https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090/); RTX 5090 575 W (https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/).
- **Yearly electricity:** 0.35 kW x 4 h x 365 x $0.18 = $92; 0.575 kW x 4 h x 365 x $0.18 = $151, for the GPU's rated draw alone.
- **Modified RTX 3080 20GB with blower coolers:** Tom's Hardware, "Old RTX 3080 GPUs repurposed and modded for Chinese market as 20GB AI cards with blower-style cooling" (https://www.tomshardware.com/news/old-rtx-3080-gpus-repurposed-for-chinese-ai-market-with-20gb-and-blower-style-cooling).

## Memory estimates

These are planning estimates (weights only, before cache and runtime), as the video says: about 4.5 bits per weight at Q4 and 8.5 at Q8.

- 27B: about 14 GB at Q4, about 27 GB at Q8.
- 70B: about 35 to 40 GB at Q4, about 70 GB at Q8.
- 120B: about 60 GB at Q4, about 120 GB at Q8. gpt-oss-120b MXFP4 is 63.4 GB (strix-halo-llm-speeds).

## Not checked

- The Qwen 3.6 27B report of about 25 tok/s without MTP and 50 with it on a 20GB RTX 3080 (https://www.reddit.com/r/LocalLLaMA/comments/1t92h41/has_anyone_bought_a_3080_20gb_mod_recently/) could not be opened on 2026-10-07; the video draws the doubling without the figures.
- The ReBAR and peer-to-peer reports on modified RTX 3080s (https://www.reddit.com/r/LocalLLaMA/comments/1vx1isa/rebar_support_for_20gb_rtx_3080/) could not be opened on 2026-10-07.
{% endraw %}

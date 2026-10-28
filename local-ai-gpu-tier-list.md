---
layout: default
title: "The Local AI GPU Tier List (RTX 3090, 5090, P40, MI50)"
permalink: /local-ai-gpu-tier-list/
date: 2026-10-28
---

# The Local AI GPU Tier List (RTX 3090, 5090, P40, MI50)

{% raw %}
Every GPU for local AI, graded S to F by what it runs for the money. Every price was checked on
its live listing on 27 October 2026 (US). Every speed is a run published by an owner or a reviewer;
none of them is our own test. Dollars per gigabyte is our own arithmetic: the price divided by the
card's memory.

## How the grades work

- **Dollars per gigabyte of memory** decides what a card can run at all. The yardstick is a used
  RTX 3090: $1,727 going rate (RigPrice) ÷ 24 GB = about $72 per GB.
- **Dollars per token per second** is how fast it feels for the money. Speeds come from the
  llama.cpp public scoreboards (Llama 2 7B Q4_0, tg128) and, where an owner or reviewer posted
  one, a run of Qwen 3.8 27B.
- Qwen 3.8 27B at 4 bit is about 18 GB (Hardware Corner's Q4_K_S file is 16.68 GiB).

## Prices (27 October 2026)

- Used Tesla P40 24GB going rate $400 (RigPrice): https://rigprice.com/gpu/tesla-p40/
- Used Radeon Instinct MI50 32GB, cheapest eBay Buy It Now $649: https://www.ebay.com/sch/i.html?_sop=15&LH_BIN=1&_nkw=instinct+mi50&LH_ItemCondition=3000
- Used Tesla T4 16GB, cheapest eBay Buy It Now $430: https://www.ebay.com/sch/i.html?_sop=15&LH_BIN=1&LH_PrefLoc=1&_nkw=tesla+t4+16gb&LH_ItemCondition=3000
- Used RTX 3060 12GB going rate $370 (RigPrice): https://rigprice.com/gpu/rtx-3060-12gb/
- RTX 5060 8GB, Gigabyte Windforce Max OC, $459.99 sold by Newegg: https://www.newegg.com/p/N82E16814932833
- RTX 5060 Ti 16GB, MSI Ventus 2X OC, $789.99 sold by Newegg: https://www.newegg.com/p/N82E16814137992
- RX 9060 XT 16GB, Sapphire Pulse, $649.99 (Newegg marketplace seller): https://www.newegg.com/p/N82E16814202457
- Arc A770 16GB, used, about $325 (RigPrice): https://rigprice.com/gpu/arc-a770-16gb/
- Intel Arc Pro B60 24GB, ASRock, $999.99 sold by Newegg: https://www.newegg.com/p/N82E16814930148
- Intel Arc Pro B70 32GB, ASRock, $1,945.99 from a marketplace seller (Newegg's own listing, out of stock, was $1,299.99): https://www.newegg.com/p/N82E16814930149
- RX 9070 XT 16GB, PowerColor Reaper, $919.99 sold by Newegg: https://www.newegg.com/p/N82E16814131871
- Used RX 7900 XTX 24GB going rate $1,259 (RigPrice): https://rigprice.com/gpu/rx-7900-xtx/
- Radeon AI PRO R9700 32GB, PowerColor, $1,799.99 sold by Newegg: https://www.newegg.com/p/N82E16814131885
- RTX 5070 12GB, Zotac Solid OC, $899.99 sold by Newegg: https://www.newegg.com/p/N82E16814500654
- RTX 5070 Ti 16GB, PNY ARGB OC, $1,349.99 sold by Newegg: https://www.newegg.com/p/N82E16814133901
- RTX 5080 16GB, PNY ARGB OC, $2,299 (Newegg marketplace seller): https://www.newegg.com/p/N82E16814133898
- Used RTX 3090 24GB going rate $1,727 (RigPrice): https://rigprice.com/gpu/rtx-3090/
- Used RTX 4090 24GB going rate about $3,500 (RigPrice): https://rigprice.com/gpu/rtx-4090/
- RTX 5090 32GB, Gigabyte Aorus, $4,920.99 new on eBay (Newegg's eBay store): https://www.ebay.com/itm/800402829841
- RTX PRO 6000 Blackwell 96GB Max-Q, $16,999.95 new on eBay: https://www.ebay.com/itm/128139635593

## Speeds

- llama.cpp CUDA scoreboard (Llama 2 7B Q4_0, tg128): https://github.com/ggml-org/llama.cpp/discussions/15013
- llama.cpp Vulkan scoreboard (Llama 2 7B Q4_0, tg128): https://github.com/ggml-org/llama.cpp/discussions/10879
- Qwen 3.8 27B Q4_K_S on RTX 5090, 4090 and 3090 at 4k context, and its file size (Hardware Corner): https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/
- RTX 5060 Ti 16GB, Qwen 3.8 27B UD-IQ3_XXS: https://njannasch.dev/blog/qwen-3-8-27b-5060ti-mtp-coding/
- RX 9060 XT 16GB, Qwen 3.8 27B UD-IQ3_XXS on Vulkan: https://www.reddit.com/r/LocalLLM/comments/1welwcx/
- Arc A770 16GB, Qwen 3.8 27B IQ4_XS on Vulkan: https://www.reddit.com/r/IntelArc/comments/1wdlyt6/i_want_to_use_qwen38_27b_a_bit_faster_on_the_a770/
- Arc Pro B60, Qwen 3.8 27B Q4_K_M, median owner run (llamaperf): https://llamaperf.com/gpu/arc-pro-b60-24gb
- Arc Pro B70, Qwen 3.8 27B Q4_K_M (llamaperf): https://llamaperf.com/gpu/intel-arc-pro-b70
- RX 9070 XT, Qwen 3.8 27B IQ4_XS on a llama.cpp fork (llamaperf): https://llamaperf.com/gpu/rx-9070-xt-16gb
- RX 7900 XTX, Qwen 3.8 27B on Vulkan (llamaperf): https://llamaperf.com/gpu/rx-7900-xtx
- Radeon AI PRO R9700, Qwen 3.8 27B IQ4_NL on ROCm (llamaperf): https://llamaperf.com/gpu/radeon-ai-pro-r9700-32gb
- MI50 32GB, Qwen 3.8 27B Q8 on a gfx906 llama.cpp fork, 22.8 tok/s (llamaperf): https://llamaperf.com/gpu/amd-mi50-32gb
- RTX 3060 12GB, Qwen3 14B Q4_K at 4k and 16k context (Hardware Corner): https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-3060-12gb/
- RTX PRO 6000 Blackwell Workstation, Llama 3.3 70B Q4_K (Hardware Corner): https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-pro-6000-blackwell/

## Specs and support

- MI50 32GB memory bandwidth 1 TB/s (AMD): https://www.amd.com/en/support/downloads/drivers.html/accelerators/instinct/instinct-mi-series/instinct-mi50-32gb.html
- ROCm 6.0 release notes, gfx906 (MI50) maintenance mode: https://rocm.docs.amd.com/en/docs-6.0.0/about/release-notes.html
- Tesla T4, 70 W (NVIDIA): https://www.nvidia.com/en-us/data-center/tesla-t4/
- Tesla T4 cooling and chassis airflow (NVIDIA forum): https://forums.developer.nvidia.com/t/t4-thermal-integration/75470
- CUDA 13 release notes (Pascal and Volta dropped): https://docs.nvidia.com/cuda/archive/13.0.3/cuda-toolkit-release-notes/index.html
- vLLM GPU requirements (compute capability 7.5+): https://docs.vllm.ai/en/latest/getting_started/installation/gpu.html
- IPEX-LLM archived January 2026: https://github.com/intel/ipex-llm

## Photos

- Gigabyte RTX 3090 Eagle OC · PantheraLeo1359531 · CC BY 4.0 · Wikimedia Commons
- Zotac RTX 3060 12GB · Qurren · CC BY-SA 4.0 · Wikimedia Commons
- PNY RTX 5060 at Computex 2025 · 4300streetcar · CC BY 4.0 · Wikimedia Commons
- PNY RTX 5060 Ti 16GB · FreeMediaKid! · CC BY-SA 4.0 · Wikimedia Commons
- RTX 5070 Founders Edition · Daniel Lu (dllu) · CC BY-SA 4.0 · Wikimedia Commons
- Palit RTX 5090 GameRock · PantheraLeo1359531 · CC BY 4.0 · Wikimedia Commons
- Intel Arc Pro B70 · Biggo Finance · CC BY-SA 4.0 · Wikimedia Commons
- Intel Arc A770 · Telaneo · CC0 · Wikimedia Commons
- Sapphire Radeon RX 7900 XTX · Geni · CC BY-SA 4.0 · Wikimedia Commons
- GTC Taiwan 2016, Tesla P4 & P40 · NVIDIA Taiwan · CC BY 2.0 · Wikimedia Commons
- Instinct MI50 · Мой Компьютер · CC BY 3.0 · Wikimedia Commons
- ASUS ROG Strix GTX 1080 · Sinchen.Lin · CC BY 2.0 · Wikimedia Commons
- Product images from NVIDIA (RTX 5070 Ti, 5080, 4090, PRO 6000, T4), AMD (RX 9060 XT, 9070 XT, Radeon AI PRO R9700) and Sparkle × Intel (Arc Pro B60), shown to identify the products reviewed.
{% endraw %}

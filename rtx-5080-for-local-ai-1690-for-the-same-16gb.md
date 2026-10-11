---
layout: default
title: "Don't Pay $1,690 For The RTX 5080 Until You See This"
permalink: /rtx-5080-for-local-ai-1690-for-the-same-16gb/
date: 2026-10-11
---

# Don't Pay $1,690 For The RTX 5080 Until You See This

{% raw %}
Research for every figure the video puts on screen or says, checked 2026-10-11.

## Prices (Newegg listings sold by Newegg, and one used market tracker)

| Card | Memory | Price | Price per GB | Source |
|---|---|---|---|---|
| MSI RTX 5080 16G Shadow 3X OC | 16 GB | $1,689.99 | $105.62 | https://www.newegg.com/p/N82E16814137914 |
| MSI RTX 5060 Ti 16G Gaming Trio OC (cheapest 5060 Ti 16GB sold by Newegg that day) | 16 GB | $799.99 | $50.00 | https://www.newegg.com/p/N82E16814137954 |
| Gigabyte RTX 5070 Ti Eagle OC 16GB (WindForce listing at $1,169.99 was sold out) | 16 GB | $1,179.99 | about $73 to $74 | https://www.newegg.com/p/N82E16814932770 |
| ASRock Intel Arc Pro B60 24GB | 24 GB | $649.99 | $27.08 | https://www.newegg.com/p/N82E16814930148 |
| Used RTX 3090, RigPrice going rate (asking prices, not sales) | 24 GB | $1,630 (script: about $1,619) | about $68 | https://rigprice.com/gpu/rtx-3090/ |
| PowerColor Radeon AI PRO R9700 32GB | 32 GB | $1,699.99 | $53.12 | https://www.newegg.com/p/N82E16814131885 |

Derived: the RTX 5080 premium over the RTX 5060 Ti is $1,690 - $800 = $890, more than the 5060 Ti's own
price. On Hardware Corner's Qwen3 14B result at 32K context (51.9 vs 25.9 tokens per second) the premium buys
26 more tokens per second, so $890 / 26 = about $34.23 per added token per second (our arithmetic). The R9700
costs about $10 more than the RTX 5080 for twice the memory.

## Speed (Hardware Corner, llama.cpp, Q4_K GGUF unless noted)

RTX 5080: https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-5080/ ·
RTX 5060 Ti 16GB: https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-5060-ti-16gb/

| Model, context | RTX 5080 | RTX 5060 Ti 16GB |
|---|---|---|
| Qwen3 14B, 32K | 51.9 tok/s | 25.9 tok/s |
| Qwen3 14B, 16K | 64.0 tok/s | 32.9 tok/s |
| Qwen3 8B, 4K | 129.1 tok/s | 69.2 tok/s |
| gpt-oss 20B MXFP4, 128K | 105.6 tok/s | 43.8 tok/s |

Memory bandwidth: RTX 5080 960 GB/s, RTX 5060 Ti 448 GB/s (both pages). A 500 token reply at 51.9 and 25.9
tokens per second takes about 9.6 s and 19.3 s once generation starts.

## Qwen3.8 27B and 16 GB (Hardware Corner)

https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/

- The Q4_K Small build tested is 16.68 GiB (27.32 billion parameters), before KV cache and runtime overhead.
- Measured VRAM use: 18 GB at 4K and 8K context, 20 GB at 32K, 22 GB at 64K.
- RTX 3090 (24 GB): 40.31 tok/s at 4K, 37.02 at 32K, 33.95 at 64K.

## GPU Battle's RTX 5080 AI suite

https://gpubattle.com/ai/geforce-rtx-5080 (suite run 2026-07-11)

- 6 of the 12 workloads do not fit in 16 GB at the tested precision, among them Qwen3 32B, Llama 3.3 70B,
  FLUX.1 dev, FLUX.1 Kontext and Qwen Image Edit.
- Llama 3.3 70B needs roughly 42 GB (the page's summary; its table lists about 46 GB).
- Llama 3.1 8B at Q4_K_M: 150.71 tok/s with 4.7 GB peak memory.
- Board power 360 W.

## Power

- RTX 5080: 360 W board power; the Newegg listing recommends an 850 W power supply.
- RTX 5060 Ti: 180 W board power; the Newegg listing recommends 600 W.
- NVIDIA specifications: https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5080/ and
  https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5060-family/

## Not checked

- Whether the Arc Pro B60 or Radeon AI PRO R9700 runs a given model or app well: software support was not
  tested, only listed prices and memory.
- The used RTX 3090 figure is an asking price from a screened tracker, not a completed sale.
- Speeds for the B60 and R9700 were not compared; price per gigabyte does not predict tokens per second.
{% endraw %}

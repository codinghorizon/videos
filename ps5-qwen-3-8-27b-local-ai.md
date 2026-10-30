---
layout: default
title: "Can Your PS5 Run Qwen 3.8 27B Local AI?"
permalink: /ps5-qwen-3-8-27b-local-ai/
date: 2026-10-30
---

# Can Your PS5 Run Qwen 3.8 27B Local AI?

{% raw %}
Every figure the video says or shows, with the public page it came from. Pages were opened and
captured on 29 October 2026; prices are that day's listings and move weekly (PRICES.md has each
listing). "Our maths" marks a division we did ourselves; nothing here is our own benchmark.

## The PS5 hardware

| Claim | Source |
|---|---|
| 8-core Zen 2 CPU, RDNA 2 GPU at up to 2.23GHz, 16GB GDDR6 at 448GB/s | [PlayStation Blog, PS5 technical specs](https://blog.playstation.com/2020/03/18/unveiling-new-details-of-playstation-5-hardware-technical-specs/) |
| PS5 Digital list price $599 (shown unavailable) | [PlayStation Direct](https://direct.playstation.com/en-us/hardware/ps5) |

## How the PS5 runs a model

| Claim | Source |
|---|---|
| A jailbreak covers firmware 7.00 to 13.60 | [cobanov/PS5LM README](https://github.com/cobanov/PS5LM) |
| The first payloads ran on the CPU with about 6GB and made about one token a minute (so 270 tokens is about 4.5 hours, our maths) | [abhi245y/PS5LM-Plus README](https://github.com/abhi245y/PS5LM-Plus) |
| PS5LM Plus is a native app running llama.cpp's Vulkan backend on the GPU | [abhi245y/PS5LM-Plus README](https://github.com/abhi245y/PS5LM-Plus) |
| The model and its KV cache get 12 GiB in one heap | [abhi245y/PS5LM-Plus README](https://github.com/abhi245y/PS5LM-Plus) |
| It serves OpenAI and Anthropic Messages compatible endpoints | [abhi245y/PS5LM-Plus README](https://github.com/abhi245y/PS5LM-Plus) |
| Switching models restarts the app, because about 5GiB stays held after the first load | [abhi245y/PS5LM-Plus README](https://github.com/abhi245y/PS5LM-Plus) |
| Reported on r/LocalLLM as Qwen 27B at 20 tok/s on a jailbroken PS5's GPU | [r/LocalLLM post](https://www.reddit.com/r/LocalLLM/comments/1x4y61f/qwen_27b_at_20_toks_on_a_jailbroken_ps5s_gpu_i/) |
| Covered as jailbroken PS5s running local AI at over 100 tok/s on the GPU | [Tom's Hardware](https://www.tomshardware.com/video-games/playstation/jailbroken-ps5s-can-now-run-local-ai-models-at-over-100-tokens-per-second-fork-of-ps5lm-goes-native-and-accesses-gpu-and-more-ram) |

## PS5 speeds

| Claim | Source |
|---|---|
| Qwen3.8-27B UD-Q2_K_XL (9.2 GiB, 32K context) at 20.3 tok/s; 19.7 tok/s on a 7,775 token answer | [abhi245y/PS5LM-Plus results table](https://github.com/abhi245y/PS5LM-Plus) |
| UD-IQ2_XXS (6.8 GiB) fits a 64K context at 20.7 tok/s | [abhi245y/PS5LM-Plus README](https://github.com/abhi245y/PS5LM-Plus) |
| Gemma 4 E4B at 61 tok/s | [abhi245y/PS5LM-Plus README](https://github.com/abhi245y/PS5LM-Plus) |
| Qwen 3.5 9B Q4_K_M at 55 tok/s on a PS5 Slim | [cobanov/PS5LM README](https://github.com/cobanov/PS5LM) |
| Prompt processing (prefill) of 35 to 50 tok/s | [NeoTeo](https://www.neoteo.com/en/a-ps5-homebrew-developer-reports-qwen38-27b-at-about-20-tokenss) |
| A 20,000 token prompt takes over 8 minutes on the PS5 and 23 seconds at 880 tok/s (our maths: 20,000 / 40 and 20,000 / 880) | derived |

## The model

| Claim | Source |
|---|---|
| Qwen3.8-27B | [Qwen model card, Hugging Face](https://huggingface.co/Qwen/Qwen3.8-27B) |
| GGUF file sizes (UD-Q2_K_XL, IQ3_S, Q4_K_M and others) | [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) |
| Q4_K_M needs about 19GB | [GPU Battle, Qwen3.8 27B benchmarks](https://gpubattle.com/guides/qwen3-8-27b-gpu-benchmarks) |

## Firmware

| Claim | Source |
|---|---|
| Current PS5 system software is 14.20 (21 October 2026) | [PlayStation LifeStyle](https://www.playstationlifestyle.net/2026/10/21/ps5-system-software-firmware-update-october-21) |
| The jailbreak stops at 13.60 and newer games already demand 14.00 | [Tom's Hardware](https://www.tomshardware.com/video-games/playstation/new-ps5-relapse-jailbreak-enables-homebrew-and-switch-emulation-but-is-hamstrung-by-rapidly-changing-firmware-revisions-jailbreak-unlocks-firmware-13-60-but-newer-games-already-demand-firmware-14-00) |
| The PS5 Pro can be jailbroken on older firmware | [TechSpot](https://www.techspot.com/news/114037-new-ps5-jailbreak-works-almost-every-firmware-version.html) |

## Gaming GPUs on the same model

| Claim | Source |
|---|---|
| RTX 5060 Ti 16GB: IQ3_S at 28.5 tok/s, prefill about 880 tok/s | [llamaperf, RTX 5060 Ti 16GB](https://llamaperf.com/gpu/rtx-5060-ti-16gb) |
| RTX 5060 Ti with MTP: just over 50 tok/s decode | [llamaperf, RTX 5060 Ti 16GB](https://llamaperf.com/gpu/rtx-5060-ti-16gb) |
| RTX 3090: Q4_K_M at 41.93 tok/s | [GPU Battle](https://gpubattle.com/guides/qwen3-8-27b-gpu-benchmarks) |
| RTX 5090: Q4_K_M at 75.74 tok/s | [GPU Battle](https://gpubattle.com/guides/qwen3-8-27b-gpu-benchmarks) |
| RTX 5090 memory bandwidth 1,792GB/s, four times the PS5's 448GB/s | [NVIDIA, RTX 5090](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/); 1,792 / 448 = 4 (our maths) |
| A 9.2GB file through 448GB/s tops out near 45 tok/s | our maths: 448 / 9.2 is about 48, less overhead |
| A viewer on our channel: IQ3_S is the best that is feasible on a 16GB card | [comment under "Is Claude Level Local AI Coding Finally Possible?"](https://youtu.be/whrm2Dnjzlk) |

## Prices and dollars per tok/s

| Claim | Source |
|---|---|
| Used PS5 Digital on 13.60, $600 | [eBay listing](https://www.ebay.com/itm/168808323377) |
| Plain used PS5 Digital, $400 | [eBay listing](https://www.ebay.com/itm/355928865299) |
| Used PS5 Pro on 13.60, $1,399.96 | [eBay listing](https://www.ebay.com/itm/287624320322) |
| RTX 5060 Ti 16GB, $789.99, sold by Newegg | [Newegg](https://www.newegg.com/p/N82E16814137992) |
| Used RTX 3090, $1,763 median eBay asking price | [RigPrice](https://rigprice.com/gpu/rtx-3090/) |
| RTX 5090, $7,688 new and $7,100 used, median eBay asking prices | [RigPrice](https://rigprice.com/gpu/rtx-5090/) |
| Dollars per tok/s: PS5 $29.56, RTX 5060 Ti $27.72, RTX 3090 $42.05, RTX 5090 $101.51 | our maths: price / tok/s |
{% endraw %}

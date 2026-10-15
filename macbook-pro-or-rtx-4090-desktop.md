---
layout: default
title: "The RTX 4090 Wins Until Your Model Hits Its 24GB Wall"
permalink: /macbook-pro-or-rtx-4090-desktop/
date: 2026-10-15
---

# The RTX 4090 Wins Until Your Model Hits Its 24GB Wall

{% raw %}
Checked 15 October 2026.

## Prices

| Figure | Value | Source |
|---|---|---|
| RTX 4090, used going rate | $3,500, the median asking price across 41 screened active listings (asking prices, not sale prices); cheapest screened pick $3,280 | [RigPrice, RTX 4090](https://rigprice.com/gpu/rtx-4090/) |
| RTX 4090, launch MSRP | $1,599 | [RigPrice, RTX 4090](https://rigprice.com/gpu/rtx-4090/) |
| RTX 4090, new, cheapest in stock | $4,299, Gigabyte Windforce at Amazon US; 90 day median $4,169 | [PC Tech Vault market watch](https://pctechvault.com/market-watch/geforce-rtx-4090/?region=all) |
| RTX 4090 desktop parts estimate (AMD build) | $6,344.97 total, with an Asus TUF RTX 4090 OC at $3,649.22; that card, the case, the 4TB SSD and the power supply are listed as unavailable; prices updated 15 October 2026 | [Build My PC, RTX 4090 full guide](https://www.buildmypconline.us/build-guides-for-custom-pcs/pc-build-with-geforce-rtx-4090-full-guide/) |
| The same estimate with the current new card | about $6,995 (6,345 − 3,649 + 4,299) | arithmetic on the two rows above |
| MacBook Pro 14 inch, M5 Max 18 core CPU / 40 core GPU, 128GB, 2TB | $6,699.00 | [Apple Store](https://www.apple.com/shop/buy-mac/macbook-pro/14-inch-space-black-standard-display-apple-m5-max-chip-18-core-cpu-40-core-gpu-128gb-memory-2tb-storage) |
| MacBook Pro 16 inch, M5 Pro 18 core CPU / 20 core GPU, 48GB, 1TB | $3,599.00 | [Apple Store](https://www.apple.com/shop/buy-mac/macbook-pro/16-inch-space-black-standard-display-apple-m5-pro-chip-18-core-cpu-20-core-gpu-48gb-memory-1tb-storage) |
| Step from the 48GB Pro to the 128GB Max | $3,100 | arithmetic |
| Price per gigabyte of unified memory | M5 Pro 48GB about $75 (3,599 / 48); M5 Max 128GB about $52 (6,699 / 128) | arithmetic |

## Specifications

| Figure | Value | Source |
|---|---|---|
| M5 Pro memory bandwidth | 307GB/s | [Apple MacBook Pro specs](https://www.apple.com/macbook-pro/specs/) |
| M5 Max (40 core GPU) memory bandwidth | 614GB/s | [Apple MacBook Pro specs](https://www.apple.com/macbook-pro/specs/) |
| M5 Max unified memory | up to 128GB (40 core GPU), on the 14 inch and the 16 inch | [Apple MacBook Pro specs](https://www.apple.com/macbook-pro/specs/) |
| M5 Pro 48GB | available on the 16 inch M5 Pro | [Apple MacBook Pro specs](https://www.apple.com/macbook-pro/specs/) |
| RTX 4090 memory | 24 GB GDDR6X, 1,008 GB/s | [NVIDIA Ada GPU architecture whitepaper](https://images.nvidia.com/aem-dam/Solutions/geforce/ada/nvidia-ada-gpu-architecture.pdf); [RigPrice](https://rigprice.com/gpu/rtx-4090/) |
| RTX 4090 board power | 450 W | [RigPrice](https://rigprice.com/gpu/rtx-4090/); NVIDIA whitepaper |
| 1,008 against 307 | 3.3 times | arithmetic |
| 128GB against 24GB | 5.3 times | arithmetic |

## Benchmarks (published by others; different runtimes and settings)

| Machine and model | Result | Source |
|---|---|---|
| M5 Max, Qwen3.8 27B 4 bit, MLX (mlx-vlm 0.6.14, MTP on) | 853.75 prompt tok/s and 47.00 generated tok/s at depth 0 (2,048 token prompt); 36.05 generated tok/s at 8,192 depth | [NathanMaine/qwen-mlx-offline BENCHMARKS.md](https://github.com/NathanMaine/qwen-mlx-offline/blob/main/docs/BENCHMARKS.md) |
| M5 Max, Qwen 3.8 27B, MTPLX 2.10.0 | 64.3 tok/s on a 3k token chat answer; 30.4 tok/s decode and 535 tok/s prefill at 88k context; 18.4 tok/s at 147k | [MTPLX, run Qwen 3.8 on a Mac](https://www.mtplx.com/docs/run-qwen-3-8-on-a-mac/) |
| M5 Max 128GB, Qwen 3.8 Flash Next, MTPLX 2.11 | up to 84 tok/s on warm agent turns; 79.3 tok/s on a 9k token code prompt | [MTPLX](https://www.mtplx.com/docs/run-qwen-3-8-on-a-mac/) |
| RTX 4090, Qwen3.8 27B UD-Q4_K_XL, llama.cpp CUDA, Q8 KV, native MTP | about 2.4K prompt tok/s (2,436.59 on a 23,604 token prompt) and 65 to 75 generated tok/s at about 124K context window; prompt processing 1,741 tok/s at 97% context occupancy | [r/Qwen_AI community report](https://www.reddit.com/r/Qwen_AI/comments/1vump89/qwen3827b_on_one_rtx_4090_124k_q8_kv_native/) |
| RTX 4090, Qwen3.8 27B at 160K context | 47 to 57 tok/s, full GPU offload (a related r/Qwen_AI report) | linked from the same r/Qwen_AI thread |
| M5 Max 128GB, Llama 3.3 70B Q4 (39.59 GiB), llama.cpp Metal, all layers on GPU | 96.91 tok/s pp512, 7.23 tok/s tg128 | [guanxiong/setup-m5-pro bench results](https://github.com/guanxiong/setup-m5-pro/blob/main/bench/bench-results-m5max-128g.md) |
| RTX 4090 + Ryzen 7900 + 192 GB RAM, Qwen 3.8 Flash Next | about 4,700 to 4,800 tok/s uncached 32K prefill; 120.10 tok/s at 32K; experts and the n-gram table stay in system RAM; "an active research checkpoint, not a claim of full-size quality parity" | [AnnoyingTechnology/nvidia-4090-flash-next-inference](https://github.com/AnnoyingTechnology/nvidia-4090-flash-next-inference) |

## Models

| Figure | Value | Source |
|---|---|---|
| Qwen 3.8 Flash Next | 125B total parameters, 6B activated per token (plus 51B of n-gram embedding tables held off the accelerator) | [arXiv 2608.30320](https://arxiv.org/abs/2608.30320) |
| Llama 3.3 70B at 4 bit | about 40 GB of weights (39.59 GiB Q4 file in the benchmark above) | [guanxiong/setup-m5-pro](https://github.com/guanxiong/setup-m5-pro/blob/main/bench/bench-results-m5max-128g.md) |

## Derived figures in the narration

- 1,000 tokens at 70 tok/s is about 14 seconds; at 47 tok/s about 21 seconds.
- 20,000 prompt tokens at about 2,400 tok/s is about 8 seconds; at about 850 tok/s about 24 seconds.

## Not checked

- No head to head on one runtime exists: every speed comparison here sets different tools, quantizations and context lengths side by side.
- The 4090 at 2 bit for a 70B model is stated from file sizes (a 2 bit 70B file is about 21 GB); no benchmark of it is cited.
- Power and noise of the MacBook Pro under sustained inference were not measured.
- The parts estimate includes components marked unavailable on the day it was read.
{% endraw %}

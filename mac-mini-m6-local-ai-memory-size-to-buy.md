---
layout: default
title: "Mac Mini M6: The 32GB Upgrade Changes Local AI"
permalink: /mac-mini-m6-local-ai-memory-size-to-buy/
date: 2026-10-14
---

# Mac Mini M6: The 32GB Upgrade Changes Local AI

{% raw %}
All prices checked on 2026-10-14 in Apple's US online store (new, sold by Apple) unless noted.

## Mac mini prices and memory

| Configuration | Price | Per installed GB | Source |
|---|---|---|---|
| Mac mini M6 (12-core CPU, 12-core GPU), 16GB, 256GB | $899 | $56.19 | https://www.apple.com/shop/buy-mac/mac-mini/m6-chip-12-core-cpu-12-core-gpu-16gb-memory-256gb-storage |
| Mac mini M6, 24GB, 256GB | $1,099 | $45.79 | https://www.apple.com/shop/buy-mac/mac-mini/m6-chip-12-core-cpu-12-core-gpu-24gb-memory-256gb-storage |
| Mac mini M6, 32GB, 256GB | $1,299 | $40.59 | https://www.apple.com/shop/buy-mac/mac-mini/m6-chip-12-core-cpu-12-core-gpu-32gb-memory-256gb-storage |
| Mac mini M5 Pro (15-core CPU, 16-core GPU), 24GB, 512GB | $1,699 | $70.79 | https://www.apple.com/shop/buy-mac/mac-mini/m5-pro-chip-15-core-cpu-16-core-gpu-24gb-memory-512gb-storage |
| Mac mini M5 Pro, 48GB, 512GB | $2,299 | $47.90 | https://www.apple.com/shop/buy-mac/mac-mini/m5-pro-chip-15-core-cpu-16-core-gpu-48gb-memory-512gb-storage |
| Mac mini M5 Pro, 64GB, 512GB | $2,699 | $42.17 | https://www.apple.com/shop/buy-mac/mac-mini/m5-pro-chip-15-core-cpu-16-core-gpu-64gb-memory-512gb-storage |

Every memory step costs $25 per added gigabyte on both chips: 16GB to 24GB and 24GB to 32GB
are $200 each, 24GB to 48GB on the M5 Pro is $600, and 48GB to 64GB is $400. The 64GB M5 Pro
costs $1,400 more than the 32GB M6. Memory is soldered and is chosen at order time.

Per installed gigabyte is our own calculation: price divided by installed memory. Part of that
memory always belongs to macOS, the runtime and open apps.

## Memory bandwidth and power (Apple)

- M6 16GB: 153GB/s. M6 24GB and 32GB: 170GB/s. M5 Pro: 307GB/s.
  https://www.apple.com/mac-mini/specs/
- Mac mini M6 (16GB/256GB): about 4W idle, 70W maximum.
  https://support.apple.com/en-us/103253

## Qwen 3.8 27B on the M6

- ComputerBase tested the Mac mini M6 with 32GB: Qwen 3.8 27B Q4_K_M in LM Studio 0.4.24 on the
  GPU at 9.5 tokens per second. Their verdict: not a high figure, about double the M4, and usable.
  https://www.computerbase.de/artikel/pc-systeme/apple-mac-mini-m6-test.99469/seite-2
- Qwen 3.8 27B Q4_K_M GGUF: 16.8GB (lmstudio-community), 16.5GB (unsloth UD-Q4_K_M), about 17GB.
  https://huggingface.co/lmstudio-community/Qwen3.8-27B-GGUF/tree/main
  https://huggingface.co/unsloth/Qwen3.8-27B-GGUF/tree/main
- Published M1 Max (32GB) comparison, Qwen 3.8 27B Q4_K_M with MTP off: MLX 19.0 tok/s,
  llama.cpp 12.0 tok/s. https://bishal.io/blog/six-local-models-m1-max-llama-cpp-vs-mlx/

## Bonsai 2 (ternary Qwen 3.8 27B)

- PrismML's Bonsai 2 27B is Qwen 3.8 27B rebuilt with ternary weights. PrismML reports 98.2% of
  the full model's benchmark average (its own evaluation). https://prismml.com/news/bonsai-2-27b
- The MLX pack is 8.60GB; the MTPLX pack with its draft head is 8.85GB.
  https://huggingface.co/prism-ml/Ternary-Bonsai-2-27B-mlx-2bit
  https://huggingface.co/Youssofal/Ternary-Bonsai-2-27B-MTPLX-Optimized-Speed
- MTPLX, a Mac runtime for it: 11.4GB peak memory and 64.4 tok/s after a 4,061-token prompt on an
  M5 Max (128GB); its documented context on a 16GB Mac is 8,192 tokens.
  https://github.com/youssofal/MTPLX
- A community recipe ran Bonsai 2 at 10.6 tok/s on a base M4 Mac mini (24GB) with Prism's
  llama.cpp fork. https://github.com/Weschera/Bonsai-2-27B-Mac/blob/main/README.md

## Used RTX 3090

- Used RTX 3090 24GB: RigPrice going rate $1,649 (median ask, 73 listings) on 2026-10-14,
  cheapest screened pick $1,590; $1,600 on 2026-10-13. $1,600 / 24GB = $66.67 per graphics GB.
  https://rigprice.com/gpu/rtx-3090/
- Hardware Corner: Qwen 3.8 27B Q4_K_S at 40.31 tok/s on an RTX 3090, 4K context.
  https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/
- RTX 3090 memory bandwidth 936GB/s (NVIDIA GA102 whitepaper).
  https://www.nvidia.com/content/PDF/nvidia-ampere-ga-102-gpu-architecture-whitepaper-v2.pdf

### Not checked
- How much memory a ten thousand token conversation needs on these Macs: no source gives that
  figure; nearby published points are 18GB at 8K and 19GB at 16K on an RTX 3090.
- The used RTX 3090 price on October 10 itself (RigPrice's history for that day was not readable);
  $1,600 is the October 13 figure, and $1,590 to $1,649 the October 14 one.
{% endraw %}

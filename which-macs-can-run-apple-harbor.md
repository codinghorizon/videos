---
layout: default
title: "Which Macs Can Run Apple's Harbor (Local AI)"
permalink: /which-macs-can-run-apple-harbor/
date: 2026-11-21
---

# Which Macs Can Run Apple's Harbor (Local AI)

{% raw %}
The sources the script cites, as listed with it. Prices were read on 2026-11-21 from each Apple
configuration page's own listing (PRICES.md has every row and every derived figure).

## Harbor (private preview)
- Harbor, leaked November 10, 2026: an Apple (Claris) app that runs local AI models across one or more Macs, Thunderbolt 5 clustering, open-weight models (9to5Mac): https://9to5mac.com/2026/11/10/apple-has-new-mac-app-coming-to-make-running-local-ai-models-easy/
- Harbor from Apple subsidiary Claris turns a Mac into a private AI inference server; two or more Macs with Thunderbolt 5 can pool their unified memory; no price or release date (iThinkDifferent): https://www.ithinkdiff.com/apple-harbor-app-private-ai-server-mac/
- Harbor, Claris private preview, no release date or pricing (AI Weekly): https://aiweekly.co/alerts/apples-harbor-app-clusters-macs-over-thunderbolt-5-for-local-ai

## Apple's own MLX cluster results
- Apple machine learning research, MLX distributed inference, Table 3 decode speed at 8,192 tokens: Muse Spark Open 15.74 tok/s on 2 M5 Ultra (pipeline), 24.99 on 2 M5 Ultra (tensor), 36.73 on 4 M5 Ultra (tensor); about 493GB of weights at 4 bit; RDMA over Thunderbolt 5: https://machinelearning.apple.com/research/mlx-distributed-inference
- Apple's four Mac Studio result reported (Mixed): https://mixed-news.com/en/apple-mlx-muse-spark-open-four-mac-studios-36-tokens/
- WWDC26 session 233, RDMA over Thunderbolt 5 from macOS 26.2 with MLX: https://developer.apple.com/videos/play/wwdc2026/233/
- RDMA over Thunderbolt 5 in macOS 26.2 on a Mac Studio cluster (Jeff Geerling): https://jeffgeerling.com/blog/2025/15-tb-vram-on-mac-studio-rdma-over-thunderbolt-5
- MLX, Apple's array framework for Apple silicon: https://github.com/ml-explore/mlx

## Which Macs have Thunderbolt 5, and memory speeds
- Mac mini specs: M6 Thunderbolt 4, 170GB/s; M5 Pro Thunderbolt 5, 307GB/s: https://www.apple.com/mac-mini/specs/
- Mac mini with M4 Pro (2024), Thunderbolt 5: https://www.apple.com/eg/mac-mini/specs/
- MacBook Air specs, M5, Thunderbolt 4: https://www.apple.com/macbook-air/specs/
- MacBook Pro specs: M6 Thunderbolt 4; M5 Pro and M5 Max Thunderbolt 5; M5 Max 614GB/s: https://www.apple.com/macbook-pro/specs/
- Mac Studio specs: M5 Max 614GB/s, M5 Ultra 1,228GB/s, Thunderbolt 5 (four ports on the back): https://www.apple.com/mac-studio/specs/

## Prices (Apple US store, 2026-11-21)
- MacBook Air 13-inch M5, 8-core GPU, 16GB, 512GB, $1,299: https://www.apple.com/shop/buy-mac/macbook-air/13-inch-midnight-m5-chip-10-core-cpu-8-core-gpu-16gb-memory-512gb-storage
- Mac mini M6 32GB, 256GB, $1,299: https://www.apple.com/shop/buy-mac/mac-mini/m6-chip-12-core-cpu-12-core-gpu-32gb-memory-256gb-storage
- Mac mini M5 Pro 24GB, 512GB, $1,699: https://www.apple.com/shop/buy-mac/mac-mini/m5-pro-chip-15-core-cpu-16-core-gpu-24gb-memory-512gb-storage
- Mac mini M5 Pro 64GB, 512GB, $2,699: https://www.apple.com/shop/buy-mac/mac-mini/m5-pro-chip-15-core-cpu-16-core-gpu-64gb-memory-512gb-storage
- Mac Studio M5 Max 40-core GPU, 128GB, 512GB, $5,099: https://www.apple.com/shop/buy-mac/mac-studio/m5-max-chip-18-core-cpu-40-core-gpu-128gb-memory-512gb-storage
- Mac Studio M5 Ultra 96GB, 1TB, $5,499: https://www.apple.com/shop/buy-mac/mac-studio/m5-ultra-chip-30-core-cpu-64-core-gpu-96gb-memory-1tb-storage
- Mac Studio M5 Ultra 256GB, 1TB, $9,499: https://www.apple.com/shop/buy-mac/mac-studio/m5-ultra-chip-30-core-cpu-64-core-gpu-256gb-memory-1tb-storage
- Mac Studio M5 Ultra 512GB, 1TB, $22,299: https://www.apple.com/shop/buy-mac/mac-studio/m5-ultra-chip-36-core-cpu-80-core-gpu-512gb-memory-1tb-storage

## Owner benchmarks
- M5 16GB MacBook Air, Qwen 3.5 9B, about 25 tok/s, custom MLX engine (one owner's report): https://llamaperf.com/report/841f288d-9dec-4c72-943d-8df639b19239
- Mac mini M6 32GB, Qwen 3.6 35B-A3B MLX 4-bit in LM Studio, 63.8 tok/s (one owner's report): https://llamaperf.com/report/d1c23d37-16c6-43b0-8eab-fafa820be02f
- Mac mini M6 32GB, Qwen 3.8 27B Q4_K_M in LM Studio, 9.5 tok/s (ComputerBase): https://www.computerbase.de/artikel/pc-systeme/apple-mac-mini-m6-test.99469/seite-2
- M5 Pro 20-core GPU 64GB, Qwen 3.6 27B 8-bit in oMLX, 9.9 tok/s (community benchmark): https://omlx.ai/benchmarks/dy8m7t7k
- M5 Max 128GB (MacBook Pro 14, 40-core GPU), gpt-oss 120B with MLX, 87.9 tok/s at 4K context, 64.5 at 32K (an owner's run published by Hardware Corner): https://www.hardware-corner.net/m5-max-local-llm-benchmarks-20261233/
- M5 Ultra 256GB, GLM-5.3 Flash 320B-A18B in oMLX, 61.7 tok/s (one owner's report): https://llamaperf.com/report/3622ad63-5fa5-4293-831e-7d60db9be6cf

## Caveats
- Harbor is a leak in private preview: Apple has published no list of supported Macs, no price and no release date. "Any M series Mac should run it" is our expectation from MLX running on Apple silicon, not a published requirement.
- Harbor has not said whether it splits a model in pipeline or tensor mode.
- Apple has not published a run of two pooled Mac minis; the two-mini speed is not measured.
- The owner benchmarks are single runs on different engines and settings, not our own tests.
- The gpt-oss 120B run was on an M5 Max in a 14-inch MacBook Pro, not a Mac Studio.
{% endraw %}

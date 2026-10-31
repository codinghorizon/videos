---
layout: default
title: "Upgrade Your PC vs Buy A Mac Mini (Local AI)"
permalink: /upgrade-your-pc-vs-mac-mini-local-ai/
date: 2026-10-31
---

# Upgrade Your PC vs Buy A Mac Mini (Local AI)

{% raw %}
Every price and speed in the video, and where it came from. Prices were checked on October 29,
2026, in US dollars. Used prices are RigPrice's screened eBay asking prices, and sold prices often
come in lower. We did not test these machines ourselves: every speed is from a review, a benchmark
site or an owner's published run, with its model, quant, runtime and card(s) as published.

"Our maths" is price divided by speed (dollars per tok/s, lower is better), on Qwen 3.8 27B at 4-bit
unless the line says otherwise.

## What an 8GB GPU already runs

- RTX 5060 8GB with 32GB of RAM runs Qwen3.6 35B-A3B (Q4_K_XL, LM Studio) at close to 30 tok/s, a
  user report on llamaperf: https://llamaperf.com/gpu/rtx-5060-8gb
- A dense model that spills off the card slows to a crawl: Gemma 4 31B (Q5_K_M) at 2.3 tok/s with 53%
  CPU offload on an RTX 3060 12GB (llamaperf): https://llamaperf.com/gpu/rtx-3060-12gb

## VRAM and system RAM, and the Strata line

- Strata's launch write-up: Qwen 3.8 Flash-Next (125B parameters) on a single 12GB consumer GPU with
  32GB of system memory. These are the project's own figures, reported by AI Weekly:
  https://aiweekly.co/alerts/open-source-strata-engine-runs-125b-qwen38-flash-next-on-a-single-12gb-consumer
- Strata's repo, its supported models and hardware (including Intel Arc on Linux and Apple Silicon):
  https://github.com/Niko1221/Strata
- "What Is Strata": 32GB of RAM is constrained, 48GB to 64GB preferred for Flash-Next:
  https://aiidelist.com/blog/what-is-strata-qwen.md

## A used RTX 3060 12GB

- Going rate $370 (RigPrice): https://rigprice.com/gpu/rtx-3060-12gb/
- One owner runs Qwen 3.8 Flash-Next at 40 tok/s with Strata on a 3060 with 64GB of RAM (Q2); a
  viewer comment under our video pmkA8bWJDdI reads "40 ts decode is good enough for daily code task".
- RTX 3060 plus RTX 2070 (20GB between them): Qwen 3.8 27B Q4_K_M in Ollama at 17.89 tok/s with
  68,115 tokens of context (llamaperf): https://llamaperf.com/gpu/rtx-3060-12gb
- Two RTX 3060s (24GB): Qwen 3.8 27B Q4_K_S at 30.8 tok/s in a llama.cpp short test, and Qwen 3.8
  Flash-Next IQ3_S with Strata at 60 tok/s (llamaperf, same page).
- Our maths: $370 / 17.89 = about $21 per tok/s (about $26 with a $99.99 power supply); two cards
  $740 / 30.8 = about $24 per tok/s before the power supply.

## Power

- NVIDIA's compare page: RTX 3060 170W with 550W required system power; RTX 3090 350W with 750W:
  https://www.nvidia.com/en-us/geforce/graphics-cards/compare/
- Rosewill CMG5 80+ Gold (850W and 1200W), $99.99 on Newegg:
  https://www.newegg.com/rosewill-atx-3-0-compatible-atx-3-1-compatible-1200-w-80-plus-gold-certified-power-supplies-cmg1200g5/p/N82E16817182454

## More system RAM

- 32GB (2x16GB) DDR4-3200, Team T-Force Vulcan Z at $249.99 (Newegg search):
  https://www.newegg.com/p/pl?d=32gb+ddr4+3200+2x16gb+desktop&Order=1
- 64GB (2x32GB) DDR5-5200, Team T-Force Delta RGB at $999.99 (Newegg), $100 more than a whole $899
  Mac mini: https://www.newegg.com/p/N82E16820331982

## Intel Arc Pro B60 24GB

- $999.99 on Newegg: https://www.newegg.com/p/N82E16814930148
- Qwen 3.8 27B at 4-bit, median 22.0 tok/s; 53 tok/s with DFlash2; 16 tok/s on stock llama.cpp
  (llamaperf): https://llamaperf.com/gpu/intel-arc-pro-b60-24gb
- Our maths: $999.99 / 22.0 = about $45 per tok/s.

## A used RTX 3090 24GB

- Going rate $1,763 (RigPrice): https://rigprice.com/gpu/rtx-3090/
- Qwen 3.8 27B at 4-bit, median 38.4 tok/s (llamaperf): https://llamaperf.com/gpu/rtx-3090
- An owner's run, a viewer comment under pmkA8bWJDdI: "Running Strata with Qwen3.8-Flash-Next IQ3_S
  (128k context). Specs: i5-14600KF @ 5.3 GHz, RTX 3090 24 GB, 64 GB Kingston DDR5-6000. Getting
  around 90 tok/s consistently"
- Our maths: ($1,763 + $99.99) / 38.4 = about $48.50 per tok/s.

## The Mac mini

- Apple's prices: M6 16GB/256GB $899
  (https://www.apple.com/shop/buy-mac/mac-mini/m6-chip-12-core-cpu-12-core-gpu-16gb-memory-256gb-storage),
  M6 24GB $1,099
  (https://www.apple.com/shop/buy-mac/mac-mini/m6-chip-12-core-cpu-12-core-gpu-24gb-memory-256gb-storage),
  M6 32GB $1,299
  (https://www.apple.com/shop/buy-mac/mac-mini/m6-chip-12-core-cpu-12-core-gpu-32gb-memory-256gb-storage),
  M5 Pro 48GB/512GB $2,299
  (https://www.apple.com/shop/buy-mac/mac-mini/m5-pro-chip-15-core-cpu-16-core-gpu-48gb-memory-512gb-storage),
  M5 Pro 64GB/512GB $2,699
  (https://www.apple.com/shop/buy-mac/mac-mini/m5-pro-chip-15-core-cpu-16-core-gpu-64gb-memory-512gb-storage).
- Memory bandwidth: M6 170 GB/s, M5 Pro 307 GB/s: https://www.apple.com/mac-mini/specs/
- Power: M6 70W maximum: https://support.apple.com/en-us/103253
- ComputerBase's M6 review: Qwen 3.8 27B at 4-bit about 9.5 tok/s, and long chats only get room from
  48GB: https://www.computerbase.de/artikel/pc-systeme/apple-mac-mini-m6-test.99469/seite-2
- Mac mini M6 32GB reports (llamaperf): Qwen 3.8 27B at 33 to 35 tok/s with Splash; Qwen 3.8
  Flash-Next about 10 tok/s with Strata at Q2_0: https://llamaperf.com/gpu/m6-32gb
- Mac mini M6 24GB: Qwen 3.8 27B at 4-bit, 9.83 tok/s in mlx-vlm (llamaperf):
  https://llamaperf.com/gpu/m6-24gb
- M5 Pro 48GB: Qwen 3.8 27B about 19 tok/s in llama.cpp with Metal (llamaperf user report):
  https://llamaperf.com/gpu/m5-pro-48gb
- M5 Pro 64GB: Qwen 3.8 Flash-Next at 40.8 tok/s with Slipstream at Q4_0 (llamaperf):
  https://llamaperf.com/gpu/m5-pro-64gb
- A viewer asked under pmkA8bWJDdI: "What about running it on a Mac mini pro 64"
- Our maths: M6 32GB $1,299 / 9.5 = about $137 per tok/s.

## Photos

- Colorful GeForce RTX 2070 Super in a case, KMBDENNISTRIDENT, CC0, Wikimedia Commons.
- Zotac GeForce RTX 3060 12GB, Qurren, CC BY-SA 4.0, Wikimedia Commons.
- 2x8GB DDR4 Corsair, Bretwa, CC BY-SA 4.0, Wikimedia Commons.
- GeForce RTX 3090, NVIDIA. Arc Pro B60, Sparkle and Intel. Mac mini and Apple M6, Apple.
- Team T-Force Delta RGB DDR5 and Rosewill CMG5 power supply (the 1200W model is shown), Newegg
  listing photos.
{% endraw %}

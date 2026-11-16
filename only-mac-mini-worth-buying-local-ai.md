---
layout: default
title: "The Only Mac Mini Worth Buying For Local AI (November 2026)"
permalink: /only-mac-mini-worth-buying-local-ai/
date: 2026-11-16
---

# The Only Mac Mini Worth Buying For Local AI (November 2026)

{% raw %}
What the shots put on screen, and where each figure comes from. Checked 2026-11-15.
Prices are in PRICES.md; this file covers every other figure and claim on screen.

## Prices and configurations
- M6 Mac mini from $899; M5 Pro from $1,699; faster M5 Pro chip $1,899 (+$200). Apple newsroom and store:
  https://www.apple.com/newsroom/2026/08/apple-unveils-a-more-powerful-mac-mini-featuring-the-all-new-m6-and-m5-pro/ ·
  https://www.apple.com/shop/buy-mac/mac-mini (capture: apple-store, apple-newsroom)
- Memory steps: M6 24GB +$200 ($1,099), 32GB +$400 ($1,299); M5 Pro 48GB +$600 ($2,299), 64GB +$1,000 and
  only with the faster chip ($2,899). https://daringfireball.net/2026/08/configurations_and_pricing_for_new_mac_minis_and_mac_studios
  (capture: dfb-prices). $25 per added GB = (1,299 - 1,099) / 8.
- Doubling the M6's drive +$200: Apple store, travis.media.
- Mac Studio M5 Max 48GB from $3,100, 128GB +$2,000 = $5,100: Daring Fireball (capture: dfb-studio).
- Used RTX 3090 averages $1,601 on eBay US: https://openclawdc.com/blog/is-a-used-rtx-3090-worth-it-local-llm/

## Usable memory
- macOS lets the GPU use about 75% of memory by default; 64GB gives about 48GB, 32GB about 21 to 24GB
  (two thirds on smaller Macs); `iogpu.wired_limit_mb` raises it. Shown as a drawing, no command on screen.
  https://github.com/ivanopcode/devnote-override-macos-metal-vram-cap (capture: vram-cap)
- 48GB at 3/4 = 36GB usable; 24GB = 16 to 18GB usable; 16GB = 11 to 12GB usable (same rule).

## Model files
- Qwen 3.8 27B UD-Q4_K_M 16.6GB, Q8_0 29GB: https://huggingface.co/unsloth/Qwen3.8-27B-GGUF/tree/main (captures: qwen27-files, qwen27-q8)
- Qwen3 14B Q4_K_M about 9GB: https://huggingface.co/Qwen/Qwen3-14B-GGUF/tree/main
- Llama 3.3 70B Q4_K_M 42.52GB: https://huggingface.co/bartowski/Llama-3.3-70B-Instruct-GGUF
- gpt-oss-120b MXFP4 63.39GB, 117B parameters with 5.1B active: https://huggingface.co/openai/gpt-oss-120b
- Llama 4 Scout Q4_K_M 65.36GB, UD-Q3_K_XL about 49GB; Qwen3 235B Q2_K 85.69GB: Hugging Face (unsloth).

## Bandwidth and speed
- M6 153 GB/s at 16GB, 170 GB/s at 24/32GB; M5 Pro 307 GB/s: https://www.apple.com/mac-mini/specs/ (captures: apple-specs, apple-specs-m6)
- Writing each word reads the whole model from memory (decoding is memory bound):
  https://www.databricks.com/blog/llm-inference-performance-engineering-best-practices
- 170 / 16.6 = about 10 rereads a second (ceiling); 307 / 16.6 = 18.5; 307 / 42.5 = about 7.
- M6 32GB, Qwen 3.8 27B Q4_K_M: 9.5 tok/s in LM Studio. https://www.computerbase.de/artikel/pc-systeme/apple-mac-mini-m6-test.99469/seite-2 (capture: computerbase)
- M5 Pro 64GB, Qwen 3.8 27B: 18.5 tok/s in llama.cpp; LM Studio 33.5 vs oMLX 16.0 across apps; MLX runs 36+.
  https://llamaperf.com/gpu/m5-pro-64gb (capture: llamaperf)
- Apple's 4.8x figure is prompt processing against M4: Apple newsroom.
- M4 to M6 bandwidth +42% (120 to 170 GB/s).
- llama.cpp Apple table, Llama 2 7B Q4_0: M4 24.11 tok/s, M5 Pro 16-core GPU 67.59, 20-core GPU 66.33; prompt 1,340 vs 1,621:
  https://github.com/ggml-org/llama.cpp/discussions/4167
- RTX 3090 936 GB/s: https://en.wikipedia.org/wiki/GeForce_RTX_30_series

## Memory prices
- DRAM contract prices Q1 2026 +93 to 98%; Q3 +13 to 18%, inventories at historic lows: TrendForce
  https://www.trendforce.com/presscenter/news/20260601-13070.html · https://www.trendforce.com/presscenter/news/20260907-13219.html
- Apple raised Mac prices over memory costs: https://www.pbs.org/newshour/economy/apple-increases-prices-for-macs-and-ipads-blaming-memory-chip-shortage-fueled-by-ai
- Mac mini base $599 to $899 (+50%): https://macworld.com/article/3220063/apple-launches-new-m6-mac-mini-with-another-price-hike.html
- M4 Pro (2024) 64GB +$600 = $15 per added GB: https://everymac.com/systems/apple/mac_mini/specs/mac-mini-m4-pro-14-core-cpu-20-core-gpu-2024-specs.html
- 32GB and 64GB Mac minis unavailable April 2026: https://www.macrumors.com/2026/04/11/some-mac-mini-mac-studio-currently-unavailable/

## Apps
- llama.cpp 77.8 vs mlx-lm 107.5 tok/s (+38%), M3 Ultra, Qwen3.5 9B 4 bit: https://terminalbytes.com/ollama-vs-llama-cpp-vs-mlx-mac-2026/
- Ollama MLX engine: preview, Macs with more than 32GB: https://ollama.com/blog/mlx
- LM Studio free for home and work, runs MLX and llama.cpp: https://lmstudio.ai/blog/free-for-work · https://lmstudio.ai/
- Ollama open source (MIT): https://github.com/ollama/ollama

## Viewer comment (beat 042-044)
- Real comment, 2026-11-08, under "best local AI for every Mac" (YouTube comments tool), shown verbatim with its typos:
  "recomendattion for m5Pro chip with 24gb??. It seems the 24gb is weird spot as its a but too tight for the
  models above 20b once fctoring browesr multitasking and notes"
  On screen: the card quotes "It seems the 24gb is weird spot as its a but too tight for the models above 20b".
{% endraw %}

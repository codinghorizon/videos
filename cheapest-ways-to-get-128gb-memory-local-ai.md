---
layout: default
title: "The Cheapest Ways To Get 128GB Memory For Local AI"
permalink: /cheapest-ways-to-get-128gb-memory-local-ai/
date: 2026-11-16
---

# The Cheapest Ways To Get 128GB Memory For Local AI

{% raw %}
Every figure on screen and in the voice, and where it comes from. Every page was opened on 2026-11-15.
Prices were checked on the day; PRICES.md holds each spoken price against its listing.
None of these figures is our own test. Each one is published by the source named. Where the script
says "by our maths", the arithmetic is shown here.

## Prices (US listings, 2026-11-15)
- GMKtec EVO-X2 128GB + 1TB: $3,499.99 (sale, was $3,999.99). The page says "Price increase coming soon".
  https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc?variant=48746069262490
- Beelink GTR9 Pro 128GB + 2TB: $4,199.00. https://www.bee-link.com/products/beelink-gtr9-pro-amd-ryzen-ai-max-395
- Mac Studio M5 Max, 40-core GPU, 128GB, 512GB: $5,099.00. This is the cheapest 128GB Mac, and 128GB is only offered with the 40-core GPU.
  https://www.apple.com/shop/buy-mac/mac-studio/m5-max-chip-18-core-cpu-40-core-gpu-128gb-memory-512gb-storage
  Its bandwidth of 614GB/s is from https://www.apple.com/mac-studio/specs/
- NVIDIA DGX Spark: $6,950.00. MSI EdgeXpert: $8,499.99. Both are on NVIDIA's own Marketplace:
  https://marketplace.nvidia.com/en-us/enterprise/personal-ai-supercomputers/
- AMD Instinct MI50 32GB HBM2 from a US eBay seller, Buy It Now: $629.99. The listing title rates it at 300W, and the card is passive (no fan).
  https://www.ebay.com/itm/960133609137
- Newegg prices:
  - ASRock Rack ROMED8-2T/BCM: $719. https://www.newegg.com/asrock-rack-romed8-2t/p/N82E16813140044
  - AMD EPYC 7532: $599.99. https://www.newegg.com/amd-epyc-7532-socket-sp3/p/N82E16819113753
  - Super Flower Leadex VII XG 1300W: $159.99. https://www.newegg.com/p/pl?d=1300w+atx+power+supply&N=100007657%204814&Order=1
  - G.Skill Trident Z5 Neo 128GB (2x64) DDR5-6000: $3,987.99. https://www.newegg.com/g-skill-trident-z5-neo-series-128gb-2-x-64gb-ddr5-6000-pc5-48000-cas-latency-cl36-desktop-memory-black/p/N82E16820374768?Item=9SIAM8PMAE4678
  - G.Skill Trident Z Neo 128GB (4x32) DDR4-3200, used: $1,295.00. https://www.newegg.com/g-skill-trident-z-neo-series-128gb-ddr4-3200-cas-latency-cl16-desktop-memory-black/p/N82E16820232953?Item=9SIAM8PM348291
  - Yeston RX 9060 XT 16GB: $729.99. https://www.newegg.com/p/N82E16814980004

## Models: total versus active parameters, and file sizes
- gpt-oss-120b has 117B total parameters and 5.1B active. Its files are 62.6 to 65.4GB in every GGUF quant, because the experts stay MXFP4.
  https://huggingface.co/openai/gpt-oss-120b , https://huggingface.co/unsloth/gpt-oss-120b-GGUF
- Qwen3-235B-A22B-2507 has 235B total and 22B active, with 94 layers. Q3_K_M is 112.4GB and Q4_K_M is 142.2GB.
  https://huggingface.co/Qwen/Qwen3-235B-A22B-Instruct-2507 , https://huggingface.co/unsloth/Qwen3-235B-A22B-Instruct-2507-GGUF
- "Under three gigabytes per token" (our maths): 5.1B active parameters at about 4.25 bits each is about 2.7GB read per token.
- "Four times the reading" (our maths): 22B active against 5.1B is 4.3 times.

## Speed on the Strix Halo (the dense versus MoE comparison)
- Dense Llama 3.1 70B Q4_K_M runs at 5.1 tok/s. gpt-oss-120b runs at 53.4 tok/s (llama-server). Qwen3-235B-A22B Q3_K_M runs at 17.2 tok/s.
  All three are from https://github.com/visorcraft/strix-halo-llm-perf . "Ten times" is 53.4 / 5.1 = 10.5.

## Usable memory
- Strix Halo: the BIOS allows 96GB at most. On Linux the GTT limit can be raised.
  https://www.jeffgeerling.com/blog/2025/increasing-vram-allocation-on-amd-ai-apus-under-linux/
  AMD's own guide (amd-ttm, keep the BIOS VRAM small): https://rocm.docs.amd.com/en/latest/how-to/system-optimization/strixhalo.html
- DGX Spark: the OS and desktop take a 7GB baseline.
  https://forums.developer.nvidia.com/t/memory-creep-on-dgx-spark-where-your-128-gb-actually-goes-and-how-to-stop-it/364886
- Mac: the "about 96GB" figure is what users report (3/4 of 128), not an Apple figure. `sudo sysctl iogpu.wired_limit_mb` raises it.
  https://github.com/ggml-org/llama.cpp/discussions/2182
- Context memory (our maths, from each config.json: 2 x layers x KV heads x head_dim x 2 bytes):
  - gpt-oss-120b: 4.5GiB at 128K. https://huggingface.co/openai/gpt-oss-120b/raw/main/config.json
  - Qwen3-235B: 23.5GiB at 128K ("about twenty five"), across 94 layers. https://huggingface.co/Qwen/Qwen3-235B-A22B-Instruct-2507/raw/main/config.json

## Each box's speed (gpt-oss-120b)
- EVO-X2 / Strix Halo, llama.cpp ROCm: 51.84 tok/s with an empty context and 19.84 at 32K. Prompt reading is 1,008 tok/s empty and 309 at 32K.
  https://forum.level1techs.com/t/one-spark-two-spark-red-strix-blue-arc/240937
  The DGX Spark ran in the same thread: prompt reading about 1,600 tok/s.
- Strix Halo bandwidth (our maths from AMD's spec): 256-bit LPDDR5X-8000 = 256GB/s.
- "Close to a minute" for a 30K-token report: 30,000 / 309 = 97s, which is within the stated range when averaged over the fill.
- Mac Studio M5 Max, oMLX v0.3.2:
  - Writing: 79.7 tok/s at 1K, 41.4 at 32K, 14.0 at 128K.
  - Prompt reading: 1,023 at 1K, 1,213 at 32K, about 500 at 128K.
  https://omlx.ai/benchmarks/d8dnhh1k
- DGX Spark, llama.cpp b6922: 60.57 tok/s empty and 40.55 at 32K. Prompt reading is 1,956 empty and 1,027 at 32K.
  https://github.com/ggml-org/llama.cpp/discussions/16578
- MI50: two cards ran gpt-oss 120B at about 58 tok/s in one builder's 8-card rig.
  https://www.reddit.com/r/LocalLLaMA/comments/1nhd5ks/completed_8xamd_mi50_256gb_vram_256gb_ram_rig_for/
  No published 4-card run of Qwen3-235B was found, and the script says so.
- GPU plus system RAM: an RTX 4070 12GB with DDR5-6000 ran gpt-oss-120b at 23.85 tok/s. With the RAM at 2000 MT/s it ran at 9.72 tok/s.
  https://carteakey.dev/blog/local-inference/optimizing-gpt-oss-120b-local-inference/
  "13 to 15" for DDR4-3200 is our maths: dual-channel DDR4-3200 is 51.2GB/s, which sits between those two runs' bandwidths. Method: https://gpuwerk.com/blog/moe-cpu-offload-llama-cpp/

## Quantization quality
- Gemma 3 27B, MMLU 5-shot (Unsloth): Q2_K_XL 68.70, Q3_K_XL 70.87, Q4_K_XL 71.47, Q8_0 71.60.
  https://unsloth.ai/docs/basics/unsloth-dynamic-2.0-ggufs
- $5,800 per point (our maths): one extra EVO-X2 ($3,499.99) / 0.60 points.

## Per-dollar figures (our maths; every row is in PRICES.md)
- Per GB: EVO-X2 $27.34, Mac $39.84, Spark $54.30, MI50 x4 $19.69, RAM route $14 (144GB).
- Per tok/s (empty context): EVO-X2 $68, Mac $64, Spark $115. At 32K: Mac $123, EVO-X2 $176.
{% endraw %}

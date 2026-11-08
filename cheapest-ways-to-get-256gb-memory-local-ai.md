---
layout: default
title: "The Cheapest Ways To Get 256GB Memory For Local AI"
permalink: /cheapest-ways-to-get-256gb-memory-local-ai/
date: 2026-11-08
---

# The Cheapest Ways To Get 256GB Memory For Local AI

{% raw %}
The sources the script cites, as listed with it. Every price is in PRICES.md, checked live on
2026-11-07. Every speed is a published result from the builders and reviewers below, never our own run.

VIEWER-COMMENT: -9_VkRUZPAA "Unfortunately a real local work station is only mac studio m5 ultra with 256gb of ram which is 10k usd before tax" (verified 2026-11-07, comments tool)
VIEWER-COMMENT: -9_VkRUZPAA "I use 2 of the 128 Strix H systems, very happy." (verified 2026-11-07)
VIEWER-COMMENT: y0N9jJ3wxOY "I built an older Threadripper Pro on Gigabyte MC62-G40 with 256GB of 8-channel DDR4 - cheaper build than Epyc. Cut the threads to one or two and save power - makes little difference to tok/s" (verified 2026-11-07)

## Captures (public/<slug>/web/, regions in src/lib/page.tsx)
- r-studio: Apple buy page, "256GB unified memory" on the $9,499 Mac Studio M5 Ultra.
- r-mac-glm: llamaperf report 6d2919ae, GLM 5.3 Flash oQ4e on the M5 Ultra, "80-90 t/s gen · 1600.0 tokens/s prompt processing".
- r-spark: Classmethod DevelopersIO, two DGX Sparks on GLM 5.3 Flash NVFP4, "17.7 → 26.5 tok/s".

## Sources
- AMD EPYC 7532, $599.99 on Newegg (November 7, 2026): https://www.newegg.com/amd-epyc-7532-socket-sp3/p/N82E16819113753
- ASRock Rack ROMED8-2T, $719.00 sold by Newegg (November 7, 2026): https://www.newegg.com/asrock-rack-romed8-2t/p/N82E16813140044
- NEMIX 256GB (8x32GB) DDR4-3200 ECC RDIMM, $3,426.99 on Newegg (November 7, 2026): https://www.newegg.com/nemix-ram-256gb-8-x-32gb/p/1X5-003Z-01P39
- AMD EPYC 7532 memory: 8 channels DDR4-3200, 204.8 GB/s per socket: https://www.amd.com/en/products/processors/server/epyc/7002-series/amd-epyc-7532.html
- 8x MI50/MI60 rig on EPYC 7532 and ROMED8-2T with 8x32GB DDR4-3200: Qwen3 235B Q4_1 about 21 tok/s, gpt-oss 120B CPU-only about 25 tok/s, about 400W idle and 750W in llama.cpp (r/LocalLLaMA): https://www.reddit.com/r/LocalLLaMA/comments/1nhd5ks/completed_8xamd_mi50_256gb_vram_256gb_ram_rig_for/
- GLM-5 Q3_K_XL on EPYC 7552 with 8-channel DDR4-2666, about 5.2 tok/s: https://openclawdc.com/blog/epyc-server-cpu-inference-moe/
- 8x MI50 32GB with vllm-gfx906 (r/LocalLLaMA): https://www.reddit.com/r/LocalLLaMA/comments/1qjaxfy/8x_amd_mi50_32gb_at_26_ts_tg_with_minimaxm21_and/
- AMD Instinct MI50 32GB used, $749.99, US seller (eBay, November 7, 2026): https://www.ebay.com/itm/960133609137
- US average residential electricity price, 18.16 cents per kWh, August 2026 (EIA): https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_5_6_a
- GMKtec EVO-X2, Ryzen AI Max+ 395, 128GB + 1TB, $3,499.99 (GMKtec, November 7, 2026): https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc
- Strix Halo results: Qwen3 235B Q3_K_M 17.2 tok/s on one box; Qwen3.5 397B UD-Q4_K_XL 11.76 tok/s over RPC on an EVO-X2 plus a Beelink GTR9 Pro: https://github.com/visorcraft/strix-halo-llm-perf
- GLM-5.3 Flash Q4_K on two Strix Halo boxes over USB4, 9.77 tok/s, 97.89 tok/s prompt (llamaperf): https://llamaperf.com/report/19c239d4-a417-442d-b030-f5dfba4423de
- G.Skill Trident Z5 Neo RGB 256GB (4x64GB) DDR5-6000, $7,799.99 on Newegg (November 7, 2026): https://www.newegg.com/g-skill-trident-z5-neo-rgb-series-256gb-4-x-64gb-ddr5-6000-pc5-48000-cas-latency-cl34-desktop-memory-black/p/N82E16820374765
- AMD Ryzen 9 9950X memory support, DDR5-5600 with two DIMMs, DDR5-3600 with four: https://www.amd.com/en/products/processors/desktops/ryzen/9000-series/amd-ryzen-9-9950x.html
- Mac Studio M5 Ultra 30-core CPU, 64-core GPU, 256GB, 1TB, $9,499 (Apple, November 7, 2026): https://www.apple.com/shop/buy-mac/mac-studio/m5-ultra-chip-30-core-cpu-64-core-gpu-256gb-memory-1tb-storage
- Mac Studio M5 Ultra, 1.2TB/s memory bandwidth (Apple Newsroom): https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/
- GLM-5.3 Flash oQ4e on the M5 Ultra in oMLX, 80 to 90 tok/s, about 1,600 tok/s prompt (llamaperf): https://llamaperf.com/report/6d2919ae-4e69-4af1-806c-f6cdb9e44612
- DeepSeek V4.1 Flash oQ4e on the Mac Studio M5 Ultra 256GB, 25.5 tok/s at 16K with expert offload to SSD (llamaperf): https://llamaperf.com/report/7bfe3121-de37-4c49-86e7-48b04ecb9981
- macOS default GPU memory limit and how to raise it (llama.cpp discussion): https://github.com/ggml-org/llama.cpp/discussions/2182
- NVIDIA Marketplace: ASUS Ascent GX10 $5,999, QSFP cable $99.99 (November 7, 2026): https://marketplace.nvidia.com/en-us/enterprise/personal-ai-supercomputers/
- Dell Pro Precision with GB10, $7,901 (Dell, November 7, 2026): https://www.dell.com/en-us/shop/desktop-computers/spd/dellpromaxwithgb10fcm1253
- DGX Spark memory bandwidth 273 GB/s (NVIDIA): https://developer.nvidia.com/blog/how-nvidia-dgx-sparks-performance-enables-intensive-ai-tasks
- GLM-5.3 Flash NVFP4 on two DGX Sparks, vLLM TP=2: 26.5 tok/s with MTP, prompt 1,369 to 1,480 tok/s from 2K to 200K (Classmethod): https://dev.classmethod.jp/en/articles/dgx-spark-2node-glm-5-3-flash-nvfp4-vllm/
- AMD Ryzen AI Halo 192GB, $7,299.99 at Micro Center (November 7, 2026): https://www.microcenter.com/product/717068/amd-ryzen-ai-halo-developer-platform-with-ryzen-ai-max-pro-495-processor-linux-os
- NVIDIA RTX PRO 6000 Blackwell 96GB Workstation Edition, $16,399.00 on Newegg (November 7, 2026): https://www.newegg.com/nvidia-blackwell-rtx-pro-6000-96gb-graphic-card/p/N82E16814132106
- GLM-5.3 Flash NVFP4 on two RTX PRO 6000s, vLLM TP2 with a DFlash-2 drafter, 186 tok/s (llamaperf): https://llamaperf.com/report/7e465124-6df1-4b04-a1a0-f75aa90441b3
- GLM-5.3 Flash GGUF sizes, UD-IQ4_XS 157GB, UD-Q4_K_XL 200GB (Unsloth): https://huggingface.co/unsloth/GLM-5.3-Flash-GGUF
- GLM-5.3 Flash, 320B total, 18B active (Artificial Analysis): https://artificialanalysis.ai/models/glm-5-3-flash
- Qwen3 235B A22B 2507 GGUF, Q4_K_M 142GB, Q8_0 250GB (Unsloth): https://huggingface.co/unsloth/Qwen3-235B-A22B-Instruct-2507-GGUF
- DeepSeek V4.1 Flash memory and quant sizes (Unsloth): https://unsloth.ai/docs/models/deepseek-v4.1-flash

## Photos (public/<slug>/photos/, credits in GB_PICS)
- Mac Studio (Apple), EVO-X2 (GMKtec), Ascent GX10 (ASUS), RTX PRO 6000 (NVIDIA), ROMED8-2T (ASRock Rack),
  Trident Z5 Neo (G.Skill): makers' own product images. EPYC 7702 and Instinct MI50 (CC BY 3.0, Мой Компьютер):
  Wikimedia Commons.
{% endraw %}

---
layout: default
title: "Can Your Local AI Machine Run DeepSeek V4.1?"
permalink: /deepseek-v4-1-memory-every-machine/
date: 2026-11-03
---

# Can Your Local AI Machine Run DeepSeek V4.1?

{% raw %}
The sources the script cites, as listed with it.

VIEWER-COMMENT: y0N9jJ3wxOY "what can you run on a 5090 with 64gb of ddr ram"
- Unsloth DeepSeek V4.1 Flash guide (memory per file, Avg score, Aider, GSQ-RCO 81.78, Nov 2 GGUFs): https://unsloth.ai/docs/models/deepseek-v4.1-flash
- Unsloth DeepSeek-V4.1-Flash-1017 GGUF files (UD-IQ1_S 233GB): https://huggingface.co/unsloth/DeepSeek-V4.1-Flash-1017-GGUF
- DeepSeek-V4.1-Flash-1017 model card (DeepSWE 77.0, Opus 5 74.0): https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash-1017
- IST Austria DAS Lab GSQ-RCO quants (1.75 bpw, 120.7GB; Coder build 72.12GB): https://huggingface.co/ISTA-DASLab
- Strata README (RTX 3060 9-11 tok/s): https://github.com/Niko1221/Strata
- Strata DeepSeek V4.1 notes (RTX 3060 46GB RAM, 257GB set; RTX 5070 64GB about 4.7 tok/s): https://github.com/Niko1221/Strata/blob/main/docs/DEEPSEEK41.md
- llamaperf DeepSeek V4.1 Flash reports (every owner speed below, by report id): https://llamaperf.com/model/deepseek-v4-1-flash/reports
- RTX 5090 + 64GB DDR5, Strata, 10.0 tok/s at 8K: llamaperf report a3d7a2c1-059e-48dd-a878-d7c172f4cd6c
- RTX 5090 + 128GB, 1017 IQ2_XXS GSQ-RCO, Strata, 35.0 tok/s: llamaperf report a0dfdadd-d718-401a-b61c-f271e90ba4fd
- Strix Halo 128GB, IQ1_M, Gufo, 24.5 tok/s (23.1 at 128K): llamaperf report 4c8cda33-07b4-446f-b27f-057fdf0e3bc9
- DGX Spark, 113.6GB VQ-8 build, YoungAi engine, 28.9-30.7 tok/s: llamaperf report db523846-0001-478d-b6a6-e7e1f2630f7b
- MacBook Pro M5 Max 128GB, 341GB Q2 GGUF, ds4 fork, 25.7 tok/s at 2K, 22.0 at 32K: llamaperf report ef1fa35e-a9d0-4ee8-bd84-3527a492447d
- Mac Studio M5 Ultra 256GB, 1017 oQ4e, oMLX, 25.5 tok/s at 16K: llamaperf report 7bfe3121-de37-4c49-86e7-48b04ecb9981
- Mac Studio M5 Ultra 256GB, oQ2.5e, oMLX, 65.6 tok/s: llamaperf report d07eb7d7 (DeepSeek V4.1 Flash reports list)
- 4x RTX 3090 + EPYC, UD-Q4_K_XL, 24.6 tok/s prose: llamaperf report cb8938f6-1eb3-4ee9-b2ce-ba37aca1df2e
- ds4 QA and performance notes (DGX Spark Q2 from SSD 9.3 tok/s; M3 Ultra 512GB Q4 18.69 tok/s at 4K): https://github.com/antirez/ds4
- DeepSeek API pricing (deepseek-flash, $0.60 per 1M output tokens off-peak, $1.20 peak): https://api-docs.deepseek.com/quick_start/pricing
- macOS default GPU memory limit (three quarters of memory on larger Macs): https://github.com/ggml-org/llama.cpp/discussions/2182
- GMKtec EVO-X2 128GB + 1TB, $3,499.99: https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc?variant=48746069262490
- NVIDIA Marketplace (DGX Spark Founders Edition $6,950, ASUS Ascent GX10 $5,999): https://marketplace.nvidia.com/en-us/enterprise/personal-ai-supercomputers/
- DGX Spark 64GB via partners: https://hothardware.com/news/nvidia-dgx-spark-64gb-release
- MacBook Pro 14 M5 Max 128GB, $6,699: https://www.apple.com/shop/buy-mac/macbook-pro/14-inch-space-black-standard-display-apple-m5-max-chip-18-core-cpu-40-core-gpu-128gb-memory-2tb-storage
- Mac Studio M5 Ultra 256GB, $9,499: https://www.apple.com/shop/buy-mac/mac-studio/m5-ultra-chip-30-core-cpu-64-core-gpu-256gb-memory-1tb-storage
- Mac Studio M5 Ultra 512GB, $22,299: https://www.apple.com/shop/buy-mac/mac-studio/m5-ultra-chip-36-core-cpu-80-core-gpu-512gb-memory-1tb-storage
- RTX 5090 Gigabyte AORUS, $6,919.99: https://www.newegg.com/gigabyte-gv-n5090aorusx-w-32gd-geforce-rtx-5090-32gb-graphics-card/p/N82E16814932763
- G.Skill Ripjaws S5 128GB DDR5-6000, $3,799.99: https://www.newegg.com/g-skill-ripjaws-s5-series-128gb-2-x-64gb-ddr5-6000-pc5-48000-cas-latency-cl34-desktop-memory-black/p/N82E16820374761
- Used RTX 3090, $1,792 median eBay asking price: https://rigprice.com/gpu/rtx-3090/
- Samsung 990 Pro 2TB, $389.99: https://www.newegg.com/samsung-2tb-990-pro-nvme-2-0/p/N82E16820147861
{% endraw %}

---
layout: default
title: "Every Way To Get 96GB VRAM For Local AI"
permalink: /every-way-to-get-96gb-vram/
date: 2026-11-26
---

# Every Way To Get 96GB VRAM For Local AI

{% raw %}
Researched 2026-11-26. Every price below was read live on 2026-11-26 from the listing cited (Newegg and eBay through
real Chrome, scripts/page-text.mjs). The question (different from the 2026-11-20 128GB video, which ranked
unified-memory boxes and MI50s at 128GB): which route to 96GB of memory a model can use gives the most speed per
dollar on ONE model, gpt-oss-120b, and which route wins for the cheapest, fastest, quietest and simplest buyer?
Every route gets the same four facts: today's price from a named listing (new or used), the GB a model can use, the
memory bandwidth from the maker's spec, and one measured tok/s on gpt-oss-120b from a named source, or "no measured
figure". None of these figures is our own test.
The finding: three used MI50s are the cheapest 96GB by far ($19.69 per GB, cards only), one RTX Pro 6000 is the
fastest (134.71 tok/s) and the most expensive per GB ($171.87), and the 128GB Mac Studio is the cheapest complete
machine per tok/s ($63.98) while giving a model about 96GB by default.

Card routes are priced as the cards alone: the PC they go in is extra. The three boxes are complete computers.

## Sources

R1: https://www.newegg.com/p/pl?d=rtx+pro+6000+blackwell+96gb&N=4131 (accessed 2026-11-26) Newegg, in-stock filter: "NVIDIA Blackwell RTX PRO 6000 Max-Q Edition 96 GB GDDR7 ECC PCI Express 5.0 x16 Graphics Card 900-5G153-2200-000 - OEM" "$16,499.99" "ADD TO CART"; PNY Max-Q "$16,999.99"; the Workstation Edition page https://www.newegg.com/p/N82E16814132106 shows $16,699.99 out of stock
R2: https://www.nvidia.com/en-us/products/workstations/professional-desktop-gpus/rtx-pro-6000/ (accessed 2026-11-26) NVIDIA: "96 GB of GPU memory"; "Memory Bandwidth 1792 GB/sec"; Workstation Edition "Max Power Consumption 600 W"
R3: https://www.hardware-corner.net/guides/rtx-pro-6000-gpt-oss-120b-performance/ (accessed 2026-11-26) Hardware Corner, RTX Pro 6000 Blackwell (workstation card), llama.cpp server version 6112, unsloth gpt-oss-120b-F16.gguf (MXFP4) "a hefty 65GB": context 12,000: prompt "2542.57 t/s", token generation "134.71 t/s", VRAM 84 GB; with Flash Attention VRAM "dropped from 91 GB to 67 GB at maximum context"; full 131,072-token context
R4: https://www.newegg.com/p/N82E16814132111 (accessed 2026-11-26) Newegg: "NVIDIA Blackwell RTX PRO 5000 48 GB GDDR7 ECC PCI Express 5.0 x16 Graphics Card - 900-5G153-2250-000" "$7,199.99", "Sold by Eluktronics", new
R5: https://www.nvidia.com/en-us/products/workstations/professional-desktop-gpus/rtx-pro-5000/ (accessed 2026-11-26) NVIDIA: "48 or 72 GB of GPU memory"; "Memory Bandwidth 1,344 GB/sec"; "Max Power Consumption 300 W"
R6: https://rigprice.com/gpu/rtx-3090 (accessed 2026-11-26) RigPrice, used RTX 3090 from screened live eBay listings: "going rate is $1,921" (latest Nov 20); "Cheapest screened pick $1,800"; "Memory bandwidth 936 GB/s"
R7: https://www.hardware-corner.net/guides/3x-rtx-3090-gpt-oss-120b-test/ (accessed 2026-11-26) Hardware Corner, three RTX 3090s rented on Vast.ai, llama.cpp version 6112, MXFP4 GGUF 65 GB, FlashAttention on: context 12,788: prompt "1158.55 t/s", generation "73.26 t/s", "67 GB" VRAM; 93,687 context: 833.07 / 41.05 t/s; "three RTX 3090s can't run the full 128k context"
R8: https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090-3090ti/ (accessed 2026-11-26) NVIDIA: RTX 3090 "Graphics Card Power (W) 350", "Memory Interface Width 384-bit"
R9: https://www.newegg.com/p/N82E16814930148 (accessed 2026-11-26) Newegg: "ASRock B60 Intel Arc Pro B60 CT 24G 192-bit GDDR6" "$999.99", "Sold by Newegg Shipped by Newegg", new
R10: https://www.intel.com/content/www/us/en/products/sku/243916/intel-arc-pro-b60-graphics/specifications.html (accessed 2026-11-26) Intel: "Memory Interface 192 bit", "Graphics Memory Bandwidth 456 GB/s"
R11: https://wccftech.com/intel-arc-pro-b70-delivers-80-percent-boost-mlperf-inference-v6-0/ (accessed 2026-11-26) Intel MLPerf Inference v6.0, GPT-OSS-120B offline: 4x Arc Pro B60 (96 GB) about 841 tokens/s, a throughput figure across many requests at once, not one user's speed. No single-user gpt-oss-120b figure on four B60s was found.
R12: https://www.ebay.com/itm/960133609137 (accessed 2026-11-26) eBay: "AMD Radeon Instinct MI50 32GB HBM2 Accelerator (2x 8-pin, 300W)", "US $629.99 Was US $699.99 (10% off)", US seller (8320, 99.7% positive), "5 SOLD TODAY", used
R13: https://www.amd.com/en/support/downloads/drivers.html/accelerators/instinct/instinct-mi-series/instinct-mi50-32gb.html (accessed 2026-11-15) (for local-ai-gpu-tier-list; AMD's page now returns 404) AMD: MI50 32GB memory bandwidth 1 TB/s
R14: https://www.reddit.com/r/LocalLLaMA/comments/1nhd5ks/completed_8xamd_mi50_256gb_vram_256gb_ram_rig_for/ (accessed 2026-11-15) (for cheapest-ways-to-get-128gb-memory-local-ai) builder's post: two MI50 cards ran gpt-oss 120B at about 58 tok/s in an 8-card rig
R15: https://www.apple.com/shop/buy-mac/mac-studio/m5-max-chip-18-core-cpu-40-core-gpu-128gb-memory-512gb-storage (accessed 2026-11-26) Apple: Mac Studio M5 Max 18-core CPU, 40-core GPU, 128GB, 512GB "Buy for $5,099.00", new
R16: https://www.apple.com/mac-studio/specs/ (accessed 2026-11-26) Apple: "M5 Max with 18-core CPU, 40-core GPU, and 16-core Neural Engine (614GB/s memory bandwidth)"; "Maximum continuous power: 480W"
R17: https://github.com/ml-explore/mlx-lm/issues/883 (accessed 2026-11-26) BrunoCerberus: "`mlx_lm.server` starts by wiring ~75% of RAM" (the reporter's analysis; Apple does not document the default): 75% of 128GB is 96GB; raised with sysctl iogpu.wired_limit_mb
R18: https://omlx.ai/benchmarks/d8dnhh1k (accessed 2026-11-15) (for cheapest-ways-to-get-128gb-memory-local-ai) oMLX v0.3.2, Mac Studio M5 Max 128GB, gpt-oss-120b: writing 79.7 tok/s at 1K, 41.4 at 32K
R19: https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc?variant=48746069262490 (accessed 2026-11-26) GMKtec: "GMKtec EVO-X2 AMD Ryzen AI Max+ 395 AI Mini PC" "Sale price $3,499.99 Regular price $3,999.99", 128GB RAM + 1TB SSD, new
R20: https://www.jeffgeerling.com/blog/2025/increasing-vram-allocation-on-amd-ai-apus-under-linux/ (accessed 2026-11-15) Strix Halo: the BIOS allows 96GB at most for the GPU; on Linux the GTT limit can be raised
R21: https://www.amd.com/en/products/processors/laptop/ryzen/ai-300-series/amd-ryzen-ai-max-plus-395.html (accessed 2026-11-15) AMD: Ryzen AI Max+ 395, 256-bit LPDDR5X-8000; 256 bits / 8 x 8,000 MT/s = 256 GB/s (our maths)
R22: https://forum.level1techs.com/t/one-spark-two-spark-red-strix-blue-arc/240937 (accessed 2026-11-15) Level1Techs: Strix Halo (EVO-X2) llama.cpp ROCm, gpt-oss-120b 51.84 tok/s with an empty context, 19.84 at 32K
R23: https://www.newegg.com/p/pl?d=gb10+128gb&N=4131 (accessed 2026-11-26) Newegg, in-stock filter: "ASUS Ascent GX10 AI Supercomputer, DGX Spark, NVIDIA GB10 Superchip, 128GB LPDDR5x, 1TB PCIe Gen4 NVMe SSD" "$5,999.00" "ADD TO CART", new. NVIDIA's own Marketplace lists DGX Spark at $6,950.00 "Out of Stock" and every GB10 box there out of stock (https://marketplace.nvidia.com/en-us/enterprise/personal-ai-supercomputers/)
R24: https://www.nvidia.com/en-us/products/workstations/dgx-spark/ (accessed 2026-11-26) NVIDIA DGX Spark: "Memory Bandwidth 273 GB/s"; "Power Supply 240 Watts"; 128 GB unified memory, GB10
R25: https://forums.developer.nvidia.com/t/memory-creep-on-dgx-spark-where-your-128-gb-actually-goes-and-how-to-stop-it/364886 (accessed 2026-11-15) the OS and desktop take a 7GB baseline: 128 - 7 = 121GB left for a model (our maths)
R26: https://github.com/ggml-org/llama.cpp/discussions/16578 (accessed 2026-11-15) llama.cpp b6922 on DGX Spark (GB10), gpt-oss-120b: 60.57 tok/s empty, 40.55 at 32K. The ASUS Ascent GX10 uses the same GB10 chip; no GX10-specific run was found.
R27: https://github.com/Niko1221/Strata (accessed 2026-11-26) Strata: "Free, open source, and yours to run."; MIT license; hardware: NVIDIA GeForce RTX 20 / 30 / 40 / 50 series; Intel Arc (Linux); Apple Silicon M1 or newer; AMD Ryzen AI Max (Strix Halo); NVIDIA DGX Spark (Linux)
R28: https://github.com/Niko1221/Strata/releases (accessed 2026-11-26) Strata 0.2.22 released 25 Nov 2026; v0.2.20: "Unified 4-tier GPU + RAM + CPU + SSD Mixture-of-Experts execution"; "hot experts in remaining VRAM"; "cold experts in pageable RAM"
R29: https://huggingface.co/openai/gpt-oss-120b (accessed 2026-11-15) gpt-oss-120b: 117B total parameters, 5.1B active; unsloth GGUF files 62.6 to 65.4GB (https://huggingface.co/unsloth/gpt-oss-120b-GGUF)

## Evidence kit

HERO: R1 R12 $16,499.99 for one RTX Pro 6000 against $1,889.97 for three used MI50s, the same 96GB (8.73 times)
COUNTER: R3 the RTX Pro 6000 writes 134.71 tok/s on gpt-oss-120b, the fastest measured figure of any route
STEELMAN: R3 Hardware Corner: "it's the only prosumer GPU that can load this model and its full context"
UNIT-CHAIN: R1 R3 R29 price -> 96GB -> gpt-oss-120b (65GB file) -> 134.71 tok/s -> $122.49 per tok/s
MONEY-OBJECT: R15 the 128GB Mac Studio M5 Max at $5,099.00
PRICES: R1 R4 R6 R9 R12 R15 R19 R23 as of 2026-11-26
BENCH: R3 gpt-oss-120b MXFP4 GGUF, llama.cpp 6112, RTX Pro 6000, 12,000-token context, 134.71 tok/s
STRATA: R27 R28 Strata keeps hot experts in VRAM and cold experts in RAM, so a mixture-of-experts model bigger than 96GB still runs; supports RTX, Intel Arc (Linux), Apple Silicon, Strix Halo and DGX Spark
VIRAL: NONE: no viral post on this exact comparison was found in today's research window
COMMUNITY: R14 a builder's eight-MI50 rig post (two cards, about 58 tok/s on gpt-oss 120B)
UNMEASURED: R11 no single-user gpt-oss-120b figure on four Arc Pro B60s; none on two RTX Pro 5000s
PATTERN: R3 R7 R22 R26 speed drops as the chat gets longer on every route measured at more than one context
SPONSOR: none (no paid sponsor; the ZoneBlade house ad, and one Amazon affiliate link for the 128GB Mac Studio from channel.json affiliate)
ARTEFACT: 2026-11-26 we priced eight routes from live listings and worked dollars per usable GB and per tok/s for each

## Derived figures (our maths)
- Two RTX Pro 5000: 2 x 7,199.99 = 14,399.98. Four 3090s: 4 x 1,800 = 7,200. Four B60s: 4 x 999.99 = 3,999.96. Three MI50s: 3 x 629.99 = 1,889.97.
- Dollars per usable GB: Pro 6000 16,499.99 / 96 = 171.87; two Pro 5000 14,399.98 / 96 = 150.00; four 3090s 7,200 / 96 = 75.00; four B60s 3,999.96 / 96 = 41.67; three MI50s 1,889.97 / 96 = 19.69; Mac 5,099 / 96 = 53.11; EVO-X2 3,499.99 / 96 = 36.46; GX10 5,999 / 121 = 49.58.
- Dollars per tok/s: Pro 6000 16,499.99 / 134.71 = 122.49; four 3090s 7,200 / 73.26 = 98.28; three MI50s 1,889.97 / 58 = 32.59; Mac 5,099 / 79.7 = 63.98; EVO-X2 3,499.99 / 51.84 = 67.52; GX10 5,999 / 60.57 = 99.04.
- Four 3090s rated power: 4 x 350 = 1,400 W.
- Pro 6000 over two Pro 5000: 16,499.99 - 14,399.98 = 2,100.01.
{% endraw %}

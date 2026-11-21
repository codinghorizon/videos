---
layout: default
title: "The $1,500 Local AI Rig Built From Scrap Parts"
permalink: /1500-local-ai-rig-from-scrap-parts/
date: 2026-11-21
---

# The $1,500 Local AI Rig Built From Scrap Parts

{% raw %}
The sources the script cites, as listed with it.

- Dell Precision T7910 listing, 2x Xeon E5-2687W v4, 64GB, 512GB SSD + 2TB, Quadro K5200 8GB, $799.99, read 2026-11-21: https://www.ebay.com/itm/137948851810
- Used Dell Precision T7910 listings (64GB configs $773.84 to $1,099.95), read 2026-11-21: https://www.ebay.com/b/Dell-Precision-T7910-PC-Desktops-All-In-One-Computers/179/bn_89095410
- Dell Precision T7910 refurbished, 64GB, 1300W PSU: https://pcserverandparts.com/dell-precision-t7910-tower-2x-intel-xeon-e5-2667-v3-3-20-ghz-8c-64gb-ddr4-1x-256gb-ssd-nvidia-quadro-k2200-4gb-gddr5-windows-10-professional-refurbished/
- Used DDR4 32GB ECC RDIMM, median used asking price $162 (120 listings, read 2026-11-21): https://cresvament.com/deals/memory/ddr4-32gb-ecc-rdimm
- Tesla P40 used listings, 100 listings, average $329, cheapest $252, read 2026-11-21: https://gpupoet.com/gpu/shop/nvidia-tesla-p40
- Tesla P40, V100, MI50 benchmarks (P40: Qwen3 32B Q4_K_M 12.4 tok/s, gpt-oss-20b 62.7 tok/s, llama.cpp, one card), idle 11W, peak 242W, about 50W resident, nvidia-pstated, Above 4G Decoding, 32GB BAR, CUDA 12, no vLLM, blower over 1A fan header: https://computingforgeeks.com/best-used-datacenter-gpu-local-ai/
- Tesla P40 guide (FP16 at 1/64 rate, Qwen3-Coder-30B-A3B Q4_K_M 29.3 tok/s from LocalScore, EPS adapter, do not force a PCIe cable, 3.6 to 10 tok/s after a duct): https://insiderllm.com/guides/used-tesla-p40-local-ai/
- Tesla P40 for local LLMs (70B Q4_K_M about 42.5GB, needs two cards): https://localaimaster.com/blog/tesla-p40-local-llm
- Tesla P40 vs RTX 3090 (P40 throttles at 88C, 60mm shroud held about 68C, EPS-keyed 8-pin, no display output, 580 driver branch last for Pascal to mid-2028, dual RTX 3090 Llama 3.3 70B Q4_K_M 19.5 tok/s layer split at 290W on PCIe 3.0, 250W and 350W board power): https://specpicks.com/reviews/tesla-p40-vs-rtx-3090-used-local-llm-rig-2026
- Dual Tesla P40 build log, AM4 Ryzen (Qwen3.6-35B-A3B UD-IQ3_S, 262K context, about 20 tok/s generation, over 1,000 tok/s prompt processing; 580 driver): https://franfabrizio.dev/posts/am4-tesla-p40-buildout/
- Two P40s, 70B Q4_K_M (miqu), about 8 tok/s with an empty prompt, 3.3 tok/s after an 8K prompt that took 85 seconds (one user, 2024): https://github.com/ggml-org/llama.cpp/issues/6386
- Cheap used P40 and V100 listings drying up (gpudojo market note, 2026-10-19): https://gpudojo.com/market-notes/2026-10-19-p40-v100-cheap-end
- Tesla blower fan kit with 40mm fan for P40, $23.98: https://www.ebay.com/itm/286377458039
- MODDIY 2x PCIe 8-pin to CPU EPS 8-pin Tesla power cable, $14.99: https://www.moddiy.com/products/5996/NVIDIA-Tesla-K80-M40-M60-P40-P10-P100-GPU-8-Pin-PCIE-Power-Cable.html
- Dell T7910 P40 build note (no spare fan connectors, SATA-powered fans): https://dshills.medium.com/integrating-nvidia-tesla-p40-into-a-consumer-level-computer-for-local-text-generation-18ae021090ec
- RTX 3060 12GB used, average $357, read 2026-11-21: https://resaleprices.com/gpu/nvidia-rtx-3060
- RTX 3060 12GB, Llama 2 7B Q4_0, 76 tok/s (llama.cpp CUDA): https://www.llamabuilds.ai/benchmarks
- AMD MI50 32GB, $629.99 buy-it-now listing: https://www.ebay.com/itm/397284758759
- AMD MI50 32GB llama-bench, Qwen3 Coder 30B A3B Q4_K_M 73.10 tok/s tg128 (ROCm): https://ahelpme.com/ai/llamacpp-ai/llama-bench-the-qwen3-coder-30b-a3b-and-amd-radeon-instinct-mi50-32gb/
- AMD MI50 (gfx906 absent from ROCm 7.14, Vulkan and community builds, no display output until vBIOS flash, 300W, passive): https://localaimaster.com/blog/amd-mi50-local-llm
- RTX 3090 used, average $1,669, read 2026-11-21: https://resaleprices.com/gpu/nvidia-rtx-3090
- RTX 3090 lowest eBay used $1,598, 2026-11-21: https://gpudojo.com/rtx-3090
- RTX 3090, Qwen3.8-27B Q4_K_XL, 41.55 tok/s at 8K (community): https://openclawdc.com/gear/rtx-3090/
- Used RTX 3090 buyer's checklist (memory junction above 100C under load: walk away): https://craftrigs.pages.dev/reviews/used-rtx-3090-buyers-checklist-2026/
- US average residential electricity price, 18.31 cents per kWh, January to July 2026 (EIA Monthly Energy Review): https://www.eia.gov/TOTALENERGY/data/monthly/pdf/sec9_10.pdf
{% endraw %}

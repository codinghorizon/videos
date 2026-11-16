---
layout: default
title: "Owning Local AI At Every Budget (Laptop To 4 GPUs)"
permalink: /owning-local-ai-every-budget/
date: 2026-11-16
---

# Owning Local AI At Every Budget (Laptop To 4 GPUs)

{% raw %}
Every figure the picture shows, and where it comes from. Prices are in PRICES.md (checked
2026-11-15); this file holds speeds, sizes, watts, noise and the arithmetic behind the shots.
Nothing here was measured by us.

| on screen | beats | figure | source |
|---|---|---|---|
| MacBook Air M5, no fan | 024-025, 035 | fanless, lower power limits | https://www.notebookcheck.net/Apple-MacBook-Air-13-M5-gasps-for-air-as-MacBook-Pro-14-M5-shows-40-higher-gaming-performance-in-Cyberpunk-2077.1264788.0.html |
| 32GB Air, Qwen 3.5 35B-A3B Q4_K_M | 026-027 | 31 tok/s | https://ai-radar.it/article/llm-su-apple-silicio-un-benchmark-di-37-modelli-su-macbook-air-m5-32gb |
| dense model on the same Air | 031-033 | ~2.5 tok/s | same |
| 35B-A3B activates ~3B per token | 029 | 3B active | https://huggingface.co/Qwen/Qwen3.5-35B-A3B |
| MacBook Pro M5 vs Air | 036-037 | +40% (40.7%) in Cyberpunk 2077 | Notebookcheck, above |
| RTX 5060 Ti 16GB, Qwen3 14B Q4_K | 044-045 | 41.1 tok/s at 4K | https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-5060-ti-16gb/ |
| 5060 Ti list price | 049 | $429 MSRP vs $838 listing (~2x) | https://rigprice.com/gpu/rtx-5060-ti-16gb/ |
| Qwen 3.8 27B Q4_K_M file | 056-057, 067 | 16.8GB | https://huggingface.co/lmstudio-community/Qwen3.8-27B-GGUF |
| Qwen 3.8 27B on a 3090 | 067-068, 201 | 40.31 tok/s at 4K, 37.02 at 32K | https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/ |
| RTX 3090 board power | 071-072, 127, 132 | 350W, 750W system PSU, 12.3 in, 3-slot | https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090-3090ti/ |
| RTX 3090 idle | 074 | 21W | https://www.servethehome.com/nvidia-geforce-rtx-3090-review-a-compute-powerhouse/7/ |
| RTX 3090 FE noise | 075, 166 | 39 dBA under stress | https://guru3d.com/review/geforce-rtx-3090-founder-review/page-33 |
| RTX 3090 age | 078 | launched Sept 2020 (~6 years) | NVIDIA, above |
| Llama 3.3 70B Q4_K_M | 089, 092 | 42.52GB | https://huggingface.co/bartowski/Llama-3.3-70B-Instruct-GGUF |
| dual 3090, Llama 3.3 70B | 093-097 | 19.5 tok/s layer split, 31.9 tensor split, 290W caps; PCIe 4.0 x8 = 3.0 x16 | https://computingforgeeks.com/build-dual-rtx-3090-llm/ |
| two capped cards | 100 | 2 x 290 = 580W | arithmetic |
| four 3090s, Qwen 3.6 27B FP16, vLLM TP4 | 118-120 | 248 tok/s total | https://ai-radar.it/article/ottimizzare-l-inference-llm-il-sweet-spot-di-efficienza-per-4x-rtx-3090?lang=en |
| 15A circuit | 124-126 | 1,800W rated, 1,440W continuous (80%, 3h+) | https://industrialmonitordirect.com/blogs/knowledgebase/nec-15a-circuit-wattage-limits-continuous-vs-non-continuous-load-calculations ; https://www.slashgear.com/2205960/what-is-the-80-percent-rule-for-circuit-breakers/ |
| four stock 3090s | 127 | 4 x 350 = 1,400W | arithmetic |
| 3090 power limit | 131-133 | 280W within ~1% of stock speed | https://jeanfbrito.github.io/posts/rtx-3090-power-limit-sweet-spot/ |
| four capped cards | 134 | 4 x 280 = 1,120W | arithmetic |
| space heater | 137-138 | 1,500W; 1,120 / 1,500 = 0.75 | https://www.perchenergy.com/energy-calculators/space-heater-electricity-use-cost |
| DeepSeek V4 Flash UD-IQ3_XXS, 8-core cloud VM, no GPU | 159-161 | 104GB, 5.61 tok/s | https://computingforgeeks.com/run-deepseek-v4-flash-locally/ |
| Gigabyte W291-Z00 4U EPYC GPU server | 164-165, 170 | well over 55 dBA at idle, 0.11kW idle | https://servethehome.com/gigabyte-w291-z00-review-amd-epyc-gpu-server/6 |
| US electricity | 174 | 18.16 cents/kWh | https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_5_6_a |
| used 3090 history | 185-186 | $600-800 March; $1,287-1,411 asking early Sept 2026 | https://www.shanethegamer.com/news/old-gpus-are-cashing-in-as-ramageddon-pushes-used-rtx-3090-prices-past-1300/ |

## Wall-meter positions (drawn, not quoted)

The meter's level pips sit at a representative draw for each level so the six are in order on a
watts axis; only the readout figures above are claims. laptop 90W, gaming card 450W, one 3090
550W, two cards 850W, four cards 1,400W, server 1,550W.
{% endraw %}

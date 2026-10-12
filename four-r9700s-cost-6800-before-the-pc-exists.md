---
layout: default
title: "Four R9700s Cost $6,800 Before You Even Get A PC"
permalink: /four-r9700s-cost-6800-before-the-pc-exists/
date: 2026-10-12
---

# Four R9700s Cost $6,800 Before You Even Get A PC

{% raw %}
Checked on 2026-10-12. Every price was read from its live listing that day.

## Radeon AI PRO R9700 32GB

- PowerColor AI PRO R9700 32GB: $1,699.99 on Newegg, "currently sold out" on the day checked. The ASRock Creator R9700 32GB was $1,699.99 and in stock in the same search; Sapphire's was $1,799.99. Four cards at $1,700 is $6,800.
  Sources: https://www.newegg.com/p/N82E16814131885 , https://www.newegg.com/p/pl?d=radeon+ai+pro+r9700+32gb+graphics+card
- Newegg's specification table for the card: 32GB GDDR6, 256 bit memory interface, 20 Gbps memory clock, power consumption 300W. 256 bits x 20 Gbps / 8 = 640 GB/s per card; four cards add up to 2,560 GB/s on paper, as four separate pools of 32GB (128GB in total).
  Source: https://www.newegg.com/p/N82E16814131885
- AMD's product page for the R9700 (specifications).
  Source: https://www.amd.com/en/products/graphics/workstations/radeon-ai-pro/ai-9000-series/amd-radeon-ai-pro-r9700.html

## DGX Spark and the GB10 boxes

- NVIDIA Marketplace: DGX Spark $6,950.00, "Out of Stock" on the day checked.
  Source: https://marketplace.nvidia.com/en-us/enterprise/personal-ai-supercomputers/dgx-spark/
- ASUS Ascent GX10 (NVIDIA GB10, 128GB LPDDR5x, 4TB PCIe Gen5 SSD): $8,299.00 on Newegg.
  Source: https://www.newegg.com/p/2SW-000N-00172?Item=9SIBM9SKYV3568
- NVIDIA's DGX Spark hardware guide: 128 GB LPDDR5x unified system memory, 256 bit, 273 GB/s; 240W external power supply; 150 x 150 x 50.5 mm (50.5 mm is just under two inches).
  Source: https://docs.nvidia.com/dgx/dgx-spark/hardware.html
- Our arithmetic: $6,800 / 128 GB = $53.1 per GB (cards alone); $8,300 / 128 GB = $64.8 per GB (the whole GB10 computer).

## Qwen3.8 27B (dense)

- llamaperf, Radeon AI PRO R9700 32GB: Qwen3.8 27B at 4 bit, 30.4 generated tokens per second, the median of 2 plain runs; no prompt processing median is listed for this model on this card.
  Source: https://llamaperf.com/gpu/radeon-ai-pro-r9700-32gb
- The same site's model page lists the R9700 at 31.3 / 279.3 tok/s for Qwen3.8 125B (6B active) with part of the model in system RAM. That is a different model, which is why the supplied script's "about thirty one" and "two hundred seventy nine" for the 27B were corrected before recording.
  Source: https://llamaperf.com/model/qwen3-8
- One DGX Spark, vLLM v0.27.1, Qwen3.8 27B NVFP4 (Unsloth), DSpark speculative decoding k=7: 29.23 tok/s on fresh code generation. Prefill: 1,527.3 tok/s at ~8K, 1,225.5 at ~32K, 861.1 at ~100K.
  Source: https://github.com/0xBakeer/Qwen3.8-27B-4-bit-on-a-single-DGX-Spark/blob/main/RESULTS.md

## Four R9700 cards, one workstation

- A r/LocalLLaMA owner's build: 4x ASRock Radeon AI PRO R9700 32GB (128GB of VRAM) at PCIe 5.0 x16, Threadripper 9955WX, Seasonic 2200W power supply, Alphacool 360 CPU AIO, Phanteks Enthoo Pro 2 Server case, 11 Arctic P12 Pro fans. llama.cpp, flash attention on, batch 2048: gpt-oss-120b 2,977.83 prompt tok/s and 97.47 generated tok/s; Qwen2.5-32B-Instruct Q4_K_M 848.68 prompt and 25.14 generated tok/s. "Pipeline Parallelism (Layer Split) is significantly faster (~97 t/s) than Tensor Parallelism/Row Split (~67 t/s) for a single user". "I used rocm 7.1.1 for llama.cpp".
  Source: https://www.reddit.com/r/LocalLLaMA/comments/1qgdb7f/4x_amd_r9700_128gb_vram_threadripper_9955wx_build/

## GPT OSS 120B on the DGX Spark

- The official llama.cpp DGX Spark benchmark, gpt-oss 120B MXFP4: pp2048 2,443.91 tok/s, tg32 58.72 tok/s.
  Source: https://github.com/ggml-org/llama.cpp/blob/master/benches/dgx-spark/dgx-spark.md
- The two results come from different builds and settings; neither was run by this channel.

## Power and noise

- Tom's Hardware's DGX Spark review: "typical power usage of about 160 W at the wall under a primarily GPU-driven load"; "the loudest noise level we could measure from the Spark was 37.5 dBA at 18" from the system" under an extended image generation load.
  Source: https://www.tomshardware.com/pc-components/gpus/nvidia-dgx-spark-review/4
- Our arithmetic at an example rate of $0.15 per kWh, 8 hours a day, 365 days: 1.2 kW (four cards at their 300W limit) = 3,504 kWh = $525.60 a year; 0.16 kW = 467.2 kWh = $70.08 a year.

## Cheaper routes

- GMKtec EVO-X2 (Ryzen AI Max+ 395), 128GB RAM + 1TB SSD: sale price $3,499.99 in GMKtec's store.
  Source: https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc?variant=48746069262490
- RigPrice, used RTX 3090 24GB: going rate (used) $1,622 across 74 active listings on the day checked; cheapest screened pick $1,520.
  Source: https://rigprice.com/gpu/rtx-3090/

## Not checked

- No benchmark matching the Spark's ~100K context Qwen3.8 27B prefill run was found for four R9700 cards.
- The GPT OSS 120B comparison is across different software builds and settings (llama.cpp versions, flags), not a controlled test.
{% endraw %}

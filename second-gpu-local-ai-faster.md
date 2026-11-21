---
layout: default
title: "Does A Second GPU Make Local AI Faster?"
permalink: /second-gpu-local-ai-faster/
date: 2026-11-21
---

# Does A Second GPU Make Local AI Faster?

{% raw %}
The sources the script cites, as listed with it.

- Used RTX 3090 going rate $1,921 (RigPrice, updated November 20, 2026): https://rigprice.com/gpu/rtx-3090/
- One vs two RTX 3090s, Qwen3.8-27B UD-Q4_K_M, llama.cpp build 10775, layer split: TG128 39.157 vs 40.556 tok/s, PP4096 1,235 vs 1,616, PP512 about 11% slower; tensor split on PCIe Gen2 x1: TG128 41.1, PP4096 140-169; both cards capped at 300W (one owner's report): https://note.com/agentworkflowlab/n/nc4683f6203e9
- Two Radeon AI PRO R9700s, llama.cpp ROCm 7.2.2: Qwen3.6 27B Q5_K_M tg128 24.85 one card, 24.31 layer split (one owner's report): https://github.com/truelies444/amd-radeon-ai-pro-r9700-llama-cpp-rocm-benchmarks
- Two RX 7900 XTXs, Qwen3.8-27B Q4_K_XL tg512: 36.05 one card, 34.03 layer split: https://github.com/ggml-org/llama.cpp/issues/28863
- Ollama FAQ, a model that fits one GPU loads on that GPU; OLLAMA_MAX_LOADED_MODELS defaults to 3 x the number of GPUs: https://docs.ollama.com/faq
- gpt-oss-120B MXFP4 on one RTX 3090 (-ngl 12) 2.33 tok/s and two RTX 3090s (-ngl 24, 50/50) 7.09 tok/s (one owner's report): https://gist.github.com/slewsys/da27a118587b6a50abe1218c55f215a0
- Dual RTX 3090 build: Llama 3.3 70B Q4_K_M 19.5 tok/s layer split, 31.9 tensor split; Qwen3 32B Q4_K_M 35.3 tok/s one card, 59.8 two cards tensor; vLLM Qwen3 32B AWQ 8 users 201.1 vs 290.8 tok/s, KV cache 11,536 vs 97,632 tokens: https://computingforgeeks.com/build-dual-rtx-3090-llm/
- Dual GPU build power: about 1,020W at the wall for two RTX 3090s, 1,200-1,500W PSU recommended, 283W per card average with tensor split: https://computingforgeeks.com/dual-gpu-llm-build-pcie-power
- One RTX 3090 with CPU offload, Llama 3.3 70B UD-Q4_K_XL, 2.03 tok/s on a Xeon E5-2673 v4: https://www.hardware-corner.net/guides/llama-cpp-vs-ik_llama-cpp/
- llama.cpp tensor split PR #19378 (experimental, merged April 2026): 2x RTX 4090 Qwen 3.5 35B-A3B Q4_0 205.74 layer vs 141.41 tensor; best on large dense models: https://github.com/ggml-org/llama.cpp/pull/19378
- llama.cpp multi-GPU docs (tensor mode experimental, limited by GPU interconnect speed): https://github.com/ggml-org/llama.cpp/blob/master/docs/multi-gpu.md
- ASRock B850 Steel Legend second x16 slot runs at x4 from the chipset, disabled when M.2 slot 4 is used: https://wccftech.com/review/asrock-b850-motherboards-review-riptide-lightning-steel-legend-livemixer-aiming-200-usd-am5-segment/amp/
- ASUS ProArt X870E-Creator WiFi, x8/x8 with both slots in use: https://www.asus.com/motherboards-components/motherboards/proart/proart-x870e-creator-wifi/techspec/
- RTX 3090 memory bandwidth 936 GB/s: https://www.techpowerup.com/gpu-specs/geforce-rtx-3090.c3622
- RTX 3060 12GB memory bandwidth 360 GB/s: https://www.techpowerup.com/gpu-specs/geforce-rtx-3060-12-gb.c3682
- Used RTX 3060 12GB going rate $380 (RigPrice, November 20, 2026): https://rigprice.com/gpu/rtx-3060-12gb/
- Qwen 3.8 27B Q4_K_M GGUF, 16.8GB: https://huggingface.co/lmstudio-community/Qwen3.8-27B-GGUF
- Draft model on the second GPU: 46.90 tok/s base, 48.28 with draft (one owner's report): https://github.com/ggml-org/llama.cpp/discussions/21975
- Corsair RM1200e, $204.99 (Corsair store): https://www.corsair.com/us/en/p/psu/CP-9020316-NA/rme-series-rm1200e-fully-modular-low-noise-atx-power-supply-cp-9020316-na
- US average residential electricity price, 18.16 cents per kWh, August 2026 (EIA): https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_5_6_a
- Used RTX 5090 going rate $6,999 (RigPrice, November 20, 2026): https://rigprice.com/gpu/rtx-5090/
- RTX 5060 Ti 16GB used going rate $810 (RigPrice, November 20, 2026): https://rigprice.com/gpu/rtx-5060-ti-16gb/
{% endraw %}

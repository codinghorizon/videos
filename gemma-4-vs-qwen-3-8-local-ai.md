---
layout: default
title: "Gemma 4 vs Qwen 3.8 (Local AI)"
permalink: /gemma-4-vs-qwen-3-8-local-ai/
date: 2026-11-08
---

# Gemma 4 vs Qwen 3.8 (Local AI)

{% raw %}
The sources the script cites, as listed with it.

VIEWER-COMMENT: T-oTMMtDJYo "gemma4 26b was a decent pick for a while"
- Gemma 4 31B model card (benchmarks for every Gemma 4 size, Apache 2.0, modalities): https://huggingface.co/google/gemma-4-31B-it
- Gemma 4 26B A4B model card (25.2B total, 3.8B active): https://huggingface.co/google/gemma-4-26B-A4B-it
- Gemma 4 12B model card: https://huggingface.co/google/gemma-4-12B-it
- Gemma 4 E4B model card: https://huggingface.co/google/gemma-4-E4B-it
- Qwen 3.8 27B model card (GPQA Diamond 89.2, LiveCodeBench v6 90.3, HLE 30.8, Apache 2.0, video input): https://huggingface.co/Qwen/Qwen3.8-27B
- Qwen 3.8 Flash Next model card (125B total, 6B active, qwen-community-1.0 licence, benchmarks): https://huggingface.co/Qwen/Qwen3.8-Flash-Next
- Unsloth Gemma 4 31B GGUF (Q4_K_M 18.3GB, Q8_0 32.6GB): https://huggingface.co/unsloth/gemma-4-31B-it-GGUF
- Unsloth Gemma 4 26B A4B GGUF (UD-Q4_K_M 16.9GB): https://huggingface.co/unsloth/gemma-4-26B-A4B-it-GGUF
- Unsloth Gemma 4 12B GGUF (Q4_K_M 7.12GB): https://huggingface.co/unsloth/gemma-4-12b-it-GGUF
- Unsloth Qwen 3.8 27B GGUF (UD-Q4_K_M 16.5GB, Q8_0 29GB): https://huggingface.co/unsloth/Qwen3.8-27B-GGUF
- Unsloth Qwen 3.8 Flash Next GGUF (UD-Q4_K_XL 111.3GB): https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF
- RTX 3060 12GB, owner report, Gemma 4 12B 40 t/s and Qwen 3.8 27B IQ2_M 20 t/s: https://llamaperf.com/report/b68e9f51-1a5a-448a-878c-d99057086f7f
- RTX 3060 12GB + 16GB RAM, Betelgeuse, Qwen 3.8 Flash Next IQ4_XS 24.0 t/s: https://llamaperf.com/report/b716ca28-6fcc-4372-bca7-351d17495c8a
- RTX 5060 Ti 16GB (Gemma 4 26B 4-bit 95.2 t/s, Qwen 3.8 27B 3-bit 28.8 t/s, MTP runs): https://llamaperf.com/gpu/rtx-5060-ti-16gb
- RTX 3090 (Qwen 3.8 27B 4-bit 37.4 t/s median of 6, Gemma 4 31B 4-bit 36.5 t/s): https://llamaperf.com/gpu/rtx-3090
- Gemma 4 26B A4B on an RTX 3090, Q4_K_XL, llama.cpp, 128.08 tok/s: https://insiderllm.com/guides/wicked-fast-gemma-4-26b-a4b-vs-qwen-3-6-27b-rtx-3090/
- RTX 5090 (Qwen 3.8 27B 4-bit 80.0 t/s median of 7, Gemma 4 26B 4-bit 243.9 t/s): https://llamaperf.com/gpu/rtx-5090
- Strix Halo (Qwen 3.8 Flash Next 4-bit 26.6 t/s median of 8): https://llamaperf.com/gpu/strix-halo
- Qwen 3.8 Flash Next on Strix Halo, 20.6 tok/s falling to 15.3 at 26K depth: https://sleepingrobots.com/dreams/qwen38-flash-next-strix-halo/
- Used RTX 3060 12GB, $380 going rate (47 listings): https://rigprice.com/gpu/rtx-3060-12gb/
- RTX 5060 Ti 16GB, $890 new going rate: https://rigprice.com/gpu/rtx-5060-ti-16gb/
- Used RTX 3090, $1,800 going rate (91 listings): https://rigprice.com/gpu/rtx-3090/
- RTX 5090, $7,544 new going rate: https://rigprice.com/gpu/rtx-5090/
- GMKtec EVO-X2 128GB, $3,499.99: https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc?variant=48746069262490
{% endraw %}

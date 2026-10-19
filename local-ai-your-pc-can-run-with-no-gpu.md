---
layout: default
title: "The Local AI Your PC Can Run With No GPU (October 2026)"
permalink: /local-ai-your-pc-can-run-with-no-gpu/
date: 2026-10-19
---

# The Local AI Your PC Can Run With No GPU (October 2026)

{% raw %}
The sources the script cites, as listed with it.

- Qwen3 30B-A3B on Ryzen 9 9950X with 2x48GB DDR5-6400, ik_llama.cpp CPU (33.9 tok/s): https://huggingface.co/ubergarm/Qwen3-30B-A3B-GGUF/discussions/2
- Qwen3 30B-A3B-2507 on Ryzen 7 8745HS, mainline llama.cpp vs ik_llama.cpp CPU (22 vs 25-26 tok/s): https://github.com/ikawrakow/ik_llama.cpp/discussions/666
- Qwen3 Coder 30B-A3B on Ryzen 9 3950X CPU (~14 tok/s): https://news.ycombinator.com/item?id=45148237
- LocalScore CPU runs on Ryzen 9 9950X3D with 2x16GB DDR5-6000 (Llama 3.2 1B, Llama 3.1 8B, Qwen3 32B): https://openbenchmarking.org/result/2505223-PTS-LOCALSCO14
- LocalScore GPU results for Llama 3.1 8B (RTX 3060 12GB): https://www.localscore.ai/model/1
- llama.cpp CPU runs on Ryzen 9 9950X with DDR5-6000 (Llama 3.1 Tulu 3 8B Q8_0): https://openbenchmarking.org/result/2509083-NE-LLAMACPU914
- llama.cpp CPU runs on Ryzen 9 5950X with 4x32GB DDR4-3600 (Llama 3.1 Tulu 3 8B Q8_0): https://openbenchmarking.org/result/2501266-NE-RYZEN595072
- llama.cpp CPU runs on a Ryzen AI 9 HX 370 laptop with 32GB LPDDR5-7500 (gpt-oss-20b Q8_0): https://openbenchmarking.org/result/2509086-NE-DKDLD849143
- Llama 7B Q4_0 on an i7-8550U laptop and a Ryzen AI 7 350 laptop, CPU: https://www.mgroeber.de/benchmarking-llamacpp-on-legacy-hardware-2.html
- Qwen3 Coder Next on a Ryzen AI 9 HX PRO 370 with 96GB DDR5-5600, CPU (7.74 tok/s): https://github.com/ggml-org/llama.cpp/issues/19480
- Qwen 3.8 Flash Next on a 96GB desktop, CPU only (11.1 tok/s): https://huggingface.co/Qwen/Qwen3.8-Flash-Next/discussions/22
- Qwen 3.8 Flash Next with GPU offload (43.7 tok/s): https://huggingface.co/Qwen/Qwen3.8-Flash-Next/discussions/29
- llama-bench thread scaling: https://github.com/ggml-org/llama.cpp/blob/master/tools/llama-bench/README.md
- Memory bandwidth and LLM speed: https://www.hardware-corner.net/memory-bandwidth-llm-speed/
- DDR4 bandwidth: https://en.wikipedia.org/wiki/DDR4_SDRAM
- DDR5 bandwidth: https://en.wikipedia.org/wiki/DDR5_SDRAM
- Qwen 3.8 27B on a used RTX 3090: https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/
- Qwen3.5 9B model card (MMLU-Pro, LiveCodeBench, WMT24++ vs gpt-oss): https://huggingface.co/Qwen/Qwen3.5-9B
- Qwen3.5 4B model card: https://huggingface.co/Qwen/Qwen3.5-4B
- Qwen3.5 35B-A3B model card (SWE-bench Verified vs GPT-5 mini): https://huggingface.co/Qwen/Qwen3.5-35B-A3B
- Qwen3.6 35B-A3B model card: https://huggingface.co/Qwen/Qwen3.6-35B-A3B
- Qwen 3.8 27B model card: https://huggingface.co/Qwen/Qwen3.8-27B
- Qwen 3.8 Flash Next model card and licence: https://huggingface.co/Qwen/Qwen3.8-Flash-Next
- Qwen models on Hugging Face (no Qwen 4 weights): https://huggingface.co/Qwen
- Phi-4-mini model card (limits of small models): https://huggingface.co/microsoft/Phi-4-mini-instruct
- gpt-oss-20b model card: https://huggingface.co/openai/gpt-oss-20b
- gpt-oss paper (SWE-bench Verified 60.7): https://arxiv.org/html/2508.10925v1
- GGUF sizes: https://huggingface.co/unsloth/Qwen3.5-4B-GGUF, https://huggingface.co/unsloth/Qwen3.5-9B-GGUF, https://huggingface.co/unsloth/Qwen3.5-35B-A3B-GGUF, https://huggingface.co/unsloth/Qwen3-30B-A3B-GGUF, https://huggingface.co/unsloth/Qwen3-32B-GGUF, https://huggingface.co/unsloth/Qwen3.8-27B-GGUF, https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF, https://huggingface.co/unsloth/gpt-oss-20b-GGUF, https://huggingface.co/bartowski/Llama-3.3-70B-Instruct-GGUF
- DDR5 prices nearly 5x year on year (TrendForce, August 2026): https://www.trendforce.com/news/2026/08/17/news-germany-ddr5-prices-near-5x-yoy-in-august-china-reportedly-sees-14-wow-jump-as-global-rally-continues/
- 32GB DDR5-6000 kits went from about $120-$130 to about $500-$520 in six months (PCPartPicker, via TechRadar, February 2026): https://www.techradar.com/pro/ram-prices-are-skyrocketing-but-this-32gb-g-skill-flare-x5-ddr5-6000-kit-is-over-usd100-off-right-now
- Patriot Viper Venom 32GB (2x16GB) DDR5-6000, $459.99 at Newegg (October 19): https://www.newegg.com/p/N82E16820225430
- Team T-Force Delta RGB 64GB (2x32GB) DDR5-5200, $919.99 at Newegg (October 19): https://www.newegg.com/p/N82E16820331982
- G.SKILL Ripjaws S5 96GB (2x48GB) DDR5-5200, $1,419.99 at Newegg (October 19): https://www.newegg.com/p/N82E16820374540
- Kingston FURY Beast 128GB (4x32GB) DDR5-5200, $2,399.99 at Newegg (October 19): https://www.newegg.com/p/0RM-001W-006P3
- GeIL ORION 32GB (2x16GB) DDR4-3200, $209.99 at Newegg (October 19): https://www.newegg.com/p/N82E16820991076
- Sapphire Pulse RX 9060 XT 16GB, $519.99 at Newegg (October 19): https://www.newegg.com/p/N82E16814202457
- Used RTX 3060 12GB going rate (October 19): https://rigprice.com/gpu/rtx-3060-12gb/
- Used RTX 3090 going rate (October 19): https://rigprice.com/gpu/rtx-3090/
- Acer Aspire Lite 16, Ryzen AI 5 330, 16GB, $749.99 at Newegg (October 19): https://www.newegg.com/p/N82E16834360453
- llama.cpp Qwen3 Next CPU kernels (PR 20334): https://github.com/ggml-org/llama.cpp/pull/20334
{% endraw %}

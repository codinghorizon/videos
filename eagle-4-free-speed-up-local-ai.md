---
layout: default
title: "Your Local AI Gets 2x Faster Without a New Graphics Card"
permalink: /eagle-4-free-speed-up-local-ai/
date: 2026-10-22
---

# Your Local AI Gets 2x Faster Without a New Graphics Card

{% raw %}
The sources the script cites, as listed with it.

- EAGLE-4 official repo (engines, hardware, speedup table, license): https://github.com/eagle-hq/EAGLE-4
- EAGLE-4 technical deep dive, fal, October 20, 2026: https://blog.fal.ai/eagle-4-technical-deepdive/
- EAGLE-4 summary (vendor-reported figures): https://daily.dev/posts/eagle-4-speeds-up-llm-inference-with-an-adaptive-speculative-decoding-drafter-2hx4eb8tv
- EAGLE-4 on AMD Instinct MI355X: https://www.amd.com/en/developer/resources/technical-articles/2026/eagle-4-on-amd-instinct-gpus.html
- EAGLE-4 does not run on a Mac; MTP on Mac Studio M2 Ultra 64GB with oMLX (Qwen3.8-27B, Ornith-1.5-35B-A3B): https://dev.to/romantsisyk/eagle-4-does-not-run-on-a-mac-i-measured-mtp-instead-92-on-one-model-19-on-another-5g9a
- CPU-only draft model speedup (Qwen2.5-Coder 3B, 12.9 to 22.1 tok/s): https://inventivehq.com/blog/llama-cpp-speculative-decoding-consumer-gpu
- RTX 5060 Ti 16GB, Qwen 3.8 27B UD-IQ3_XXS with MTP (29.18 to 63.89 tok/s at 4K; 23.62 to 45.48 at 32K): https://njannasch.dev/blog/qwen-3-8-27b-5060ti-mtp-coding/
- RTX 3090, Qwen3.8-27B UD-Q4_K_XL with MTP (41.55 to 66.39 tok/s; n-max 5 +32%; 0.8B draft -29.8%; output divergence): https://hackmd.io/@thc1006/qwen3-8-27b-speculative-decoding-rtx-3090
- RTX 4090, RTX 5090 and L40S with Ollama default MTP and vLLM (39.9 to 76.2; 76.8 to 129.7; 413 tok/s at 4 requests; driver 570 at 59.9): https://computingforgeeks.com/ollama-vs-vllm-vs-llama-cpp/
- RX 7900 XTX MTP on Vulkan (Qwen3.6-27B, about 81 tok/s): https://blog.bymar.co/posts/speculative-decoding-local-llms-2026/
- RX 7900 XTX owner's report: https://www.reddit.com/r/LocalLLM/comments/1ta42t1/llamacpp_turboquant_mtp_on_7900_xtx/
- llama.cpp MTP support, PR #22673, merged May 16, 2026 (Vulkan note): https://github.com/ggml-org/llama.cpp/pull/22673
- llama.cpp speculative decoding docs (draft-mtp, draft-eagle3, supported EAGLE-3 drafts): https://github.com/ggml-org/llama.cpp/blob/master/docs/speculative.md
- Google, Gemma 4 multi-token prediction drafters, May 5, 2026 (up to 3x; about 2.2x on Apple Silicon for 26B at batch 4 to 8): https://blog.google/innovation-and-ai/technology/developers-tools/multi-token-prediction-gemma-4/
- Gemma 4 MTP docs: https://ai.google.dev/gemma/docs/mtp/overview
- Ollama releases: https://github.com/ollama/ollama/releases
- Ollama draft_num_predict option (user report): https://github.com/open-webui/open-webui/discussions/27479
- Ollama qwen3.8 library page: https://ollama.com/library/qwen3.8
- LM Studio 0.4.14 (MTP): https://lmstudio.ai/changelog/lmstudio-v0.4.14
- LM Studio 0.3.10, speculative decoding (2.43x best prompt on Qwen2.5-32B with a 0.5B draft, M3 Pro): https://lmstudio.ai/blog/lmstudio-v0.3.10
- RTX 5060 Ti 16GB, $838 lowest screened new listing (October 21): https://rigprice.com/gpu/rtx-5060-ti-16gb/
- Used RTX 3090, $1,700 going rate (October 21): https://rigprice.com/gpu/rtx-3090/
- Used RTX 4090, $3,500 asking (October 20): https://rigprice.com/gpu/rtx-4090/
- RTX 5090, $7,769.99 cheapest new at Newegg (October 21): https://www.newegg.com/asus-rog-astral-rog-astral-rtx5090-32g-gaming-geforce-rtx-5090-32gb-graphics-card-triple-fans/p/N82E16814126750
- Price board: https://locallyexplains.site/prices/
{% endraw %}

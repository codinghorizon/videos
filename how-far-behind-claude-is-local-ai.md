---
layout: default
title: "How Far Behind Claude Is Local AI Right Now?"
permalink: /how-far-behind-claude-is-local-ai/
date: 2026-11-21
---

# How Far Behind Claude Is Local AI Right Now?

{% raw %}
The sources the script cites, as listed with it.

- Artificial Analysis Intelligence Index leaderboard (Fable 5.2 65, Opus 5.5 59, Sonnet 5.5 55, Kimi K3.1 Pro 46, DeepSeek V4.1 Flash 1017 33, Qwen3.8 Flash-Next 29, Qwen3.8 27B 20): https://artificialanalysis.ai/leaderboards/models
- Claude Haiku 5.5 (index 36, output speed 254 tok/s): https://artificialanalysis.ai/models/claude-haiku-5-5
- Claude Opus 5.5 (index 59, output speed 105-113 tok/s, 356.95 s to first answer token at Max, 5.78 s at Low, index 35 at Low): https://artificialanalysis.ai/models/claude-opus-5-5
- Claude Sonnet 5.5 (index 55, 136-147 tok/s): https://artificialanalysis.ai/models/claude-sonnet-5-5
- Claude Fable 5.2 (index 65): https://artificialanalysis.ai/models/claude-fable-5-2
- Artificial Analysis Intelligence Index v5 methodology: https://artificialanalysis.ai/articles/artificial-analysis-intelligence-index-v5
- Open-weights index (Kimi K3.1 Pro 46): https://artificialanalysis.ai/models/open-source
- Qwen 3.8 27B on Artificial Analysis (20): https://artificialanalysis.ai/models/qwen3-8-27b
- Qwen 3.8 Flash-Next on Artificial Analysis (29): https://artificialanalysis.ai/models/qwen3-8-flash-next
- DeepSeek V4.1 Flash 1017 on Artificial Analysis (33): https://artificialanalysis.ai/models/deepseek-v4-1-flash-1017
- Claude 3.7 Sonnet, SWE-bench Verified 63.7% without scaffold (February 24, 2025): https://www.anthropic.com/news/claude-3-7-sonnet
- Claude Sonnet 4, SWE-bench Verified 72.7% (May 22, 2025): https://www.anthropic.com/news/claude-4
- Claude Sonnet 4.6 system card, SWE-bench Verified 79.6 (February 2026): https://www.anthropic.com/claude-sonnet-4-6-system-card
- Claude Opus 5.5, Terminal-Bench 4.0 66.4%: https://www.anthropic.com/news/claude-opus-5-5
- Claude plans (Pro $20 a month): https://claude.com/pricing
- Qwen3.6 35B-A3B model card (35B total, 3B active, SWE-bench Verified 73.4): https://huggingface.co/Qwen/Qwen3.6-35B-A3B
- gpt-oss-20b model card (SWE-bench Verified 60.7): https://arxiv.org/html/2508.10925
- Qwen 3.8 27B model card: https://huggingface.co/Qwen/Qwen3.8-27B
- Qwen 3.8 Flash-Next model card (125B total): https://huggingface.co/Qwen/Qwen3.8-Flash-Next
- Qwen 3.8 Flash-Next 4-bit needs 64GB (Unsloth): https://unsloth.ai/docs/models/qwen3.8-next
- DeepSeek V4.1 Flash model card (552B total, Terminal-Bench 4.0 31.2): https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash
- Kimi K3.1 Pro model card (Terminal-Bench 4.0 65.7): https://huggingface.co/moonshotai/Kimi-K3.1-Pro
- Kimi K3 model card (2.8T parameters): https://huggingface.co/moonshotai/Kimi-K3
- RTX 3060 12GB, Qwen3.6 35B-A3B UD-Q4_K_M with partial MoE offload, 37.91 tok/s at 8,192 context, 9.8GB VRAM: https://insiderllm.com/benchmarks/
- RTX 5060 Ti 16GB, gpt-oss 20B MXFP4 58.1 tok/s at 64K (Hardware Corner): https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-5060-ti-16gb/
- RTX 3090, Qwen3.6 35B-A3B UD-Q4_K_XL in llama.cpp at 65K context, 101.7 / 80.9 tok/s (Amine Raji): https://aminrj.com/posts/llamacpp-qwen36-35b/
- RTX 3090, Qwen 3.8 27B Q4_K_S 33.95 tok/s at 64K (Hardware Corner): https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/
- RTX 5090, Qwen3.6 35B-A3B UD-Q4_K_M llama.cpp CUDA tg128 270.97 tok/s: https://huggingface.co/datasets/omegaprime669/rtx-5090-benchmarks
- Qwen 3.8 Flash-Next on a Ryzen AI Max+ 395 mini PC, 20 tok/s short prompt and 15.3 at about 26K with a hipCUB-patched llama.cpp: https://sleepingrobots.com/dreams/qwen38-flash-next-strix-halo/
- Tuned EngramHalo.cpp fork, 28-38 tok/s: https://sleepingrobots.com/dreams/engramhalo-qwen38-flash-next-strix-halo/
- DeepSeek V4.1 Flash 1017 on a 512GB M5 Ultra (oMLX, 61.2-80.3 tok/s from 1K to 195K context): https://omlx.ai/benchmarks/performance/ike0mcrd
- RTX 3060 12GB, $459.99 new (Gigabyte Windforce OC): https://www.newegg.com/p/N82E16814932658
- RTX 5060 Ti 16GB, $799.99 new (PNY Dual Fan OC): https://www.newegg.com/p/N82E16814133993
- Used RTX 3090, $1,921 going rate (RigPrice, November 20, 2026): https://rigprice.com/gpu/rtx-3090/
- RTX 5090, cheapest $6,199.99 at Newegg (ASUS ProArt OC): https://www.tweaktown.com/news/114681/nvidia-rtx-5090-returns-to-newegg-stock-but-prices-start-at-over-3x-msrp/index.html
- GMKtec EVO-X2 128GB, $3,499.99: https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc?variant=48746069262490
- Mac Studio M5 Ultra 512GB, $22,299 with 1TB: https://macrumors.com/2026/10/28/mac-studio-m5-ultra-512gb-ram/
- Locally price tracker: https://locallyexplains.site/prices/
{% endraw %}

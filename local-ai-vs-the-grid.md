---
layout: default
title: "Local AI vs Paying Per Request (The Grid)"
permalink: /local-ai-vs-the-grid/
date: 2026-11-22
---

# Local AI vs Paying Per Request (The Grid)

{% raw %}
The sources the script cites, as listed with it.

- The Grid pricing page (30-day averages: Text Standard $0.035, Text Prime $0.120, Code Prime $0.120, Agent Standard $0.035, Code Max $1.709 per 1M tokens; tool calling, streaming, structured outputs), read 2026-11-21: https://thegrid.ai/pricing
- The Grid live model list (text-prime $0.0997 and text-standard $0.0295 per 1M; MiniMax-M3 served 91% of text-prime over the 30 days to 2026-11-12 and is now listed as retired; allowed text-prime models DeepSeek V4.1 Flash, GLM-5.2, Kimi K2.6; code-prime DeepSeek V4.1 Flash, Kimi K2.6; text-standard and agent-standard 99% GPT-6 Luna, 1% GPT-OSS 120B; code-max Claude Opus 5.5 100%), read 2026-11-21: https://api.thegrid.ai/v1/models
- The Grid current instruments (quality floors, TTFT caps, throughput floors: Text Standard 70 tok/s, Text Prime 40 tok/s and 5 s; "How to choose": routing across tiers): https://thegrid.ai/docs/instrument-specifications/current-instruments
- The Grid order book and matching (input and output tokens counted the same, tokens currently do not expire): https://thegrid.ai/docs/concepts/order-book-and-matching
- The Grid quickstart (base URL https://api.thegrid.ai/v1, API key, model string): https://thegrid.ai/docs/start-here/quickstart
- The Grid reselling tokens (requires Advanced Mode): https://thegrid.ai/docs/concepts/reselling
- The Grid errors and rate limits (free accounts 100 requests a day, lifted by a first deposit; concurrency by deposit, $50 to $150 = 30 concurrent requests): https://thegrid.ai/docs/api-reference/errors-and-rate-limits
- The Grid data handling and privacy (free accounts' prompts and completions stored; any first deposit makes an account paid with zero data retention; providers configured with ZDR or a similar control): https://thegrid.ai/docs/data-handling-and-privacy/data-handling-and-privacy
- The Grid brand facts (Grid Markets LLC, built by Spectral Labs): https://thegrid.ai/brand-facts.json
- RTX 3060 12GB used, average $357, read 2026-11-21: https://resaleprices.com/gpu/nvidia-rtx-3060
- RTX 3060 power 170 W: https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3060-3060ti/
- RTX 5060 Ti 16GB, PNY Dual Fan OC, $799.99 new, read 2026-11-21: https://www.newegg.com/p/N82E16814133993
- RTX 3090 used, lowest eBay listing $1,598, read 2026-11-21: https://gpudojo.com/rtx-3090
- RTX 5090 cheapest new on Newegg $6,199.99, over 3x MSRP (TweakTown): https://www.tweaktown.com/news/114681/nvidia-rtx-5090-returns-to-newegg-stock-but-prices-start-at-over-3x-msrp/index.html
- RTX Pro 6000 Blackwell Max-Q 96GB, $16,999.99 on Newegg, read 2026-11-21: https://www.newegg.com/p/pl?d=rtx+pro+6000+blackwell
- llama.cpp gpt-oss benchmarks, tg128 and pp2048 (gpt-oss-20b: RTX 3060 30.64 / 2,229.95 with some expert layers on CPU, RTX 5060 Ti 111.51 / 3,839.21, RTX 3090 161.77 / 5,170.56, RTX 5090 282.51 / 9,848.38; gpt-oss-120b MXFP4 59.02 GiB on RTX Pro 6000 Max-Q 170.62 / 4,494.20): https://github.com/ggml-org/llama.cpp/discussions/15396
- gpt-oss-120b MXFP4 on RTX Pro 6000 Max-Q in vLLM, 500 requests, 4,630 tok/s average, 0 errors (one owner's report): https://forums.developer.nvidia.com/t/gpt-oss-120b-mxfp4-on-rtx-pro-6000-blackwell-max-q-sm120-full-debug-path-what-was-actually-broken-and-what-finally-worked/365333
- RTX Pro 6000 Max-Q power consumption 300 W: https://www.nvidia.com/en-us/products/workstations/professional-desktop-gpus/rtx-pro-6000-max-q/
- RTX 5060 Ti power 180 W: https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5060-family/
- RTX 3090 power 350 W: https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090-3090ti/
- RTX 5090 power 575 W: https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/
- DeepSeek V4.1 Flash model card (552B total parameters): https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash
- US average residential electricity price, 18.16 cents per kWh, August 2026 (EIA Electric Power Monthly, table 5.6.A): https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_5_6_a
{% endraw %}

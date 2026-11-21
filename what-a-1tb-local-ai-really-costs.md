---
layout: default
title: "What A 1TB Local AI Really Costs"
permalink: /what-a-1tb-local-ai-really-costs/
date: 2026-11-21
---

# What A 1TB Local AI Really Costs

{% raw %}
The sources the script cites, as listed with it.

- Mistral Large 4 model card (1T total, 49B active per token / 52B with embeddings and output layers, FP8 weights): https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B
- Mistral Large 4 file listing, 1,060.6GB in 54 FP8 shards: https://huggingface.co/mistralai/Mistral-Large-4-1T-A52B/tree/main
- Mistral docs model page, 1.05T total, 52B active: https://docs.mistral.ai/models/mistral-large-4-0
- llama.cpp GGUF sizes, Q8_0 1,115GB, Q4_K_M 635GB, Q2_K 381GB, IQ2_XXS 298GB: https://huggingface.co/ggml-org/Mistral-Large-4-1T-A52B-GGUF
- Unsloth GGUF sizes and RAM guidance: https://unsloth.ai/docs/models/mistral-large-4
- Hugging Face blog, Mistral Large 4 local runs: about 15 tok/s generation and 90 tok/s prefill on one M3 Ultra 512GB at Q2_K in llama.cpp; about 30 tok/s and 500 tok/s prefill on 4x RTX Pro 6000 at IQ2_XXS: https://huggingface.co/blog/mistral-large4
- Mistral API pricing, $0.70 input / $2.10 output per million tokens: https://docs.mistral.ai/inference/pricing
- Mistral Le Chat plans, Pro $14.99 a month: https://mistral.ai/pricing
- Dell PowerEdge R740 configurator (chassis $399, 2x Xeon Gold 6248R $550 each, 12x 64GB DDR4-2933 $590 each, 2x 1600W PSU $69), read 2026-11-21: https://newserverlife.com/configure/dell-poweredge-r740_8sff/
- Kimi K2 quant author's bandwidth estimate and multi-NUMA note: https://huggingface.co/ubergarm/Kimi-K2-Thinking-GGUF/discussions/8
- Mac Studio M5 Ultra 512GB, $22,299: https://macrumors.com/2026/10/28/mac-studio-m5-ultra-512gb-ram/
- Apple Mac Studio store: https://www.apple.com/shop/buy-mac/mac-studio
- Mac Studio M5 Ultra 1.2TB/s memory bandwidth: https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/
- Mac Studio power, M5 Ultra 385W maximum, 9W idle: https://support.apple.com/en-us/102027
- V-Color DDR5 256GB (4x64GB) RDIMM kit, $11,599.99 on Newegg, read 2026-11-21: https://www.newegg.com/V-Color-256GB/p/1X5-0039-00027
- 64GB DDR5 RDIMM price history (mid-$300s in September 2025): https://www.nexus-compute.com/blog/64gb-ddr5-rdimm-price-2026
- AMD EPYC 9175F, $1,999 on Newegg: https://www.newegg.com/amd-epyc-9175f-socket-sp5/p/N82E16819113871
- Supermicro H13SSL-N, $649 on Newegg: https://www.newegg.com/p/pl?d=supermicro+h13ssl-n
- Kimi K2.5 on EPYC 9175F with 768GB DDR5-6400, CPU only, llama.cpp Q4_K_S, 10.27 tok/s (32B active); Q4_K_M with a 16,148-token prompt, 2.44 tok/s: https://loftllc.dev/en/docs/tech/llm-research/kimi-k2-5-1t-cpu-inference-and-long-context/
- Kimi K2.6 on an M3 Ultra 512GB, about 20-26 tok/s fresh, about 13 tok/s past 7-13K tokens of context (one owner's report): https://rentamac.io/run-kimi-k2-on-mac/
- Apple MLX distributed inference, 2x M5 Ultra 512GB, Muse Spark Open (816B) 24.99 tok/s tensor parallel: https://machinelearning.apple.com/research/mlx-distributed-inference
- RDMA over Thunderbolt 5 (Apple TN3205): https://developer.apple.com/documentation/technotes/tn3205-low-latency-communication-with-rdma-over-thunderbolt
- RTX Pro 6000 Blackwell listings on Newegg: https://www.newegg.com/p/pl?d=rtx+pro+6000+blackwell
- RTX Pro 6000 Blackwell Max-Q 96GB (300W), $16,999.99 in stock on Newegg, read 2026-11-21: https://www.newegg.com/p/pl?d=rtx+pro+6000+blackwell+max-q
- US average residential electricity price, 18.16 cents per kWh, August 2026 (EIA): https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_5_3
- Mac Studio resale (eBay sold prices compiled by a reseller, 2026-10-06): https://macpro-la.com/blogs/news/mac-studio-price-guide-2026
- Artificial Analysis, Mistral Large 4 Intelligence Index 26: https://artificialanalysis.ai/models/mistral-large-4
- Artificial Analysis leaderboard, Claude Opus 5.5 59: https://artificialanalysis.ai/leaderboards/models
- Claude plans, Pro $20 a month: https://claude.com/pricing
{% endraw %}

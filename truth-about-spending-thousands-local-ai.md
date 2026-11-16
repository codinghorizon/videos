---
layout: default
title: "The Truth About Spending Thousands On Local AI"
permalink: /truth-about-spending-thousands-local-ai/
date: 2026-11-16
---

# The Truth About Spending Thousands On Local AI

{% raw %}
Every figure the shots put on screen, and its source. The sources are the script's own
`### SOURCES` list (original-scripts/truth-about-spending-thousands-local-ai.md), each checked
on 15 November 2026 before recording; the prices are also in PRICES.md with the day they were
read. Nothing here is our own benchmark. "By our maths" figures are arithmetic on the cited
numbers, and the arithmetic is shown.

## A. Opening (001 to 007)
- GMKtec EVO-X2, 128GB, $3,499.99 (shown as $3,500): gmktec.com product page, 15 Nov 2026.
- RTX 5060 Ti 16GB, $799.99 new (shown as $800): Newegg, cheapest listing, 12 Nov 2026.

## B. What you can run at home today (008 to 017)
- Qwen 3.8 27B, dense, Apache 2.0: huggingface.co/Qwen/Qwen3.8-27B.
- Arena text: GPT-6 Astra (Max) 1474, Qwen3.8-27B 1434 (40 points): arena.ai/leaderboard/text.
- Expected score 1/(1+10^(40/400)) = 0.44, so 44 in 100: Elo formula from the LMSYS
  leaderboard post (lmsys.org/blog/2023-12-07-leaderboard). Our maths.
- UD-Q4_K_M file 16.6GB: huggingface.co/unsloth/Qwen3.8-27B-GGUF.

## C. The model and the app are two choices (018 to 028)
- M5 Pro 64GB, Qwen 3.8 27B: LM Studio 33.5 tok/s, another app 16.0: one owner's report on
  llamaperf.com/gpu/m5-pro-64gb. Labelled on screen as one report.
- Ollama MIT licence (github.com/ollama/ollama); LM Studio free for home and work
  (lmstudio.ai/blog/free-for-work).

## D. Why own it (029 to 042)
- LM Studio: "Nothing you enter into LM Studio when chatting with LLMs leaves your device":
  lmstudio.ai/docs/app/offline.
- ChatGPT pricing page, "Content is used to train our models, Opt-out available":
  chatgpt.com/pricing.
- $20 and $200 plans: claude.com/pricing. $3,500 / $20 = 175 months (14.5 years);
  $3,500 / $200 = 17.5 months: our maths.

## E. Everyday jobs (043 to 051)
- Qwen3 14B Q4_K_M, 9GB: huggingface.co/Qwen/Qwen3-14B-GGUF.
- RTX 5060 Ti 16GB, Qwen3 14B Q4_K at 4K: 41.1 tok/s: hardware-corner.net RTX 5060 Ti page.

## F. Big memory mini PCs and Macs (052 to 066)
- EVO-X2, Ryzen AI Max+ 395, 128GB, $3,499.99: gmktec.com. $3,499 / 128GB = $27 per GB: our maths.
- Ryzen AI Max+ 395, 256-bit LPDDR5x-8000: amd.com product page.
- gpt-oss-120b 53.4 tok/s; Llama 3.1 70B Q4_K_M 5.1 tok/s on Strix Halo:
  github.com/visorcraft/strix-halo-llm-perf.
- gpt-oss-120b, 117B parameters, 5.1B active: huggingface.co/openai/gpt-oss-120b.
- Mac mini M5 Pro 64GB $2,699 ($42 per GB, our maths): apple.com/shop/buy-mac/mac-mini.
  307GB/s: apple.com/mac-mini/specs.
- macOS lets the GPU use about 75% of memory (about 48GB of 64GB):
  github.com/ivanopcode/devnote-override-macos-metal-vram-cap.

## G. The small Nvidia boxes (067 to 081)
- DGX Spark Founders Edition $6,950, ASUS Ascent GX10 $5,999: NVIDIA Marketplace, 15 Nov 2026.
- Spark launched at $3,999; 64GB model from $4,999: implicator.ai report.
- 128GB, 273GB/s: docs.nvidia.com/dgx/dgx-spark/hardware.html.
- gpt-oss-120b in llama.cpp, tg 55.67 tok/s at 4K (shown 55.7): llama.cpp benches/dgx-spark.
- $6,950 vs $3,999 = 74% more; $5,999 / 128GB = $47 per GB; $4,999 / 64GB = $78 per GB: our maths.

## H. Bandwidth and dollars per tok/s (082 to 103)
- RTX 3090 936GB/s: Wikipedia, GeForce RTX 30 series. Used 24GB going rate $1,899: RigPrice.
- Qwen 3.8 27B on an RTX 3090, 40.31 tok/s at 4K: hardware-corner.net Qwen 3.8 27B tests.
- RTX 5060 Ti 448GB/s: nvidia.com GeForce compare. 28.8 tok/s (3-bit median): llamaperf.com.
- RTX 5090 32GB, 1,792GB/s: PCGamesN. $6,249.99 on Newegg, 12 Nov 2026. 80.0 tok/s: llamaperf.com.
- $ per tok/s: 1,899/40.3 = $47; 799.99/28.8 = $28; 6,249.99/80.0 = $78: our maths.
- RTX 5060 Ti 16GB at $800 is $50 per GB (chapter O): our maths.

## I. Engines that spread a model (104 to 120)
- RTX 4070 12GB, 64GB DDR5-6000, gpt-oss-120b experts on the CPU: 23.85 tok/s; 9.72 at
  2000 MT/s: carteakey.dev write-up. Labelled on screen as one report, one of several changes.
- Gemma 4 26B-A4B streamed from SSD on an 8GB Jetson Orin Nano, 2 to 3 tok/s: dev.to/anyesh.

## J. The spec sheet (121 to 137)
- Speed limit = bandwidth / file size: 936 / about 18GB (Q4_K_S) = 52 tok/s; measured 40.3,
  about 77%: our maths on the sources above.
- KV cache 64 KiB per token, so 128K tokens is about 8GB: github.com/karginb/blackwell-qwen-3.8-bench.

## K. Operating systems and laptops (138 to 149)
- AMD up to 96GB for graphics on Windows: amd.com newsroom, 6 Jan 2025.
- RTX 5090 Laptop GPU 24GB, Qwen 3.8 27B 4-bit median 33.5 tok/s: llamaperf.com.
- RTX 5090 laptops from $4,299 (ASUS ROG Strix SCAR 16): Newegg.

## L to M. The problem first, and mixing in the cloud (150 to 169)
- OpenRouter Qwen 3.8 27B, $0.647 to $3.20 per million output tokens by provider,
  15 Nov 2026: openrouter.ai/qwen/qwen3.8-27b.

## N. Better models on the same hardware (170 to 177)
- Qwen 3.8 27B SWE-bench Pro 61.7 vs Qwen3.6-27B 53.5 (+8): Qwen 3.8 27B model card.

## O to P. The cheap start, and who should spend (178 to 205)
- LocalScore, Llama 3.1 8B Q4_K_M, older laptop chips 3.3 to 5.6 tok/s: localscore.ai/model/1.
- Mac mini M6 24GB $1,099: apple.com. Qwen 3.8 27B 4-bit 9.83 tok/s: llamaperf.com/gpu/m6-24gb.

### Not checked
- Nothing on screen is unsourced. Prices move daily; every price is as read on the date given.
{% endraw %}

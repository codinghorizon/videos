---
layout: default
title: "Mac Mini vs Your $200 AI Subscription (Local AI)"
permalink: /mac-mini-vs-200-ai-subscription/
date: 2026-11-16
---

# Mac Mini vs Your $200 AI Subscription (Local AI)

{% raw %}
Every figure the picture puts on screen, and where it comes from. Prices were checked on the day
(2026-11-15) and are tabled in PRICES.md. The rows here repeat them with their sources.

## Plans ($200 a month)

- ChatGPT Pro, $200 tier: GPT-6 Astra reasoning, longer Codex sessions, 400K reasoning context (on screen "$200", "400K tokens"). Sources: https://chatgpt.com/pricing and https://help.openai.com/en/articles/9793128-about-chatgpt-pro-tiers
- Claude Ultra, $200: "No 5-hour limit", "10x Pro usage every week", "$200 a month in API credits, up from $100 on Max", Claude Code (on screen as captured, beats 032-036): https://claude.com/pricing
- Google AI Ultra 20x, $199.99 (US): Gemini 4, YouTube Premium, storage from 20TB (on screen "$199.99"): https://gemini.google/us/subscriptions/?hl=en ; tiers cross-checked at https://dupple.com/learn/google-ai-pro-vs-ultra
- $20 plan, ChatGPT Plus and Claude Pro (on screen "$20"): https://claude.com/pricing
- A year of a $200 plan: 200 x 12 = $2,400.

## Mac mini prices (Apple US configurator, 2026-11-15)

- M6 16GB $899, 24GB $1,099, 32GB $1,299; M5 Pro 24GB $1,699, 48GB $2,299, 64GB $2,699: https://www.apple.com/shop/buy-mac/mac-mini
- Memory options: M6 16GB, configurable to 24GB or 32GB; M5 Pro 24GB, configurable to 48GB or 64GB: https://www.apple.com/mac-mini/specs/
- Bandwidth: M6 153GB/s (16GB) or 170GB/s; M5 Pro 307GB/s, "nearly double": same specs page
- Payback: 899 / 200 = 4.5 months; 2,699 / 200 = 13.5 months.

## What each memory size runs (published runs, never ours)

- 16GB M6, 9B Q4_K in llama.cpp: 26.9 tok/s generation, 721 ms to first token (on screen "26.9 tok/s", "under a second"): https://www.mindstudio.ai/blog/m6-mac-mini-local-ai-performance
- Qwen 3.8 27B Q4_K_M is 18GB (on screen "18GB"): https://ollama.com/library/qwen3.8/tags
- 24GB M6, Qwen 3.8 27B 4-bit MLX: 9.8 tok/s, about 30K usable context: https://huggingface.co/mlx-community/Qwen3.8-27B-4bit/discussions/4
- 32GB M6 (llamaperf): Gemma 4 26B at 48.2 tok/s with 80K context; Qwen 3.8 27B Q4_K_M at 11.8 tok/s at 32K in LM Studio; about 30 tok/s in the fastest app (ANEMLL Forge, 27.0): https://llamaperf.com/mac/m6
- Gemma 4 26B is a mixture of experts with 4B active: https://ollama.com/library/gemma4
- 48GB M5 Pro, Qwen 3.8 27B in llama.cpp: 16.5 tok/s (about 40% over 11.8): https://llmcheck.net/models/qwen38-27b-on-m5-pro/
- 64GB M5 Pro in Ollama: qwen3.6:35b-a3b-mtp 86.79 tok/s, qwen3.8:27b-mlx 34.25 tok/s: https://github.com/daniel29348679/m5pro-llm-bench (checked 2026-11-15: the README says "an Apple M5 Pro with 64 GB", form factor unstated, so the script says "M5 Pro", never "Mac mini"; 34.25 is Ollama's package with its inline MTP draft head, and both rows are draft-assisted)
- M5 Pro 16-core vs 20-core GPU, llama.cpp TG128: 67.59 vs 66.33 tok/s (on screen "67", "66"): https://github.com/ggml-org/llama.cpp/discussions/4167
- gpt-oss-120b is 65GB, more than the 64GB maximum: https://ollama.com/library/gpt-oss

## Reading the prompt (prefill)

- 32GB M6, Qwen 3.8 27B, 96,000-token prompt read at 123.0 tok/s: 96,000 / 123 / 60 = 13 minutes: https://llamaperf.com/mac/m6
- 64GB M5 Pro, Qwen 3.8 27B, 88,535-token prompt: 504.7 tok/s in the fastest engine (88,535 / 504.7 / 60 = 2.9 minutes), 99.9 tok/s in the slowest (14.8 minutes): https://llamaperf.com/mac/m5

## The viewer comment (on screen, word for word)

- "an agent loop is prefill-bound. Every step re-sends the whole conversation plus tool schemas" from a viewer under this channel's "How To Start Running Local AI The Correct Way (2026)", 2026-10-22: https://www.youtube.com/watch?v=T5vomLianVw

## Owning one, a month

- Power: M6 70W max, M5 Pro 145W max (Apple): https://support.apple.com/en-us/103253
- US average residential electricity 18.16 cents per kWh, August 2026 (EIA): https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_5_6_a
- Power a month at 8 hours a day: M6 0.070 x 8 x 30 x 0.1816 = $3.05; M5 Pro 0.145 x 8 x 30 x 0.1816 = $6.32
- Price over three years: 1,299 / 36 = $36; 2,699 / 36 = $75
- A month to own: $39 (32GB M6) and $81 (64GB M5 Pro); with a $20 plan on top, 200 - (81 + 20) = $99 saved.

## Renting the same model

- Qwen 3.8 27B on OpenRouter, 20+ hosts, median about $0.15 per million in and $2.20 per million out: https://openrouter.ai/qwen/qwen3.8-27b
- A month flat out on the 64GB M5 Pro: 34.25 x 3,600 x 8 x 30 = 29.6M tokens (said "29.5 million"); x $2.20 / 1M = $65
- An 88,000-token codebase read at $0.15 per million: about 1 cent.

## Who keeps paying

- Claude Code, $150 to $250 per developer per month at API prices: https://code.claude.com/docs/en/costs

## Captures (public/mac-mini-vs-200-ai-subscription/web/)

- openrouter-qwen.png, the provider table: https://openrouter.ai/qwen/qwen3.8-27b
- claude-ultra.png, the Ultra card (the UK £ line is cropped out): https://claude.com/pricing
- claude-code-costs.png, "per developer per month": https://code.claude.com/docs/en/costs
- apple-specs.png, the memory options: https://www.apple.com/mac-mini/specs/
- apple-power.png, 70W max: https://support.apple.com/en-us/103253
- llamaperf-m6.png, the 11.8 tok/s run: https://llamaperf.com/mac/m6
- llamaperf-m6-prefill.png, the 123 tok/s prefill run: https://llamaperf.com/mac/m6
- m5pro-bench.png, the 86.79 tok/s row: https://github.com/daniel29348679/m5pro-llm-bench
- chatgpt-pro.png, the Pro tiers help page: https://help.openai.com/en/articles/9793128-about-chatgpt-pro-tiers

## Photos (public/mac-mini-vs-200-ai-subscription/photos/)

- macmini.jpg, macmini-top.jpg, chip-m6.jpg, apple-m5-pro-m5-max-chips.jpg: Apple press images, credited on screen.
{% endraw %}

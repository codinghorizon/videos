---
layout: default
title: "ChatGPT vs Claude vs Gemini vs Local AI (The Math)"
permalink: /chatgpt-claude-gemini-vs-local-ai-math/
date: 2026-11-13
---

# ChatGPT vs Claude vs Gemini vs Local AI (The Math)

{% raw %}
Every figure the picture shows, with where it came from. Prices are in PRICES.md (checked 2026-11-12).
Power: US average residential 18.16 c/kWh (EIA Electric Power Monthly, table 5.6.a, August 2026),
four hours a day at full load. Gap the machine covers: $200 plan minus a $20 plan = $180 a month.

## The plans
- ChatGPT Pro $100 / $200 / $500 tiers; Pro runs GPT-6 Astra, longer Codex sessions, API credits that expire each cycle. https://learn.chatgpt.com/docs/pricing , https://chatgpt.com/pricing
- Claude Pro $20, Max $100, Ultra $200: "No 5-hour limit", "10x Pro usage every week", "$200 a month in API credits, up from $100 on Max". Capture: web/claude-ultra-200.png. https://claude.com/pricing
- Google AI Pro $19.99, AI Ultra from $99.99, $199.99 for 20x usage vs AI Pro. Capture: web/google-ultra-199.png. https://gemini.google/us/subscriptions/?hl=en

## The rungs (payback = price / (180 - power per month))
| machine | price | watts | power/yr | payback | source |
|---|---|---|---|---|---|
| RTX 5060 Ti 16GB | $839 new (RigPrice cheapest new) | 180 | $48 | 4.8 months | web/rigprice-5060ti.png |
| used RTX 3090 24GB | $1,825 going rate | 350 | $93 | 10.6 months | web/rigprice-3090.png |
| GMKtec EVO-X2 128GB | $3,499.99 | 140 peak | $37 | 19.8 months | gmktec.com variant JSON |
| Mac Studio M5 Max 128GB | $5,099 (Apple, 2026-11-09) | ~106 measured | ~$28 ($2.34/mo) | 28.7 months | apple.com, tbreak review |
| used RTX 5090 32GB | $7,000 going rate | 575 | $152 | 41.8 months | web/rigprice-5090.png |
| 3x ASUS Ascent GX10 | 3 x $5,999 = ~$18,000 | - | - | 90 months of $200 before power | openclawdc roundup |

## Speeds
- gpt-oss-20b on RTX 5060 Ti 16GB: 111.51 tok/s (llama.cpp discussion 15396).
- Qwen 3.8 27B 3-bit on RTX 5060 Ti 16GB: median 28.8 tok/s (llamaperf).
- Qwen 3.8 27B Q4_K_S on RTX 3090: 40.31 tok/s at 4K, 33.95 at 64K (Hardware Corner).
- gpt-oss-120b MXFP4 on EVO-X2: 52.6 tok/s (Framework community).
- gpt-oss-120b on Mac Studio M5 Max 128GB: 75.65 tok/s in Ollama, ~106W (tbreak, 2026-09-21).
- Kimi K3 IQ1_S 330.2GB on three DGX Spark-class boxes: 6.59 tok/s freeform prose.

## Renting instead
- Qwen 3.8 27B on OpenRouter (StreamLake): $0.175/M in, $1.05/M out. 3090 output a month = 40 tok/s x 4h x 30 = 17.28M tokens -> $18.14; minus $7.73 power = ~$10.41 saved a month -> ~14.6 years to repay $1,825.

## Quality
- Artificial Analysis Intelligence Index v5.0.1: Claude Fable 5.2 Max 65, Gemini 4 Carbon High 60, Claude Opus 5.5 Max 59, Kimi K3.1 Pro 46, Qwen3.8 27B 20 (under a third of the top).
- Arena text: Gemini 4 Carbon (High) 1526 vs Qwen3.8-27B 1434 (2026-11-11): 92-point gap -> Qwen picked ~37% of the time (1/(1+10^(92/400))).

## Viewer comment
- 8DcNySDOOdw: "casual users should go subscription based".
{% endraw %}

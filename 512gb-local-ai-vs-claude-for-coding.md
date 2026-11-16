---
layout: default
title: "I Priced 512GB Of Local AI vs Claude For Coding"
permalink: /512gb-local-ai-vs-claude-for-coding/
date: 2026-11-16
---

# I Priced 512GB Of Local AI vs Claude For Coding

{% raw %}
Every figure on screen, with its primary source. Checked 2026-11-15. Every speed and score is a
published result, not our own test; the break-even sums are our own arithmetic, shown in full.

## The bill

| figure | source |
|---|---|
| Pro $20, Max $100 (5x Pro), Ultra $200 a month; all include Claude Code | https://claude.com/pricing |
| Max 20x is now called Ultra | https://support.claude.com/en/articles/17728952 |
| Five-hour and weekly usage limits on Max | https://support.claude.com/en/articles/11049741-what-is-the-max-plan |
| Average developer "$150-250 per developer per month" at API prices | https://code.claude.com/docs/en/costs |
| Opus 5.5 API $4 in / $20 out per million tokens | https://platform.claude.com/docs/en/about-claude/pricing |
| Light month $18 = 2M in x $4 + 0.5M out x $20 (our sums) | derived |

## The box

| figure | source |
|---|---|
| Mac Studio M5 Ultra from $5,499; 1.2TB/s memory bandwidth | https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/ |
| 36-core CPU / 80-core GPU from $6,799; top configuration $29,799 | https://www.apple.com/shop/buy-mac/mac-studio |
| 256GB and 512GB need the 36/80 chip; up to 16TB; six Thunderbolt 5 ports | https://www.apple.com/mac-studio/specs/ |
| 256GB +$4,000, so $10,799 with 1TB | https://daringfireball.net/2026/08/configurations_and_pricing_for_new_mac_minis_and_mac_studios |
| 512GB +$15,500, so $22,299 with 1TB | https://macrumors.com/2026/10/28/mac-studio-m5-ultra-512gb-ram/ |
| 385W maximum measured power | https://support.apple.com/en-us/102027 |
| US average electricity 18.16 cents a kWh (Aug 2026) | https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_5_6_a |

## The models

| figure | source |
|---|---|
| DeepSeek V4.1 Flash, 552B total / 16B active; 432GB at 4-bit MLX | https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash , https://huggingface.co/mlx-community |
| Biggest gaming card: GeForce RTX 5090, 32GB (shown at 005, not spoken) | https://www.nvidia.com/en-gb/geforce/graphics-cards/50-series/rtx-5090/ |
| GLM-5.3, 418GB at 4-bit | https://huggingface.co/zai-org/GLM-5.3-Flash , https://artificialanalysis.ai/models/glm-5-3 |
| MiniMax M3.1 Flash 248GB; Qwen 3.8 Flash-Next 112GB | https://huggingface.co/MiniMaxAI/MiniMax-M3.1-Flash , https://huggingface.co/Qwen/Qwen3.8-Flash-Next |
| Kimi K3 family, 2.8T parameters: does not fit 512GB | https://huggingface.co/moonshotai/Kimi-K3 |

## The scores

| figure | source |
|---|---|
| Terminal-Bench 4.0: Opus 5.5 66.4, Kimi K3.1 Pro 65.7, DeepSeek V4.1 Flash 42.3, GLM-5.3 41.8 | https://huggingface.co/moonshotai/Kimi-K3.1-Pro (Moonshot's own table) |
| DeepSWE v1.1: DeepSeek V4.1 Flash 77.0, Kimi K3.1 Pro 75.5, Opus 5.5 74.2, GLM-5.3 66.9 | same table |
| DeepSeek's own card: Terminal-Bench 4.0 31.2, DeepSWE 74.2 | https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash |
| Opus 5.5 Terminal-Bench 4.0 66.4%, released 2026-09-22 | https://www.anthropic.com/news/claude-opus-5-5 |
| Artificial Analysis Intelligence Index: Fable 5.2 65, Opus 5.5 59, Kimi K3.1 Pro 46, DeepSeek V4.1 Flash 33, GLM-5.3 32 | https://artificialanalysis.ai/leaderboards/models , https://artificialanalysis.ai/models/open-source |

## Speed, linking, setup

| figure | source |
|---|---|
| DeepSeek V4.1 Flash on a 512GB M5 Ultra: 4,346 tok/s prefill at 128K, 61-80 tok/s generation, 408GB peak | https://omlx.ai/benchmarks/performance/ike0mcrd |
| 65K prompt 24.4 s on M5 Ultra vs 59.7 s on M3 Ultra | https://macstories.net/stories/m5-ultra-mac-studio-review-the-dream-mac-for-local-ai-agents |
| MLX over Thunderbolt 5: 15.74 tok/s on 2 Macs, 24.99 tensor parallel, 36.73 on 4 | https://machinelearning.apple.com/research/mlx-distributed-inference |
| Four Mac Studios over RDMA, rdma_ctl from Recovery, every Mac cabled to every other | https://jeffgeerling.com/blog/2025/15-tb-vram-on-mac-studio-rdma-over-thunderbolt-5 |
| Claude Code against Ollama: ANTHROPIC_BASE_URL, 64k context or higher | https://docs.ollama.com/integrations/claude-code |
| LM Studio and llama.cpp speak the Anthropic Messages API | https://lmstudio.ai/docs/integrations/claude-code , https://huggingface.co/blog/ggml-org/anthropic-messages-api-in-llamacpp |
| Anthropic does not support routing Claude Code to non-Claude models | https://code.claude.com/docs/en/llm-gateway |
| opencode local providers | https://opencode.ai/docs/providers/ |

## Our sums

- Power: 0.385 kW x 8 h x 22 days x $0.1816 = $12 a month.
- Saved: $200 - $12 = $188; $100 - $12 = $88.
- 512GB box: 22,299 / 188 = 119 months (almost 10 years). Against Max: 22,299 / 88 = 253 months (21 years).
- One 256GB box: 10,799 / 188 = 57.4, about 58 months. Two: 21,598 / 188 = 115 months, about a decade.
- Four 512GB boxes: $89,196 = 37 years of a $200 plan.
- Team of five on Ultra: $1,000 a month, so one box pays off in under two years.

### Not checked

- Every speed and benchmark figure is published by its source, not measured by us.
- Moonshot's table and DeepSeek's own card disagree on DeepSeek V4.1 Flash's Terminal-Bench score
  (42.3 against 31.2); the video says so.
{% endraw %}

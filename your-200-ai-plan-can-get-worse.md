---
layout: default
title: "Your $200 AI Plan Can Get Worse. Your Local AI Can't"
permalink: /your-200-ai-plan-can-get-worse/
date: 2026-10-06
---

# Your $200 AI Plan Can Get Worse. Your Local AI Can't

{% raw %}
Every figure the picture puts on screen, with the page it came from. All pages were read on
2026-10-06 unless a line says otherwise.

## The trackers

**BridgeBench Nerf Bench** (https://www.bridgebench.ai/nerf-bench)
- Each model starts at 100% on its first test; "90% to 110% is normal variance".
- Claude Opus 5.5: Sep 22 100.0% (launch), Sep 27 99.2%, Oct 1 103.8%, Oct 2 94.2%, Oct 4 96.5% (−3.5% vs launch), status "Normal".
- Models tracked 4; beyond normal variance (±10%): None; latest test Oct 4.
- GPT-6 Astra 98.0% (−2.0%); GPT-6.1 Sol 106.7% (+6.7%).

**BridgeBench methodology** (https://www.bridgebench.ai/blog/the-methodology-of-nerfbench)
- "Power is 60% correctness, 20% output tokens and 20% cost, each compared with the reference."
- "We keep the exact prompts, tests and answers private so they can't be trained on."
- "routing, system instructions, reasoning settings and output limits can change too. NerfBench measures the model as it's served, so all of those count."

**LiveNerf** (https://github.com/ninjahawk/livenerf)
- "Progress (2026-10-05): 12 of 30 days collected, none missed. The baseline (days 1–10) is complete; window 1 started with day 11."
- "the first possible call is around 2026-10-24."
- Frozen prompts, pinned CLI, exact graders; "a Claude Code update changes the harness, and a changed harness looks exactly like a changed model."

**Marginlab, Claude Code tracker** (https://marginlab.ai/trackers/claude-code/)
- "We are collecting a new Opus 5.5/high baseline from runs beginning September 24, 2026. Degradation detection is paused."
- "Performance deltas will be available once baseline is established."
- "We always use the latest available Claude Code release ... This allows us to detect degradation related to both model changes and harness changes."

**Marginlab, Codex tracker** (https://marginlab.ai/trackers/codex/)
- "We are collecting a new GPT-6 Sol/high baseline from runs beginning September 24, 2026. Degradation detection is paused."
- Today's pass rate shown: 54% (50 eval test cases).

## Model versions

**OpenAI API reference** (https://developers.openai.com/api/reference/overview)
- "The best way to ensure consistent prompting behavior and model output is to use pinned model versions, and to run evals for your applications."

## Plans

- Claude Pro: "$20 if billed monthly" (https://claude.com/pricing).
- ChatGPT Plus: $20 a month on US checkout (https://openai.com/chatgpt/pricing; the page renders its prices by region, confirmed by search on the day).
- ChatGPT Pro 200 (https://help.openai.com/en/articles/9793128-about-chatgpt-pro-tiers): "New subscriptions that aren’t eligible for grandfathering include a lower usage allowance than previously offered with Pro 200 ... The monthly price remains $200." Grandfathered customers "can use the previous included allowance through October 29, 2026".

## Hardware

- GMKtec EVO-X2, 64 GB RAM + 1 TB SSD: $2,199.99 (sale, from $2,599.99). The 128 GB configurations are listed without their own price. "On the 128G version, local AI runs Qwen3:235B ... an average speed of 11 tokens/s." (https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc)
- Mac Studio M5 Max "starts at $2,499 (U.S.)"; M5 Ultra "starts at $5,499 (U.S.)" (https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/). M5 Ultra base memory 96GB (https://www.apple.com/mac-studio/specs/).
- Used RTX 3090, eBay Best Match, ship to 10001: ZOTAC Gaming RTX 3090 Trinity OC 24GB, $1,399.99 + $12.20 delivery. Listings on the same page ran from $1,175 to $2,300. (https://www.ebay.com/sch/i.html?_nkw=rtx+3090+24+gb+used&_sop=12)

## Derived

- $2,199 / $200 = 11.0 months; / $20 = 110 months; 110 months = 9.2 years ($240 a year).
- $2,499 / $200 = 12.5 (about 13); / $20 = 125 months. $5,499 / $200 = 27.5 (about 28).
- $1,412 / $200 = 7.1 months; / $20 = 70.6 months.

## Not checked

- The "two thousand six hundred ninety one upvotes" the narration attributes to the Opus nerf thread could not be found on any page read. The closest published figures are 2,651 votes on the LiveNerf author's r/ClaudeAI update and 1,090 on an r/ClaudeCode post (pasqualepillitteri.it, 2026-10). The number is not shown on screen.
- The narration calls the Claude Code tracker that runs the latest release "Anthropic's public Claude Code tracker"; the page that says this is Marginlab's (marginlab.ai). The picture names neither.
- eBay listings change by the hour; the price is the top Best Match listing at capture time.
{% endraw %}

---
layout: default
title: "DeepSeek V4 Flash Makes Claude Look Expensive Now"
permalink: /deepseek-v4-flash-premium-models-are-wasting-money/
date: 2026-08-22
---

# DeepSeek V4 Flash Makes Claude Look Expensive Now

{% raw %}
Every figure, price, date, version and licence this video puts on screen, chased to a
primary source. Checked 22 August 2026.

## DeepSeek V4 Flash, the model

| Claim | Value | Source |
| --- | --- | --- |
| Total parameters | 284B | [Hugging Face, DeepSeek V4 Flash model card](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) |
| Active parameters per token | 13B | [Hugging Face model card](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) |
| Architecture | Mixture of experts | [Hugging Face model card](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) |
| Context length | 1,000,000 tokens | [DeepSeek API docs, pricing](https://api-docs.deepseek.com/quick_start/pricing) |
| Maximum output | 384,000 tokens | [DeepSeek API docs, pricing](https://api-docs.deepseek.com/quick_start/pricing) |
| Thinking and non thinking modes | Both, thinking is the default | [DeepSeek API docs, pricing](https://api-docs.deepseek.com/quick_start/pricing) |
| Licence | MIT | [Hugging Face model card](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) |
| Open weights | Published on Hugging Face | [Hugging Face model card](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) |
| Current build | DeepSeek V4 Flash 0731 | [DeepSeek API docs, pricing](https://api-docs.deepseek.com/quick_start/pricing) |
| Concurrency limit | 2,500 | [DeepSeek API docs, pricing](https://api-docs.deepseek.com/quick_start/pricing) |

## DeepSeek V4 Pro, the model

| Claim | Value | Source |
| --- | --- | --- |
| Total parameters | 1.6T | [DeepSeek API docs, V4 release notes](https://api-docs.deepseek.com/news/news260424/) |
| Active parameters per token | 49B | [DeepSeek API docs, V4 release notes](https://api-docs.deepseek.com/news/news260424/) |
| Context length | 1,000,000 tokens | [DeepSeek API docs, pricing](https://api-docs.deepseek.com/quick_start/pricing) |
| Thinking and non thinking modes | Both | [DeepSeek API docs, pricing](https://api-docs.deepseek.com/quick_start/pricing) |
| Current build | DeepSeek V4 Pro 0813 | [DeepSeek API docs, pricing](https://api-docs.deepseek.com/quick_start/pricing) |
| Concurrency limit | 500 | [DeepSeek API docs, pricing](https://api-docs.deepseek.com/quick_start/pricing) |

Both V4 models were announced together, both open weight, both at one million context.

## DeepSeek API pricing

DeepSeek moved from flat rates to peak and off peak billing on **16 August 2026**. Peak
hours are 01:00 to 04:00 and 06:00 to 10:00 UTC, and off peak rates are half the peak
rates. Per one million tokens, in US dollars:

| Model | Cache hit input | Cache miss input | Output |
| --- | --- | --- | --- |
| V4 Flash, off peak | $0.007 | $0.22 | $0.66 |
| V4 Flash, peak | $0.014 | $0.44 | $1.32 |
| V4 Pro, off peak | $0.022 | $0.66 | $1.98 |
| V4 Pro, peak | $0.044 | $1.32 | $3.96 |

Source: [DeepSeek API docs, pricing](https://api-docs.deepseek.com/quick_start/pricing).

The same page notes a further change to the peak and off peak rules effective
23 August 2026, applying off peak rates throughout the day at weekends.

Caching is automatic disk based prefix caching: a request whose prompt shares a prefix
with an earlier one bills the shared portion at the cache hit rate.

**The narration quotes the flat rates that applied before 16 August 2026** ($0.14 cache
miss, $0.0028 cache hit and $0.28 output for Flash; $0.435, $0.003625 and $0.87 for Pro).
Those were correct until that date and are no longer DeepSeek's published prices. The
script was supplied finished and is recorded word for word, so the narration could not be
corrected. **No DeepSeek price appears as a figure anywhere in the picture.** The pricing
shots draw the shape of the gap instead: relative tier heights, model marks at the height
their price puts them, and multiples between tiers. See `### Not checked` in MANIFEST.md.

## Premium routes, for comparison

These are current and are printed on screen.

| Model | Input per 1M | Output per 1M | Source |
| --- | --- | --- | --- |
| Claude Opus 4.6 | $5 | $25 | [Claude platform docs, pricing](https://platform.claude.com/docs/en/about-claude/pricing) |
| Claude Sonnet 5 | $2 | $10 | [Claude platform docs, pricing](https://platform.claude.com/docs/en/about-claude/pricing) |
| GPT 5 | $1.25 | $10 | [OpenAI, API pricing](https://openai.com/api/pricing/) |

Anthropic's cache read price is 0.1 times the base input price, and a five minute cache
write is 1.25 times base, so Opus 4.6 reads a cache hit at $0.50 per million and Sonnet 5
at $0.20 per million.

**Claude Sonnet 5 pricing correction.** The narration says Sonnet 5 is $2 and $10 through
31 August 2026 and then moves to $3 and $15. Anthropic's pricing page now states that the
$2 and $10 rate, announced at launch as introductory pricing through 31 August 2026, **is
now the standard price**, and that the scheduled increase to $3 and $15 on 1 September 2026
**will not occur**. The picture shows $2 and $10 as the standard price and never shows
$3 or $15.

## Caveats

- Every price above is a list price for first party API access. Hosted providers,
  marketplaces and negotiated contracts differ, and the video does not claim otherwise.
- DeepSeek's peak and off peak split means a single "the price of Flash" figure does not
  exist; which one applies depends on when a request lands.
- The routing argument the video makes is unchanged by the price move: Flash output at
  $0.66 off peak is still far below Opus 4.6 at $25 and GPT 5 at $10 per million.
- No benchmark scores are claimed anywhere in this video and none appear on screen.
- The four way routing test the video describes is a method the viewer is asked to run.
  It is not presented as a test that has been run, and no result from it is shown.
{% endraw %}

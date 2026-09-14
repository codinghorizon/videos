---
layout: default
title: "ChatGPT vs Claude: Your Best Model May Cost Extra"
permalink: /chatgpt-vs-claude-the-20-dollar-choice/
date: 2026-09-14
---

# ChatGPT vs Claude: Your Best Model May Cost Extra

{% raw %}
Every figure, name and claim the finished shots put on screen, chased to a source.
Checked 13 September 2026.

## Price and what the two plans include

**Claude Pro is $20 a month billed monthly**, and $17 a month billed annually ($200 up
front). The plan page lists "Includes Claude Code" and "Includes Claude Cowork" among the
Pro features, and describes usage as a rolling five hour session with weekly limits on top
for paid plans.
Source: https://claude.com/pricing

**ChatGPT Plus is $20 a month.** OpenAI lists voice conversations, image generation, file
uploads and analysis, and deep research tools where available, plus expanded access to
ChatGPT Work and Codex.
Source: https://help.openai.com/en/articles/6950777-what-is-chatgpt-plus
Source: https://chatgpt.com/plans/plus/

**Claude Pro carries Sonnet 5 and Opus 5.** Sonnet 5 is the default model and Opus 5 is
the strongest model available on Pro.
Source: https://claude.com/pricing
Source: https://www.anthropic.com/news/claude-sonnet-5

## Fable 5.1 is not covered by the Pro allowance

Anthropic released Claude Fable 5.1 on 1 September 2026. Its help centre article on Fable
models states that Fable 5.1 "isn't included in your plan's usage limits" and that on Pro
these models run on pay as you go usage credits, billed at standard API rates. Fable 5.1
was not part of the one time credit that accompanied Fable 5's move to credits in July
2026.
Source: https://support.claude.com/en/articles/15424964-claude-fable-models-on-your-plan
Source: https://www.anthropic.com/claude-fable-and-mythos-5-1

## What ChatGPT Plus reaches, and where

**GPT 5.6 Sol in ordinary Chat, at Medium and High reasoning.** Extra High and the Pro
reasoning option are not part of Plus; they belong to Pro, Business and Enterprise.
Source: https://help.openai.com/en/articles/20001354-gpt-56-in-chatgpt
Source: https://openai.com/index/gpt-5-6/

**GPT 6 Astra is included on Plus in ChatGPT Work and Codex**, and reaching GPT 6 in
ordinary Chat takes a Pro plan. GPT 6 Astra was released on 3 September 2026 and became
generally available the following day.
Source: https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex
Source: https://openai.com/index/gpt-6-astra/

**Sol, Terra and Luna** are the three GPT 5.6 tiers in ChatGPT.
Source: https://openai.com/index/gpt-5-6/

## Terminal Bench 4.0

Anthropic's published comparison alongside the Fable 5.1 and Mythos 5.1 launch gives
Terminal Bench 4.0 as:

| Model | Terminal Bench 4.0 |
| --- | --- |
| Claude Mythos 5.1 | 60.9% |
| Claude Fable 5.1 | 55.8% |
| Claude Opus 5 | 52.3% |
| Claude Fable 5 | 42.0% |
| GPT 5.6 Sol | 37.3% |

The gap between Opus 5 and GPT 5.6 Sol is therefore 15.0 points. It is a vendor published
result on a particular harness, not a measurement of either subscription working on a real
codebase.
Source: https://www.anthropic.com/claude-fable-and-mythos-5-1
Cross checked against: https://www.vellum.ai/blog/claude-fable-5-1-mythos-5-1-benchmarks-explained

## Context window

**A one million token context window in chat on all paid plans for Fable 5.1, Opus 5 and
Sonnet 5.** Older Opus and Sonnet 4.6 models get 500K, and everything else 200K.

In **Claude Code**, Fable 5.1, Fable 5, Sonnet 5, Opus 5, Opus 4.8 and Opus 4.7 support a
million tokens, but the help centre states that Pro users need to enable usage credits to
reach the million token context window for Opus models. On Max, Team and Enterprise the
upgrade is automatic.
Source: https://support.claude.com/en/articles/8606394-how-large-is-the-context-window-on-paid-claude-plans

## Tokens per second, and the Intelligence Index

Artificial Analysis, measuring the underlying models over the API:

| Model | Output tokens per second | Intelligence Index |
| --- | --- | --- |
| GPT 6 Astra, Medium | about 50 | 50 |
| Claude Opus 5, Medium effort | about 49 | 45 |

The Intelligence Index at v4.3 is a composite of ten evaluations: AA Briefcase, GDPval AA
v2, AutomationBench AA, Terminal Bench v4.0, SciCode, Humanity's Last Exam, GDP.pdf,
CritPt, AA Omniscience and AA LCR v1.1. It is a composite score rather than a share of
tasks solved.

These are live figures that move between measurement runs. At the time the script was
written the Opus 5 Medium output speed read about 48 tokens per second; the comparison
page read about 49 when checked on 12 September 2026. Either way the two models stream at
effectively the same rate.
Source: https://artificialanalysis.ai/models/gpt-6-astra-medium
Source: https://artificialanalysis.ai/models/comparisons/gpt-6-astra-medium-vs-claude-opus-5-medium

## Limits

**Claude Pro** resets on a rolling five hour window with a weekly window on top, and chat
and Claude Code draw on the same usage. Anthropic does not publish exact token counts for
those caps.
Source: https://claude.com/pricing
Source: https://support.claude.com/en/articles/8606394-how-large-is-the-context-window-on-paid-claude-plans

**ChatGPT Plus** meters ChatGPT Work and Codex together on a shared allowance, separate
from Chat, in rolling five hour windows with weekly allowances. OpenAI's own estimates for
Plus are roughly 5 to 45 local GPT 6 Astra messages per five hours, against 10 to 100 for
GPT 5.6 Sol, 25 to 200 for Terra and 250 to 2,000 for Luna. They are estimates, and a
substantial agent task consumes far more of the allowance than a short question even
though both start as one message.
Source: https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex
Source: https://www.techrepublic.com/article/news-openai-five-hour-codex-limit-chatgpt-plus/

**Neither subscription includes general API usage.** API consumption for an application
you build is billed separately at API rates.
Source: https://claude.com/pricing
Source: https://openai.com/api/pricing/
{% endraw %}

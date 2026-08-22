---
layout: default
title: "This Free Mystery AI Model Should Not Exist Yet"
permalink: /ox-alpha-mystery-model/
date: 2026-08-22
---

# This Free Mystery AI Model Should Not Exist Yet

{% raw %}
Every figure, date and claim the finished picture puts on screen, chased to a source.
Checked 22 August 2026. The script was rewritten after the first pass; this file covers
what the finished narration says and what the finished picture puts on screen.

## The model listing

| Fact | Value | Source |
| --- | --- | --- |
| Model id | `stealth/ox-alpha` | https://openrouter.ai/stealth/ox-alpha |
| Provider name shown | Stealth | https://openrouter.ai/stealth/ox-alpha |
| Appeared | 20 August 2026 | https://openrouter.ai/stealth/ox-alpha |
| Context window | 1,048,576 tokens | https://openrouter.ai/stealth/ox-alpha |
| Max output | 131,072 tokens | https://openrouter.ai/stealth/ox-alpha |
| Input modalities | Text, image, video | https://openrouter.ai/stealth/ox-alpha |
| Tool calling | Yes, `tools` and `tool_choice` | https://openrouter.ai/stealth/ox-alpha |
| Structured output | Yes, `response_format`, without JSON schema enforcement | https://openrouter.ai/stealth/ox-alpha |
| Reasoning | Listed as a reasoning model | https://openrouter.ai/stealth/ox-alpha |
| Price, prompt tokens | $0 | https://openrouter.ai/stealth/ox-alpha |
| Price, completion tokens | $0 | https://openrouter.ai/stealth/ox-alpha |
| Preview length | Free for roughly one week from launch | https://officechai.com/ai/stealth-model-ox-alpha-available-for-free-for-a-week-on-openrouter-and-opencode/ |

The listing positions it for coding, sustained agentic work and production workloads.
Source: https://openrouter.ai/stealth/ox-alpha

## The data policy

OpenRouter's model page states: "Prompts and completions for this model are retained by
the provider and are not used for training; all other use is governed by the Stealth Model
Terms."

Source: https://openrouter.ai/stealth/ox-alpha

Retained by the provider and not used for training are two separate statements. The
provider is not named during the preview, so there is no published entity behind the
retention commitment. Other frontends that route to the same model may state different
retention terms.

## The community benchmark run

One run, by independent researcher Ben Davis, on DeepSWE, a long horizon software
engineering benchmark. Ten deterministic tasks.

| Model | Score on that run |
| --- | --- |
| Ox Alpha | 80% pass@1, 8 of 10 |
| Claude Fable 5 | 65% |
| GLM-5.3 | 62% |
| Grok 4.6 | 62% |
| GPT-5.6-sol | 52% |

Source: https://finance.biggo.com/news/9dc856ba-634d-467a-bea2-6ba70233113c

The same report carries the caveat directly: sample sizes and attempt counts vary by
model, Ox Alpha's sample is small, and the figures are preliminary. Ten tasks is not a
controlled comparison and should not be read as a ranking.

## The GLM identification evidence

Not officially confirmed. No lab has claimed the model and OpenRouter has not named the
provider. What exists is circumstantial technical evidence, gathered by Ben Davis:

- **Tokenizer.** 25 prompts tested. Token counts match GLM-5.3 exactly, with a consistent
  +75 token difference attributed to a hidden wrapper. Consistent with a shared vocabulary.
- **Video encoder.** Four video sets tested. Ox Alpha and GLM-5V-Turbo show identical video
  token consumption, frame rate independent sampling, roughly 147 tokens per second of
  duration, and per frame resolution scaling.
- **Other signals.** Audio input rejection behaviour and output style, including emoji rate.
- **Stated confidence.** Davis puts it at 99% certain the model is in Zhipu's GLM-5.x
  series. Independent write ups put combined fingerprinting at roughly 90%.

Sources:
https://finance.biggo.com/news/9dc856ba-634d-467a-bea2-6ba70233113c
https://kingy.ai/blog/ox-alpha-glm-5-3-flash-evidence/

Self identification is explicitly not part of this evidence. A model asked what it is will
answer from context rather than from fact.

## Z.ai, formerly Zhipu AI

| Fact | Value | Source |
| --- | --- | --- |
| International rebrand to Z.ai | July 2025, around GLM-4.5 | https://www.turingpost.com/p/zhipu |
| GLM lineage on screen | GLM-4.5, GLM-5, GLM-5.2, GLM-5.3 | https://presenc.ai/research/zhipu-glm-model-lineage-2026 |
| GLM-5 max output | 131,072 tokens | https://glm-5.org/ |
| GLM-5.2 | 13 June 2026, context extended to 1M tokens | https://presenc.ai/research/zhipu-glm-model-lineage-2026 |

GLM-5's stated 131,072 token max output is the same figure Ox Alpha advertises, which is
part of why the family is the leading guess.

## Chinese labs named in the script

- **DeepSeek** — moved the industry cost conversation with aggressively priced open weight
  reasoning models. https://www.deepseek.com/
- **Qwen** — Alibaba's open model family, widely pulled into developer workflows.
  https://qwen.ai/
- **Kimi** — Moonshot AI, made very long context a mainstream feature rather than a lab
  demo. https://www.moonshot.ai/
- **GLM** — Z.ai, competing specifically at the agentic and coding layer.
  https://z.ai/

## Not confirmed

- The identity of the provider behind `stealth/ox-alpha`. Every attribution in circulation
  is fingerprinting, not an announcement.
- Whether the free price, the rate limits or the retention terms survive the preview.
- Whether the DeepSWE result reproduces at a larger sample or under a different harness.
{% endraw %}

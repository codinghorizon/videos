---
layout: default
title: "Claude Fable 5.1 Has One Number You Cannot Ignore"
permalink: /claude-fable-5-1-performance-jump/
date: 2026-09-03
---

# Claude Fable 5.1 Has One Number You Cannot Ignore

{% raw %}
Every figure, price, date and benchmark result the video puts on screen, chased to a
primary source.

Anthropic released Claude Fable 5.1 and Claude Mythos 5.1 on 1 September 2026. Both are
the same model with different safeguard configurations; Mythos 5.1 is available only
through a trusted access programme.

Primary sources used throughout:

- Anthropic, "Introducing Claude Fable 5.1 and Claude Mythos 5.1" —
  https://www.anthropic.com/claude-fable-and-mythos-5-1
- Claude Platform docs, "Claude Fable 5.1" overview —
  https://platform.claude.com/docs/en/models/fable-5-1/overview
- Claude Platform docs, "Choosing a model" —
  https://platform.claude.com/docs/en/about-claude/models/choosing-a-model
- Anthropic, "Claude Fable 5.1 and Claude Mythos 5.1 System Card", 1 September 2026 —
  https://www.anthropic.com/claude-fable-5-1-mythos-5-1-system-card

## Benchmark results

All four rows below come from the comparison table on Anthropic's launch page. Anthropic
ran the table itself, including the competitor figures, which is stated in the video.

### Terminal-Bench 4.0 (agentic coding in a terminal)

| Model | Score |
| --- | --- |
| Claude Fable 5.1 | 55.8% |
| Claude Opus 5 | 52.3% |
| Claude Fable 5 | 42.0% |
| GPT-5.6 Sol | 37.3% |

The relative improvement over Fable 5 is (55.8 − 42.0) / 42.0 = 32.9%, which the video
states as a 33% relative jump.

Claude Mythos 5.1, under its more permissive cyber safeguards, reaches 60.9% on the same
benchmark. The video does not use this figure.

Source: https://www.anthropic.com/claude-fable-and-mythos-5-1

### Terminal-Bench-Science 0.1 (multistep research work in a terminal)

| Model | Score |
| --- | --- |
| Claude Fable 5.1 | 52.6% |
| Claude Opus 5 | 29.0% |
| Claude Fable 5 | 24.7% |
| GPT-5.6 Sol | 22.4% |

Anthropic reports a standard error of roughly 3.5 to 4.5 points on this benchmark, and it
is a young benchmark at version 0.1. Both caveats are stated in the video.

52.6 against 24.7 is a factor of 2.13; 52.6 against 22.4 is a factor of 2.35. The video's
"more than double" holds for both comparisons.

Source: https://www.anthropic.com/claude-fable-and-mythos-5-1

### AutomationBench (business workflow automation)

| Model | Score |
| --- | --- |
| Claude Fable 5.1 | 31.4% |
| Claude Opus 5 | 26.9% |
| GPT-5.6 Sol | 19.6% |
| Claude Fable 5 | 17.1% |

Source: https://www.anthropic.com/claude-fable-and-mythos-5-1

### CursorBench 3.2.0 (editor style coding)

| Model | Score |
| --- | --- |
| Claude Fable 5.1 | 73.4% |
| Claude Fable 5 | 70.5% |
| Claude Opus 5 | 70.0% |
| GPT-5.6 Sol | 67.2% |

Fable 5.1 is 3.4 points above Opus 5 here (73.4 − 70.0), which the video contrasts with the
23.6 point gap on Terminal-Bench-Science.

Source: https://www.anthropic.com/claude-fable-and-mythos-5-1

### GDPval-AA v2 (Elo)

| Model | Rating |
| --- | --- |
| Claude Fable 5.1 | 1853 |
| Claude Opus 5 | 1824 |
| Claude Fable 5 | 1723 |
| GPT-5.6 Sol | 1711 |

Source: https://www.anthropic.com/claude-fable-and-mythos-5-1

## Pricing

Claude Fable 5.1 is listed at $10 per million input tokens and $50 per million output
tokens, unchanged from Claude Fable 5. Cache reads are $0.25 per million tokens, reduced
from $1.00, a cut of 75%. Five minute cache writes are $12.50 per million and one hour
cache writes are $20 per million. Batch API requests take a 50% discount.

Claude Opus 5 is listed at $5 per million input tokens and $25 per million output tokens,
so Fable 5.1 is twice the headline price on both sides.

Source: https://platform.claude.com/docs/en/models/fable-5-1/overview

Anthropic estimates the cache read change makes typical Fable workloads cost about 25%
less than Fable 5, and says savings on highly agentic work "will often be much larger, up
to approximately 45%". Anthropic states these figures are based on four weeks of its own
August 2026 usage.

Source: https://www.anthropic.com/claude-fable-and-mythos-5-1

GPT-5.6 Sol is listed at $4 per million input tokens and $20 per million output tokens.
OpenAI announced this as a promotional reduction in late August 2026, from $5 and $30, and
has said it runs at least through 21 November 2026. Short context here means requests up
to 272,000 input tokens.

Sources:
- https://developers.openai.com/api/docs/pricing
- https://community.openai.com/t/20-price-reduction-for-gpt-5-6-sol-api-codex-credits-and-chatgpt-work/1391726
- https://aws.amazon.com/about-aws/whats-new/2026/08/bedrock-openai-gpt-56-sol-reduced-pricing/

## Anthropic's own model guidance

The Claude Fable 5.1 overview states: "For most workloads, start with Claude Opus 5. Use
Claude Fable 5.1 for demanding reasoning and long-horizon agentic work, or when your evals
on Claude Opus 5 at higher effort still fall short."

Fable 5.1 is also listed with slower comparative latency than Opus 5, a 1M token context
window, a 128K maximum output, and a reliable knowledge cutoff of June 2026.

Source: https://platform.claude.com/docs/en/models/fable-5-1/overview

## Safeguards

Anthropic says Claude Code users can expect an average of around 60% fewer interventions
per session from its cyber safeguards, compared with the safeguards that launched with
Fable 5.

Fable 5.1 can now be used to identify software vulnerabilities in source code. Exploit
generation, penetration testing and some binary based vulnerability scanning remain
redirected or restricted.

In biology, Anthropic says the newer safeguards fire 85% less often on benign requests
about elementary biology and medical questions than the safeguards that launched with
Fable 5. Research and development life science work can still route to other models;
Claude Mythos 5.1 offers the same capabilities to participants in Anthropic's Project
Glasswing trusted access programme, currently a set of United States organisations, with
Anthropic saying it is coordinating with the US government to widen access.

Enterprise Frontier Safeguards let eligible customers store data on their own cloud
infrastructure rather than Anthropic's, with any human review done by the customer by
default. Anthropic says it is available on Claude Code, Claude Enterprise, the Claude
Platform, Amazon Bedrock and Microsoft Foundry, rolling out in phases from autumn 2026.

Sources:
- https://www.anthropic.com/claude-fable-and-mythos-5-1
- https://www.anthropic.com/claude-fable-5-1-mythos-5-1-system-card

## Customer reported results

These are figures the named organisations supplied to Anthropic for its launch. They are
not independently reproduced benchmarks, which the video says.

**Millennium.** A piece of code had an extremely rare crash, about one run in a million,
that nobody on the team had explained in four to five years. Anthropic says Fable 5.1
disassembled an external vendor library, matched it against the core dump, and traced the
crash to a bug in that library.

**MongoDB.** Anthropic reports a complex prototype researched and built in about three
days, including hours of unattended work and strong verification loops, with a full visual
walkthrough.

**Browserbase.** 82% of tasks completed on its hardest browser agent benchmark, at about
ten minutes each, against 74% for Claude Opus 5 and 57% for Claude Fable 5.

**Crosby.** RedlineBench, a contract redlining benchmark, rose from 47.9 to 57.0 over
Fable 5.

**Samaya.** A 55.9% rubric score on its FrontierFinance benchmark, against 49.2% for
Fable 5.

Source: https://www.anthropic.com/claude-fable-and-mythos-5-1

## Not independently verified

- Every competitor figure in the benchmark table above was produced by Anthropic rather
  than by OpenAI or by an independent evaluator. The video states this.
- Terminal-Bench-Science is at version 0.1 and Anthropic reports a standard error of
  several points on it.
- All five customer results are self reported by the organisations named and were not
  reproduced independently.
- Anthropic's 25% and 45% cost reduction estimates are derived from its own August 2026
  usage data and were not reproduced independently. Third party measurements diverge:
  Artificial Analysis measured Fable 5.1 at maximum effort at $3.76 per task, about 20%
  above Fable 5, because it emits roughly 1.7 times the output tokens, while Cognition
  measured $2.68 per task against $5.84 for Fable 5 on its own coding benchmark. The video
  does not put either third party figure on screen.
{% endraw %}

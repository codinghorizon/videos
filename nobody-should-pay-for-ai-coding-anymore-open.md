---
layout: default
title: "Nobody Should Pay for AI Coding Anymore (Open Models Won)"
permalink: /nobody-should-pay-for-ai-coding-anymore-open/
date: 2026-08-01
---

# Nobody Should Pay for AI Coding Anymore (Open Models Won)

Every figure stated in this video, with where it came from. All prices and scores were
checked on 31 July 2026. Model pricing and leaderboards move quickly, so figures are
correct as of that date and not afterwards.

## Prices

| Model | Input per 1M | Cache read per 1M | Output per 1M |
| --- | --- | --- | --- |
| DeepSeek V4 Flash | $0.14 | $0.0028 | $0.28 |
| DeepSeek V4 Pro | $0.435 | $0.003625 | $0.87 |
| Claude Haiku 4.5 | $1.00 | $0.10 | $5.00 |
| Claude Sonnet 5 | $2.00 | $0.20 | $10.00 |
| Claude Opus 5 | $5.00 | $0.50 | $25.00 |

Source: DeepSeek API pricing, https://api-docs.deepseek.com/quick_start/pricing
Source: Anthropic model pricing, https://platform.claude.com/docs/en/docs/about-claude/pricing

Two notes on the Anthropic column. Claude Sonnet 5 is on introductory pricing of $2 and
$10 through 31 August 2026, after which the published standard rate is $3 and $15. And a
cache read is billed at one tenth of the base input price, which is where the 10x figure
in the video comes from. DeepSeek discounts a cache hit far harder: $0.003625 against
$0.435 on V4 Pro is a factor of 120.

The 29x headline is Claude Opus 5 output against DeepSeek V4 Pro output, $25.00 against
$0.87. It is a comparison of the two most capable models on each side, on the one number
that gets quoted most often.

## What one task actually costs

The video sizes a single agent task at 180,000 tokens read and 20,000 written. That shape
is an illustrative figure for a coding agent working in a repository, not a measurement,
and it is the reason the effective gap is smaller than the sticker gap: a coding request
is mostly input, and the input prices sit much closer together than the output prices do.

At those volumes and the prices above:

- DeepSeek V4 Pro: $0.096 per task
- Claude Opus 5: $1.40 per task
- Ratio: 14.6x, against a sticker ratio of 29x

The monthly figures scale that by 40 tasks a day over 20 working days, which is 800 tasks:
about $77 on open weights and about $1,120 on Claude Opus 5. The routed figure of about
$301 pays the cheap model for all 800 and the expensive model for the 160 that escalate,
because a task that failed on the cheap model still cost its tokens.

The 80 per cent routine share is an assumption used to make the arithmetic concrete. It is
not a measured rate and will differ by codebase and by team.

## Benchmarks

SWE bench Verified, resolved rate, as published:

| Model | Score | Weights |
| --- | --- | --- |
| Claude Opus 5 | 96.0 | closed |
| Claude Opus 4.8 | 88.6 | closed |
| DeepSeek V4 Pro | 80.6 | open |
| Gemini 3.1 Pro | 80.6 | closed |
| DeepSeek V4 Flash | 79.0 | open |
| Kimi K2.5 | 76.8 | open |

Source: DeepSeek V4 Pro model card, https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro
Source: Anthropic Claude Opus 5 launch materials, https://claude.com
Source: SWE bench, https://www.swebench.com/

SWE bench Verified is 500 held out issues, so the 15.4 point gap between the best closed
score and the best open one is about 77 more issues resolved.

Every score in that table is self reported by the lab that trained the model, run on its
own scaffold. Different scaffolds produce different numbers for the same weights, and
Claude Opus 5 in particular is quoted at both 96.0 and 97.0 depending on the tracker and
the number of trials. Treat one point either way as noise.

### The harder benchmarks

| Benchmark | Model | Score |
| --- | --- | --- |
| SWE bench Verified | Claude Opus 5 | 96.0 |
| Terminal Bench 2.1 | Claude Opus 5 | 89.1 |
| SWE bench Pro, public split | Claude Opus 4.6 | 51.9 |

Source: SWE bench Pro public leaderboard, https://labs.scale.com/leaderboard/swe_bench_pro_public

These three are the same frontier on benchmarks of increasing difficulty, not a comparison
between open and closed. That comparison is deliberately absent: DeepSeek publishes a
Terminal Bench 2.0 score and Anthropic publishes a 2.1 score, the versions are not
comparable, and setting them side by side would invent a result neither number supports.

SWE bench Pro is the contamination point. Its public split is 731 issues drawn from 41
professionally maintained repositories, and it was built specifically to address the risk
that public benchmark tasks have leaked into training sets. The same frontier models that
clear 90 per cent on Verified score around half that on Pro.

The claim that public benchmarks leak into training data is a documented concern about
SWE bench Verified rather than a proven result about any specific model. The video states
it as a reason to discount a saturated score, which is what the SWE bench Pro authors
themselves give as the motivation for building it.

### The open frontier catching up

| Model | SWE bench Verified |
| --- | --- |
| Qwen3 Coder 480B | 69.6 |
| Kimi K2.5 | 76.8 |
| MiniMax M2.5 | 80.2 |
| DeepSeek V4 Pro | 80.6 |

Plotted in release order rather than against a calendar, because the releases are what
moved and they are not evenly spaced. The projection past the last real point in the
closing section is drawn, not measured, and the video says so on screen.

## The weights

DeepSeek V4 Pro is 1.6 trillion total parameters with 49 billion activated per token,
released April 2026 under the MIT licence with a 1 million token context window. The
published download is about 865GB, and that is already a mixed FP4 and FP8 build rather
than full precision.

DeepSeek V4 Flash is 284 billion total parameters with 13 billion activated.

Source: https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro
Source: https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash

Licences quoted on screen: DeepSeek V4 is MIT, Qwen3 Coder is Apache 2.0, Kimi K2.5 is a
modified MIT licence, and Mistral's open models are Apache 2.0. Each is stated on that
model's own card.

## Hardware

An eight GPU H100 node carries 640GB of HBM, which is less than the 865GB the V4 Pro
weights occupy. Serving it therefore needs two nodes.

On demand pricing for an eight GPU H100 node sits around $17 an hour at the competitive
end of the market, with quoted rates spanning roughly $16.80 to $19.20 and hyperscaler
pricing considerably above that. Two nodes running continuously for 30 days at $17 an hour
each is about $24,480 a month.

Source: GPU cloud pricing surveys collated at https://getdeploying.com/gpus/nvidia-h100

That hourly rate is a market range rather than one vendor's list price, and it is the
figure most likely in this video to be out of date first. It also excludes storage,
networking and the engineering time to keep the thing serving.

## The cost of a person

The median annual wage for software developers in the United States was $148,100 as of
May 2025. At 2,080 paid hours that is about $71 an hour, and the video uses a loaded rate
of $100 an hour to account for employment overhead on top of salary.

Source: U.S. Bureau of Labor Statistics, Occupational Outlook Handbook, Software
Developers, Quality Assurance Analysts, and Testers,
https://www.bls.gov/ooh/computer-and-information-technology/software-developers.htm

The 1.4 multiplier is a common rule of thumb rather than a published figure. At $100 an
hour, the roughly $1,120 a month that 800 tasks cost on the most expensive model is about
twelve hours of one developer's time.

## Compounding

The two chained accuracy figures are arithmetic rather than measurements. Over 40 steps,
0.99 to the power of 40 is 66.9 per cent and 0.97 to the power of 40 is 29.6 per cent. The
per step rates themselves are illustrative: they show why a two point difference in single
step reliability matters far more on a long agent run than on a single question.

The 40 lap figure for a real agent task, the tool call failure rates, the throughput
figures and the task success curve against task length are all illustrative of a shape
that is widely reported rather than measurements of a specific model.

## Caveats

- Every benchmark score here is self reported by the lab that produced the model, on its
  own scaffold. None of them were independently reproduced.
- Model pricing changed twice in the month before this was written. The Claude Sonnet 5
  rate in particular rises on 1 September 2026.
- The token mix per task, the 80 per cent routing share, the per step accuracy rates and
  the tool call failure rates are illustrative figures chosen to make the arithmetic
  concrete. They are not measurements.
- The $100 loaded hourly rate depends on a 1.4 overhead multiplier that is a convention
  rather than a published statistic.
- The GPU rental figure is a market range, and the two node requirement assumes serving
  the full published weights rather than a further quantised community build.
- The projection past the last measured point in the closing section is not evidence.

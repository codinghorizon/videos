---
layout: default
title: "Open Models Are 14x Cheaper Per Task. Here Is The Catch"
permalink: /nobody-should-pay-for-ai-coding-anymore/
---

# Open Models Are 14x Cheaper Per Task. Here Is The Catch

Every figure quoted in this video, where it came from, and the arithmetic behind it.
All prices are US dollars per million tokens unless stated otherwise. All benchmark
scores and prices are as published in late July 2026; both move often, so treat the
dates as part of the figure.

## Sources

| What | Where |
| --- | --- |
| SWE-bench Verified leaderboard, 29 July 2026 | https://benchlm.ai/benchmarks/sweVerified |
| SWE-bench Verified, open weights flags and vendor prices | https://llm-stats.com/benchmarks/swe-bench-verified |
| SWE-bench Pro leaderboard | https://llm-stats.com/benchmarks/swe-bench-pro |
| DeepSeek API pricing, verified 25 July 2026 | https://deepseek.ai/pricing |
| DeepSeek V4 Pro specs and pricing | https://openrouter.ai/deepseek/deepseek-v4-pro |
| DeepSeek V4 licence, parameters, weight size, hardware | https://localaimaster.com/models/deepseek-v4 |
| Anthropic API pricing, batch and cache rates | https://benchlm.ai/anthropic/api-pricing |
| Cost per task method and comparison table | https://ssojet.com/blog/cheapest-ai-coding-models |
| Measured cost per task on a real harness | https://github.com/Vexp-ai/vexp-swe-bench |
| Token usage per task type, cache read share | https://tokenade.net/en/stats/token-usage-by-task-type |
| H200 cloud pricing across 33 providers | https://getdeploying.com/gpus/nvidia-h200 |
| Kimi K3 pricing and weights status | https://www.digitalapplied.com/blog/open-weight-model-wave-july-2026-momentum-tracker |

## The benchmark

SWE-bench Verified is 500 human validated GitHub issues taken from real repositories.
A model is scored on whether the patch it produces makes the repository's own tests
pass, so the score is a resolved rate rather than a similarity judgement.

Scores on SWE-bench Verified, 29 July 2026:

| Model | Score | Weights |
| --- | --- | --- |
| Claude Opus 5 | 96.0 | closed |
| Claude Mythos 5 | 95.5 | closed |
| Claude Fable 5 | 95.0 | closed |
| Ornith 1.0 397B | 82.4 | open |
| Claude Opus 4.6 | 80.8 | closed |
| DeepSeek V4 Pro (Max) | 80.6 | open |
| Gemini 3.1 Pro | 80.6 | closed |
| MiniMax M3 | 80.5 | open |
| Kimi K2.6 | 80.2 | open |
| GPT-5.2 | 80.0 | closed |
| DeepSeek V4 Flash (Max) | 79.0 | open |

Two gaps are quoted from that table:

- Best closed against best open weights: `96.0 - 82.4 = 13.6` points.
- Claude Opus 4.6 against DeepSeek V4 Pro: `80.8 - 80.6 = 0.2` points. Opus 4.6 is a
  previous generation flagship, which is the basis for the claim that open weights
  caught the prior frontier rather than the current one.

Gemini 3.1 Pro at 80.6 is level with DeepSeek V4 Pro to the tenth of a point, and
GPT-5.2 sits at 80.0, which is why the video says closed models are also clustered at
that level rather than the cluster being an open weights problem.

DeepSeek V4 Pro Max and DeepSeek V4 Flash Max are the highest reasoning effort
settings of those two models. Lower settings score lower on the same board: V4 Pro
(High) 79.4, V4 Flash (High) 78.6.

## SWE-bench Pro

SWE-bench Pro is the harder variant, built from longer multi step tasks that need
extended reasoning rather than a single localised fix. Scores:

| Model | Score |
| --- | --- |
| Claude Fable 5 | 80.0 |
| GLM 5.2 | 62.1 (top open weights) |
| MiniMax M3 | 59.0 |
| Kimi K2.6 | 58.6 |
| DeepSeek V4 Pro Max | 55.4 |

`80.0 - 55.4 = 24.6` points. That is the figure behind the claim that the gap widens
as tasks get closer to real work: 13.6 points on Verified becomes 24.6 points on Pro
for the same pair of vendors.

## Model and licence facts

DeepSeek V4 shipped on 24 April 2026 with weights and code under a single MIT licence,
which permits commercial use, fine tuning and redistribution.

- V4 Pro: 1.6 trillion total parameters, roughly 49 billion active per token, 1 million
  token context window.
- V4 Flash: 284 billion total, roughly 13 billion active.

Kimi K3 is quoted as a counterexample to open meaning cheap: $3.00 input and $15.00
output, with open weights announced for late July 2026 and not published as of the
figures above.

## Prices per million tokens

| Model | Input | Cache read | Output |
| --- | --- | --- | --- |
| DeepSeek V4 Pro | $0.435 | $0.003625 | $0.87 |
| DeepSeek V4 Flash | $0.14 | $0.0028 | $0.28 |
| Kimi K3 | $3.00 | $0.30 | $15.00 |
| Claude Opus 5 | $5.00 | $0.50 | $25.00 |

Anthropic cache reads are 10 per cent of the base input rate, so `$5.00 x 0.10 = $0.50`.
Anthropic's batch API takes 50 per cent off both directions, giving Claude Opus 5
batch rates of $2.50 input and $12.50 output, with results returned within 24 hours.

Per token multiples between DeepSeek V4 Pro and Claude Opus 5:

- Input: `5.00 / 0.435 = 11.49`, quoted as 11.5 times.
- Output: `25.00 / 0.87 = 28.74`, quoted as 28.7 times.
- Cache read: `0.50 / 0.003625 = 137.9`, quoted as 138 times.

## Cost per resolved task, fixed attempt model

The comparison uses one fixed token budget per attempt for every model, so the only
things that vary are the published prices and the published solve rate. The budget is
50,000 input tokens for repository context and conversation history, and 12,000 output
tokens for reasoning and the patch. Cost per resolved task is the cost of one attempt
divided by the solve rate, which prices in the fact that a failed attempt still costs
a full attempt.

DeepSeek V4 Pro, one attempt:

```
input   0.050M x $0.435 = $0.021750
output  0.012M x $0.870 = $0.010440
attempt                 = $0.032190
per resolved task = 0.032190 / 0.806 = $0.039938   -> $0.040
```

Claude Opus 5, one attempt:

```
input   0.050M x $5.00  = $0.250000
output  0.012M x $25.00 = $0.300000
attempt                 = $0.550000
per resolved task = 0.55 / 0.96 = $0.572917        -> $0.573
```

`0.572917 / 0.039938 = 14.34`, quoted as 14.3 times. The solve rate advantage of the
more expensive model is already inside that number, because it is the divisor.

Claude Opus 5 on the batch API:

```
input   0.050M x $2.50  = $0.125
output  0.012M x $12.50 = $0.150
attempt                 = $0.275
per resolved task = 0.275 / 0.96 = $0.286458       -> $0.286
```

`0.286458 / 0.039938 = 7.17`, quoted as about 7 times the open model's standard price.

As a sanity check on the modelled figure, an open harness measured $0.67 per task
running Claude Code over a 100 task subset of SWE-bench Verified at a 73 per cent
pass rate. That is the same order as the $0.573 the fixed budget model predicts.

## What the fixed attempt model hides

Over 100 tickets, using the same attempt cost and the published solve rates:

```
Claude Opus 5    100 x $0.550000 = $55.00   resolves 96.0
DeepSeek V4 Pro  100 x $0.032190 = $ 3.22   resolves 80.6
saving                           = $51.78
extra unresolved  96.0 - 80.6    = 15.4 tickets
saving per extra failure  51.78 / 15.4 = $3.3624   -> $3.36
```

At a chosen rate of $100 per hour for engineer time, $100/60 = $1.6667 per minute, so
`3.3624 / 1.6667 = 2.02` minutes. That is the two minute figure: each extra failure
has to be diagnosed and fixed in about two minutes before the saving is gone. The
$100 per hour rate is a stated assumption, not a measured figure; the conclusion
scales linearly with whatever rate you substitute.

The 15.4 extra failures are not a random sample of the backlog. The SWE-bench Pro
figures above show the same vendors separating by 24.6 points rather than 13.6 once
tasks get longer and need multi step reasoning, so the failures concentrate in the
harder tail.

## Real token volumes

A coding task in the SWE-bench class consumes between 1 million and 3.5 million tokens
per task in measured agentic runs, including retries and self correction. The same task
run twice can differ by up to 30 times in total tokens, and higher token consumption
does not correlate with higher accuracy.

In a production agent workflow, 82 to 83 per cent of input tokens were cache reads:
context the agent has already paid to read, being re read as the conversation grows.

The 62,000 token attempt used in the fixed model is therefore optimistic by between 16
and 56 times against that measured range.

## Cost per resolved task at real volumes

Modelling one task as 1.5 million input tokens with 83 per cent of them served as cache
reads, plus 100,000 output tokens:

```
cache reads  1.5M x 0.83 = 1.245M
new input    1.5M x 0.17 = 0.255M
output                   = 0.100M
total                    = 1.600M
```

Those are the token volumes shown on screen: cache reads 1.25M, new input 0.26M,
output 0.10M. As a share of every token processed, cache reads are
`1.245 / 1.600 = 77.8` per cent, which is the sense in which cache reads are the
largest single line on the bill.

DeepSeek V4 Pro:

```
1.245M x $0.003625 = $0.004513
0.255M x $0.435    = $0.110925
0.100M x $0.870    = $0.087000
total              = $0.202438
per resolved task  = 0.202438 / 0.806 = $0.251164  -> $0.25
```

Claude Opus 5:

```
1.245M x $0.50  = $0.622500
0.255M x $5.00  = $1.275000
0.100M x $25.00 = $2.500000
total           = $4.397500
per resolved task = 4.3975 / 0.96 = $4.580729      -> $4.58
```

`4.580729 / 0.251164 = 18.24`, quoted as 18.2 times. The multiple grows from 14.3 to
18.2 once cache reads are priced in, because DeepSeek's cache read discount is far
deeper than Anthropic's: 99.2 per cent off its own input rate against 90 per cent off.

Redoing the 100 ticket comparison at these volumes:

```
DeepSeek V4 Pro  100 x $0.202438 = $ 20.24   resolves 80.6
Claude Opus 5    100 x $4.397500 = $439.75   resolves 96.0
saving                           = $419.51
saving per extra failure  419.51 / 15.4 = $27.24
```

At $100 per hour, `27.24 / 1.6667 = 16.3` minutes, quoted as 16 minutes. The headroom
per failure grows from two minutes to sixteen purely because the task got bigger, which
is the reversal the video describes.

## Running the weights yourself

DeepSeek V4 Pro's BF16 weights are about 3.2 TB on disk. Quantised to four bits they
are about 800 GB.

An eight GPU H200 node provides `8 x 141 GB = 1,128 GB` of VRAM, so the full precision
weights do not fit on a single node while the four bit version does.

H200 cloud pricing varies widely by provider. On demand rates run from about $2.30 to
$5.99 per GPU hour, with a tracked median around $4.22. An eight GPU H200 node is
quoted at $34.32 per hour.

```
$34.32 x 24 x 30 = $24,710.40 per month, running continuously
```

Against DeepSeek's own API price for a task at the real volumes above:

```
24,710.40 / 0.202438 = 122,065 tasks per month   -> about 122,000
122,065 / 30         = 4,069 tasks per day       -> about 4,000
```

Below roughly 4,000 tasks a day, paying DeepSeek's API is cheaper than renting the
hardware to serve the same model, before any staff time to operate it.

## Caveats worth knowing

- Leaderboard scores are as reported by public aggregators on the dates given. Vendors
  and harnesses report differently, and a score is a property of a model plus a harness
  plus a prompt, not of a model alone.
- The fixed attempt model deliberately holds token counts constant across models so
  that price and solve rate are the only variables. Real models differ in how many
  turns and tokens they spend on the same task, which this does not capture.
- Cost per resolved task divides by the solve rate. That charges retries to the price
  but assumes a failed attempt costs exactly one attempt, which understates cases where
  an agent loops before giving up.
- GPU rental prices span roughly a 90 per cent range between the cheapest and dearest
  listings for the same card, so the self hosting break even moves a long way depending
  on the provider and commitment term.
- The $100 per hour engineer rate is an assumption chosen to make the trade off legible,
  not a measured figure.

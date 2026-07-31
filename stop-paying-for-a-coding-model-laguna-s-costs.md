---
layout: default
title: "Stop Paying for a Coding Model. Laguna S Costs 20 Cents"
permalink: /stop-paying-for-a-coding-model-laguna-s-costs/
date: 2026-07-31
---

# Stop Paying for a Coding Model. Laguna S Costs 20 Cents

Every figure this video puts on screen, and where it came from. Checked 31 July 2026.

## The model

**Laguna S 2.1 was released by poolside on 21 July 2026.**
Source: poolside, "Introducing Laguna S 2.1", https://poolside.ai/blog/introducing-laguna-s-2-1

**118 billion total parameters, roughly 8 billion activated per token.** It is a mixture of
experts model built for agentic software engineering.
Source: poolside launch post, and the Hugging Face model card at
https://huggingface.co/poolside/Laguna-S-2.1

**The weights are published on Hugging Face under the OpenMDW-1.1 licence**, which permits
commercial and non-commercial use and modification. BF16, FP8, INT4 and NVFP4 checkpoints
are published, along with GGUF and MLX conversions.
Sources: https://huggingface.co/poolside/Laguna-S-2.1,
https://huggingface.co/poolside/Laguna-S-2.1-FP8,
https://huggingface.co/poolside/Laguna-S-2.1-NVFP4

**Context: 1,048,576 tokens on the paid endpoint, 262,144 on the free one.** The published
checkpoint is configured for 262,144 tokens; training included a long context extension
stage to 1,048,576, and poolside states 1M in both thinking and no thinking modes.
Sources: poolside launch post; Hugging Face model card;
https://openrouter.ai/poolside/laguna-s-2.1 and
https://openrouter.ai/poolside/laguna-s-2.1:free

## The benchmark

**Terminal-Bench 2.1: 70.2% with max thinking, 60.4% with thinking off.** Terminal-Bench
runs long horizon tasks in a real shell and grades the end state of the machine rather than
an answer.
Source: poolside launch post, benchmark table

**DeepSeek V4 Pro Max scores 64.0% on the same table, at 1.6 trillion total parameters
with 49 billion active.** That is the 6.2 point gap and the roughly 13x parameter
difference the video states (1.6T / 118B = 13.6).
Source: poolside launch post, benchmark table

**One open model on that table scores higher: Tencent Hy3, 295B total with 21B active, at
71.7%.** Laguna S 2.1 is not the top open model on this benchmark.
Source: poolside launch post, benchmark table

**Other results poolside published on the same day**, not used on screen but relevant to
how broad the claim is: SWE-Bench Multilingual 78.5% thinking / 71% no thinking, SWE-Bench
Pro (public) 59.4% / 53%, DeepSWE v1.1 40.4% / 16.5%, SWE Atlas 46.2%, Toolathlon Verified
49.7%.
Source: poolside launch post

**Caveat carried on screen: these are the vendor's own published figures.** The video says
so in the shot rather than in a footnote, because independent reruns of a ten day old
position are thin.

## The prices

**Laguna S 2.1 on OpenRouter lists at $0.10 per million input tokens and $0.20 per million
output tokens**, with cache reads at $0.01 per million. At the time of checking the model
page showed a 10% discount, $0.09 and $0.18, which is why the video says the listed price
moves.
Sources: poolside launch post (list price);
https://openrouter.ai/poolside/laguna-s-2.1 (live card, 31 July 2026)

**The free endpoint is free, at 262,144 tokens of context, and OpenRouter states that
inputs and outputs on the free route may be used to train and improve models.**
Source: https://openrouter.ai/poolside/laguna-s-2.1:free

**One provider serves the model on OpenRouter.** The model page states that OpenRouter
forwards every request to a single host with no routing decision to make, so there is no
failover and no second price.
Source: https://openrouter.ai/poolside/laguna-s-2.1, 31 July 2026

**GPT-5.6 Terra is $2.00 per million input tokens and $12.00 per million output tokens**,
after OpenAI cut Terra by 20% and Luna by 80% on 30 July 2026. Sol was unchanged at $5.00 /
$30.00 and Luna is $0.20 / $1.20.
Sources: https://www.aipricing.guru/openai-pricing/ (read 31 July 2026);
OpenAI, "Advancing the price-performance frontier with GPT-5.6",
https://openai.com/index/advancing-the-price-performance-frontier-with-gpt-5-6/

## The arithmetic

Everything below is worked from the list prices above. It is a modelled example, not a
measurement of anyone's invoice, and the video says so on screen.

**One session, assumed at 2,000,000 input tokens and 250,000 output tokens:**

- Laguna S 2.1: 2.0 x $0.10 + 0.25 x $0.20 = $0.20 + $0.05 = **$0.25**
- GPT-5.6 Terra: 2.0 x $2.00 + 0.25 x $12.00 = $4.00 + $3.00 = **$7.00**
- Ratio: $7.00 / $0.25 = **28x**

**One developer, twenty sessions a day, twenty two working days: 440 sessions.**

- Laguna S 2.1: 440 x $0.25 = **$110**
- GPT-5.6 Terra: 440 x $7.00 = **$3,080**

The session size is an assumption. The prices it multiplies are not.

## The memory

**Weights at each precision, from the parameter count:**

- BF16, two bytes per parameter: 118e9 x 2 = 236 GB
- FP8, one byte: 118 GB
- Four bit: about 59 GB

These are the weights alone, before the KV cache, the activations or any serving overhead.

**poolside states the model is small enough to run on a single NVIDIA DGX Spark**, which
carries 128 GB of unified memory shared between CPU and GPU. The four bit checkpoint at
roughly 59 GB is what makes that fit with room left for the cache; the FP8 checkpoint at
118 GB does not leave meaningful headroom on a 128 GB machine.
Sources: poolside launch post; NVIDIA DGX Spark product page,
https://www.nvidia.com/en-us/products/workstations/dgx-spark/ and the DGX Spark system
overview, https://docs.nvidia.com/dgx/dgx-spark/system-overview.html

## Caveats

- The benchmark figures are poolside's own. Independent reruns were thin at the time of
  checking, and a position ten days old on a leaderboard is not a settled ranking.
- 70.2% is the max thinking figure. The same model scores 60.4% with thinking off, and
  thinking costs output tokens, so the cheap price and the high score are not free of each
  other.
- The session size used for the cost comparison is an assumption, chosen to look like an
  ordinary agentic coding run. A different workload changes the multiple.
- Listed prices moved during the week this was checked, on both sides of the comparison.
- Self hosting economics are stated as a shape rather than a number: no hourly GPU rate,
  utilisation figure or crossover volume is claimed, because those depend on hardware and
  traffic that are not measured here.

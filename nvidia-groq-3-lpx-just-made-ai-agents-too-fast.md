---
layout: default
title: "Nvidia Just Made AI Agents Too Fast To Ignore!"
permalink: /nvidia-groq-3-lpx-just-made-ai-agents-too-fast/
date: 2026-09-01
---

# Nvidia Just Made AI Agents Too Fast To Ignore!

{% raw %}
Every figure, date and benchmark this video puts on screen, chased to a primary source.

## The headline benchmark

**3,431 output tokens per second.** Artificial Analysis benchmarked Gemma 4 31B on
NVIDIA Groq 3 LPX at 100K context and measured a median speed of 3,431 output tokens per
second.
Source: NVIDIA Technical Blog, "How NVIDIA Groq 3 LPX Unlocks Ultrafast Interactivity at
Long Context on NVIDIA Vera Rubin".
https://developer.nvidia.com/blog/how-nvidia-groq-3-lpx-unlocks-ultrafast-interactivity-at-long-context-on-nvidia-vera-rubin/

**3,400 tokens per second**, the rounded figure, and **4x faster responsiveness for agents
and latency sensitive workloads than the nearest alternative platform**.
Source: NVIDIA Newsroom, "NVIDIA Groq 3 LPX Now in Full Production With World Class Speed
for Agentic AI", 24 August 2026.
https://nvidianews.nvidia.com/news/nvidia-groq-3-lpx-now-in-full-production-with-world-class-speed-for-agentic-ai

**870 tokens per second for the fastest public endpoint.** NVIDIA's own chart states
"NVIDIA Groq 3 LPX at 3,431 tokens per second versus 870 for the fastest public endpoint
(Artificial Analysis, August 20, 2026)."
Source: NVIDIA Technical Blog, as above.

**Model and context.** Gemma 4 31B, 100,000 token input context.
Source: NVIDIA Newsroom and NVIDIA Technical Blog, as above.

**5,000 tokens in about 1.5 seconds versus about 50 seconds at 100 tokens per second.**
"At this rate, decoding 5,000 tokens takes about 1.5 seconds versus 50 seconds at 100
tokens per second."
Source: NVIDIA Technical Blog, as above.

## The hardware

Per LPU accelerator: **500 MB of compiler managed SRAM** and **150 TB/s of on chip memory
bandwidth**. Per LPX rack: **256 interconnected LPU accelerators**, **128 GB total SRAM
capacity** and **40 PB/s on chip SRAM bandwidth**.
Source: NVIDIA Technical Blog, "Inside NVIDIA Groq 3 LPX: The Low Latency Inference
Accelerator for the NVIDIA Vera Rubin Platform".
https://developer.nvidia.com/blog/inside-nvidia-groq-3-lpx-the-low-latency-inference-accelerator-for-the-nvidia-vera-rubin-platform

The rack totals are consistent with the per chip figures: 256 x 500 MB is 128 GB, and
256 x 150 TB/s is 38.4 PB/s, which NVIDIA states as 40 PB/s.

**Prefill and decode are split across the two kinds of silicon.** "Vera Rubin NVL72 handles
prefill and hands off the KV cache once per turn. Groq 3 LPX uses this KV cache, along with
weights held in SRAM, to perform the entire decode step."
Source: NVIDIA Technical Blog, "How NVIDIA Groq 3 LPX Unlocks Ultrafast Interactivity...".

**Deterministic, compiler scheduled execution.** The LPU uses a spatial execution model in
which the compiler explicitly schedules computation, data movement and synchronisation,
rather than relying on dynamic hardware schedulers, with a chip to chip protocol in
hardware that cancels clock drift across hundreds of accelerators.
Source: NVIDIA Technical Blog, "Inside NVIDIA Groq 3 LPX...".

Independent corroboration of 500 MB per LPU, 150 TB/s per LPU and 256 LPUs for 128 GB of
SRAM.
Source: The Register, "What Nvidia's first Groq 3 LPU benchmarks do and don't tell us about
its $20B gamble", 24 August 2026.
https://www.theregister.com/systems/2026/08/24/what-nvidias-first-groq-3-lpu-benchmarks-do-and-dont-tell-us-about-its-20b-gamble/5291880

## The power and revenue claims

**Up to 35x higher inference throughput per megawatt** and **up to 10x more revenue per
watt**, for trillion parameter, high context workloads, when Vera Rubin is paired with
Groq 3 LPX. Both are NVIDIA platform claims rather than third party measurements.
Source: NVIDIA, Vera Rubin platform materials.
https://blogs.nvidia.com/blog/vera-rubin-lpx-spectrum-x-nvlink-fusion/
https://www.nvidia.com/en-us/data-center/lpx/

## The nearest alternative

The Register identifies the nearest alternative in NVIDIA's comparison as Cerebras, at
**882 tokens per second under the same conditions**, and notes that Cerebras needed one and
at most two 44 GB CS-3 accelerators for that result where NVIDIA used at least 64 chips.
It also notes that Gemma 4 31B is a best case and questions how the result scales to larger
mixture of experts models.
Source: The Register, as above.

## Cerebras

**Gemma 4 31B at 1,851 output tokens per second**, measured by Artificial Analysis, and
described by Cerebras as 35x the speed of a typical GPU endpoint. Announced 29 June 2026.
Source: Cerebras, "Gemma 4 on Cerebras, The Fastest Inference is Now Multimodal".
https://www.cerebras.ai/blog/gemma-4-on-cerebras-the-fastest-inference-is-now-multimodal

**GPT OSS 120B at 1,697 tokens per second**, the fastest provider measured, ahead of
SambaNova at 707 and Groq at 476.
Source: Artificial Analysis, gpt-oss-120b provider benchmarking.
https://artificialanalysis.ai/models/gpt-oss-120b/providers

**Kimi K2.6, a trillion parameter model, at 981 tokens per second in enterprise trials**,
described by Artificial Analysis as the fastest performance it has measured on a trillion
parameter model.
Source: Cerebras, "Cerebras Brings Kimi K2.6 Inference to Enterprises".
https://www.cerebras.ai/blog/cerebras-kimi-k2-Enterprise

## AMD and Cerebras

Announced 23 July 2026: a disaggregated inference solution pairing AMD Helios rack scale
systems with the Cerebras Wafer Scale Engine. AMD Helios provides the scalable throughput
engine; the Cerebras Wafer Scale Engine provides ultra fast, ultra low latency decode and
token generation. The two are **expected to deliver up to 5x higher tokens per second per
watt**. Availability first through Cerebras Cloud in the second half of 2026.

The 5x baseline is a Cerebras only configuration, not a general industry baseline.
Source: AMD Newsroom and Cerebras.
https://ir.amd.com/news-events/press-releases/detail/1293/amd-and-cerebras-announce-industry-leading-ultra-low-latency-and-high-throughput-ai-inference-solution
https://www.cerebras.ai/press-release/amd-and-cerebras-announce-industry-leading-ultra-low-latency-and-high-throughput-ai-inference

## The NVIDIA and Groq arrangement

NVIDIA secured a licence to Groq's LPU inference technology and absorbed key engineering
staff, including founder Jonathan Ross and president Sunny Madra, in a deal reported at
around $20 billion. Groq's cloud business was not part of the transaction, and Groq
continues to operate as an independent inference cloud.
Source: Tom's Hardware and The Register.
https://www.tomshardware.com/tech-industry/semiconductors/nvidia-confirms-20-billion-groq-deal-to-bolster-ai-inference-dominance

## Adopters

Groq is among the first to bring NVIDIA Groq 3 LPX and Vera Rubin NVL72 to market, working
with Dell Technologies on deployment.
Source: Groq. https://groq.com/blog/groq-among-the-first-to-bring-nvidia-groq-3-lpx-and-vera-rubin-nvl72-to-market

Nebius Token Factory is the first AI cloud to adopt NVIDIA Groq 3 LPX.
Source: Nebius. https://nebius.com/blog/posts/nvidia-groq-3-lpx-nebius-token-factory

## Caveats

The description of the LPX benchmark endpoint as private is supported indirectly rather
than stated in those words: NVIDIA's own comparison is against the fastest **public**
endpoint, and press coverage at the time of the announcement notes that no public API date
had been given for LPX. NVIDIA does not use the word private.

The 35x throughput per megawatt and 10x revenue per watt figures are NVIDIA platform
projections for trillion parameter, high context workloads. They are not third party
measurements and are not a price change available to buy today.
{% endraw %}

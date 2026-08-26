---
layout: default
title: "NVIDIA Groq 3 LPX Makes AI Agents Feel Alive Now"
permalink: /nvidia-groq-3-lpx-agent-latency/
date: 2026-08-26
---

# NVIDIA Groq 3 LPX Makes AI Agents Feel Alive Now

{% raw %}
Every figure, name and comparison this video puts on screen, chased to a primary source.
Numbers that could not be sourced are not rendered.

## The acquisition

NVIDIA agreed to acquire Groq's intellectual property and key engineering staff for about
20 billion dollars, in a definitive agreement dated 24 December 2025. It is the largest
transaction in the company's history, ahead of the roughly 7 billion dollar Mellanox
purchase in 2019.

The structure matters and the video's phrasing simplifies it: NVIDIA licensed Groq's LPU
intellectual property and hired members of its engineering team, including founder
Jonathan Ross and president Sunny Madra. It did not buy Groq as a company, and Groq
continues to operate as an inference cloud.

- CNBC, 24 December 2025 — https://www.cnbc.com/2025/12/24/nvidia-buying-ai-chip-startup-groq-for-about-20-billion-biggest-deal.html
- CNBC, 24 August 2026 — https://www.cnbc.com/2026/08/24/nvidia-says-groq-racks-will-be-online-this-year-after-20-billion-deal.html
- Tom's Hardware — https://www.tomshardware.com/tech-industry/semiconductors/nvidia-confirms-20-billion-groq-deal-to-bolster-ai-inference-dominance

## What Groq 3 LPX is

NVIDIA's own description: "the interactive AI inference accelerator for NVIDIA Vera
Rubin", a rack mount accelerator that extends the Vera Rubin platform. Rubin GPUs handle
large scale context processing while LPX accelerates the latency sensitive decode stage.
Announced in full production on 24 August 2026.

- NVIDIA product page — https://www.nvidia.com/en-us/data-center/lpx/
- NVIDIA newsroom, full production — https://nvidianews.nvidia.com/news/nvidia-groq-3-lpx-now-in-full-production-with-world-class-speed-for-agentic-ai
- NVIDIA blog — https://blogs.nvidia.com/blog/vera-rubin-lpx-spectrum-x-nvlink-fusion/

## The benchmark number

"Median speed across samples with 100K input context length was 3,431 tokens/second",
measured on Gemma 4 31B in Artificial Analysis benchmarking. The comparison baseline
NVIDIA gives in the same post is 870 output tokens per second for the fastest public
endpoint.

Same post, other figures:

- 10K input context: 3,382 output tokens per second, against 1,402 for the fastest public endpoint.
- SPEED-Bench coding benchmark: 4,767 output tokens per second median, P80 of 5,520.
  20 per cent of tasks on that dataset completed at over 5,500 tokens per second.
- Generating 5,000 output tokens: 50 seconds at 100 tokens per second, 1.5 seconds at the
  measured LPX speed. NVIDIA states that as a 34x speedup.
- The agentic session NVIDIA traces reaches a 500,000 token limit over more than 226 steps.

The newsroom release rounds the headline figure to "record 3,400 output tokens per second
in Artificial Analysis benchmarking running Gemma 4 31B".

- NVIDIA Technical Blog — https://developer.nvidia.com/blog/how-nvidia-groq-3-lpx-unlocks-ultrafast-interactivity-at-long-context-on-nvidia-vera-rubin/

## Hardware specifications

Per LPU accelerator:

- 500 MB of SRAM
- 150 TB/s of SRAM bandwidth
- 2.5 TB/s scale up bandwidth

Per rack:

- 256 interconnected LPU accelerators
- 40 PB/s of SRAM bandwidth
- 640 TB/s of scale up bandwidth
- 128 GB of SRAM fused with 12 TB of DDR5 memory

The technical blog describes the same rack as "256 LP30 local processing units (LPUs)"
with "128 GB of total SRAM-based memory collectively in those chips" and "96 C2C links
per chip running at 112 Gbps each", scheduling computation and communication overlap on
320 byte vectors.

- NVIDIA product page — https://www.nvidia.com/en-us/data-center/lpx/
- NVIDIA Technical Blog — https://developer.nvidia.com/blog/how-nvidia-groq-3-lpx-unlocks-ultrafast-interactivity-at-long-context-on-nvidia-vera-rubin/

## The power and revenue claims

NVIDIA states "35x higher throughput per megawatt (MW) for trillion-parameter models" and
"10x more revenue per watt" for Vera Rubin paired with LPX. The video says "10 times more
revenue opportunity", which is a looser wording of the same claim.

NVIDIA also claims "4x faster responsiveness for agents and latency-sensitive workloads
than the nearest alternative platform".

All four are vendor figures, published by NVIDIA about its own product, and the product
page marks its performance table "Projected performance subject to change". They are
presented on screen as NVIDIA's claims rather than as independent results.

- NVIDIA product page — https://www.nvidia.com/en-us/data-center/lpx/
- NVIDIA newsroom — https://nvidianews.nvidia.com/news/nvidia-groq-3-lpx-now-in-full-production-with-world-class-speed-for-agentic-ai

## Early adopters

Nebius is named as the first AI cloud to adopt Groq 3 LPX. Groq itself plans to be among
the earliest adopters of the platform built on the IP it sold.

- NVIDIA newsroom — https://nvidianews.nvidia.com/news/nvidia-groq-3-lpx-now-in-full-production-with-world-class-speed-for-agentic-ai
- Groq — https://groq.com/blog/groq-among-the-first-to-bring-nvidia-groq-3-lpx-and-vera-rubin-nvl72-to-market

## Caveats

- Every performance figure in this video originates with NVIDIA. There is no independent
  reproduction of the 3,431 tokens per second result at the time of writing.
- The 35x throughput per megawatt and 10x revenue per watt figures are marked as
  projections by NVIDIA, not measured results.
- The video says NVIDIA "bought" Groq. The deal was for intellectual property and staff,
  not the company.
- "10 times more revenue opportunity" in the narration is NVIDIA's "10x more revenue per
  watt". The per watt qualifier is dropped in the spoken line.
{% endraw %}

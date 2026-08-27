---
layout: default
title: "OpenAI Just Put Nvidias AI Chip Monopoly On Notice"
permalink: /openai-jalapeno-nvidia-deepseek/
date: 2026-08-27
---

# OpenAI Just Put Nvidias AI Chip Monopoly On Notice

{% raw %}
Sources for every figure, date and benchmark this video puts on screen. Checked 26 August 2026.

## The chip

**Jalapeno is OpenAI's first custom accelerator, designed with Broadcom, and it is for
inference rather than training.** Broadcom supplies the silicon implementation plus the
networking and connectivity; Celestica does board, rack and system integration. OpenAI
describes it as generation one of a multi generation platform.

- OpenAI, *OpenAI and Broadcom unveil LLM optimized inference chip* — https://openai.com/index/openai-broadcom-jalapeno-inference-chip/
- Broadcom investor relations, *OpenAI and Broadcom Unveil LLM-Optimized Intelligence Processor* — https://investors.broadcom.com/news-releases/news-release-details/openai-and-broadcom-unveil-llm-optimized-intelligence-processor
- CNBC, 24 June 2026, *OpenAI and Broadcom reveal Jalapeno, first AI chip in partnership* — https://www.cnbc.com/2026/06/24/openai-and-broadcom-reveal-jalapeno-first-ai-chip-in-partnership.html

**Deployment begins inside OpenAI's own infrastructure by the end of 2026, in limited
volume, with a larger rollout into 2027. OpenAI says it will keep deploying Nvidia and
other accelerators alongside it.**

- Converge Digest, *OpenAI Jalapeno inference chip performance* — https://convergedigest.com/openai-jalapeno-inference-chip-performance/
- The Register, 25 August 2026 — https://www.theregister.com/systems/2026/08/25/openais-upcoming-jalapeno-chip-looks-like-itll-be-an-inference-beast/5292052

**Gen 2 is described as deep in development and Gen 3 as taking shape.** Gen 2 targets
performance per watt; Gen 3 targets economical low latency serving through aggregate HBM
bandwidth rather than raw bandwidth alone.

- ServeTheHome, *OpenAI Jalapeno Custom AI ASIC at Hot Chips 2026* — https://www.servethehome.com/openai-jalapeno-asic-at-hot-chips-2026/

## The published part specifications

Presented by OpenAI at Hot Chips 2026 and reported from the session.

| Figure on screen | Value | Where |
|---|---|---|
| Package power | 700 W (never above 550 W on any tested workload) | Hot Chips 2026, Tom's Hardware |
| Memory | 216 GiB HBM4 | Hot Chips 2026 |
| Memory bandwidth | 15.4 TB/s per chip | Hot Chips 2026 |
| Peak matrix compute | 13.4 PFLOP/s (mxfp4) | Hot Chips 2026 |
| Local domain | 128 chips at 600 GB/s | Hot Chips 2026 |
| Global domain | 2,048 chips at 200 GB/s | Hot Chips 2026 |
| Full system | 27 EFLOP/s, 432 TiB | Hot Chips 2026 |
| Comparison power | GB200 1,200 W, GB300 1,400 W | Tom's Hardware |

The KV cache is kept local on Jalapeno rather than moved between specialised systems, and
idle silicon blocks are powered down per phase. That is the design point the video's
serving system beats draw.

- ServeTheHome — https://www.servethehome.com/openai-jalapeno-asic-at-hot-chips-2026/
- Tom's Hardware, 25 August 2026 — https://www.tomshardware.com/tech-industry/semiconductors/openai-says-its-jalapeno-chip-beats-nvidias-gb300-in-first-published-benchmarks

## The benchmark

**InferenceX is a public inference benchmark suite from SemiAnalysis.** SemiAnalysis ran it
with OpenAI engineers in OpenAI's own lab. The published comparison covers three open
models: GPT OSS 120B, DeepSeek R1 670B, and Moonshot AI's Kimi K2.5 at 1 trillion
parameters.

- InferenceX by SemiAnalysis — https://inferencex.semianalysis.com/
- SemiAnalysis newsletter, *OpenAI Jalapeño: Better Than Nvidia Blackwell* — https://newsletter.semianalysis.com/p/openai-jalapeno-better-than-nvidia

**Across the suite:** 1.5x to 1.9x more throughput per kilowatt at peak, and 1.7x to 3.6x
lower end to end latency, against Nvidia GB200 and GB300 rack systems. Minimum time
between tokens improved 2.7x to 4.1x across the three models.

- Tom's Hardware — https://www.tomshardware.com/tech-industry/semiconductors/openai-says-its-jalapeno-chip-beats-nvidias-gb300-in-first-published-benchmarks
- Neowin — https://www.neowin.net/news/openais-upcoming-jalapeo-ai-chip-outperforms-nvidia-gb300-in-inference-tests/

## The DeepSeek R1 numbers, which the video states largest

Every figure the shots render for DeepSeek R1 against Nvidia GB300:

| On screen | Value | Ratio as drawn |
|---|---|---|
| Peak mixed tokens per second per kilowatt | 19,641 against 11,781 | 1.7x, divided from the pair |
| End to end latency | 1.65 s against 5.99 s | 3.6x, divided from the pair |
| Minimum time between tokens | top of the published range | 4.1x |

The shots compute every multiple from the two values beside it rather than printing a
typed number, so the chart and the caption cannot disagree.

- OpenAI, *Jalapeño's first results show industry leading speed and efficiency in AI inference* — https://openai.com/index/jalapeno-first-results/
- Enterprise DNA AI Pulse, 25 August 2026 — https://enterprisedna.co/resources/ai-pulse/ai-pulse-2026-08-25-openai-s-jalapen-o-inference-chip-beats-nvidia-s-blackwell-i/
- Tech Times, 26 August 2026 — https://www.techtimes.com/articles/325577/20260826/jalapeno-beats-nvidia-gb300-efficiency-semianalysis-confirms-19x-lead.htm

## The other custom silicon named on screen

Google TPU, Amazon Trainium and Inferentia, Microsoft Maia and Meta MTIA are all real,
shipping programmes, and all of them are captive to their builders rather than rentable as
parts.

- Spheron, *Hyperscaler Custom AI Chips in 2026* — https://www.spheron.network/blog/hyperscaler-custom-ai-chips-2026-trainium-tpu-maia-mtia-vs-nvidia-gpu/
- Hashrate Index, *Inside the Custom AI Chip Race* — https://hashrateindex.com/blog/hyperscaler-ai-asic-market-report-part-1/
- CNBC, 26 August 2026, *OpenAI's Jalapeño AI chip brings new threat to Nvidia margins* — https://www.cnbc.com/2026/08/26/openai-jalapeno-ai-chip-nvidia.html

## What the comparison is conditioned on

Stated plainly because the video's own caveat chapter draws it:

- The figures are **power normalised** using each accelerator's published package thermal
  design power, which is what makes a 700 W part comparable with a 1,400 W one at all.
- Specific model configurations and specific operating points were chosen.
- The competitive analysis **excluded speculative decoding**.
- OpenAI has not published system level power consumption, only package TDP.
- The comparison systems were selected for the benchmark, and Nvidia's next systems are
  not standing still.

- The Register — https://www.theregister.com/systems/2026/08/25/openais-upcoming-jalapeno-chip-looks-like-itll-be-an-inference-beast/5292052
- Tom's Hardware — https://www.tomshardware.com/tech-industry/semiconductors/openai-says-its-jalapeno-chip-beats-nvidias-gb300-in-first-published-benchmarks

## Not chased to a primary source

These appear in the narration and are illustrative rather than measured. The shots that
carry them draw a mechanism rather than printing a figure as fact.

- The per step latency and per task token counts in the coding agent beats. No published
  figure exists for a generic agent loop, so those shots show the shape of the cost rather
  than claiming a measured one.
- The cost, margin, price and invoice figures in the pricing chapters. OpenAI does not
  publish unit economics, so those shots are drawn as relationships and levers.
- Jevons paradox as applied to inference demand. It is a well established economic
  observation, and its application here is the script's argument rather than a measurement.
- Workload share splits and negotiation terms in the "not the only answer" beats. These
  are directional, and the shot draws movement rather than stating a market share.
{% endraw %}

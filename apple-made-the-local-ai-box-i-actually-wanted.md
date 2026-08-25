---
layout: default
title: "Apple Just Made The Local AI Box Developers Need"
permalink: /apple-made-the-local-ai-box-i-actually-wanted/
date: 2026-08-25
---

# Apple Just Made The Local AI Box Developers Need

{% raw %}
Every figure, price, core count and capacity the finished picture puts on screen, chased to
a primary source. Anything that could not be chased to one is listed at the bottom and is
not drawn.

Announcement date: 25 August 2026. Pre-orders opened the same day; both machines ship
22 September 2026.

---

## The M6 Mac mini

| Figure on screen | Value | Source |
| --- | --- | --- |
| Starting price | $899 (US), $799 education | [Apple Newsroom, Mac mini with M6 and M5 Pro](https://www.apple.com/newsroom/2026/08/apple-unveils-a-more-powerful-mac-mini-featuring-the-all-new-m6-and-m5-pro/) |
| CPU | 12 cores | same |
| GPU | 12 cores, Neural Accelerators in every core | same |
| Neural Engine | dual 16 core, up to 2x the previous generation | same |
| Unified memory | 16 GB standard, configurable to 32 GB | same |
| Memory bandwidth | up to 170 GB/s | same |
| Storage | up to 2 TB, described as 2x faster than M4 | same |
| AI performance | up to 4x faster than M4 Mac mini | same |
| Graphics | up to 2x faster than M4 Mac mini | same |
| LLM processing | up to 4.8x faster than M4, up to 13.5x faster than M1, measured in LM Studio | same |
| Process node | 2 nm | [Apple Newsroom, M6 and M5 Ultra](https://www.apple.com/newsroom/2026/08/apple-introduces-m6-and-m5-ultra-for-a-big-leap-in-performance-and-ai-compute/) |
| Bandwidth in context | 170 GB/s is a 10% rise over M5 and 2.5x M1 | same |
| Ports and radios | three Thunderbolt 4, HDMI, 2.5 Gb Ethernet, Wi Fi 7, Bluetooth 6 | [MacRumors, 25 Aug 2026](https://www.macrumors.com/2026/08/25/apple-announces-2026-mac-mini/) |

**32 GB is the ceiling, not a step on the way to more.** Apple's own wording is "16GB of
unified memory as standard, configurable up to 32GB". The video's line about a higher
configuration going past 32 GB is conditional, and the answer for the M6 mini is that it
does not: the machine that does is the M5 Pro.

Those two ratios are what the generation chart is drawn from, rather than from remembered
per chip numbers: 170 divided by 2.5 gives the M1's 68 GB/s, and 170 divided by 1.1 gives
the M5's 155 GB/s. The M4's 120 GB/s comes from its own tech specs page. Nothing between
them is filled in.

## The M5 Pro Mac mini

| Figure | Value | Source |
| --- | --- | --- |
| Starting price | $1,699 (US) | [Apple Newsroom, Mac mini](https://www.apple.com/newsroom/2026/08/apple-unveils-a-more-powerful-mac-mini-featuring-the-all-new-m6-and-m5-pro/) |
| CPU | up to 18 cores | same |
| GPU | up to 20 cores | same |
| Unified memory | up to 64 GB | same |
| Memory bandwidth | 307 GB/s | same |
| Storage / ports | up to 8 TB, three Thunderbolt 5 | same, and MacRumors as above |

## The M4 Mac mini, which it replaces

| Figure | Value | Source |
| --- | --- | --- |
| Launch price | $599 (US) | [Apple Newsroom, Oct 2024](https://www.apple.com/newsroom/2024/10/apples-new-mac-mini-is-more-mighty-more-mini-and-built-for-apple-intelligence/) |
| CPU / GPU | 10 cores each | [Apple Support, Mac mini 2024 tech specs](https://support.apple.com/en-us/121555) |
| Unified memory | 16 GB standard, configurable to 32 GB | same |
| Memory bandwidth | 120 GB/s | same |
| Price before this announcement | had risen to $799 | [MacRumors, 25 Aug 2026](https://www.macrumors.com/2026/08/25/apple-announces-2026-mac-mini/) |

So the base memory did not move between M4 and M6, and the ceiling did not move either.
What moved is bandwidth (120 to 170 GB/s), core counts (10 to 12) and price.

## The Mac Studio, announced the same day

| Machine | Price | CPU | GPU | Unified memory | Bandwidth |
| --- | --- | --- | --- | --- | --- |
| Mac Studio, M5 Max | $2,499 | 18 core | up to 40 core | up to 128 GB | 614 GB/s |
| Mac Studio, M5 Ultra | $5,499 | up to 36 core | up to 80 core | up to 512 GB | 1.2 TB/s |

Source: [Apple Newsroom, Mac Studio with M5 Max and M5 Ultra](https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/).
The 512 GB configuration is noted as arriving later than the rest of the line.

---

## The other side: graphics memory

Desktop GeForce RTX 50 series memory capacity, which is the wall the video describes:

| Card | Memory |
| --- | --- |
| RTX 5090 | 32 GB GDDR7 |
| RTX 5080 | 16 GB GDDR7 |
| RTX 5070 Ti | 16 GB GDDR7 |
| RTX 5070 | 12 GB GDDR7 |
| RTX 5060 Ti | 16 GB or 8 GB GDDR7 |
| RTX 5060 | 8 GB GDDR7 |

Source: [NVIDIA GeForce graphics card comparison](https://www.nvidia.com/en-us/geforce/graphics-cards/compare/).

Power, for the chapter that says a gaming PC draws an absurd amount to answer one question:
the RTX 5090's total graphics power is **575 W**, and NVIDIA's own required system power is
**1000 W**. Source: [NVIDIA GeForce RTX 5090](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/).
Those are the two figures the picture uses. A whole system's measured draw is not published
anywhere this could check, so no system figure is put on screen.

The 24 GB tier the script names is the RTX 3090 and RTX 4090 generation, and the RTX 5090
laptop part; it is not a desktop RTX 50 series capacity. Where the picture draws the ladder
it draws the cards by name so the number belongs to a real product.

## How big a model actually is

Download sizes for the default quantized builds Ollama publishes, which is what a viewer
would actually pull:

| Model | Size |
| --- | --- |
| Qwen3 4B | 2.5 GB |
| Qwen3 8B | 5.2 GB |
| Qwen3 14B | 9.3 GB |
| Qwen3 30B | 19 GB |
| Qwen3 32B | 20 GB |
| Qwen3 235B | 142 GB |

Source: [Ollama model library, Qwen3](https://ollama.com/library/qwen3).

These are weights only. Context, the key and value cache, and everything else already
running on the machine sit on top, which is why the picture draws a reserve alongside the
model rather than filling a vessel to its brim.

## The runtimes the video names

- **Ollama** and **LM Studio** are the two applications most people run models through.
  Apple's own M6 AI comparison is quoted "in LM Studio", which is the detail that makes the
  claim checkable rather than a keynote number.
- **llama.cpp** reaches the GPU on a Mac through **Metal**, Apple's graphics and compute
  API.
- **MLX** is Apple's own array framework for Apple Silicon, written around the fact that
  the CPU and GPU share one memory pool, so arrays are not copied across a bus.
- **CUDA** is NVIDIA's, and is the reason research code and inference libraries target
  NVIDIA hardware first.

Source: [Apple Newsroom, M6 and M5 Ultra](https://www.apple.com/newsroom/2026/08/apple-introduces-m6-and-m5-ultra-for-a-big-leap-in-performance-and-ai-compute/) for the LM Studio measurement, and the projects' own documentation for what each one is.

---

## Not checked, and therefore not drawn

- **Tokens per second for the M6 on any specific model.** No independent measurement exists
  yet; the machine had not shipped when this was made. Every shot about speed shows motion
  and relative bore rather than a figure.
- **What Apple's "up to 4x faster AI performance" is measured on.** Apple states an LM
  Studio LLM figure separately (4.8x versus M4), but the headline 4x is not broken down by
  workload. The picture treats the 4x as Apple's claim, attributed, rather than as a
  measured result.
- **Real world memory headroom on a 16 GB machine.** How much the operating system and a
  normal set of applications leave for a model varies by machine and by what is open, so
  the reserve drawn beside a model is illustrative and is labelled as the system's share
  rather than given a precise figure.
- **Whether the M4 Mac mini remains on sale, and at what price.** Coverage of the
  announcement did not state it.
- **Second hand NVIDIA pricing.** The script's "used Nvidia desktop might still win" is an
  opinion about value and no price is put on screen for it.
{% endraw %}

---
layout: default
title: "Your Mac Is Not Slow Your Runtime Is The Problem"
permalink: /your-mac-is-not-slow-your-runtime-is/
date: 2026-09-04
---

# Your Mac Is Not Slow Your Runtime Is The Problem

{% raw %}
Every figure, name and claim this video puts on screen, chased to a primary source.

## MTPLX

An MLX native runtime and Mac app for native multi token prediction speculative decoding
on Apple Silicon, by youssofal.

- Repository: https://github.com/youssofal/MTPLX
- Model catalogue: https://huggingface.co/Youssofal

**The headline claim.** The README states: "the model drafts several tokens ahead of
itself, verifies each drafted block in a single batched forward pass, and commits tokens
through exact rejection sampling with residual correction. Same model, same output
distribution, measured 1.6x faster on a 16 GB M4 Mac mini and 2.24x on an M5 Max."
Source: https://github.com/youssofal/MTPLX

**M4 Mac mini, the paired figures.** The README states: "On a 16 GB M4 Mac mini, tuning the
9B model lands on depth 1: 14.4 tok/s baseline becomes 23.0 tok/s." 14.4 to 23.0 is 1.597x,
which is the 1.6x quoted.
Source: https://github.com/youssofal/MTPLX

**M5 Max, the fast figure.** The Qwen3.6-27B-MTPLX-Optimized-Speed card states: "On the
local Apple M5 Max fanmax sustained benchmark, this artifact reached 63.056 tok/s and
62.886 tok/s at depth 3 on the long-code 192-token prompt when using its
contract-recommended 3-bit draft-only LM head."
Source: https://huggingface.co/Youssofal/Qwen3.6-27B-MTPLX-Optimized-Speed

**Its own heads, not a separate draft model.** The README describes the MTP head as what
enables native speculative decoding: the model drafts its own tokens, with no external
draft model required. That is the distinction the script draws against ordinary
speculative decoding, which pairs a small drafter with a large verifier.
Source: https://github.com/youssofal/MTPLX

**Auto tuning.** `mtplx tune --retune` compares plain autoregressive decoding against
depths 1, 2 and 3 on the machine it is run on, and keeps a recommendation only where the
MTP path wins.
Source: https://github.com/youssofal/MTPLX

**Which models carry MTP heads.** The README states that Qwen 3.5, 3.6 and 3.8 ship with
built in MTP heads.
Source: https://github.com/youssofal/MTPLX

## Qwen3.8-27B

Apache 2.0, natively multimodal with image and video understanding, tool use and long
horizon agentic work, and a native context length of 262,144 tokens.
Source: https://huggingface.co/Qwen/Qwen3.8-27B

## Apple M5 Max

Up to a 40 core GPU, up to 128 GB unified memory, and up to 614 GB/s unified memory
bandwidth. (The script quotes the ceiling of the configurable range, which is what Apple
publishes; it is not what every machine ships with.)
Sources: https://www.apple.com/newsroom/2026/03/apple-debuts-m5-pro-and-m5-max-to-supercharge-the-most-demanding-pro-workflows/
and https://support.apple.com/en-us/126319

## Apple M4, as fitted to the Mac mini

10 core CPU, 10 core GPU, 16 core Neural Engine, 120 GB/s memory bandwidth, 16 GB unified
memory as standard.
Source: https://support.apple.com/en-us/121555

## NVIDIA GeForce RTX 5090

32 GB GDDR7 on a 512 bit interface.
Source: https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/

## NVIDIA RTX PRO 6000 Blackwell Workstation Edition

96 GB GDDR7 with ECC, 1792 GB/s memory bandwidth.
Source: https://www.nvidia.com/en-us/products/workstations/professional-desktop-gpus/rtx-pro-6000/

## Caveats

**The M5 Max baseline of about 28 tokens per second is not a published figure.** The 2.24x
multiplier and the 63.056 tok/s depth 3 result are both published; a 28 tok/s starting
point is what those two produce when divided, and no source states it directly. The only
baseline numbers published on the same benchmark window are greedy diagnostics of the
MTPLX artifact itself, between 57.668 and 61.527 tok/s, which measure a different thing.
The figure is therefore not drawn on screen.
Sources: https://github.com/youssofal/MTPLX and
https://huggingface.co/Youssofal/Qwen3.6-27B-MTPLX-Optimized-Speed

**Acceptance rate is workload dependent.** The claim that code accepts better than prose,
and that context length, sampler, thermals and model size move the result, is the reasoning
the project gives for shipping its tuner. It is not separately measured here.

**"Fifty times a day" is a figure of speech**, not a measured frequency, and is not put on
screen as a number.
{% endraw %}

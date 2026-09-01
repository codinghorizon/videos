---
layout: default
title: "FreeToken Just Broke The Local AI VRAM Limit Again"
permalink: /freetoken-deepseek-one-rtx-5090/
date: 2026-09-01
---

# FreeToken Just Broke The Local AI VRAM Limit Again

{% raw %}
Every figure, date and benchmark this video puts on screen, chased to a primary source.

## The paper

**FreeToken: Efficient Edge Native MoE Serving with Bandwidth Adaptive Execution.**
Shuo Yang, Xiaoze Fan, Melissa Pan, Haocheng Xi, Zhe Wang, Shanlin Sun, Kurt Keutzer,
Song Han, Matei Zaharia, Chenfeng Xu, Ion Stoica. Submitted 17 August 2026.
Source: arXiv:2608.16157.
https://arxiv.org/abs/2608.16157

The abstract states the thesis the video is built on: FreeToken "treats a personal machine
not as a small GPU, but as a unified, elastic inference platform", and co designs "model
layout and loading, expert residency, CPU GPU execution, agentic state reuse, and runtime
memory management". It claims support for "more than 20 MoE models" across hardware
"ranging from an 8GB laptop GPU to a single workstation GPU", and describes the range as
"a 35B model on a laptop to a 284B model on a gaming desktop and the 753B GLM 5.2 on a
single workstation GPU".
Source: arXiv:2608.16157, abstract.

**The implementation is open source**, at github.com/FlashML-org/FreeToken, with a CLI and
desktop client distributed through FlashML.ai.
Source: InfoQ, "FreeToken Unlocks Frontier MoE Inference on Consumer Hardware via Dynamic
Co-Execution", August 2026.
https://www.infoq.com/news/2026/08/freetoken-local-inference/

## The RTX 5090 result

**22 to 25 tokens per second, DeepSeek V4 Flash, RTX 5090 desktop.**
Source: arXiv:2608.16157.

**The desktop behind that number: 32 GB of VRAM, a Ryzen 9 9950X3D with 32 cores, and
192 GB of DDR5.** This is the point the video keeps returning to: the RAM figure is part
of the result, not background detail.
Source: arXiv:2608.16157, evaluation hardware.

**DeepSeek V4 Flash activates 6 of 256 routed experts in each of its 43 layers**, so only
13B of its 284B parameters take part in any single token, and at the deployed precision
that active footprint fits inside the 32 GB of an RTX 5090.
Source: arXiv:2608.16157.

**The RTX 5090 has 32 GB of GDDR7** on the Blackwell architecture.
Source: NVIDIA, GeForce RTX 5090 product page.
https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/

## The 753B result

**GLM 5.2 at 14.9 tokens per second on one RTX PRO 6000, against 7.3 tokens per second for
llama.cpp in the same test**, which the paper records as 2.0x.
Source: arXiv:2608.16157.

**The RTX PRO 6000 Blackwell has 96 GB of GDDR7** and is a workstation card rather than a
consumer one.
Source: NVIDIA, RTX PRO 6000 Blackwell Workstation Edition product page.
https://www.nvidia.com/en-us/products/workstations/professional-desktop-gpus/rtx-pro-6000/

**GLM 5.2 is 753B total parameters with about 40B active**, released by Z.ai on 13 June
2026 under MIT, with a one million token context window.
Source: arXiv:2608.16157 for the parameter split as tested; Z.ai / Hugging Face model card
for the release and licence.
https://huggingface.co/zai-org/GLM-5.2

## The small hardware result

**Qwen3.6 35B A3B at 77 to 83 tokens per second on an RTX 5090**, and **39.3 tokens per
second on an 8 GB RTX 4060 laptop GPU**.
Source: arXiv:2608.16157.

**Qwen3.6 35B A3B is 35B total parameters with 3B active per token**, an open weight
sparse MoE released by the Qwen team on 16 April 2026 under Apache 2.0.
Source: Qwen, Qwen3.6-35B-A3B model card.
https://huggingface.co/Qwen/Qwen3.6-35B-A3B

## The comparison against existing local engines

**The baselines are llama.cpp, Ollama, KTransformers and MoE Infinity.**
Source: arXiv:2608.16157.

**1.5 to 2.3 times higher decode throughput than the strongest baseline on RTX 5090
workloads.** The paper reports 1.8 to 2.3x on Qwen3.6 and 1.5 to 1.9x on DeepSeek V4 Flash
for that machine, so 1.5 to 2.3x is the span across both. Across all five consumer systems
tested the range is quoted as 1.3 to 2.1x.
Source: arXiv:2608.16157.

Against Ollama and llama.cpp specifically, rather than against the strongest baseline, the
reported gap is much larger: 3 to 4x faster decode and 6 to 30x faster prefill on
equivalent MoE models.
Source: InfoQ, as above.

## Time to first token

**FreeToken stays below 44 seconds across every workload in the test matrix, and each
baseline exceeds 150 seconds in at least one setting.**
Source: arXiv:2608.16157.

## How it actually works

**Prefill overlaps expert movement with computation.** FreeToken "double buffers expert
movement with computation: while the GPU evaluates the current layer, the next layer's
experts stream over PCIe".
Source: arXiv:2608.16157.

**Agentic state is reused at semantic boundaries.** Checkpoints are anchored at "thinking
segments, tool calls and outputs, and conversation turns" rather than at arbitrary token
positions, which is what lets an agent turn resume instead of recomputing.
Source: arXiv:2608.16157.

**Generation uses a shared LRU expert cache.** FreeToken "maintains a shared LRU residency
space whose contents continuously follow the experts selected by the router".
Source: arXiv:2608.16157.

**The choice between fetching an expert over PCIe and running it on the CPU is made from
the measured bandwidth of the machine it is running on**, which is what "bandwidth
adaptive execution" in the title refers to.
Source: arXiv:2608.16157, abstract and system design.

## The models named in the comparison chapter

**DeepSeek V4 Flash: 284B total, 13B active, one million token context.**
Source: DeepSeek, DeepSeek-V4-Flash model card.
https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash

**Kimi K3 is the size argument the video makes about open access.** Moonshot AI released
it on 27 July 2026 under a modified MIT licence, at 2.8 trillion total parameters with
about 104B active, and the native MXFP4 checkpoint on Hugging Face is roughly 1.56 TB.
That is the scale at which storage, memory and serving become the whole project, which is
the point the video uses it to make.
Source: Moonshot AI, Kimi K3 model card and release notes.
https://huggingface.co/moonshotai/Kimi-K3

## Not chased to a primary source

- The specific claim that FreeToken's 5090 desktop figure was measured at a particular
  quantisation is not stated as a single number in the material available; the paper says
  the active footprint fits 32 GB "at the deployed precision" without the video needing to
  name one, so no precision figure appears on screen.
- The Kimi K3 active parameter count and checkpoint size come from the model card and
  secondary coverage of the release rather than from a paper, and only the size argument,
  not a benchmark, is used on screen.
{% endraw %}

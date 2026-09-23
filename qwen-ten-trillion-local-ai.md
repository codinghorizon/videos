---
layout: default
title: "Qwen wants 10 trillion. What happens to local AI?"
permalink: /qwen-ten-trillion-local-ai/
date: 2026-09-23
---

# Qwen wants 10 trillion. What happens to local AI?

{% raw %}
Checked 23 September 2026. Every figure, date and benchmark score the picture renders is
below with the primary source it came from. The video separates four things and so does
this file: what was announced, what has been published and measured, what is arithmetic,
and what is interpretation.

Where a figure could not be chased to a primary source it is **not drawn**. Those are
listed under "Not put on screen" at the foot.

## The announcement

Primary source: [Alibaba Cloud, Apsara announcement, 22 September 2026](https://www.alibabacloud.com/en/press-room/alibaba-unveils-roadmap-on-full-stack-ai-strategy?_p_lc=1).

| On screen | Value | Where it comes from |
| --- | --- | --- |
| Qwen 4 status | In training | The announcement |
| The 5 to 10 trillion range | Qwen 4.5 and Qwen 5 | The announcement, which attaches the range to the LATER generations |
| Zhenwu V900 memory | 216 GB | The announcement |
| Zhenwu V900 availability | Planned, Q1 2027 | The announcement |
| Data centre target | Exceeds 20 GW by 2032 | The announcement |
| Self improvement experiment | 33 automated cycles, Artificial Analysis 40 to 45 | The announcement, as a company reported experiment |

**What the announcement does not contain**, which beat 011 draws as three amber rows
because the absence is itself a claim the video makes: no benchmark forecast for any
future model, no active parameter count for one, no release date, and no commitment to
downloadable ten trillion parameter weights.

Ten trillion is therefore drawn throughout as an **ambition attached to later
generations**, never as the confirmed size of Qwen 4.

## Qwen's published models

Primary sources: [Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B),
[Qwen3.8-Flash-Next model card](https://huggingface.co/Qwen/Qwen3.8-Flash-Next),
[Qwen3.8 architecture paper](https://arxiv.org/html/2608.30320v1).

Flash Next's card counts 125B main parameters, 6B active, plus 51B of n gram embeddings
and 4B of multi token prediction parameters. Those four figures are what beat 031 stacks.

| Evaluation, as Qwen's own table reports it | Flash Next | Qwen3.8-27B |
| --- | ---: | ---: |
| DeepSWE 1.1 | 58.7 | 42.2 |
| SWE-bench Pro | 62.5 | 61.7 |

| Evaluation, as the 27B card reports it | Qwen3.8-27B | Opus 4.6 Max |
| --- | ---: | ---: |
| SWE-bench Pro | 61.7 | 53.4 |
| Terminal Bench 2.1 | 73.0 | 78.2 |

**Two qualifications are drawn on screen rather than kept in this file**, because the
video states them and the picture must not contradict them:

- DeepSWE reports the better of two agent harnesses, so beat 037 says the surrounding
  tools matter. The comparison is not a single fixed setup.
- The SWE-bench Pro comparison against Opus mixes Qwen's own reevaluation, run on
  corrected tasks under the Claude Code harness, with Opus's officially published score.
  Beat 065 draws that seam. It does not establish that Qwen beats newer cloud models, and
  Terminal Bench 2.1 reverses the order, which is what beat 067 shows.

The 27B card describes a 262,144 token native context, image and video understanding,
adjustable thinking effort, Apache 2.0 weights, and quantization links for local use.
A maximum advertised context is not a promise of practical context on a 24 GB card, so
beat 091 draws a context budget rather than the headline number.

The architecture paper describes the n gram embedding tables being **held off the
accelerator**. That is evidence about a shipping architecture and is drawn as such; it is
not a confirmed design for any ten trillion model, which is what beat 034 labels amber.

## The alternatives

| Model | Figures drawn | Source |
| --- | --- | --- |
| Nemotron 3.5 Lightning 30B-A3B | 30B total, 3B active, hybrid Mamba and attention MoE, configurable reasoning, released 11 August 2026 | [NVIDIA model card](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16) |
| Mistral Small 4 | 119B total, image and text input, configurable reasoning, 256K context, Apache 2.0 | [Announcement](https://mistral.ai/news/mistral-small-4/) and [specifications](https://docs.mistral.ai/models/mistral-small-4-0-26-03) |
| DeepSeek V4.1 Flash | 552B total, 8B active for input and 16B for output, native visual understanding, MIT weights, released 10 September 2026 | [Release notes](https://api-docs.deepseek.com/news/news260910/) and [weights](https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash) |

Three points the picture is careful about:

- Nemotron's full precision recipes target data centre hardware. A small active count is an
  efficiency opportunity, not a measured speed on an RTX 3090, so beat 045 draws an amber
  "not measured" rather than a number.
- Mistral's announcement and its model documentation count active parameters differently,
  so the video uses the unambiguous total of 119B and nothing else.
- DeepSeek reports one quarter of the previous generation's HBM **for its KV cache**, not a
  fourfold reduction in total model memory. Beat 055 draws the weights untouched beside the
  cache for exactly this reason.

## The arithmetic

Ideal four bit weight storage is `N x 4 / 8` bytes. These are calculations drawn as
calculations, with the caveat on screen: they are not download sizes, not full running
memory, and not a guarantee of quantization quality.

| Parameters | Ideal four bit weights |
| --- | ---: |
| 10 trillion | 5 TB |
| 119 billion | 59.5 GB |
| 27 billion | 13.5 GB |

Real quantized files add overhead and the conversation needs its own memory, per
[llama.cpp's quantization documentation](https://github.com/ggml-org/llama.cpp/blob/master/tools/quantize/README.md)
and its [cache implementation](https://github.com/ggml-org/llama.cpp/blob/master/src/llama-kv-cache.cpp).
Offloading changes where weights sit and how fast they are reached; it does not make them
stop existing, which is what beats 024 and 025 draw.

## The hardware on the desk

[RTX 3090 specifications](https://www.nvidia.com/en-eu/geforce/graphics-cards/30-series/rtx-3090/)
confirm 24 GB of graphics memory. The 64 GB of system memory is an assumed desktop
configuration and is drawn as the assumption it is.

## Distillation

[DeepSeek R1's model card](https://huggingface.co/deepseek-ai/DeepSeek-R1) documents
distilled Qwen and Llama based models. That is the concrete precedent beat 077 shows, and
it is a precedent only: it is not a commitment that Alibaba will distribute distilled
versions of any future flagship. Beat 081 labels that amber.

## Not put on screen

These are asserted by the narration and could not be chased to a primary source, so no
shot renders them as a figure:

- **Any benchmark score for Qwen 4, 4.5 or 5.** None is published. The picture draws an
  empty, outlined forecast slot instead of a number.
- **A release date for any of those generations.** Not announced.
- **Whether ten trillion parameter weights will ever be downloadable.** Not stated.
- **Any tokens per second figure on an RTX 3090** for Nemotron, Mistral, DeepSeek or Qwen.
  No source measures these models on that card, so no speed is drawn anywhere.
- **The teacher and student checkout example**, which is explicitly hypothetical and is
  drawn as an illustration rather than as a reported result.
{% endraw %}

---
layout: default
title: "Someone Ran Kimi K3 On 8 GB RAM And It Hurts Badly"
permalink: /kimi-k3-8gb-ram-reddit/
date: 2026-08-20
---

# Someone Ran Kimi K3 On 8 GB RAM And It Hurts Badly

{% raw %}
Every figure, name and requirement the video puts on screen, chased to a primary source.

## Primary sources

- **P1** Moonshot AI, Kimi K3 model card — https://huggingface.co/moonshotai/Kimi-K3
- **P2** Moonshot AI, Kimi K3 repository — https://github.com/MoonshotAI/Kimi-K3
- **P3** Fareed Khan, `kimi-k3-in-c` repository and README — https://github.com/FareedKhan-dev/kimi-k3-in-c
- **P4** Kimi API platform documentation — https://platform.kimi.ai/docs/guide/kimi-k3-quickstart

## The model

| Figure on screen | Value | Source |
| --- | --- | --- |
| Total parameters | 2.8T (2.78 trillion as `kimi-k3-in-c` counts the shipped checkpoint) | P1, P3 |
| Activated parameters per token | 104B, about 3.7% of the total | P1, P3 |
| Number of layers | 93 | P1, P3 |
| Number of experts | 896 | P1 |
| Selected experts per token | 16 | P1, P3 |
| Context length | 1,048,576 tokens | P1 |
| Attention | Kimi Delta Attention and Gated MLA | P1 |
| Released | API 16 July 2026, weights 27 July 2026 | P2 |

Moonshot describes K3 as "an open-weight, native multimodal agentic model" and positions it
for "long-horizon coding, knowledge work, and reasoning", stating that it "sustains long
engineering sessions, navigates massive repositories, and orchestrates terminal tools" (P1,
P2). That is the basis for the video's line about long horizon coding and terminal tool
orchestration.

**Nuance the shots must respect:** 896 is the routed expert count **per layer**. P3 counts
82,432 routed experts in total across the 92 MoE layers. The 896 and 16 figures are drawn as
one layer's selection, which is what the model card figure describes, and no shot claims 896
is the whole model.

## The engine and the run

| Figure on screen | Value | Source |
| --- | --- | --- |
| Project | `kimi-k3-in-c`, portable C99, no BLAS, no framework, no GPU | P3 |
| Engine size | 176 KB of C | P3 |
| Naive bfloat16 requirement | 5,560 GB, stated in the video as 5.56 TB | P3 |
| Shipped checkpoint | 1.56 TB, exactly 1,560,936,091,448 bytes | P3 |
| Checkpoint shards | 96 | P3 |
| Routed experts as share of checkpoint | 1.447 TB, 93% | P3 |
| Routed expert quantization | 0.53125 bytes per weight, a half byte plus an E8M0 scale | P3 |
| Always active trunk at bfloat16 | 113.49 GB, stated in the video as around 113 GB | P3 |
| Packed trunk file | 109 GB | P3 |
| Peak RAM, laptop preset | 8.24 GB | P3 |
| Free storage required | about 1.7 TB | P3 |
| Output across memory budgets | byte identical | P3 |

The video's "compact 4 bit form" describes the 0.53125 bytes per weight figure above: four
bits of weight plus a shared E8M0 exponent scale.

## Speed

| Preset | Seconds per token | Source |
| --- | --- | --- |
| Laptop, 8 GB | 26.5 | P3 |
| Desktop, 32 GB | 24.2 | P3 |
| Workstation, 64 GB | 19.8 | P3 |
| Server, 128 GB and above | 5.6 | P3 |
| Captured demo run | 8 tokens in 261.5 s, 32.69 s/token average | P3 |

The presets are named for the memory budget they emulate. P3 reports them as measured on the
author's own machine rather than on four different computers, which is why the video says "on
its measured machine".

## Requirements

Linux and x86-64, with AVX2 and FMA required on the CPU and AVX-512 explicitly unnecessary.
GCC 9 or later, or Clang 10 or later. Python 3.9+ for the packing tools only. P3 states the
engine targets Linux; macOS, Apple Silicon and Windows are not supported paths in the current
version. (P3)

## The captured demo

The README's first runnable example uses the prompt `The capital of France is` and generates
` Paris.` followed by continuation text beginning `The Eiffel`. P3 states directly: "This is a
base model, so what follows ' Paris.' is a continuation rather than a reply; there is no chat
template." A second example continues `def fibonacci(n):` into a recursive implementation. (P3)

## The post

Fareed Khan published `kimi-k3-in-c` on 1 August 2026 and posted it to r/LocalLLaMA under the
title "I pushed Kimi K3 onto one CPU with 8 GB of RAM". The repository reached GitHub's
trending page within days. (P3)

## The other runtimes named

- **Unsloth** — compression and quantization work that makes large open weight models runnable
  on local hardware.
- **llama.cpp** — the C/C++ inference runtime whose support for a new architecture is what
  usually decides whether a released model can be run locally at all.
- **Ollama** and **LM Studio** — local runtimes that present a model as a product surface and
  do not expose the byte movement underneath, which is the contrast the video draws.

## Not verified to a primary source

- The comparison figure for a hosted Kimi endpoint's latency. The video's claim that the
  hosted API is faster than 26 s per token is true by a very large margin and is not in
  dispute, but no single published latency number is cited for it, so no hosted figure is
  rendered on screen. The reference bar in the speed comparison is drawn as "hosted" without
  a number.
- The "4B vision model in 3 GB" and "30B coding model on a gaming GPU" examples are the
  script's illustrations of the local AI category rather than references to named releases,
  and the shots draw them as classes of machine rather than as identified products.
{% endraw %}

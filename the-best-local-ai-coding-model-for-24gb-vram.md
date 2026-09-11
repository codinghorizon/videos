---
layout: default
title: "A 24GB Local Model Beat Claude Where It Should Not"
permalink: /the-best-local-ai-coding-model-for-24gb-vram/
date: 2026-09-11
---

# A 24GB Local Model Beat Claude Where It Should Not

{% raw %}
Every figure the finished picture puts on screen, chased to a primary source.

## The headline claim

**Qwen3.8-27B scores 61.7 on SWE-bench Pro, 73.0 on Terminal-Bench 2.1 (Terminus) and 90.3
on LiveCodeBench v6.** The model card reports all three. It is a dense 27B model with a
native context of 262,144 tokens, extensible to roughly 1,000,000 with scaling, and it is a
native vision language model that understands images and video.
Source: [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B)

**Claude Opus 4.6 Max is listed at 53.4 on SWE-bench Pro** in the same comparison row.
The two numbers are not produced under identical conditions: the 61.7 was measured on a
refined set in which Qwen corrected problematic tasks and re-ran the baselines, while the
53.4 is the officially reported Opus figure on the original benchmark, and the harnesses
differ. Qwen3.8-27B leads Opus 4.6 Max on 16 of the 24 benchmarks in the model card and
still loses on knowledge reasoning, including Humanity's Last Exam at 30.8 against 40.0.
Sources:
[Qwen3.8-27B benchmarks, official and independent](https://www.qubrid.com/blog/qwen38-27b-benchmarks-official-and-independent-results),
[every test where the 27B beats Opus 4.6 Max](https://regolo.ai/qwen3-8-27b-benchmarks-every-test-where-alibabas-27b-model-beats-claude-opus-4-6-max/)

## Generation over generation

| Benchmark | Qwen3.8-27B | Qwen3.6-27B |
| --- | --- | --- |
| SWE-bench Pro | 61.7 | 53.5 |
| Terminal-Bench 2.1 | 73.0 | 63.4 |
| LiveCodeBench v6 | 90.3 | 83.9 |

Source: [Qwen3.8-27B benchmarks](https://www.qubrid.com/blog/qwen38-27b-benchmarks-official-and-independent-results),
[Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B)

## Dense against sparse, same generation

**Qwen3.6-27B** is a dense 27B model: 77.2 on SWE-bench Verified, 53.5 on SWE-bench Pro,
59.3 on Terminal-Bench 2.0 and 83.9 on LiveCodeBench v6. It is Apache 2.0 licensed and
beats the far larger Qwen3.5-397B-A17B on those coding benchmarks.
Sources: [Qwen/Qwen3.6-27B](https://huggingface.co/Qwen/Qwen3.6-27B),
[the-decoder on Qwen3.6-27B](https://the-decoder.com/qwen3-6-27b-beats-much-larger-predecessor-on-most-coding-benchmarks/)

**Qwen3.6-35B-A3B** is the sparse model of the same generation, 35B total with about 3B
active: 73.4 on SWE-bench Verified, 49.5 on SWE-bench Pro and 80.4 on LiveCodeBench v6,
measured with an internal agent scaffold of bash and file edit tools.
Source: [Qwen/Qwen3.6-35B-A3B](https://huggingface.co/Qwen/Qwen3.6-35B-A3B)

## What the files actually weigh

GGUF sizes, taken from the published repositories rather than from a rule of thumb.

| Build | Size |
| --- | --- |
| Qwen3.8-27B Q4_K_M | 17.1 GB |
| Qwen3.8-27B Q4_K_M (lmstudio-community) | 16.8 GB |
| Qwen3.8-27B UD-Q4_K_XL | 17.9 GB |
| Qwen3.8-27B Q5_K_M | 19.8 GB |
| Qwen3.6-27B Q4_K_M | 16.8 GB |
| Qwen3.6-27B UD-Q4_K_XL | 17.6 GB |
| Qwen3.6-27B Q5_K_M | 19.5 GB |
| Qwen3.6-27B Q6_K | 22.5 GB |
| Qwen3.6-35B-A3B UD-Q4_K_M | 22.1 GB |
| Qwen3.6-35B-A3B UD-Q3_K_M | 16.6 GB |
| GLM-4.7-Flash Q4_K_M | 18.3 GB |
| Qwen3-Coder-30B-A3B-Instruct Q4_K_M | 18.6 GB |

Sources: [unsloth/Qwen3.6-27B-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-GGUF/tree/main),
[unsloth/Qwen3.6-35B-A3B-GGUF](https://huggingface.co/unsloth/Qwen3.6-35B-A3B-GGUF/tree/main),
[unsloth/GLM-4.7-Flash-GGUF](https://huggingface.co/unsloth/GLM-4.7-Flash-GGUF/tree/main),
[unsloth/Qwen3-Coder-30B-A3B-Instruct-GGUF](https://huggingface.co/unsloth/Qwen3-Coder-30B-A3B-Instruct-GGUF/tree/main),
[Qwen3.8-27B GGUF sizes](https://www.orcarouter.ai/blog/qwen-3-8-27b-gguf),
[Unsloth: run Qwen3.8 locally](https://unsloth.ai/docs/models/qwen3.8)

The reason the sparse model of that generation is squeezed is visible in the table: the
35B-A3B's 4-bit build is 22.1 GB, and the 3-bit build that does fit is 16.6 GB.

## Context and the KV cache

Qwen3.8-27B uses a hybrid stack: sixteen repeats of three Gated DeltaNet layers followed by
one Gated Attention layer, so only 16 of its 64 layers hold a growing KV cache. The full
262,144 token context costs roughly 17 GB of cache even with that design, which puts 32k at
roughly 2 GB and 64k at roughly twice that. At Q4_K_M with 64k context the model plus cache
measures 17.11 GB, or 18.04 GB with the vision tower loaded.
Sources: [Qwen3.8 27B VRAM and KV cache math](https://umesh-malik.com/blog/qwen3-8-27b-vram-kv-cache-math),
[Qwen3.8-27B VRAM requirements](https://www.orcarouter.ai/blog/qwen-3-8-27b-vram-requirements)

## The fast models

**gpt-oss-20b** has 20.9B total parameters and 3.61B active per token across 24 layers, 32
experts with the top 4 selected. The released checkpoint is 12.8 GiB, and MXFP4
quantization of the MoE weights lets it run within 16 GB of memory.
Sources: [gpt-oss model card, arXiv 2508.10925](https://arxiv.org/html/2508.10925v1),
[openai/gpt-oss-20b](https://huggingface.co/openai/gpt-oss-20b),
[deployment centric analysis, arXiv 2508.16700](https://arxiv.org/html/2508.16700)

**Qwen3-Coder-30B-A3B-Instruct** has 30.5B total parameters with 3.3B active per forward
pass, 128 experts with 8 active, and a native 262,144 token context extensible to about 1M.
It was trained for agentic coding and tool use.
Sources: [Qwen/Qwen3-Coder-30B-A3B-Instruct](https://huggingface.co/Qwen/Qwen3-Coder-30B-A3B-Instruct),
[Bedrock model card](https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-qwen-qwen3-coder-30b-a3b-instruct.html)

**GLM-4.7-Flash** is a 30B total, roughly 3B active mixture of experts model from Z.ai. It
reports 59.2 on SWE-bench Verified and 64.0 on LiveCodeBench v6. In the same comparison,
gpt-oss-20b scores 34 and Qwen3-30B-A3B-Thinking scores 22 on SWE-bench Verified. It also
reports 79.5 on tau-squared-Bench for interactive tool invocation.
Sources: [GLM-4.7 overview, Z.AI developer documentation](https://docs.z.ai/guides/llm/glm-4.7),
[Unsloth GLM-4.7-Flash](https://unsloth.ai/docs/models/glm-4.7-flash),
[GLM-4.7-Flash benchmarks and setup](https://binaryverseai.com/glm-4-7-flash-benchmarks-setup-pricing-vs-qwen3/)

## The three 24GB cards

| Card | Memory | Bandwidth |
| --- | --- | --- |
| GeForce RTX 3090 | 24 GB GDDR6X, 384 bit at 19.5 Gbps | 936 GB/s |
| GeForce RTX 4090 | 24 GB GDDR6X | 1008 GB/s |
| Radeon RX 7900 XTX | 24 GB GDDR6 | 960 GB/s |
| GeForce RTX 5090 | 32 GB GDDR7, 512 bit at 28 Gbps | 1792 GB/s |

Sources: [NVIDIA RTX 3090 and 3090 Ti](https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090-3090ti/),
[RTX 4090 against RX 7900 XTX, TechSpot](https://www.techspot.com/review/2786-geforce-rtx-4090-vs-radeon-7900-xtx/),
[NVIDIA RTX 5090](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/),
[RTX 5090 Founders Edition review, TechPowerUp](https://www.techpowerup.com/review/nvidia-geforce-rtx-5090-founders-edition/46.html)

Local token generation is dominated by moving weights through memory, which is why the
three 24GB cards sit within about 8 per cent of each other on bandwidth despite two
generations between the oldest and the newest.

## What SWE-bench measures

SWE-bench takes real issues from real repositories and checks whether the model's final
patch makes the repository's own tests pass, rather than asking for a single function.
The score therefore depends on the whole agent around the model as well as the model: the
tool set, the prompt, the context length and the number of attempts. Vendor tables are
usually run at full precision with a large context and a tuned agent loop, which is a
different test from a 4-bit quant at 32k tokens inside a different application.

## Not chased to a primary source

- The description of Qwen3-Coder-30B-A3B's 4-bit build as landing "in the mid teens in
  gigabytes". The published Q4_K_M for that model is 18.6 GB; smaller 4-bit conversions
  exist but no mid teens figure could be confirmed at a primary source, so no figure is
  drawn for it.
- The claim that a 22 GB model file does not comfortably fit a 24 GB card is a practical
  observation about runtime, cache and display overhead rather than a published figure.
- Relative pricing, availability and second hand cost of the RTX 3090 are not sourced and
  no figure for them appears on screen.
{% endraw %}

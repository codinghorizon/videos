---
layout: default
title: "The Qwen Speed Run That Changes Local AI Forever"
permalink: /qwen-3-8-27b-91-tokens-local-ai/
date: 2026-09-06
---

# The Qwen Speed Run That Changes Local AI Forever

{% raw %}
Every figure, name and benchmark the video puts on screen, chased to a primary source.

---

## The model

**Qwen3.8-27B**, Alibaba's Qwen family. Open weights on Hugging Face.

| Claim | Value | Source |
| --- | --- | --- |
| Parameters | 27B, dense | [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Layers | 64 | [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Native context | 262,144 tokens | [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Extended context | 1,000,000 with YaRN, supported by vLLM and SGLang | [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Vision | Image and video input, native vision language model | [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Thinking mode | On by default, with `reasoning_effort` at xhigh, medium, low | [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Multi token prediction | Trained with MTP, usable by compatible inference engines | [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Attention | 3:1 hybrid of Gated DeltaNet linear attention and gated full attention, 24 query / 4 KV heads, head dim 256 | [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Vocabulary | 248,320 | [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Predecessor | Qwen3.6-27B | [Qwen/Qwen3.6-27B](https://huggingface.co/Qwen/Qwen3.6-27B) |
| Official FP8 checkpoint | Published separately | [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) |

## Benchmarks

Vendor reported on the official model card, comparing Qwen3.8-27B against Qwen3.6-27B.
Independent replication is not yet available for these, so they are a ceiling rather than
a measurement.

| Benchmark | Qwen3.8-27B | Qwen3.6-27B |
| --- | --- | --- |
| SWE-bench Pro | 61.7 | 53.5 |
| QwenSWEBench | 79.0 | 49.3 |
| OSWorld-Verified | 84.3 | 63.9 |
| Terminal Bench 2.1 | 73.0 | 63.4 |
| LiveCodeBench v6 | 90.3 | 83.9 |
| GPQA Diamond | 89.2 | 87.8 |
| IFBench | 79.5 | 69.1 |

Source: [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B)

The video states SWE-bench Pro, QwenSWEBench and OSWorld-Verified. The other four rows
are recorded here for context and are not put on screen.

## The 91 tokens per second run

A published deployment and tuning writeup for Qwen3.8-27B-Uncensored-FP8 on two RTX 5090
cards. Every figure below is from that writeup.

**Hardware and configuration**

| Setting | Value |
| --- | --- |
| GPUs | 2 x RTX 5090, 32 GB each |
| Engine | vLLM |
| Tensor parallel size | 2 |
| Model | FP8 quantized checkpoint |
| Served context | 131,072 tokens, of 262,144 native |
| GPU memory utilization | 0.96 |
| Max batched tokens | 8,192 |
| Prefix caching | Enabled, xxhash |
| Speculative method | `qwen3_5_mtp`, one speculative token |

**Measured decode throughput**, single request, temperature 0, 220 completion tokens

| Configuration | Tokens per second |
| --- | --- |
| Baseline, bf16 KV cache, no prefix caching, no MTP | 56.7 |
| Prefix caching only, bf16 KV cache | ~56.7 |
| FP8 KV cache | 76.3 |
| MTP speculative decoding | 88 to 91 |
| MTP and FP8 KV cache together | 49.3 |

**Multi token prediction detail**

| Metric | Value |
| --- | --- |
| Draft token acceptance rate | 73.8% |
| Mean acceptance length | 1.74 tokens |

**KV cache budget**

| KV cache dtype | Budget |
| --- | --- |
| bf16 | 336,719 tokens |
| FP8 | 634,971 tokens |

Source: [fentz26/Qwen3.8-27B-5090](https://github.com/fentz26/Qwen3.8-27B-5090)

This is the source of the video's four load bearing speed figures: 56.7 baseline, 76.3
with FP8 KV cache, 88 to 91 with MTP, and 49 when the two are combined. The regression
when both are enabled is stated explicitly in the writeup, not inferred.

Prefix caching not moving raw decode is also from that writeup: it changes the cost of
repeated prefill, not the speed of generation.

## What the weights actually weigh

| Build | Size | Source |
| --- | --- | --- |
| BF16, 18 safetensor shards | 55.56 GB decimal | [Qwen3.8-27B quantization comparison](https://kingy.ai/blog/qwen3-8-27b-best-quantization-gguf/) |
| Official FP8 repository | ~30.88 GB | [Qwen3.8-27B quantization comparison](https://kingy.ai/blog/qwen3-8-27b-best-quantization-gguf/) |
| Q8 GGUF | 26.90 to 29.30 GiB | as above |
| Q6_K GGUF | 20.89 to 23.29 GiB | as above |
| Q5_K GGUF | 17.27 to 18.83 GiB | as above |
| Q4_K_M GGUF | 15.66 to 17.67 GiB | as above |
| IQ3_S GGUF | 12.89 GiB | as above |
| IQ2_S GGUF | 10.38 GiB | as above |

Two notes on how these line up with the video.

The narration says BF16 is "roughly fifty four gigabytes just for the weights". The
official shards total 55.56 GB decimal, which is 51.7 GiB. A 27B model at two bytes per
parameter is 54 GB by arithmetic. The narration's figure sits inside that band and is
stated as an approximation, so it is treated as sound.

The narration says Q6 GGUF "lands around the twenty one gigabyte class". Q6_K is 20.89 to
23.29 GiB, and GiB is the unit a GPU reports free memory in, so the bottom of that range
is the twenty one gigabyte class exactly. Confirmed.

The narration says four bit builds reach "the mid teens". Q4_K_M is 15.66 to 17.67 GiB.
Confirmed.

The narration says FP8 pushes the weights "into the high twenties". A 27B model at one
byte per parameter is 27 GB of weights. The published FP8 repository is 30.88 GB, which
includes more than the weight tensors. The narration is describing the weights, so it is
treated as sound, and no FP8 file size figure is put on screen.

## Hardware guidance

| Tier | What is reported | Source |
| --- | --- | --- |
| 16 GB GPU | Possible with a ~10.7 GB two bit or ~13.4 GB three bit build, or by offloading part of a Q4 build to system RAM. Not a recommended configuration for this model. | [Qwen3.8-27B local hardware guide](https://kingy.ai/blog/qwen3-8-27b-local-hardware-requirements/) |
| 12 GB laptop GPU with 32 GB system RAM, dynamic Q4 with CPU offload | 3.26 tok/s on a long answer, 4.42 to 4.53 tok/s on short factual and coding answers | as above |
| 24 GB GPU | Runs a good four bit build. Positioned as the practical everyday starting point. | as above |
| 32 GB GPU | Breathing room. Q4 or Q5 with practical context. | as above |

RTX 3090, RTX 3090 Ti and RTX 4090 are all 24 GB cards, which is the class the video
names at that tier.

## Apple silicon

| Machine | Measured | Source |
| --- | --- | --- |
| M4 Mac Mini, 32 GB unified memory, MLX 4 bit | 5 to 6 tokens per second, described as the only measured figure published for base M4 silicon | [Qwen3.8-27B on Apple silicon](https://thomas-wiegold.com/blog/qwen-3-8-27b-best-local-llm/) |
| M4 MacBook Air, 24 GB | Fewer than ten tokens per second once a few thousand tokens in, memory bandwidth bound | as above |

The MLX four bit build is about 18 GB and needs roughly 16 to 19 GB of unified memory,
which makes 24 GB the realistic floor on a Mac.

Generation speed on Apple silicon tracks memory bandwidth rather than capacity. Published
bandwidth figures for the current line put M5 Ultra at 1.2 TB/s, M3 Ultra at 819 GB/s and
M5 Max at 614 GB/s, all far above a base M4. This is the mechanism behind the video's
point that capacity lets a model load and bandwidth is what makes it feel alive.

### Not found

**No published measurement puts a 32 GB Mac at three to four tokens per second.** The
nearest measured figure for that machine is 5 to 6 tok/s on an M4 Mac Mini. The 3.26 to
4.53 tok/s range that does exist in the sources was measured on a 12 GB RTX 5070 Ti laptop
using CPU offload, which is a different machine and a different failure mode. No token per
second figure is put on screen anywhere in that chapter as a result.

## Software named in the video

| Name | What it is |
| --- | --- |
| vLLM | Open source inference and serving engine, OpenAI compatible endpoint, tensor parallelism, prefix caching, speculative decoding |
| SGLang | Open source serving engine, listed by Qwen as supporting the YaRN extension to 1M context |
| GGUF | The file format used by llama.cpp and the applications built on it |
| AWQ | Activation aware weight quantization |
| YaRN | Context window extension method |
| CUDA graphs | NVIDIA mechanism for replaying a captured sequence of GPU work with less per launch overhead |

## Caveats

- Every benchmark score in this file is vendor reported on the model card. No independent
  replication of SWE-bench Pro 61.7, QwenSWEBench 79.0 or OSWorld-Verified 84.3 was
  available.
- The 91 tokens per second figure comes from one published deployment on one pair of
  cards, with a specific quantized checkpoint, a 131,072 token served context and one
  speculative token. It is a single documented run, not a general expectation.
- The Qwen3.8-27B-Uncensored-FP8 checkpoint used in that run is a community build, not the
  official Qwen FP8 release.
- GGUF file sizes vary between the people who publish them, which is why several rows above
  are ranges rather than single numbers.
- No 32 GB Mac has been measured at three to four tokens per second, as recorded above.
{% endraw %}

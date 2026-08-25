---
layout: default
title: "Your Laptop Is Secretly Wasting Local AI Power"
permalink: /make-your-machine-actually-good-at-local-ai/
date: 2026-08-25
---

# Your Laptop Is Secretly Wasting Local AI Power

{% raw %}
Sources for every figure, name and capability this video states or puts on screen.

## Gemma 3

Google publishes Gemma 3 in five sizes: 270M, 1B, 4B, 12B and 27B.

Context windows differ by size. The model card states: "Total input context of 128K tokens
for the 4B, 12B, and 27B sizes, and 32K tokens for the 1B and 270M sizes."

So the video's "Gemma 3 has versions listed with a 128 thousand token context window" is
correct as stated: it is the three larger sizes that carry 128K, not the whole family. The
shot showing the context bar is labelled to that effect.

- https://ai.google.dev/gemma/docs/core/model_card_3

## Qwen3 Coder

Qwen3-Coder-30B-A3B-Instruct is a mixture of experts model. The model card states "Number
of Parameters: 30.5B in total and 3.3B activated", which is the "thirty billion parameter
version with only a fraction of the parameters active at once" the video describes.

Its context length is "262,144 natively", extendable "up to 1M tokens using Yarn", and the
card describes it as "optimized for repository-scale understanding". That supports both
"advertises long context for repository scale work" and "some models talk about 256
thousand tokens or even more": 262,144 is 256K.

The largest variant, Qwen3-Coder-480B-A35B-Instruct, is "480B in total and 35B activated",
which is the 480 billion parameter model named in the parameter ladder.

- https://huggingface.co/Qwen/Qwen3-Coder-30B-A3B-Instruct
- https://huggingface.co/Qwen/Qwen3-Coder-480B-A35B-Instruct

## gpt oss

OpenAI released gpt-oss-120b and gpt-oss-20b as open weight models under Apache 2.0,
described as "designed for powerful reasoning, agentic tasks, and versatile developer use
cases", with full chain of thought and configurable reasoning effort.

On the memory figure, the model card states the aim is to have "the `gpt-oss-20b` model run
within 16GB of memory". That is the source for "designed to run on consumer style hardware
with around sixteen gigabytes of memory".

gpt-oss-20b is 21B total parameters with 3.6B active, natively quantized to MXFP4.
gpt-oss-120b is the larger of the pair and is the 120 billion parameter model named in the
parameter ladder.

- https://huggingface.co/openai/gpt-oss-20b
- https://github.com/openai/gpt-oss

## llama.cpp

The project README supports every capability the video attributes to it: a "Plain C/C++
implementation without any dependencies" for CPU builds, "Custom CUDA kernels for running
LLMs on NVIDIA GPUs (support for AMD GPUs via HIP and Moore Threads GPUs via MUSA)" for GPU
backends, and "CPU+GPU hybrid inference to partially accelerate models larger than the total
VRAM capacity" for the hybrid case.

GGUF is llama.cpp's model file format, and the repository carries the conversion tooling
(`convert_hf_to_gguf.py`) and the `gguf-py` package for it.

The CUDA line is also the basis for the video's point about software support: the strength
of the tooling around NVIDIA is a property of the tools, not of the silicon.

- https://github.com/ggml-org/llama.cpp

## LM Studio

**Idle TTL.** LM Studio documents exactly the setting the video describes: "Idle TTL
(technically: Time-To-Live) defines how long a model can stay loaded in memory without
receiving any requests. When the TTL expires, the model is automatically unloaded from
memory." The default for JIT loaded models is 60 minutes, and the idle timer resets on each
request. Auto Evict, alongside it, unloads a previously loaded model before loading a new
one.

**The estimator.** `lms load --estimate-only` previews memory requirements before a model is
loaded. The estimate "accounts for factors like context length, flash attention, and whether
the model is vision-enabled", and reports whether the model may be loaded given the
configured resource guardrails. That is the estimator the video recommends using instead of
assuming maximum GPU offload is best.

- https://lmstudio.ai/docs/app/api/ttl-and-auto-evict
- https://lmstudio.ai/docs/cli/local-models/load

## Unified memory on Apple silicon

Apple silicon puts the CPU and GPU on one package over a single memory pool. Apple's own
developer material describes the consequence directly: with a unified memory architecture
"the traditional management of copies between system RAM and video RAM goes away", and Metal
"exposes the UMA through shared resources that allow the GPU and CPU to read and write the
same memory", so resource management becomes synchronising access "rather than duplicating
or shadowing data between system memory and video memory".

Apple also states the practical consequence for this subject: the unified memory
architecture "enables the entire chip to access a large single pool of memory", which allows
its machines "to run larger AI models completely on device".

This is the whole basis for the video's Apple Silicon chapter, and specifically for the claim
that the difference is about avoiding a hard VRAM wall rather than about being faster.

- https://developer.apple.com/videos/play/tech-talks/10580/
- https://developer.apple.com/documentation/metal/choosing-a-resource-storage-mode-for-apple-gpus
- https://www.apple.com/newsroom/2025/10/apple-unleashes-m5-the-next-big-leap-in-ai-performance-for-apple-silicon/

## Model sizes named in passing

The 70 billion parameter tier the video opens its parameter ladder with is a real and common
open weight size; the 120 billion and 480 billion tiers are gpt-oss-120b and
Qwen3-Coder-480B-A35B, both cited above. The 7 billion, 12 billion and 30 billion figures
used in the quantization comparison are size classes rather than specific models, and the
video treats them that way.

## Not checked

These are the video's own judgements rather than sourceable facts, and the picture states
them as opinion or does not put a number on screen for them at all.

- That four bit and five bit quantizations are "the practical middle ground" for most local
  use. Widely held, and a preference rather than a measured threshold. Quality loss from
  quantization is real and model dependent, and no single primary source establishes a
  universal cutoff.
- That two bit quantization is "survival mode" and a poor starting point for a daily
  assistant. Same category: a judgement about usable quality.
- That NVIDIA is "the easiest recommendation" for Windows and Linux users. The underlying
  fact that CUDA is broadly supported is sourced above; whether that makes it the easiest
  recommendation is an opinion.
- Every VRAM comfort tier: 8 GB entry level, 12 GB workable, 16 GB better, 24 GB comfortable,
  32 GB and above roomier. These are the author's buying advice, not published thresholds.
- Every laptop memory tier: 16 GB as a floor, 32 GB as the sensible target, 64 GB as where it
  stops feeling cramped. Same.
- That a clean 12 billion model can feel better than a wounded 30 billion one, and that a
  fast 7 billion coder can beat a slower larger model in practice. Both are claims about
  felt experience across an unspecified set of tasks, and the shots draw them as a
  demonstration rather than as a benchmark result.
- Every rate, latency and frame counter drawn on an instrument in this video is a depicted
  machine state used to show a mechanism working. None of them is a measurement of a named
  model on named hardware, and no shot puts a tokens per second or latency figure on screen
  as a result.
{% endraw %}

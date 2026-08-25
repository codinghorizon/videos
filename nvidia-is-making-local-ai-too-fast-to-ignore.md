---
layout: default
title: "NVIDIA Just Made Local AI Too Fast To Ignore Now"
permalink: /nvidia-is-making-local-ai-too-fast-to-ignore/
date: 2026-08-25
---

# NVIDIA Just Made Local AI Too Fast To Ignore Now

{% raw %}
Every figure, product name and mechanism the finished picture puts on screen, chased to
a primary source. Where a claim is illustrative rather than measured, it is listed under
**Not checked** at the end and is not printed as a number on screen.

## Two hundred tokens per second

NVIDIA's own local AI post reports **over 200 tokens per second** for Muse Glimmer, a 30
billion parameter model aimed at always on local agent work, running on a GeForce RTX
5090. The same post reports **131 tokens per second** for Qwen3.8-27B on a single GeForce
RTX 5090 using multi token prediction.

- NVIDIA, *NVIDIA and Local AI Community Fuel Open Source Models and Intelligent Agents*,
  11 August 2026. https://blogs.nvidia.com/blog/local-ai-open-source-models-agents-nemotron/

This is the figure the video is built around. It is a vendor published number for a named
model on a named GPU, not a general claim about all local inference.

## What NVIDIA actually names

NVIDIA's local AI landing page for developers names the hardware as **GeForce RTX**,
**RTX PRO**, **RTX Spark**, **DGX Spark** and **DGX Station**, and the software as
**Ollama**, **llama.cpp**, **vLLM**, **SGLang**, **TensorRT**, **PyTorch**, **ONNX**,
**Windows ML** and **ComfyUI**. It also covers building agents with agentic harnesses and
MCP tool connections against a local backend.

- NVIDIA, *Run AI Locally*. https://developer.nvidia.com/local-ai

NVIDIA states that it worked with vLLM, Ollama, llama.cpp and LM Studio on local
deployment of its Nemotron 3.5 Lightning models, in both NVFP4 and GGUF formats.

- NVIDIA, *NVIDIA and Local AI Community Fuel Open Source Models and Intelligent Agents*,
  11 August 2026. https://blogs.nvidia.com/blog/local-ai-open-source-models-agents-nemotron/

## RTX Spark

RTX Spark is a real, announced product: a class of Windows PC built on the GB10 Grace
Blackwell superchip, announced at COMPUTEX and covered by NVIDIA on 31 May 2026, with
**1 petaflop of AI compute and 128 GB of unified memory**.

- NVIDIA, *NVIDIA Levels Up Local AI Agents Across RTX PCs and DGX Spark*, 31 May 2026.
  https://blogs.nvidia.com/blog/rtx-ai-garage-computex-spark-local-agents/

## DGX Spark, the published numbers

NVIDIA's DGX Spark product page states:

- **128 GB LPDDR5x, coherent unified system memory**
- **Test, validate, and inference with AI models up to 200 billion parameters**
- **Fine-tune models up to 70 billion parameters**
- **Memory bandwidth 273 GB/s**
- **Up to 1 PFLOP FP4** (NVIDIA notes this is theoretical FP4 TOPS using sparsity)

- NVIDIA, *NVIDIA DGX Spark*.
  https://www.nvidia.com/en-us/products/workstations/dgx-spark/

The video uses the 128 GB and 200 billion parameter figures together, exactly as NVIDIA
pairs them, and immediately separates capacity from speed using the bandwidth figure from
the same page.

## GeForce RTX 5090, the card the 200 figure was measured on

NVIDIA's product page states **32 GB GDDR7** on a **512 bit** memory interface.

- NVIDIA, *GeForce RTX 5090*.
  https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/

The bandwidth figure of about **1,792 GB/s** is the arithmetic of that 512 bit bus with
28 Gbps GDDR7, and is the figure carried consistently across independent coverage of the
card. It is listed under Not checked below because NVIDIA's own page states the bus width
and memory type rather than a single bandwidth number.

The contrast the video draws is between two published numbers: about four times the
memory on the deskside machine, and roughly a sixth of the bandwidth.

## Why decoding is sequential, and the three tricks

**Continuous batching** replaces a finished request in a batch with a new one immediately
and schedules per iteration rather than waiting for a whole batch to drain, which is what
keeps the GPU busy.

- vLLM, *Inside vLLM: Anatomy of a High-Throughput LLM Inference System*.
  https://vllm.ai/blog/2025-09-05-anatomy-of-vllm

**Automatic prefix caching** reuses the KV cache blocks of a shared prefix across
requests. vLLM's design notes give the motivating case directly: a system prompt that is
constant across requests, and multi turn dialogue where each new message builds on all
the preceding context.

- vLLM, *Automatic Prefix Caching*.
  https://docs.vllm.ai/en/stable/design/prefix_caching/

**Speculative decoding** has a small draft model propose several tokens which the larger
target model then verifies, and vLLM describes it as a way to reduce inter token latency
on memory bound workloads, noting that real gains depend on model family, traffic
pattern, hardware and sampling settings.

- vLLM, *Speculative Decoding*.
  https://docs.vllm.ai/en/latest/features/speculative_decoding/

## Which workloads accept more drafted tokens

The acceptance rate is not uniform. Structured output, code and instruction following
accept a high share of drafted tokens; creative, adversarial and high entropy generation
accept fewer. Code editing in particular benefits because much of the original code is
reused across successive edits.

- Red Hat Developer, *How speculative decoding delivers faster LLM inference*, 12 June
  2026.
  https://developers.redhat.com/articles/2026/06/12/how-speculative-decoding-delivers-faster-llm-inference

The video draws this as an ordering of workloads rather than as a set of measured
percentages, because the ordering is what the source supports.

## Not checked

- The exact acceptance rate for each workload type. The ordering is sourced; the
  individual percentages are not, so no percentage is printed on screen.
- The 1,792 GB/s memory bandwidth for the GeForce RTX 5090. NVIDIA publishes the memory
  type and the 512 bit bus width rather than a single bandwidth figure, and the number
  used here is the standard arithmetic of those two.
- The ten, fifty and two hundred tokens per second thresholds used to describe how
  routing changes. These are the script's framing of a gradient, not measured points.
- The claim that roughly seventy per cent of a developer's requests are routine enough to
  run locally. This is the script's illustration of a split, not a measured share of any
  population, and the picture draws it as a share moving rather than as a finding.
- Every tokens per second reading, counter, price and score shown for an unnamed or
  hypothetical setup. These dramatise the narration's own hypotheticals and are not
  measurements of any named product.
- Pricing for any of the hardware named. No price is claimed in the narration or shown on
  screen.
{% endraw %}

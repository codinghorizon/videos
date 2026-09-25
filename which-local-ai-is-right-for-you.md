---
layout: default
title: "Your local AI choice could make it feel broken"
permalink: /which-local-ai-is-right-for-you/
date: 2026-09-25
---

# Your local AI choice could make it feel broken

{% raw %}
Sources for what the video shows and states. Every capture was made on 25 September 2026
with scripts/shot-web.mjs into channels/codinghorizon/public/which-local-ai-is-right-for-you/web/.

## The example machines

The windows laptop with 8 GB of VRAM, the mac with 32 GB of shared memory and the
computer with no graphics card are a hypothetical set of three developers, as the
narration says. They are not measurements of particular products.

## Model names are not the whole specification

- Ollama's library page for qwen3.5 lists each tag with its download size, context
  window and input types. At the time of capture it listed qwen3.5:0.8b at 1.0GB,
  qwen3.5:2b at 2.7GB, qwen3.5:4b at 3.4GB and qwen3.5:9b at 6.6GB, all at a 256K
  context with text and image input, with the family running from 0.8b to 122b.
  https://ollama.com/library/qwen3.5 (captured 25 September 2026)

## Model files are downloaded

- The Qwen3.5-9B repository on Hugging Face publishes its weights as four safetensors
  shards of 5.28 GB, 5.34 GB, 5.37 GB and 3.33 GB, with the repository listed at
  19.3 GB in total. https://huggingface.co/Qwen/Qwen3.5-9B/tree/main (captured
  25 September 2026)

## A connected tool can leave the machine

- Ollama documents a web search API that models can call as a tool. Requests go to
  `POST https://ollama.com/api/web_search` and require an Ollama account and API key,
  so a local model using it sends its search queries to a hosted service.
  https://docs.ollama.com/capabilities/web-search (captured 25 September 2026)

## The example error

- In Python, `date.fromisoformat('')` raises `ValueError: Invalid isoformat string: ''`,
  which is the error a blank date field produces in the invoicing example.
  https://docs.python.org/3/library/datetime.html#datetime.date.fromisoformat

## Memory, quantization and context

- The Qwen3.5-9B GGUF repository lists the same model at several quantizations, each a
  separate file of a different size, which is what the four bit against sixteen bit beats
  show. https://huggingface.co/unsloth/Qwen3.5-9B-GGUF/tree/main
- Hugging Face's GGUF documentation describes the format and its quantization types.
  https://huggingface.co/docs/hub/gguf
- The 14 GB download on a 16 GB card, the tray fills and the spill into system RAM are
  illustrative, as the narration frames them ("Take a 14 GB model download"). No figure
  on screen in those beats is a measurement.
- Apple's MacBook Pro and Mac mini specification pages list memory as unified memory
  shared by the chip. https://www.apple.com/macbook-pro/specs/ ,
  https://www.apple.com/mac-mini/specs/
- Apple's Activity Monitor guide defines memory pressure.
  https://support.apple.com/guide/activity-monitor/view-memory-usage-actmntr1004/mac

## Hardware and backends

- NVIDIA's product pages for the GeForce RTX 4060, RTX 4090 and RTX 5090 are the source of
  the card photographs. https://www.nvidia.com/en-us/geforce/graphics-cards/
- NVIDIA CUDA Toolkit. https://developer.nvidia.com/cuda-toolkit
- AMD ROCm documentation. https://rocm.docs.amd.com/en/latest/
- Intel Arc graphics. https://www.intel.com/content/www/us/en/products/details/discrete-gpus/arc.html
  Intel's ipex-llm repository, which at capture was marked archived.
  https://github.com/intel/ipex-llm
- llama.cpp lists its backends (CUDA, HIP, Metal, SYCL, Vulkan and others) in its README
  and build docs, and its feature matrix marks where backends differ.
  https://github.com/ggml-org/llama.cpp ,
  https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md ,
  https://github.com/ggml-org/llama.cpp/blob/master/docs/backend/SYCL.md ,
  https://github.com/ggml-org/llama.cpp/wiki/Feature-matrix
- Ollama's hardware support page lists the GPUs it supports.
  https://docs.ollama.com/gpu

## Model families

- Qwen 3.5 on Ollama: sizes, tags, inputs and context. https://ollama.com/library/qwen3.5 ,
  https://ollama.com/library/qwen3.5/tags ; Qwen3 Coder: https://ollama.com/library/qwen3-coder
- Gemma 4 on Ollama: e2b, e4b, 12b, 26b and 31b, positioned for reasoning, coding, agentic
  and multimodal use. https://ollama.com/library/gemma4 ; terms of use:
  https://ai.google.dev/gemma/terms
- DeepSeek V4 on Ollama is listed as cloud variants; the Pro listing gives 1.6T total
  parameters with 49B activated and a 1M context. https://ollama.com/library/deepseek-v4-pro ,
  https://ollama.com/library/deepseek-v4-flash , https://ollama.com/library?sort=newest ;
  the weight releases: https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro ,
  https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash
- Mistral Small on Ollama: the 24B model and its note that benchmark results use an
  internal evaluation pipeline. https://ollama.com/library/mistral-small
- Ollama's cloud models documentation. https://docs.ollama.com/cloud

## Benchmarks

- HumanEval, the hand written function completion set. https://github.com/openai/human-eval
- SWE-bench, repository level issue resolution. https://www.swebench.com
- Every score bar, token rate race and scorecard in the benchmark and audition chapters is
  illustrative and labelled so, apart from the 80 and 35 tokens a second, which are the
  narration's own example.

## Software

- Ollama: download for macOS, Windows and Linux, and its local API.
  https://ollama.com/download , https://docs.ollama.com/api/introduction
- LM Studio: the app, its system requirements (8 GB Macs may work with smaller models and
  modest context) and its OpenAI compatible local server. https://lmstudio.ai ,
  https://lmstudio.ai/docs/app/system-requirements , https://lmstudio.ai/docs/app/api
- Jan. https://jan.ai
- MLX and mlx-lm from Apple's ml-explore. https://github.com/ml-explore/mlx ,
  https://github.com/ml-explore/mlx-lm , https://huggingface.co/mlx-community
{% endraw %}

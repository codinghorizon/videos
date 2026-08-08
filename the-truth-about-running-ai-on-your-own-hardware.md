---
layout: default
title: "The Truth About Running AI On Your Own Hardware"
permalink: /the-truth-about-running-ai-on-your-own-hardware/
date: 2026-08-08
---

# The Truth About Running AI On Your Own Hardware

Every figure, product and claim the video puts on screen, with where it comes from.
Checked on 8 August 2026.

---

## Memory sizing for local models

**Ollama's own RAM guidance: 8 GB for a 7B model, 16 GB for a 13B, 32 GB for a 33B.**

This is the sizing rule the video uses to introduce memory as the first hard limit, and
it is Ollama's own wording in its model library documentation: at least 8 GB of RAM to
run the 7B models, 16 GB for the 13B models and 32 GB for the 33B models.

The video's narration goes one step further and gives a 70B model at around 64 GB. That
step is not in Ollama's guidance, which stops at 33B, so **it is not printed on screen**:
the shot shows the two published figures and then a taller rung with no number on it.

- https://github.com/ollama/ollama — model library RAM guidance

**Quantization.**

Quantization stores each parameter with fewer bits than the precision the model was
trained at, which is what brings a model that would otherwise need tens of gigabytes down
to something an ordinary machine can hold. The 16, 8, 5 and 4 bit steps the video draws
are the common GGUF quantization levels distributed for local models.

- https://github.com/ggml-org/llama.cpp — quantization formats and the memory they use

---

## VRAM against system RAM

**Splitting a model across GPU and CPU.**

llama.cpp offloads as many layers as fit into VRAM and runs the rest on the CPU out of
system memory, which is why exceeding a card's VRAM makes a model slower rather than
impossible. This is the mechanism behind the beat where the slab is cleaved and the top
half is carried across the wall.

- https://github.com/ggml-org/llama.cpp — GPU offload and layer splitting

**NVIDIA GeForce RTX 5090: 32 GB of GDDR7.**

The flagship consumer Blackwell card, with 32 GB of GDDR7 on a 512-bit interface. The
video's point is that this is an enormous amount of memory for a consumer graphics card
and still not enough to hold every large model at a useful quantization and context size.

- https://www.nvidia.com/en-gb/geforce/graphics-cards/50-series/rtx-5090/

**AMD Radeon RX 7900 XTX: 24 GB, with llama.cpp acceleration through HIP and ROCm.**

RDNA 3 (gfx1100) is officially supported by ROCm, and llama.cpp builds against HIP/ROCm
as well as Vulkan, so AMD hardware does run local models. The video's claim is only that
NVIDIA remains the broader-compatibility choice because so much machine learning software
is built around CUDA, not that AMD cannot run them.

- https://www.amd.com/en/products/graphics/desktops/radeon/7000-series/amd-radeon-rx-7900xtx.html
- https://github.com/ggml-org/llama.cpp/discussions/15021 — llama.cpp performance on AMD ROCm (HIP)

---

## Running without a GPU

**CPU inference is a supported path, not a workaround.**

llama.cpp was written for CPU inference first and still supports it, which is what allows
a machine with plenty of system RAM and no capable graphics card to load models larger
than that card could hold. The cost is throughput: the video's slow token stream is the
honest picture of what that feels like on a large model.

- https://github.com/ggml-org/llama.cpp — CPU inference

---

## Apple Silicon and unified memory

**A Mac does not split system RAM from GPU VRAM.**

Apple Silicon uses a single pool of unified memory that the CPU and GPU both address, so
the GPU is not limited to a separate, smaller allocation the way a discrete card is. That
is the whole reason a high memory Mac can hold models that will not fit on a consumer GPU.

- https://developer.apple.com/documentation/metal — unified memory on Apple silicon

**Mac Studio with M2 Ultra: configurable up to 192 GB of unified memory.**

Apple's own specification. The video uses the older M2 Ultra deliberately, because the
point is that this capacity has been buyable for a while rather than that it is new.

- https://support.apple.com/en-gb/111835 — Mac Studio (2023) technical specifications
- https://www.apple.com/newsroom/2023/06/apple-introduces-m2-ultra/

**MLX, and WWDC 2026.**

Apple presented running local agentic AI on the Mac through MLX at WWDC 2026, including
coding agents driven against a local OpenAI-compatible MLX-LM server, and distributed
inference spreading one model across several Macs over Thunderbolt or Ethernet.

- https://developer.apple.com/videos/play/wwdc2026/232/ — Run local agentic AI on the Mac using MLX
- https://developer.apple.com/videos/play/wwdc2026/233/ — Explore distributed inference and training with MLX
- https://github.com/ml-explore/mlx

---

## How much hardware you actually need

**LM Studio: 16 GB of RAM recommended, and at least 4 GB of dedicated VRAM on Windows.**

Straight from LM Studio's published system requirements, for both Apple Silicon Macs and
Windows systems. The video's point is that this is a starting line rather than a
comfortable configuration.

- https://lmstudio.ai/docs/app/system-requirements

---

## Context windows

**The KV cache grows with the context window, and it takes memory the model wanted.**

Attention keys and values for every token already in context are held in memory so they
do not have to be recomputed, so a longer window costs memory on top of the weights. This
is why a model that fits at a small context stops fitting at a large one.

- https://github.com/ggml-org/llama.cpp — KV cache and context size

**GLM-4.7 Flash: around 23 GB of VRAM at a 64,000 token context.**

Ollama's own figure, published alongside `ollama launch`. The same page recommends
raising the context length to at least 64,000 tokens for coding tools, which is exactly
the combination the video is pointing at: the context setting a coding agent wants is
what pushes the model past most consumer cards.

- https://ollama.com/blog/launch
- https://ollama.com/library/glm-4.7-flash

---

## Local models against frontier models

**Ollama can launch coding tools against local or cloud models.**

`ollama launch` sets up and runs Claude Code, OpenCode, Codex and Droid against local
models such as glm-4.7-flash and qwen3-coder, or against Ollama's cloud models. The same
announcement is where the guidance about coding tools working best at a full context
length comes from, and where the cloud alternative is offered for hardware that cannot
hold it.

- https://ollama.com/blog/launch

---

## The competition

**Open and open-weight model families named in the video.**

Qwen, Gemma, DeepSeek, GPT-OSS and GLM, alongside Meta's Llama, are the families the
video points at when it says the field is no longer one company releasing weights and
everyone else following.

- https://github.com/QwenLM/Qwen3
- https://ai.google.dev/gemma
- https://github.com/deepseek-ai
- https://openai.com/index/introducing-gpt-oss/
- https://github.com/zai-org/GLM-4.5
- https://www.llama.com/

**Switching between them.**

Both LM Studio and Ollama let you hold several models locally and change which one is
loaded, which is the "choice at the model level" the video closes that chapter on.

- https://lmstudio.ai/docs
- https://docs.ollama.com/

---

## Privacy

**A downloaded model can run with no network at all, and can serve a local API.**

LM Studio runs offline once a model is on disk and exposes an OpenAI-compatible server on
the local machine or local network, which is the mechanism behind the video's claim that
prompts and documents need never leave the machine.

- https://lmstudio.ai/docs/app/api — OpenAI compatibility endpoints
- https://lmstudio.ai/docs/app/basics — running offline

---

## What is not sourced, and is not on screen

- **A 70B model at around 64 GB.** Said in the narration, attributed there to Ollama.
  Ollama's published guidance stops at 33B and 32 GB, so no such figure appears in the
  picture.
- **£3,000 and £5,000 machines, and a $20 a month service.** Round illustrative numbers
  for the size of the trade, not quotes for particular products.
- **A forty minute agent run.** An illustration of a long autonomous task, not a measured
  benchmark.
- **12 GB of VRAM against 32 GB of system RAM.** A representative gaming PC used to draw
  the two pools, not a specific machine.

---
layout: default
title: "The Local AI Mini PC I Would Actually Buy Today"
permalink: /mini-pcs-amd-vs-nvidia-vs-mac-local-ai/
date: 2026-09-09
---

# The Local AI Mini PC I Would Actually Buy Today

{% raw %}
Every figure, capacity and benchmark the finished picture puts on screen, chased to a
primary source. Anything that could not be sourced is listed at the bottom and is
deliberately not rendered as a number in any shot.

## Nvidia

**GeForce RTX 3090 — 24 GB GDDR6X.** 10,496 CUDA cores, 384 bit bus, 350 W.
Source: NVIDIA GeForce RTX 30 Series specifications.
https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090-3090ti/

**GeForce RTX 4090 — 24 GB GDDR6X.** 16,384 CUDA cores, 384 bit bus, 450 W. Same memory
capacity as the 3090 one generation later, which is the point the script makes.
Source: NVIDIA GeForce RTX 40 Series specifications.
https://www.nvidia.com/en-us/geforce/graphics-cards/40-series/rtx-4090/

**GeForce RTX 5090 — 32 GB GDDR7, 512 bit interface.**
Source: NVIDIA GeForce RTX 5090 product page.
https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/

**RTX PRO 6000 Blackwell — 96 GB GDDR7.** 24,064 CUDA cores, 512 bit bus, 1.792 TB/s peak
memory bandwidth, up to 4000 AI TOPS.
Source: NVIDIA RTX PRO 6000 Blackwell Workstation Edition product page and datasheet.
https://www.nvidia.com/en-us/products/workstations/professional-desktop-gpus/rtx-pro-6000/

**DGX Spark — 128 GB LPDDR5x coherent unified system memory, 273 GB/s.** GB10 Blackwell
GPU with 5th generation Tensor Cores, 20 core Arm CPU, up to 1 PFLOP FP4. NVIDIA states
inference on models up to 200 billion parameters, fine tuning up to 70 billion, and up to
700 billion across four linked units.
Source: NVIDIA DGX Spark product page.
https://www.nvidia.com/en-us/products/workstations/dgx-spark/

**CUDA as the default path.** PyTorch's own install matrix ships CUDA builds as the
standard accelerated option on Linux and Windows; ROCm is offered separately and Metal
support is through MPS rather than a CUDA equivalent.
Source: PyTorch "Get Started" install selector.
https://pytorch.org/get-started/locally/

## AMD

**Ryzen AI Max+ 395 — up to 128 GB unified memory, up to 96 GB convertible to VRAM.**
16 Zen 5 cores and 32 threads, Radeon 8060S with 40 graphics cores, XDNA 2 NPU rated
50+ peak AI TOPS, 4 nm Strix Halo. The 96 GB figure is AMD Variable Graphics Memory, not
a separate memory pool.
Source: AMD Ryzen AI Max+ 395 product page and AMD's Ryzen AI Max+ 395 launch blog.
https://www.amd.com/en/products/processors/laptop/ryzen/ai-max-300-series/amd-ryzen-ai-max-plus-395.html
https://www.amd.com/en/blogs/2025/amd-ryzen-ai-max-395-processor-breakthrough-ai-.html

**Framework Desktop published throughput — gpt-oss-20b MXFP4 at 58 tok/s, gpt-oss-120b
MXFP4 at 38 tok/s.** Framework states both were measured using LM Studio on Fedora 42.
The 120B figure is published for the Max+ 395 128 GB configuration only. Framework also
lists the top configuration as 128 GB total with 96 GB dedicated VRAM on Windows, and
notes the VRAM split can be overridden higher on Linux.
Source: Framework Desktop product page, machine learning tab.
https://frame.work/desktop?tab=machine-learning

**ROCm and llama.cpp on Radeon and Ryzen are documented by AMD directly**, including a
step by step guide for running gpt-oss 20B and 120B on Ryzen AI processors and Radeon
cards, and Windows support for newer Radeon hardware.
Source: AMD developer blog.
https://www.amd.com/en/blogs/2025/how-to-run-openai-gpt-oss-20b-120b-models-on-amd-ryzen-ai-radeon.html

**GMKtec EVO X2** ships the Ryzen AI Max+ 395 in a mini desktop chassis, and is named in
the script alongside Framework Desktop as an example rather than as a spec claim. No
performance figure from GMKtec is rendered on screen.

## Apple

**Mac Studio unified memory — M4 Max up to 128 GB, M3 Ultra up to 512 GB.** Apple
describes 512 GB as "the most unified memory ever in a personal computer".
Source: Apple Newsroom, "Apple unveils new Mac Studio, the most powerful Mac ever",
March 2025.
https://www.apple.com/newsroom/2025/03/apple-unveils-new-mac-studio-the-most-powerful-mac-ever/

**The 600 billion parameter claim is Apple's own wording.** Apple states Mac Studio with
M3 Ultra is "capable of running large language models (LLMs) with over 600 billion
parameters entirely in memory". It is a capacity claim about holding a model, not a
throughput claim, which is exactly the distinction the script draws.
Source: as above, and Apple Newsroom, "Apple reveals M3 Ultra, taking Apple silicon to a
new extreme".
https://www.apple.com/newsroom/2025/03/apple-reveals-m3-ultra-taking-apple-silicon-to-a-new-extreme/

**Unified memory architecture.** Apple silicon places CPU, GPU and Neural Engine on one
memory pool rather than a separate VRAM bank, which is the mechanism behind the softer
memory wall.
Source: Apple, Apple silicon overview.
https://developer.apple.com/documentation/apple-silicon

**Local runtimes on Apple silicon.** MLX is Apple's own array framework for Apple silicon;
llama.cpp ships a Metal backend; Ollama and LM Studio both distribute macOS builds.
Sources:
https://github.com/ml-explore/mlx
https://github.com/ggml-org/llama.cpp
https://ollama.com/download
https://lmstudio.ai/

## Model footprints

**Qwen3 Coder 30B A3B — 30 billion total parameters, 3.3 billion activated per token.**
The 4 bit distribution is 19 GB of weights, which is the basis for the script's "nineteen
to twenty gigabyte zone" at short context. Being mixture of experts reduces compute per
token, not the memory needed to hold the weights, which is the point of the beat.
Source: Ollama model library, qwen3-coder.
https://ollama.com/library/qwen3-coder

**DeepSeek R1 Distill Qwen 32B — 20 GB at q4_K_M**, rising to 35 GB at q8_0 and 66 GB at
fp16. Weights alone are 20 GB, so a modest context window on top puts real usage in the
mid twenties in gigabytes, which is what makes it awkward on a 24 GB card.
Source: Ollama model library, deepseek-r1 tags.
https://ollama.com/library/deepseek-r1/tags

**Context windows of 128K and 256K tokens are published model card figures**, and the KV
cache that serves them is allocated in addition to the weights. Qwen3 Coder 30B A3B is
published with a 256K native context.
Source: Qwen3-Coder-30B-A3B-Instruct model card.
https://huggingface.co/Qwen/Qwen3-Coder-30B-A3B-Instruct

## Not sourced, and therefore not printed on screen

**The MLX throughput trio in the Mac chapter.** The script cites independent MLX results
of roughly 79 tokens per second for gpt-oss 120B, roughly 94 for Qwen3.6 35B A3B, and
roughly 20 for four bit DeepSeek R1 class runs on a 512 GB M3 Ultra Mac Studio. Published
independent figures close to these exist but do not match the stated configuration:
a 256 GB M3 Ultra measured Qwen3.5 35B A3B at 95 tok/s at 4 bit and 80 tok/s at 8 bit, and
separately reported gpt-oss 120B generation on M3 Ultra at around 60 tokens per second at
8 bit with noted run to run instability. No primary source was found for 79, or for the
DeepSeek figure at that class. **None of these three numbers is rendered in any shot.**
The Mac throughput beats show the machine and the loaded models rather than a scoreboard.
References consulted:
https://rapidmlx.com/blog/mlx-model-benchmark-m3-ultra
https://github.com/ml-explore/mlx-lm/issues/432

**Availability of the 512 GB Mac Studio.** Apple withdrew the 512 GB M3 Ultra
configuration in March 2026, reported as a memory supply decision. The capacity figure and
Apple's 600 billion parameter claim remain accurate for the machine as shipped and specced,
so the shot presents 512 GB as the configuration Apple built rather than as something to
order today.
References consulted:
https://9to5mac.com/2026/03/05/apple-no-longer-offers-m3-ultra-mac-studio-with-original-highest-ram-configuration/
https://www.macsparky.com/blog/2026/03/apple-drops-512gb-ram-option-on-m3-ultra-mac-studio/

**Pricing.** No price is stated in the script and none is rendered on screen. Local AI
hardware pricing moved sharply through 2026 on memory cost, so any figure would date the
video faster than the argument does.
{% endraw %}

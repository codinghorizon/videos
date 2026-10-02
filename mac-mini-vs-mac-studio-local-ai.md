---
layout: default
title: "The Mac Mini Has a Local AI Limit Nobody Sees Coming"
permalink: /mac-mini-vs-mac-studio-local-ai/
date: 2026-10-02
---

# The Mac Mini Has a Local AI Limit Nobody Sees Coming

{% raw %}
Checked 2 October 2026. Apple's performance figures are Apple's own tests, as its footnotes
say; none is an independent measurement. Model sizes are four bit arithmetic unless a real
file is cited.

## Mac mini (M6 and M5 Pro)

- [Apple Newsroom, 25 August 2026: Mac mini with M6 and M5 Pro](https://www.apple.com/newsroom/2026/08/apple-unveils-a-more-powerful-mac-mini-featuring-the-all-new-m6-and-m5-pro/)
  - "Mac mini with M6 starts at $899 (U.S.)"; "Mac mini with M5 Pro starts at $1,699 (U.S.)".
  - M6: "Up to 13.5x faster LLM prompt processing in LM Studio when compared to Mac mini with
    M1, and up to 4.8x faster than M4."
  - M5 Pro: "Up to 8.5x faster LLM prompt processing performance in LM Studio when compared to
    Mac mini with M2 Pro, and up to 4x faster than M4 Pro."
  - M6: "16GB of standard unified memory configurable up to 32GB, as well as higher memory
    bandwidth up to 170GB/s".
  - M5 Pro: "supports up to 64GB of unified memory with 307GB/s of memory bandwidth".
  - Footnote: "Testing was conducted by Apple in July 2026."
- [Mac mini technical specifications](https://www.apple.com/mac-mini/specs/)
  - M6: 16GB standard, configurable to 24GB or 32GB; 153GB/s memory bandwidth on the base
    configurations, 170GB/s with the upgraded memory. Three Thunderbolt 4 ports.
  - M5 Pro: 24GB standard, configurable to 48GB or 64GB; 307GB/s memory bandwidth. Three
    Thunderbolt 5 ports.
  - Listed configurations from $899, $1099, $1299 and $1699.

## Mac Studio (M5 Max and M5 Ultra)

- [Apple Newsroom, 25 August 2026: Mac Studio with M5 Max and M5 Ultra](https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/)
  - "Mac Studio with M5 Max starts at $2,499 (U.S.)"; "Mac Studio with M5 Ultra starts at
    $5,499 (U.S.)".
  - M5 Ultra: "Up to 9.8x faster LLM prompt processing in LM Studio when compared to Mac
    Studio with M1 Ultra, and up to 4x faster than M3 Ultra."
  - M5 Max: "Up to 10.7x faster LLM prompt processing in LM Studio when compared to Mac Studio
    with M1 Max, and 3.9x faster than M4 Max."
  - "up to 512GB of unified memory"; "Mac Studio with 512GB of unified memory is coming in
    late October."
  - Footnote: "Testing was conducted by Apple in July 2026."
- [Mac Studio technical specifications](https://www.apple.com/mac-studio/specs/)
  - M5 Max: 36GB unified memory standard, configurable to 48GB, 64GB or 128GB; 460GB/s memory
    bandwidth, 614GB/s on the configurable 40 core GPU chip.
  - M5 Ultra: 96GB unified memory standard, configurable to 256GB or 512GB; 1.2TB/s memory
    bandwidth.

## Model sizes

- Four bit arithmetic: parameters × 4 bits ÷ 8 bits per byte. 8 billion parameters is 4GB,
  32 billion is 16GB, 70 billion is 35GB. This is weights only, before runtime overhead,
  context cache or anything else on the machine.
- Real four bit files are larger than the arithmetic, because some tensors are kept at higher
  precision:
  - [Qwen2.5 Coder 32B Instruct GGUF](https://huggingface.co/bartowski/Qwen2.5-Coder-32B-Instruct-GGUF):
    Q4_K_M is 19.85GB.
  - [Llama 3.3 70B Instruct GGUF](https://huggingface.co/bartowski/Llama-3.3-70B-Instruct-GGUF):
    Q4_K_M is 42.52GB.
  - [Llama 3.1 8B Instruct GGUF](https://huggingface.co/bartowski/Meta-Llama-3.1-8B-Instruct-GGUF):
    Q4_K_M is 4.92GB.

## Software on Apple Silicon

- [MLX](https://github.com/ml-explore/mlx): "MLX is an array framework for machine learning
  on Apple silicon, brought to you by Apple machine learning research." MIT licence.
- [LM Studio](https://lmstudio.ai/): "Powered by the LM Studio runtime, with MLX and
  llama.cpp under the hood."
- [Ollama](https://ollama.com/): runs open models locally on macOS, Windows and Linux.

## Outside the Mac

- [NVIDIA GeForce RTX 5090](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/):
  "equipped with 32 GB of super-fast GDDR7 memory". CUDA is NVIDIA's own platform.
- [AMD Ryzen AI Max+ 395](https://www.amd.com/en/products/processors/laptop/ryzen/ai-300-series/amd-ryzen-ai-max-plus-395.html)
  (former codename Strix Halo): Max. Memory 128 GB, 256-bit LPDDR5x.
- [Framework Desktop specifications](https://frame.work/desktop): Ryzen AI Max+ 395 with
  128GB LPDDR5x-8000 memory, soldered.
- [AMD playbook: LM Studio on Ryzen AI Max+](https://developer.amd.com/playbooks/lmstudio-rocm-llms):
  AMD's own guide to running and serving models with LM Studio on these systems.

## What is illustrative

The sizes of the runtime's working space, the context cache, macOS and apps, the editor, the
browser and other workloads drawn in this video are illustrative and are labelled so on
screen. They vary with the model architecture, the context length, the runtime and its
settings, and what else is open.
{% endraw %}

---
layout: default
title: "Your PC Could Run Better Local AI Than You Think"
permalink: /upgrade-or-buy-local-ai/
date: 2026-09-26
---

# Your PC Could Run Better Local AI Than You Think

{% raw %}
Every figure the video states, with the page it comes from. Pages were checked on
25 September 2026.

## Memory arithmetic

- **A 27 billion parameter model at four bits needs about 13.5 GB for its weights.**
  Four bits is half a byte, so 27,000,000,000 × 0.5 bytes = 13.5 GB (decimal gigabytes).
  This is the weights alone, before file overhead, context or runtime.
- **A 70 billion parameter model at four bits has a weight floor of about 35 GB.**
  70,000,000,000 × 0.5 bytes = 35 GB, on the same basis.
- **The same arithmetic gives the other figures the video draws**: 8B at four bits is
  4 GB, 14B is 7 GB, 20B is 10 GB and 35B is 17.5 GB of weights, before anything else.
- **Real model files run larger than this floor**, and the runtime also needs memory for
  the conversation context and its own working space. Google's Gemma 4 documentation says
  its published estimates "only account for the memory required to load the static model
  weights. They don't include the additional VRAM needed for supporting software or the
  context window."
  https://ai.google.dev/gemma/docs/core

## The key and value cache

- **More context means more memory for the key and value cache.** Hugging Face's
  Transformers documentation: "A key-value (KV) cache eliminates this inefficiency by
  storing kv pairs derived from the attention layers of previously processed tokens."
  https://huggingface.co/docs/transformers/main/en/cache_explanation
- Google's Gemma 4 documentation, on the context window: "Memory consumption will increase
  dynamically based on the total number of tokens in your prompt and the generated
  response." https://ai.google.dev/gemma/docs/core

## Graphics cards

- **GeForce RTX 5090: 32 GB of GDDR7, 1792 GB/sec of memory bandwidth.** NVIDIA's RTX 5090
  page: "equipped with 32 GB of super-fast GDDR7 memory"; its specifications table gives
  Memory Configuration 32 GB GDDR7 and Memory Bandwidth 1792 GB/sec.
  https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/
- **RTX 5090 power and size.** The same page's full specifications: Total Graphics Power
  575 W, Required System Power 1000 W, supplementary power 4x PCIe 8-pin cables (adapter in
  box) or 1x 600 W PCIe Gen 5 cable, length 304 mm, two slots.
- **A lower power card, for example.** NVIDIA RTX PRO 2000 Blackwell: Memory Configuration
  16 GB GDDR7 with error-correcting code (ECC), Memory Bandwidth 288 GB/s, Max Power
  Consumption 70 W.
  https://www.nvidia.com/en-us/products/workstations/professional-desktop-gpus/rtx-pro-2000/
- **A laptop GPU with the same name can have less memory.** NVIDIA's GeForce RTX 50 Series
  laptop specifications give the GeForce RTX 5090 Laptop GPU a Standard Memory Configuration
  of 24 GB GDDR7, against 32 GB GDDR7 for the desktop GeForce RTX 5090.
  https://www.nvidia.com/en-us/geforce/laptops/50-series/

## NVIDIA DGX Spark

- **128 GB of LPDDR5x unified system memory, a Blackwell GPU, 273 GB/s.** NVIDIA's DGX
  Spark specifications: GPU Blackwell Architecture; System Memory 128 GB LPDDR5x, coherent
  unified system memory; Memory Bandwidth 273 GB/s.
  https://www.nvidia.com/en-us/products/workstations/dgx-spark/
- The DGX Spark User Guide, Hardware Overview, gives the memory as "128 GB LPDDR5x unified
  system memory, 256-bit interface, 4266 MHz, 273 GB/s bandwidth".
  https://docs.nvidia.com/dgx/dgx-spark/hardware.html
- **"Models up to 200 billion parameters", and 405 billion for two systems.** The User
  Guide lists "Support for AI models up to 200 billion parameters (or 405B for dual-Spark
  configuration)". The product page says "AI models up to 200 billion parameters at your
  desktop", and now describes connecting "up to four NVIDIA DGX Spark systems to work with
  AI models of up to 700 billion parameters".
- **The bandwidth comparison.** 1792 GB/sec for the RTX 5090 against 273 GB/s for the DGX
  Spark is 1792 / 273 = 6.56 times, which is the "over six times the raw memory bandwidth
  on paper" the video states.

## Apple

- **Mac Studio with M5 Max: up to 128 GB of unified memory.** Apple's Mac Studio technical
  specifications: M5 Max with 36GB unified memory, "Configurable to: 48GB, 64GB, or 128GB
  (M5 Max with 18-core CPU and 40-core GPU)". The same page gives that configuration's
  memory bandwidth as 614GB/s.
  https://www.apple.com/mac-studio/specs/
- **Mac Studio with M5 Ultra: up to 512 GB.** Same page: M5 Ultra with 96GB unified memory,
  "Configurable to: 256GB or 512GB (M5 Ultra with 36-core CPU and 80-core GPU)".
- **Mac mini: M6 up to 32 GB, M5 Pro up to 64 GB.** Apple's Mac mini technical
  specifications list three M6 configurations, configurable to at most 32GB, and an M5 Pro
  configuration "Configurable to: 48GB or 64GB".
  https://www.apple.com/mac-mini/specs/

## Models

- **Gemma 4 sizes.** Google: "Gemma 4 models are available in 5 parameter sizes: E2B, E4B,
  12B, 31B and 26B A4B", including "a powerful 31B parameter dense model" and "a highly
  efficient 26B MoE model". https://ai.google.dev/gemma/docs/core
- **Gemma 4 memory at Q4.** Google's Table 1, Q4_0 (4-bit) column: Gemma 4 12B 6.7 GB,
  Gemma 4 26B A4B 14.4 GB, Gemma 4 31B 17.5 GB (and BF16 57.7 GB for 26B A4B). The caption:
  "Approximate GPU or TPU memory required to load Gemma 4 models based on parameter count,
  quantization level and 20% overhead of loading additional things."
- **Free space on each card.** The figures the video reads out on the Gemma ladder are the
  card's capacity minus Google's Q4 figure: 8 − 6.7 = 1.3 GB, 16 − 14.4 = 1.6 GB and
  24 − 17.5 = 6.5 GB, before any context.
- **Mixture of experts.** Google: "While it only activates 4 billion parameters per token
  during generation, all 26 billion parameters must be loaded into memory to maintain fast
  routing and inference speeds."
- **Qwen3.8 27B.** The Qwen/Qwen3.8-27B model card on Hugging Face, released under the
  Apache 2.0 licence and described as a dense model.
  https://huggingface.co/Qwen/Qwen3.8-27B
  The card's size badge reads 28B parameters, which counts its vision encoder; the language
  model is 27B, which is the figure the video uses.

## Not checked

- Context and runtime shares drawn on the video's memory rule are illustrative. They depend
  on the model's architecture, the runtime and the cache format, and the video labels them
  as such rather than giving them a number.
- Which models count as "useful" at each tier, and how well a small model handles a given
  coding task, are judgements rather than measurements.
- Relative speeds drawn between system RAM and VRAM are illustrative; only the published
  memory bandwidths are stated as figures.
{% endraw %}

---
layout: default
title: "$500 for local AI and one GPU changes everything"
permalink: /best-local-ai-machine-under-500/
date: 2026-10-01
---

# $500 for local AI and one GPU changes everything

{% raw %}
Checked 30 September 2026. Prices change daily; every price below is dated.

## Model sizes (Qwen 3.5 on Ollama)

- Ollama's library lists `qwen3.5:9b` at **6.6GB**, `qwen3.5:27b` at **17GB** and
  `qwen3.5:4b` at **3.4GB**, each with a 256K context and **Text, Image** input.
  The 9B tag is also `qwen3.5:latest`.
  Source: <https://ollama.com/library/qwen3.5/tags>
- The Ollama listing describes Qwen 3.5 as "a family of open-source multimodal models" and
  tags the family `vision`, `tools` and `thinking`.
  Source: <https://ollama.com/library/qwen3.5>
- Qwen's model card for Qwen3.5-9B tags it Image-Text-to-Text and describes it as a
  "Causal Language Model with Vision Encoder", with a "Unified Vision-Language Foundation".
  Source: <https://huggingface.co/Qwen/Qwen3.5-9B>
- A listed download size is the size of the quantized weights file. At run time the
  runtime also holds the conversation's context (KV cache) and its own buffers, so the
  memory in use is larger than the download.

## Offloading to system memory

- llama.cpp supports "CPU+GPU hybrid inference to partially accelerate models larger than
  the total VRAM capacity", which is how a 17GB model can run partly on a 12GB card.
  Source: <https://github.com/ggml-org/llama.cpp> (README, Description)

## NVIDIA GeForce RTX 3060 12GB

- NVIDIA lists the RTX 3060 with 12 GB or 8 GB of GDDR6, 3584 CUDA cores, a graphics card
  power of 170 W and a required system power of 550 W.
  Source: <https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3060-3060ti/>
- TechPowerUp's GPU database lists the RTX 3060 12 GB (GA106, 12 GB GDDR6, 192 bit) with a
  TDP of 170 W and a suggested PSU of 450 W.
  Source: <https://www.techpowerup.com/gpu-specs/geforce-rtx-3060-12-gb.c3682>
- llama.cpp ships "Custom CUDA kernels for running LLMs on NVIDIA GPUs" and lists CUDA
  (Nvidia GPU) among its supported backends.
  Source: <https://github.com/ggml-org/llama.cpp>

## Used RTX 3060 prices

- PCPrice.Watch reports a used RTX 3060 median of €252 across 1,415 completed eBay sales
  in seven markets over 90 days (typically €232 to €269), updated 30 September 2026.
  Source: <https://www.pcprice.watch/gpu-buying-guide/rtx-3060-price-used-and-specs>
- BestValueGPU's US page was titled "RTX 3060 Price History: $459 new, $300 used (Sep
  2026)" in search results, and a summary of it gave an early September average of about
  $291 used. The page itself could not be opened to confirm this.
  Source: <https://bestvaluegpu.com/history/new-and-used-rtx-3060-price-history-and-specs/>

## Intel Arc B580

- Intel's specification page lists the Arc B580 with a Recommended Customer Price of
  **$249.00**, launch Q4'24, **12 GB GDDR6** on a 192 bit bus at 456 GB/s, **TBP 190 W**,
  **Vulkan 1.3**, and a **minimum power supply of 600 W** with one 8-pin connector.
  Source: <https://www.intel.com/content/www/us/en/products/sku/241598/intel-arc-b580-graphics/specifications.html>
- TechPowerUp lists the Arc B580 (BMG-G21) with 12 GB GDDR6 on a 192 bit bus.
  Source: <https://www.techpowerup.com/gpu-specs/arc-b580.c4244>
- US street prices in 2026 have sat around $300: Tom's Hardware and PC Guide report three
  models near $300 with most sold out, and VideoCardz reported a drop to $290. The Intel
  Limited Edition at $249 appears occasionally and sells out.
  Sources: <https://www.tomshardware.com/pc-components/gpus/where-to-buy-the-intel-arc-b580>,
  <https://www.pcguide.com/news/intel-arc-b580-stock-dries-up-but-three-models-of-the-flagship-gpu-are-still-available-two-with-a-discount-price/>,
  <https://videocardz.com/newz/intel-arc-b580-drops-to-290-becomes-the-cheapest-12gb-graphics-card-right-now>

## Intel software support in llama.cpp

- llama.cpp lists "Vulkan and SYCL backend support", with SYCL targeting Intel GPUs and
  Vulkan targeting GPUs generally.
  Source: <https://github.com/ggml-org/llama.cpp> (Supported backends)
- llama.cpp's community Vulkan benchmark thread collects llama-bench results from users,
  B580 owners among them.
  Source: <https://github.com/ggml-org/llama.cpp/discussions/10879>
- InsiderLLM's B580 guide lists Qwen3 8B at 13.3 tokens per second on the B580, citing
  Phoronix and OpenBenchmarking testing of llama.cpp's Vulkan backend under Linux.
  Sources: <https://insiderllm.com/guides/intel-arc-b580-local-llm/>,
  <https://www.phoronix.com/review/llama-cpp-vulkan-eoy2025>
- An example of a driver specific failure on Intel hardware: llama.cpp issue #18946,
  "ErrorOutOfDeviceMemory" and memory accounting failures in the Vulkan and SYCL backends
  on an Intel Core Ultra 258V (Lunar Lake), opened 20 January 2026 and closed as not
  planned.
  Source: <https://github.com/ggml-org/llama.cpp/issues/18946>

## RTX 2060

- TechPowerUp lists the GeForce RTX 2060 (TU106) with 6 GB of GDDR6 on a 192 bit bus.
  Source: <https://www.techpowerup.com/gpu-specs/geforce-rtx-2060.c3310>

## Not confirmed

- The tracker behind "a working RTX 3060 near $295 on average, with recorded price points
  spanning roughly $212 to $295" could not be re-found. The nearest US figures found were
  about $291 to $300 used (BestValueGPU, above).
- "One reported setup reaching about 30 generated tokens per second" for Qwen 3 8B on a B580
  through Vulkan could not be re-found. The one figure found for that combination is the
  13.3 tokens per second quoted above, from a different setup (Linux).
- "$250 to above $300" for current B580 listings, and "unavailable at the official store",
  are consistent with the sources above but were not checked against a single dated listing
  page.
{% endraw %}

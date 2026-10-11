---
layout: default
title: "Don't Preorder NVIDIA's First 128GB CUDA Laptop Yet"
permalink: /128gb-cuda-laptop-most-buyers-should-wait/
date: 2026-10-11
---

# Don't Preorder NVIDIA's First 128GB CUDA Laptop Yet

{% raw %}
Checked on 2026-10-11.

## Surface Laptop Ultra

- The 128GB configuration (NVIDIA RTX Spark N1X, 6,144 core GPU, 20 core CPU, 128GB unified memory, 1TB SSD, Windows 11 Pro) is listed at $5,899.99 on the Microsoft Store, marked out of stock for preorder on the day checked. The entry configuration (5,120 core GPU, 18 core CPU, 24GB, 512GB SSD) is $2,599.99.
  Source: https://www.microsoft.com/en-us/store/configure/surface-laptop-ultra/8wg5vqp0x4b8
- Microsoft's launch post: an NVIDIA Grace CPU with up to 20 cores, an NVIDIA Blackwell RTX GPU with up to 6,144 cores, up to 128GB of unified memory, "access to the CUDA ecosystem", "Run AI models exceeding 120B parameters locally", availability beginning October 16. Footnote 1: "128GB total system memory in a unified memory architecture dynamically shared between CPU and GPU. Maximum amount addressable by the GPU depends on system configuration and workload and is less than the total." Footnote 2: the 1 petaflop figure is "theoretical FP4 performance of 1 petaflop using the sparsity feature".
  Source: https://blogs.windows.com/devices/2026/10/07/pre-order-our-most-powerful-surface-devices-ever/
- No independent token generation benchmark of the laptop was found on the day checked; Microsoft's post gives none.
- NVIDIA's RTX Spark page: "the full CUDA stack, right on your PC".
  Source: https://www.nvidia.com/en-us/products/rtx-spark/
- NVIDIA's RTX Spark porting guide: "Compatibility depends on the application and its dependencies, so validate target configurations."
  Source: https://docs.nvidia.com/rtx-spark/rtx-spark-porting-guide/latest/index.html

## Surface RTX Spark Dev Box

- $5,999 (MSRP), 128GB of unified memory, up to 1 petaflop, sold on Microsoft.com in the US, shipping in November. $5,999 minus $5,899 is $100.
  Source: https://blogs.windows.com/devices/2026/10/07/pre-order-our-most-powerful-surface-devices-ever/

## DGX Spark (desktop, same platform family)

- NVIDIA's hardware guide: 128GB LPDDR5x unified system memory, 256 bit interface, 273 GB/s bandwidth; a 20 core Arm CPU (10 Cortex-X925 and 10 Cortex-A725).
  Source: https://docs.nvidia.com/dgx/dgx-spark/hardware.html
- The official llama.cpp DGX Spark benchmark (tg32, generation): gpt-oss 120B MXFP4 58.72 tok/s; Qwen3 Coder 30B A3B Q8_0 61.06 tok/s, falling to 40.23 tok/s at 16,384 tokens of context.
  Source: https://github.com/ggml-org/llama.cpp/blob/master/benches/dgx-spark/dgx-spark.md
- Dense Qwen3 32B on a DGX Spark: about 10.5 tok/s with vLLM and NVFP4 weights on one published model card (the narration says "around 10.7"); an NVIDIA forum user reported 9.46 tok/s with Ollama. That is roughly a sixth of the 58.7 tok/s gpt-oss 120B figure.
  Sources: https://huggingface.co/gdubicki/Qwen3-32B-NVFP4 , https://forums.developer.nvidia.com/t/dgx-spark-performance/356716
- GIGABYTE AI TOP ATOM (GB10, 128GB LPDDR5X, 4TB PCIe 5.0 SSD) is $7,999.99 on Newegg, sold and shipped by Newegg; the 1TB option is $5,999.99.
  Source: https://www.newegg.com/p/N82E16859252047

## ASUS ROG Flow Z13 (Ryzen AI Max+ 395)

- The 128GB model (GZ302EA-XS99, 1TB SSD) is $3,299.99 in the ASUS US store, in stock on the day checked.
  Source: https://rog.asus.com/us/laptops/rog-flow/rog-flow-z13-2025/spec/
- ASUS's VRAM allocation guide: on the 128GB Flow Z13 the integrated GPU's allocation can be raised to a maximum of 96GB (in Armoury Crate).
  Source: https://rog.asus.com/in/articles/guides/how-to-adjust-the-rog-flow-z13s-vram-allocation/
- AMD's Ryzen AI Max+ 395: 16 Zen 5 cores, Radeon 8060S graphics with 40 GPU cores, 256 bit LPDDR5x-8000, up to 128GB. 256 bits at 8,000 MT/s is 256 GB/s.
  Source: https://www.amd.com/en/products/processors/laptop/ryzen/ai-300-series/amd-ryzen-ai-max-plus-395.html
- Tom's Hardware measured the Ryzen AI Max+ 395 at a peak of 56 tokens per second on GPT-OSS 120B at 4 bit ("we clocked ... the last-gen Ryzen AI Max+ 395 at 56 tokens per second").
  Source: https://www.tomshardware.com/pc-components/cpus/amd-attempts-to-get-ahead-of-expected-rtx-spark-launch-with-gorgon-halo-ai-benchmarks-company-says-it-has-shipped-over-half-a-million-agentic-pcs-to-date
- Our arithmetic: $5,899 minus $3,300 is about $2,600; $2,600 / $3,300 is about 79 percent.

## MacBook Pro M5 Max

- Apple: M5 Max with up to 128GB of unified memory and up to 614GB/s of memory bandwidth. 614 / 273 is 2.25.
  Source: https://www.apple.com/newsroom/2026/03/apple-introduces-macbook-pro-with-all-new-m5-pro-and-m5-max/
- The 14 inch MacBook Pro, M5 Max 18 core CPU, 40 core GPU, 128GB, 2TB is $6,699.00 from Apple. $6,699 minus $5,899 is $800.
  Source: https://www.apple.com/shop/buy-mac/macbook-pro/14-inch-space-black-standard-display-apple-m5-max-chip-18-core-cpu-40-core-gpu-128gb-memory-2tb-storage

## Cloud plans and the break even

- Claude Pro is $20 a month and Claude Max 20x is $200 a month in the US.
  Source: https://claude.com/pricing
- Our arithmetic: $5,899 / $20 = 295 months = 24.6 years; $5,899 / $200 = 29.5 months. Electricity is not included.

## Caveats

- No figure here is a Surface Laptop Ultra inference result: none had been published on the day checked.
- The DGX Spark, Ryzen AI Max+ 395 and M5 Max figures come from different sources and test settings; they are context, not a controlled head to head test.
- The "around 10.7 tokens per second" dense Qwen3 32B figure in the narration was not found in a primary source; the nearest published figures are about 10.5 (vLLM, NVFP4) and 9.46 (Ollama).
{% endraw %}

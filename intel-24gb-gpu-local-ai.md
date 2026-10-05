---
layout: default
title: "Intel's $799 24GB GPU Takes On The Used RTX 3090"
permalink: /intel-24gb-gpu-local-ai/
date: 2026-10-05
---

# Intel's $799 24GB GPU Takes On The Used RTX 3090

{% raw %}
Every figure the video states or shows, with where it comes from. Pages were read on 5 October 2026.

## Intel Arc Pro B60 (Sparkle)

- SPARKLE announced the Arc Pro B60 24GB series launch on January 12, 2026. The 24GB Blower Edition lists an MSRP of USD $799, available at launch through retail partners including Micro Center and Newegg. Passive 24GB and Passive 48GB versions are listed for system integrators, industrial, server and enterprise projects.
  https://www.sparkle.com.tw/en/sparkle-news/view/93E0b95ea8A0
- Intel's specification page for the Arc Pro B60: 24 GB GDDR6, 192 bit interface, 456 GB/s graphics memory bandwidth, 19 Gbps memory speed, total board power 200 W, oneAPI and OpenVINO support.
  https://www.intel.com/content/www/us/en/products/sku/243916/intel-arc-pro-b60-graphics/specifications.html
- SPARKLE's product sheet for the SBP60DW-48G, the Arc Pro B60 Dual: 24 + 24 GB of GDDR6, 456 + 456 GB/s, two GPUs on one board, Linux multi GPU LLM support, 440 W total board power.
  https://www.sparkle.com.tw/files/20260414160508432.pdf
- SPARKLE's warranty policy covers brand new SPARKLE graphics cards bought through authorised distributors and sellers, for the original owner, with terms handled by the local distributor or seller.
  https://www.sparkle.com.tw/en/warranty

## NVIDIA GeForce RTX 3090

- NVIDIA's GeForce RTX 30 Series comparison: RTX 3090 with 24 GB GDDR6X on a 384 bit interface, graphics card power 350 W (Founders Edition / reference design).
  https://www.nvidia.com/en-us/geforce/graphics-cards/compare/
- Memory bandwidth 936 GB/s, as listed on aiindigo's RTX 3090 page (19.5 Gbps GDDR6X on a 384 bit bus).
  https://aiindigo.com/hardware/nvidia-rtx-3090-24gb
- Used price: about $1,199 on eBay on 1 October 2026 (bestvaluegpu data, shown on aiindigo's page, "price as of Oct 1, 2026"), 27% above a 12 month average of about $946. The same page cites runaihome averages of about $1,250 to $1,265 in August 2026. Launch MSRP was $1,499.
  https://aiindigo.com/hardware/nvidia-rtx-3090-24gb

## Published generation speeds

- RTX 3090: 161.89 ± 0.18 tokens per second generation (tg128) on Llama 2 7B Q4_0 with flash attention, and 158.16 without it, on llama.cpp's CUDA scoreboard.
  https://github.com/ggml-org/llama.cpp/discussions/15013
- Intel: in the r/IntelArc thread "Arc Pro B60 first tests/impressions", a commenter reports "13 tokens per second on vulkan vs 40 tokens per second on sycl on qwen2.5-coder 14b on llama.cpp". The commenter describes this on the Arc B580, which they note is the same chip as the B60 (same 456 GB/s bandwidth). The thread's own B60 owner reports GPT-OSS 20B at 60+ tokens per second and Granite 4H Small 32B at 25 to 30.
  https://www.reddit.com/r/IntelArc/comments/1oqnc68/arc_pro_b60_first_testsimpressions/

The two speeds are different models, quantizations and builds, so they are not a controlled comparison.

## Software paths for Intel GPUs

- llama.cpp lists SYCL (Intel GPU), Vulkan (GPU) and OpenVINO (in progress, Intel CPUs, GPUs and NPUs) among its supported backends; CUDA targets NVIDIA GPUs.
  https://github.com/ggml-org/llama.cpp
  https://github.com/ggml-org/llama.cpp/blob/master/docs/backend/SYCL.md
  https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md
  https://github.com/ggml-org/llama.cpp/blob/master/docs/backend/OPENVINO.md
- IPEX-LLM, Intel's LLM acceleration library for Intel GPUs, was archived by its owner on 28 January 2026; its README states Intel no longer provides development or support for it.
  https://github.com/intel/ipex-llm

## Model fit on 24 GB

- aiindigo's fit table for a 24 GB card at Q4_K_M: 7B/8B fits, 14B fits, 32B is tight, 70B does not fit; 32B at Q4 fits with limited context.
  https://aiindigo.com/hardware/nvidia-rtx-3090-24gb

## Arithmetic used on screen

- $799 ÷ 24 GB = $33.29 per GB; $1,199 ÷ 24 GB = $49.96 per GB.
- $799 ÷ 40 tokens per second = $19.98 per token per second; $1,199 ÷ 162 = $7.40.
- 350 W − 200 W = 150 W. 150 W × 8 h × 365 days = 438 kWh, × $0.15 = $65.70 a year. Around the clock: 1,314 kWh, × $0.15 = $197.10. Rated board power, not a wall measurement.
- Two B60 cards at MSRP: 2 × $799 = $1,598. Two used RTX 3090s at about $1,199: $2,398, with 700 W of rated board power.
- $1,200 − $799 = $401, 50% above the B60's list price.

## Not checked

- An early $600 price for the B60 repeated in some reports; SPARKLE's announcement gives $799.
- A September monthly low of about $1,337 for the used RTX 3090 and an average near $1,300 from other trackers: bestvaluegpu's history page could not be read.
- A two year warranty term in one regional distributor's listing.
- The B60 speed attributed in the narration to "a B60 owner" running Qwen2.5 Coder 14B at Q4_K_M: the published comment reports it on a B580 and does not name the quantization.
{% endraw %}

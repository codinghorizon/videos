---
layout: default
title: "Four V100s Nearly Matched The RTX 5090. Here Is Why"
permalink: /tesla-v100-local-ai/
date: 2026-10-14
---

# Four V100s Nearly Matched The RTX 5090. Here Is Why

{% raw %}
Every figure the video shows or says, with where it came from. Prices were checked on 14 October 2026.
The used prices are completed eBay sales on the date given, and the new price is a live Newegg listing.
All of them move, so check the live market before buying.

## The benchmark

| Figure | Source |
|---|---|
| Four V100 SXM2 16GB modules vs one RTX 5090 | [r/LocalLLaMA: "NVFP4 on VOLTA!..."](https://www.reddit.com/r/LocalLLaMA/comments/1vsq3zg/nvfp4_on_volta_despite_being_built_for_blackwell/) ("4× V100-SXM2-16GB vs 1× RTX 5090"); [v100-skinny README](https://github.com/dnv2003/v100-skinny) ("four Tesla V100-SXM2-16GB") |
| Decode 219.1 tok/s (V100s) vs 214.7 tok/s (RTX 5090), Qwen3.8 27B | Reddit thread and README ("Decode throughput 219.1 ± 5.9 tok/s 214.7 ± 9.2 tok/s") |
| Same task, both correct, ranges overlap | Reddit thread ("AIME 2026 problem 1, five seeds"; "Correct answers 5/5 5/5"; "The intervals overlap.") |
| The 5090 reached the answer sooner: 6.56 s vs 6.90 s | Reddit thread ("Time to correct answer 6.90 ± 0.30 s 6.56 ± 1.34 s") |
| Same base model, different quantized files | Reddit thread ("same base model / different published quantized artifacts") |
| Tensor parallelism, custom QPN kernels, multi token prediction | Reddit thread ("four-GPU tensor parallelism… native MTP"; "QPN, the kernel I wrote") |
| V100 has no FP8 or FP4 Tensor Core instructions; weights translated for Volta | Reddit thread ("The V100 has no FP4 Tensor Core instruction and no FP8 Tensor Core instruction"; "translates each tiny fragment directly into the FP16 register format Volta's existing Tensor Cores can consume") |
| V100 Skinny: custom Qwen serving software for SM70 | [v100-skinny README](https://github.com/dnv2003/v100-skinny) ("OpenAI-compatible serving"; "vLLM -> 1Cat-vLLM (SM70) -> v100-skinny"; "Requires 4× SM70 GPUs, CUDA 12.8+") |
| PCIe reproduction: four V100 PCIe 32GB, no NVLink, 178.9 tok/s, about 18% below | Same Reddit thread, a reply ("4× Tesla V100 PCIe 32GB, TP4"; "No NVLink"; "Decode tok/s 178.9 ± 3.3"); 178.9 / 219.1 = 18.3% lower (our arithmetic) |
| About 76 tok/s at ~65K context at a shorter prediction depth | Reddit thread ("At ~65K live context, k=3 is currently the right V100 profile: 76.3 tok/s vs 65.5 with MTP off and 54.7 at k=7") |

## Hardware

| Figure | Source |
|---|---|
| V100: 900 GB/s; 300 W (SXM2), 250 W (PCIe) | [NVIDIA V100 page](https://www.nvidia.com/en-gb/data-center/tesla-v100/) ("900 GB/s"; "Max Consumption 300 WATTS 250 WATTS") |
| Four V100s: about 1,200 W; 3,600 GB/s on paper | Our arithmetic: 4 × 300 W; 4 × 900 GB/s |
| RTX 5090: 1,792 GB/s; the four-card total is about 2× on paper | [NVIDIA RTX 5090 page](https://www.nvidia.com/en-gb/geforce/graphics-cards/50-series/rtx-5090/) ("Memory Bandwidth 1792 GB/sec"); 3,600 / 1,792 = 2.0 (our arithmetic) |
| V100 launched in 2017, about nine years old | Reddit thread ("four 2017 V100s") |
| Tesla P40: 24 GB, 346 GB/s, 250 W, INT8 inference (47 TOPS INT8) | [NVIDIA Tesla P40 data sheet](https://www.nvidia.com/content/dam/en-zz/Solutions/Data-Center/tesla-product-literature/184427-Tesla-P40-Datasheet-NV-Final-Letter-Web.pdf) |

## Software support

| Claim | Source |
|---|---|
| CUDA 13 removes offline compilation and library support for Maxwell, Pascal and Volta; CUDA 12.x still builds for them | [CUDA 13.0 release notes](https://docs.nvidia.com/cuda/archive/13.0.3/cuda-toolkit-release-notes/index.html) ("Offline compilation and library support for these architectures have been removed in CUDA Toolkit 13.0 major version release. The use of CUDA Toolkits through the 12.x series to build applications for these architectures will continue to be supported") |
| Mainline vLLM needs compute capability 7.5 or higher (Volta is 7.0) | [vLLM GPU installation](https://docs.vllm.ai/en/latest/getting_started/installation/gpu.html) ("GPU: compute capability 7.5 or higher") |
| A V100 llama.cpp fork with its own builds and benchmarks | [llama.cpp-v100](https://github.com/1115714829/llama.cpp-v100) ("llama.cpp optimized for NVIDIA Tesla V100 (Volta, SM70)") |

## Other speeds

| Figure | Source |
|---|---|
| P40: 427 tok/s reading new prompt text with 32K tokens already in context (965 tok/s at short context) | [p40-long-context-bench report](https://github.com/kennel-org/p40-long-context-bench/blob/main/reports/2026-07-02_p40_llamacpp_qwen_longctx.md) (32768 row: 427.15 prefill, 37.52 decode; 512 row: 964.54); model Qwen3.6 35B A3B, Q4_K_M, llama.cpp |
| RTX 3090: about 40 tok/s on Qwen3.8 27B | [HardwareCorner Qwen3.8 27B tests](https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/) (4k context: 40.31 tok/s generation; Q4_K_S, llama.cpp) |
| RTX 5060 Ti 16GB: about 41 tok/s on Qwen3 14B at short context | [HardwareCorner RTX 5060 Ti 16GB benchmarks](https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-5060-ti-16gb/) (Qwen3 14B Q4_K: 41.1 at the shortest context, 25.9 at 32k) |

## Prices (14 October 2026)

| Figure | What it is | Source |
|---|---|---|
| $242.50, $289.99, $299.99 | Tesla P40 24GB, eBay sales on Sep 5, Sep 22 and Sep 12 | [1](https://www.ebay.com/itm/168648994843), [2](https://www.ebay.com/itm/117426242870), [3](https://www.ebay.com/itm/336786905447) |
| $10 to $12 per GB | P40 sales ÷ 24 GB | Our arithmetic |
| $218.50 | V100 16GB PCIe with cooler shroud, sold Sep 23 ($14/GB) | [eBay](https://www.ebay.com/itm/407222271561) |
| $659.95 | V100 32GB PCIe (HP PG500-216), sold Sep 15 ($21/GB) | [eBay](https://www.ebay.com/itm/168689170866) |
| $645 | V100 32GB SXM2 module, sold Sep 13 | [eBay](https://www.ebay.com/itm/188686477534) |
| $159.99 | V100 16GB SXM2 module, no heatsink, sold Sep 7; four = $640 | [eBay](https://www.ebay.com/itm/227487616362) |
| $1,599 | RTX 3090 Founders Edition, sold Oct 6 ($67/GB) | [eBay](https://www.ebay.com/itm/377547336000) |
| $799.99 | MSI RTX 5060 Ti 16GB Gaming Trio OC, new, sold by Newegg, Oct 14 ($50/GB) | [Newegg](https://www.newegg.com/p/N82E16814137954) |

### Not checked
- The exact board the benchmark's four SXM2 modules sat on: the thread does not name it. SXM2 modules need an SXM2 carrier or
  server board; the PCIe reproduction is the one the thread says ran without NVLink.
- The two systems ran different quantized files of the same base model, so this is a system comparison, not a same-weights test.
{% endraw %}

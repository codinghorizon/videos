---
layout: default
title: "The $13,999 DGX Spark Pair Reads 3x Faster Than A Mac"
permalink: /m5-ultra-mac-studio-two-dgx-sparks-real-price/
date: 2026-10-13
---

# The $13,999 DGX Spark Pair Reads 3x Faster Than A Mac

{% raw %}
Every figure the video shows or says, with where it came from. Prices were checked on 13 October 2026
and move often; check the live listing before buying.

## Prices

| Figure | What it is | Source |
|---|---|---|
| $5,499 | Cheapest M5 Ultra Mac Studio: 30-core CPU, 64-core GPU, 96GB memory, 1TB SSD | [Apple store](https://www.apple.com/shop/buy-mac/mac-studio) ("M5 Ultra ... Buy from $5499"); configuration from [Tom's Hardware's review](https://www.tomshardware.com/desktops/mini-pcs/apple-mac-studio-m5-ultra-review) |
| $12,299 | Full M5 Ultra (36-core CPU, 80-core GPU), 256GB, 4TB, as tested | [Tom's Hardware review](https://www.tomshardware.com/desktops/mini-pcs/apple-mac-studio-m5-ultra-review) ("Price as Configured $12,299.00") |
| +$4,000 | Moving from 96GB to 256GB | Tom's Hardware review ("Moving from 96GB of RAM to 256GB adds $4,000") |
| $10,799 | The tested machine with a 1TB SSD instead of 4TB | Our arithmetic: $12,299 minus the review's "$1,500 increase" for the 4TB SSD |
| 512GB, late October | Apple's 512GB option for M5 Ultra | Apple store ("512GB memory option for M5 Ultra coming late October") |
| $6,950 | NVIDIA DGX Spark, 128GB, 4TB, Founders Edition; listed Out of Stock | [NVIDIA marketplace](https://marketplace.nvidia.com/en-us/enterprise/personal-ai-supercomputers/); the increase reported by [ServeTheHome](https://www.servethehome.com/nvidia-dgx-spark-64gb-launched-and-big-128gb-gb10-price-increases/) (3 Oct 2026, from $3,999 at launch) and [The Register](https://www.theregister.com/systems/2026/10/02/nvidia-debuts-4999-dgx-spark-with-half-the-ram-and-storage-amid-memory-crunch/5300622) |
| $99 | NVIDIA "QSFP Cable 0.4m for DGX Spark"; listed Out of Stock | NVIDIA marketplace |
| $13,999 | Two Sparks and the cable | Our arithmetic: 2 x $6,950 + $99 |
| $3,200 | How much cheaper the 256GB, 1TB Mac is than the pair | Our arithmetic: $13,999 - $10,799 |
| two-unit bundle | "NVIDIA DGX Spark Bundle - 2 Units ... 1 connecting cable ... Contact Us" | NVIDIA marketplace |
| from $5,999 | Partner GB10 boxes with 128GB (ASUS Ascent GX10 1TB $5,999; MSI EdgeXpert $6,499.99; ASUS GX10 4TB $7,999), all Out of Stock | NVIDIA marketplace |
| $3,499.99 | GMKtec EVO-X2 (Ryzen AI Max+ 395), 128GB RAM, 1TB SSD; in stock (the 64GB version is $2,199.99) | [GMKtec store](https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc) |

## Hardware

| Figure | Source |
|---|---|
| DGX Spark: 128GB LPDDR5x, 273 GB/s | [NVIDIA DGX Spark hardware guide](https://docs.nvidia.com/dgx/dgx-spark/hardware.html) ("273 GB/s bandwidth"); [product page](https://www.nvidia.com/en-us/products/workstations/dgx-spark/) |
| 240 W external power supply; GB10 TDP 140 W | NVIDIA hardware guide ("240W external power supply (included)", "GB10 SOC Thermal Design Power (TDP) is 140W") |
| ConnectX-7, up to 200 Gb/s, two QSFP ports, pairs cluster directly | [Tom's Hardware DGX Spark review](https://www.tomshardware.com/pc-components/gpus/nvidia-dgx-spark-review) ("two QSFP ports for the onboard ConnectX 7 NIC running at up to 200 Gbps") |
| Up to four Sparks clustered | NVIDIA product page ("connection of up to four NVIDIA DGX Spark systems") |
| 29 dB operating, 13 dB idle (declared A-weighted sound pressure, operator position) | [NVIDIA DGX Spark support](https://www.nvidia.com/en-us/support/dgx-spark/) |
| M5 Ultra: 1.2 TB/s memory bandwidth | Tom's Hardware M5 Ultra review ("boosted the chip's memory bandwidth to 1.2 TB/s") |
| Mac Studio M5 Ultra: 480 W maximum continuous power | Tom's Hardware M5 Ultra review, specifications table |
| Strix Halo (Ryzen AI Max): 256 GB/s | [Framework](https://frame.work/blog/introducing-the-framework-desktop) ("the massive 256GB/s memory bandwidth that Ryzen AI Max delivers") |

## Our arithmetic

- 1.2 TB/s / 273 GB/s = 4.4.
- Two Sparks: 2 x 273 = 546 GB/s, theoretical, only if both are busy with work that splits cleanly.
- 2 x 128GB = 256GB of physical memory, in two separate pools.

## Measured speeds

| Figure | Source |
|---|---|
| Two Sparks (vLLM, tensor parallel) read a 32K-token codebase in ~17 s; the M5 Ultra took ~50 s (DeepSeek V4 Flash) | [Matched test of an M5 Ultra 256GB against two DGX Sparks](https://youtu.be/_yrw6c5gw3E) |
| Writing: DeepSeek V4 Flash ~38 tok/s on both; Qwen 3.8 Flash 45 tok/s on the Mac, 38 on the Sparks | Same test |
| Cached follow-up at 16K context: ~3 s on the Mac, ~1.4 s on the Sparks | Same test |
| One Spark against the M5 Ultra on Qwen 3.8 27B (Q4_K_M): the Mac's prompt processing is ahead, generation almost four times higher | Tom's Hardware M5 Ultra review ("prompt processing speeds are even faster than Nvidia's DGX Spark's ... almost four times higher than the DGX Spark across the board") |
| The Spark's higher raw compute makes it much faster than Strix Halo at prompt processing | Tom's Hardware DGX Spark review, performance page |
| Reading a prompt (prefill) is compute-bound; writing tokens (decode) is memory-bandwidth-bound | Tom's Hardware DGX Spark review; the matched test above |

### Not checked

- No energy-per-token measurement exists for either machine; the power figures are supply ratings and ceilings.
- The two-Spark cluster has one public matched test (above); one model setup, one runtime per machine.
- "Widely reported sold out" reflects NVIDIA's own store and partner listings on 13 October 2026; retailer stock varies by region.
- Resale values are not predicted.
{% endraw %}

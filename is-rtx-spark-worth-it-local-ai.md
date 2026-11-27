---
layout: default
title: "Is The $2,599 RTX Spark Worth It For Local AI?"
permalink: /is-rtx-spark-worth-it-local-ai/
date: 2026-11-27
---

# Is The $2,599 RTX Spark Worth It For Local AI?

{% raw %}
Every figure the video quotes, and where it comes from. Prices were read live on 27 November 2026
(the full price table, with each listing's exact configuration, is in PRICES.md and on the
channel's hardware prices page).

## How much memory the GPU gets

- **NVIDIA RTX Spark porting guide, unified memory (UMA).** The rule for how much of the shared
  memory the graphics side can use: capacity minus 16 GB, clamped to between 50% and 80% of
  capacity. That gives 12 GB on the 24 GB model, 16 GB on 32 GB, 32 GB on 48 GB, 48 GB on 64 GB and
  102.4 GB on 128 GB.
  https://docs.nvidia.com/rtx-spark/rtx-spark-porting-guide/latest/uma/index.html
- **NVIDIA RTX Spark porting guide, overview.** Chip specs: 20 core Grace CPU, 6,144 core
  Blackwell RTX GPU on the top chip (5,120 on the lower one), 45 to 80 W, unified memory.
  https://docs.nvidia.com/rtx-spark/rtx-spark-porting-guide/latest/overview.html

## Speed

- **StorageReview, Microsoft Surface Laptop Ultra for Business review (RTX Spark N1X, 128 GB).**
  Local model token speeds on the 128 GB machine: Qwen3.6-35B-A3B at 89.2 tok/s (64K context, from
  the article's chart; the headline rounds it to 89), gpt-oss at 58.0 tok/s (64K) and 59.2 tok/s
  (128K). Memory bandwidth 300 GB/s (LPDDR5X-9400). Comparison specs: DGX Spark 273 GB/s, 140 W.
  https://www.storagereview.com/review/microsoft-surface-laptop-ultra-for-business-review-rtx-spark-n1x
- **Artificial Analysis, NVIDIA RTX Spark local agent performance.** Agent workload results on the
  RTX Spark.
  https://artificialanalysis.ai/articles/nvidia-rtx-spark-agentperf-local
- **Gaming laptop memory bandwidth (896 GB/s)** for the RTX 5080 / 5090 laptop GPUs compared on
  screen: NVIDIA's GeForce RTX 50 Series laptops spec table.
  https://www.nvidia.com/en-us/geforce/laptops/50-series/

## Reviews and launch coverage

- **Notebookcheck: Microsoft Surface Laptop Ultra debuts with RTX Spark, 128 GB unified memory and
  $2,599 starting price.**
  https://www.notebookcheck.net/Microsoft-Surface-Laptop-Ultra-debuts-with-RTX-Spark-128-GB-unified-memory-and-2-599-starting-price.1418420.0.html
- **Tom's Hardware: Microsoft Surface Laptop Ultra (RTX Spark) review.**
  https://www.tomshardware.com/tablets/microsoft-surface/microsoft-surface-laptop-ultra-rtx-spark-review
- **The New Stack: Surface Laptop Ultra and local AI.**
  https://thenewstack.io/surface-ultra-local-ai

## Prices (checked 27 November 2026)

- **Microsoft Store, Surface Laptop Ultra configurator.** $2,599.99 (24 GB), $3,299.99 (32 GB),
  $3,699.99 (6,144 core, 32 GB), $3,999.99 (48 GB), $4,299.99 (64 GB), $5,899.99 (128 GB).
  https://www.microsoft.com/en-us/store/configure/surface-laptop-ultra/8wg5vqp0x4b8
- **Newegg, MSI Vector 16 RTX 5080 (marketplace seller).** $2,699.00.
  https://www.newegg.com/msi-vector-16-0-wqxga-intel-core-ultra-9-275hx-nvidia-geforce-rtx-5080-16gb-ddr5-memory-1tb-ssd-grey/p/1TS-0016-05FW8
- **Newegg, HP HyperX Omen MAX 16 RTX 5090 (marketplace seller, cheapest RTX 5090 laptop by
  price).** $3,919.00.
  https://www.newegg.com/hp-hyperx-omen-16-0-wqxga-intel-core-ultra-9-290hx-plus-nvidia-geforce-rtx-5090-16gb-ddr5-memory-512gb-ssd-black/p/1TS-000D-1TCR0
- **NVIDIA Marketplace, DGX Spark.** $6,950.00.
  https://marketplace.nvidia.com/en-us/enterprise/personal-ai-supercomputers/
- **GMKtec, EVO-X2 128 GB / 1 TB.** $3,499.99 on sale, $3,999.99 regular.
  https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc?variant=48746069262490
- **Sifty, Lenovo Legion Pro 7i Gen 10 (sponsored segment).** Two sellers: Best Buy $4,079.00 and
  Lenovo $5,454.99, nearly $1,400 apart.
  https://www.sifty.com/p/Legion-Pro-7i-16IAX10H-16-Gen-10/068422f0-fd39-70b3-8000-45727e09f42b
- **OpenAI, ChatGPT pricing.** The $20 a month and $200 a month plan tiers.
  https://openai.com/chatgpt/pricing/

## Derived figures

About $217 per GPU gigabyte on the base model (2,599.99 / 12); about $58 per GPU gigabyte on the
128 GB model (5,899.99 / 102.4); $169 per GB on the MSI RTX 5080 (2,699 / 16); $1,600 between the
64 GB and 128 GB Surface; about $1,050 between the 128 GB Surface and the DGX Spark; $2,400 between
the 128 GB Surface and the EVO-X2 on sale.

## Speeding models up

- **Strata** (free, open source) for running and speeding up local models.
  https://github.com/Niko1221/Strata/releases
{% endraw %}

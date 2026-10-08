---
layout: default
title: "Your Local AI Lab Costs More Than The GPU (Three Builds)"
permalink: /home-local-ai-lab-full-cost/
date: 2026-10-08
---

# Your Local AI Lab Costs More Than The GPU (Three Builds)

{% raw %}
Every figure the video says or shows, with the source it comes from. Prices were checked on
7 October 2026 unless a source states its own date. Prices are US, before tax.

## The parts and their prices

- **RTX 5060 Ti 16GB, $799.99.** MSI Ventus 2X 16G OC Plus, sold and shipped by Newegg.
  https://www.newegg.com/p/N82E16814137958
- **GIGABYTE AI TOP ATOM (NVIDIA GB10), $7,999.99,** 128GB LPDDR5X unified memory and a 4TB
  PCIe 5.0 NVMe SSD, sold by Newegg.
  https://www.newegg.com/p/N82E16859252047
- **CyberPower CP1500PFCLCD, $239.95,** 1500VA / 1000W, PFC sine wave. Newegg and Best Buy list
  it at $239.95; CyberPower's specification gives 1500VA / 1000W.
  https://www.newegg.com/cyberpower-cp1500pfclcd-nema-5-15r/p/N82E16842102134
  https://www.bestbuy.com/product/cyberpower-pfc-sinewave-series-1500va-battery-back-up-system-black/JX8P9297PT
- **APC Back-UPS 650VA / 360W, about $80.** Best Buy, $79.99 in the script writer's capture of
  7 October 2026 (see Not checked).
- **TP-Link TL-SG108 8 port gigabit switch, $19.99,** sold by Newegg.
  https://www.newegg.com/p/N82E16833704173
- **A 2TB NVMe SSD for about $250.** HUADISK 2TB PCIe 4.0 (7,100MB/s) at $259.99 and its
  5,000MB/s version at $229.99 on Newegg; the Crucial P310 2TB was $308.99 there the same day.
  https://www.newegg.com/HUADISK-2TB-NVMe-1-4/p/0D9-0118-00006
- **A 4TB NVMe SSD for about $456.** The cheapest name-brand 4TB NVMe on Newegg was the Team
  Group T-Force G50 EVO 4TB at $455.99. (The supplied script said $326 from a 2 October deal;
  corrected before recording.)
  https://www.newegg.com/team-group-4tb-t-force-nvme/p/N82E16820985406
- **A network cable, about $10.** Not tied to one listing.
- **The $500 and $2,000 hosts** are the channel's reference build budgets, not listings.
  https://codinghorizon.dev/best-local-ai-machine-under-500/
  https://codinghorizon.dev/best-local-ai-machine-2000/

## The totals (arithmetic)

- Starter: $500 + $800 + $80 + $30 = **$1,410**. Without the host: **$910**.
- Serious: $2,000 + $250 + $240 + $30 = **$2,520**.
- No compromise: $8,000 + $240 + $30 = **$8,270** (the GB10 already has its 4TB drive).

## The software

- **Ollama serves models to other machines on the network.**
  https://docs.ollama.com/faq#how-can-i-expose-ollama-on-my-network
- **Open WebUI connects to Ollama.**
  https://docs.openwebui.com/getting-started/quick-start/connect-a-provider/starting-with-ollama/
- **Tailscale Serve shares a local service with devices on your tailnet** ("Available within
  your tailnet" is the line it prints).
  https://tailscale.com/docs/features/tailscale-serve

## Model sizes

- **Qwen 3.5 122B, about 70 GB quantized.** Unsloth's Q4_K_S GGUF is 71.7 GB (Ollama's default
  qwen3.5:122b tag is 81 GB).
  https://huggingface.co/unsloth/Qwen3.5-122B-A10B-GGUF
  https://ollama.com/library/qwen3.5/tags
- **Qwen 3 235B at 4 bit, 142 GB.** Ollama's qwen3:235b tag.
  https://ollama.com/library/qwen3/tags
- 3 × 142 = 426 GB; 426 + 3 × 70 = 636 GB.

## Power

- **NVIDIA ratings: RTX 5060 Ti 180 W, RTX 5070 Ti 300 W, RTX 5080 360 W** (total graphics
  power). StorageReview: "The NVIDIA GeForce RTX 5080 has a listed peak power draw of 360W."
  https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5060-family/
  https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5070-family/
  https://www.nvidia.com/en-au/geforce/graphics-cards/50-series/rtx-5080/
- **584 W, an RTX 5080 system under an AI workload.** StorageReview: "the system power
  increased from 239W as the test was preparing to 584W when the GPU was put under load."
  https://www.storagereview.com/review/nvidia-geforce-rtx-5080-review-the-sweet-spot-for-ai-workloads
- **The tier estimates.** Loaded: card limit + a 100 W host allowance (180 + 100 = 280 W;
  300 + 100 = 400 W; the no compromise tier uses StorageReview's measured 584 W). Idle: 45 W and
  51 W from published GPU idle readings (ComputerBase) for the whole system; these are the
  script's estimates, not our measurements.
  https://www.computerbase.de/artikel/grafikkarten/nvidia-geforce-rtx-5060-ti-16-gb-test.92119/seite-8
  https://www.computerbase.de/artikel/grafikkarten/nvidia-geforce-rtx-5070-ti-test.91379/seite-9
- **500 W ≈ 1,700 BTU per hour.** 1 W = 3.412 BTU/h; 500 × 3.412 = 1,706.

## Electricity and the monthly bill

- **18.2 cents per kWh, US residential average forecast for 2026.** EIA Short-Term Energy
  Outlook, released 6 October 2026 (table "Electricity, Coal and Renewables").
  https://www.eia.gov/outlooks/steo/report/elec_coal_renew.php
- 30 day months at 18.2c/kWh:
  - 45 W all month: 45 × 720 h = 32.4 kWh = $5.90 (the script says about $5.80).
  - Starter, 20 h idle at 45 W + 4 h at 280 W: 60.6 kWh = **$11.03**.
  - Serious, 20 h at 51 W + 4 h at 400 W: 78.6 kWh = **$14.31**.
  - No compromise, 4 h at 584 W plus ~54 W idle: ~102 kWh = **$18.60**.
  - Eight loaded hours instead of four add about $5, $8 and $12.

## Against the cloud plans

- $20 a month = $240 a year; $200 a month = $2,400 a year (ChatGPT Plus / Pro and Claude
  Pro / Max price tiers).
- Starter: $20 − $11 = $9 saved a month; $1,410 / $9 = 157 months ≈ 13 years; $910 / $9 =
  101 months ≈ 8.5 years; an $800 GPU / $9 ≈ 89 months ≈ 7 years.
- Serious: $2,520 / ($200 − $14.30) = 13.6 months ≈ 14; the $2,000 host alone, 10.8 ≈ 11.
- GB10: $200 − $18.60 = $181.40 saved; $8,270 / 181.4 = 45.6 ≈ 46 months.

## Not checked

- The APC 650VA / 360W price: Best Buy's search page lazy-loads prices and could not be read
  headlessly on 7 October; $79.99 is the script writer's capture from the same day.
- The idle wattages (45 W, 51 W, ~54 W) are the script's estimates from published GPU idle
  readings, not measurements of these exact builds. The narration says the 100 W host
  allowance is part of the idle values; the arithmetic shows it belongs to the loaded values.
- The cable price ($10) is not tied to one listing.
{% endraw %}

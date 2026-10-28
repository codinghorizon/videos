---
layout: default
title: "Desktop vs Laptop vs Mini PC For Local AI (October 2026)"
permalink: /desktop-vs-laptop-vs-mini-pc-local-ai/
date: 2026-10-28
---

# Desktop vs Laptop vs Mini PC For Local AI (October 2026)

{% raw %}
Every price was read live on 28 October 2026 (US listings). Every speed is a published run by
someone else, never our own testing; tok/s means generation (decode) speed without speculative
decoding unless a line says otherwise. Bandwidth figures are the makers' specs.

## How the video measures each machine

- **Memory decides what fits; bandwidth decides how fast.** A model's weights are read once per
  generated token, so bandwidth divided by the model's size is a ceiling on tokens per second.
  Mac mini M6: 170 GB/s over a ~17 GB 4-bit Qwen 3.8 27B gives about 10 tok/s, and ComputerBase
  measured "knapp 10" (9.5).
- **The yardstick model** is Qwen 3.8 27B at 4-bit (about 17 GB). Smaller cards use Qwen3 14B 4-bit
  (about 9 GB).
- **Dollars per GB** = the machine's price divided by the memory a model can use (the graphics
  card's own memory on a tower or gaming laptop, the shared pool on a Mac or Strix Halo machine).
- **Electricity:** US average residential price **18.16 cents/kWh** (August 2026, EIA Electric
  Power Monthly Table 5.6.A). Running cost = watts x 4 hours a day x 365 / 1000 x $0.1816; the
  4 hours is our assumption and the watts are the rated board power, a maximum.
  https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_5_6_a

## $1,500

**Tower: ABS Cyclone Aqua, RTX 5060 Ti 16GB, $1,599.99 at Newegg.**
https://www.newegg.com/abs-cyclone-aqua-gaming-pc-geforce-rtx-5060-ti-intel-core-i7-14700f-16gb-1tb-ssd-c1a47n56t1-black/p/N82E16883360993
- 16 GB, 448 GB/s, 180 W (NVIDIA compare page). https://www.nvidia.com/en-us/geforce/graphics-cards/compare/
- Qwen3 14B Q4_K: **41.1 tok/s** at 4K context (Hardware Corner, llama.cpp CUDA).
  https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-5060-ti-16gb/
- Qwen 3.8 27B fits only at 3-bit: llamaperf median 28.8 tok/s. https://llamaperf.com/gpu/rtx-5060-ti-16gb
- $1,599.99 / 16 GB = **$100 per GB**.

**Laptop: MacBook Air 13" M5, 24GB, $1,499 at Apple.**
https://www.apple.com/shop/buy-mac/macbook-air/13-inch-midnight-m5-chip-10-core-cpu-10-core-gpu-24gb-memory-512gb-storage
- 153 GB/s (Apple specs). https://www.apple.com/macbook-air/specs/
- A user run on the M5 Air (32GB, same chip and bandwidth): Qwen3 30B-A3B 4-bit MLX, **57 tok/s**
  cold, settling to 44 on battery and 39 on mains after about 150 seconds. The Air has no fan.
  https://llamaperf.com/gpu/m5-32gb
- $1,499 / 24 GB = **$62 per GB**.

**Mini PC: Mac mini M6, 32GB, $1,499 at Apple.**
https://www.apple.com/shop/buy-mac/mac-mini/m6-chip-12-core-cpu-12-core-gpu-32gb-memory-512gb-storage
- 170 GB/s for the 24 and 32 GB M6 (Apple specs). https://www.apple.com/mac-mini/specs/
- ComputerBase, LM Studio: Qwen 3.8 27B 4-bit "knapp 10" tok/s (**9.5**), Qwen3 14B 4-bit
  "knapp 18" tok/s. https://www.computerbase.de/artikel/pc-systeme/apple-mac-mini-m6-test.99469/seite-2
- $1,499 / 32 GB = **$46.84 per GB**.
- Same 14B model: 41.1 on the tower against just under 18 on the mini, more than twice as fast.

**Skip: the 8 GB box.** The ABS RTX 5060 **8GB** desktop on the same Newegg search sells at
$1,499.99, $100 less than the 16 GB tower. https://www.newegg.com/p/pl?d=abs+cyclone+aqua+5060+ti+16gb&N=4131

## $2,500

**Tower: PRC PearlGlass, RTX 3090 24GB, $2,549.99 on Newegg Marketplace (Price Right Computers).**
https://www.newegg.com/p/3D5-000V-001F2
- The listing does not say whether the card is new or used.
- 24 GB, 936 GB/s (NVIDIA GA102 spec), 350 W (NVIDIA compare page).
- Hardware Corner: Qwen3 14B Q4_K 70.0, Qwen3 30B-A3B Q4_K **153.6** tok/s.
  https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-3090/
- llamaperf: Qwen 3.8 27B 4-bit median **38.4 tok/s**. https://llamaperf.com/gpu/rtx-3090
- $2,549.99 / 24 GB = **$106 per GB**; $2,549.99 / 38.4 tok/s = **$66 per tok/s**.

**Laptop: MSI Stealth A16 AI+, RTX 5080 Laptop GPU 16GB, $2,599.99 at Best Buy.**
https://www.bestbuy.com/product/msi-stealth-a16-ai-copilot-pc-16-240hz-qhd-oled-ultra-thin-gaming-laptop-amd-ryzen-ai-r9-365-32gb-rtx-5080-1tb-ssd-core-black/J3P7TXRSLL/sku/13015871
- 16 GB, 896 GB/s (NVIDIA laptop spec). https://www.nvidia.com/en-us/geforce/laptops/50-series/
- MSI rates the GPU at **105 W** in this model; the desktop RTX 5080 is 360 W.
  https://www.msi.com/Laptop/Stealth-A16-AI-Plus-A3XWX/Specification
- No published LLM run on the laptop RTX 5080 was found. The desktop RTX 5080 runs Qwen3 14B Q4_K
  at **80.6 tok/s** (Hardware Corner); the laptop has 93% of its bandwidth, so the video shows the
  laptop's speed as an **estimate**. https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-5080/
- Same 16 GB as the $1,599.99 tower for $1,000 more; $2,599.99 / 16 GB = **$162.50 per GB**.

**Mini PC: Mac mini M5 Pro, 48GB, $2,499 at Apple.**
https://www.apple.com/shop/buy-mac/mac-mini/m5-pro-chip-18-core-cpu-20-core-gpu-48gb-memory-512gb-storage
- 307 GB/s (Apple specs).
- A user run, llama.cpp Metal: Qwen 3.8 27B about **19 tok/s**. https://llamaperf.com/gpu/m5-pro-48gb
- $2,499 / 48 GB = **$52 per GB**, half what the tower charges; the 3090 tower is $50 more.

## $3,500

**Tower: a parts build around the PowerColor Radeon AI PRO R9700 32GB, $3,416.84 at Newegg.**
- R9700 $1,799.99: https://www.newegg.com/powercolor-ai-pro-r9700-32g-b-radeon-ai-pro-r9700-32gb-graphics-card/p/N82E16814131885
- Ryzen 7 9700X $339.00, Gigabyte B850 AI TOP $339.99, Patriot Viper Venom 32GB DDR5-6000
  **$459.99** (https://www.newegg.com/patriot-memory-viper-venom-32gb-2-x-16gb-ddr5-6000-pc5-48000-cas-latency-cl36-desktop-memory-matte-black/p/N82E16820225430),
  Thermalright Peerless Assassin 120 SE $47.90, Rosewill 1200 W $99.99, Crucial E100 2TB $249.99,
  Montech AIR 903 MAX $79.99.
- 32 GB, 640 GB/s, 300 W (Sapphire R9700 spec). https://www.sapphiretech.com/en/commercial/radeon-ai-pro-r9700
- llamaperf: Qwen 3.8 27B 4-bit median **29.8 tok/s**. https://llamaperf.com/gpu/radeon-ai-pro-r9700
- $3,416.84 / 29.8 = **$115 per tok/s**.

**Mini PC: GMKtec EVO-X2, Ryzen AI Max+ 395, 128GB, $3,499.99 at GMKtec (sale).**
https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc
- 256 GB/s (256-bit LPDDR5X-8000, AMD). Up to **96 GB** as graphics memory on Windows (AMD):
  https://www.amd.com/en/newsroom/press-releases/2025-1-6-amd-announces-expanded-consumer-and-commercial-ai-.html
- visorcraft, on this machine (llama.cpp Vulkan, 120 W): gpt-oss-120b **53.4 tok/s**, Llama 3.1 70B
  Q4_K_M **5.10 tok/s**, Qwen3 30B-A3B 86.07 tok/s.
  https://github.com/visorcraft/strix-halo-llm-perf/blob/main/BENCHMARKS.md
- Noise, Tom's Hardware: "the fans becoming audible across my living room while running our CPU
  benchmarks." https://www.tomshardware.com/desktops/mini-pcs/gmktec-evo-x2-ai-mini-pc-review
- $3,499.99 / 128 GB = **$27 per GB**.
- Electricity, 4 hours a day: EVO-X2 at 120 W about **$32 a year**; an RTX 3090 card alone at
  350 W about **$93 a year**; over three years the gap is about **$183**.

**Laptop: ASUS ROG Flow Z13 (GZ302EA-XS99), same chip, 128GB, $3,299.99 at Abt.**
https://www.abt.com/ASUS-ROG-Flow-Z13-2-in-1-Laptop-13-Inch-AMD-Ryzen-AI-Max-395-128GB-RAM-1TB-SSD-AMD-XDNA-NPU-in-Black-GZ302EAXS99/p/224545.html
- No published LLM run on the Z13 itself; it is the same chip as the EVO-X2 at a lower power limit
  (Notebookcheck: up to 93 W in Manual mode), so it is shown as at most the mini PC's speed.
  https://www.notebookcheck.net/Asus-ROG-Flow-Z13-GZ302EA-Convertible-Review-AMD-s-Strix-Halo-GPU-is-neck-and-neck-with-the-RTX-4070-Laptop.963266.0.html

**The Mac alternative: MacBook Pro 16" M5 Pro, 48GB/1TB, $3,599 at Apple.**
https://www.apple.com/shop/buy-mac/macbook-pro/16-inch-space-black-standard-display-apple-m5-pro-chip-18-core-cpu-20-core-gpu-48gb-memory-1tb-storage
- The same chip and memory as the $2,499 Mac mini, for $1,100 more.

## Laptop graphics names

- **RTX 5090 Laptop:** 24 GB, 896 GB/s; the desktop RTX 5090 is 32 GB and 1,792 GB/s.
  https://www.nvidia.com/en-us/geforce/laptops/50-series/ and https://www.nvidia.com/en-us/geforce/graphics-cards/compare/
- llamaperf: Qwen 3.8 27B 4-bit on the RTX 5090 Laptop, median **33.5 tok/s**, below the RTX 3090
  desktop's 38.4. https://llamaperf.com/gpu/rtx-5090-laptop-24gb
- Cheapest RTX 5090 laptop on Newegg that day: ASUS ROG Strix SCAR 16 at **$4,299**.
  https://www.newegg.com/p/pl?d=gaming+laptop+5090

## Not checked

- Whether the PRC PearlGlass RTX 3090 is new or used: the listing does not say.
- No published LLM run on the laptop RTX 5080 or on the Flow Z13; both are shown as estimates.
- The MacBook Air run is on the 32 GB Air (same chip and bandwidth), not the 24 GB model.
- Power figures are graphics-card or chip maximums; the rest of each system draws extra.
- The RTX 3090's 936 GB/s comes from NVIDIA's GA102 spec; TechPowerUp's page was blocked that day.
- Prices move every week; each is the listing on 28 October 2026.
{% endraw %}

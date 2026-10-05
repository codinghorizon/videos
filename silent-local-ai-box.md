---
layout: default
title: "Don't Buy a Loud GPU Tower for Local AI All Day"
permalink: /silent-local-ai-box/
date: 2026-10-05
---

# Don't Buy a Loud GPU Tower for Local AI All Day

{% raw %}
Every figure shown in the video, with where it comes from. Pages were read on 5 October 2026.

## Electricity arithmetic

All yearly costs use the published idle (or measured) draw, 8,760 hours a year and $0.16 per kilowatt hour.

| Draw | kWh a year | Cost a year |
| --- | --- | --- |
| 4 W (Mac mini M6, idle) | 35.0 | $5.61 |
| 6 W (Mac mini M5 Pro, idle) | 52.6 | $8.41 |
| 7 W (Mac Studio M5 Max, idle) | 61.3 | $9.81 |
| 9 W (Mac Studio M5 Ultra, idle) | 78.8 | $12.61 |
| 87 W (Acemagic M1A PRO+, Silent mode at the wall, under load) | 762 | $121.94 |
| 163 W (Acemagic M1A PRO+, Performance mode at the wall, under load) | 1,428 | $228.47 |
| 385 W (Mac Studio M5 Ultra, Apple's maximum) | 3,373 | $539.66 |

Dollars per token per second: $899 / 9.5 tokens per second = $94.6.

Weights at 4 bit, at roughly half a byte per parameter: 27B about 13.5 GB, 70B about 35 GB, 120B about 60 GB, before cache and runtime overhead.

## Mac mini (M6 and M5 Pro)

- **Apple, Mac mini power consumption and thermal output.** Mac mini (M6), M6 with 16 GB and 256 GB SSD: 4 W idle, 70 W maximum. Mac mini (M5 Pro), 64 GB and 8 TB: 6 W idle, 145 W maximum. https://support.apple.com/en-nz/103253
- **Apple, Mac mini (M6 or M5 Pro) tech specs.** M6: 16 GB unified memory, configurable to 24 GB or 32 GB (170 GB/s). M5 Pro: 307 GB/s memory bandwidth, configurable to 48 GB or 64 GB. The ECMA-109 acoustic table gives a sound pressure level at the operator position of 4 dB at idle (configuration tested: M5 Pro, 48 GB, 8 TB); the electrical summary line on the same page reads 5 dBA at idle. https://support.apple.com/en-us/128108
- **Apple Newsroom, 22 September 2026.** "Mac mini with M6 starts at $899, while Mac mini with M5 Pro is available at $1,699. Mac Studio with M5 Max starts at $2,499, while Mac Studio with M5 Ultra starts at $5,499." https://www.apple.com/newsroom/2026/09/the-new-mac-mini-and-mac-studio-are-available-today/
- **ComputerBase, Apple Mac mini M6 im Test, 21 to 23 September 2026.** Idle about 4 W at the wall; up to 60 W under maximum load. Under sustained full load (HandBrake) 35.7 dB(A) at 40 cm. Qwen3.8 27B (Q4_K_M, LM Studio 0.4.24): 9.5 tokens per second; Qwen3 14B (Q4_K_M): 17.8 tokens per second, on the 32 GB model. https://www.computerbase.de/artikel/pc-systeme/apple-mac-mini-m6-test.99469/

## Mac Studio (M5 Max and M5 Ultra)

- **Apple, Mac Studio power consumption.** M5 Max (36 GB): 7 W idle, 200 W maximum. M5 Ultra (512 GB): 9 W idle, 385 W maximum. https://support.apple.com/en-au/102027
- **Apple, Mac Studio (M5 Max or M5 Ultra) tech specs.** M5 Max: 36 GB, configurable to 48, 64 or 128 GB. M5 Ultra: 96 GB, configurable to 256 GB or 512 GB. ECMA-109 table: 7 dB at the operator position at idle (configuration tested: M5 Ultra, 96 GB). https://support.apple.com/en-euro/128107
- **Apple Store.** 512 GB memory option for M5 Ultra "coming late October". https://www.apple.com/shop/buy-mac/mac-studio
- **COMPUTER BILD, Apple Mac Studio 2026 M5 Max: Test des Desktop-PC, 24 September 2026.** 21 W in normal operation, 182 W at full load; 0.1 sone in normal operation, 1.0 sone at full load. https://www.computerbild.de/artikel/Tests-PC-Hardware-Apple-Mac-Studio-2026-M5-Max-Test-des-Desktop-PC-3bc9c91-41239213.html
- **Tom's Hardware, Apple Mac Studio (M5 Ultra) review, 21 September 2026.** Tested with Qwen 3.8-27B-Q4_K_M in llama.cpp; tokens per second "double that of the M4 Max and almost four times higher than the DGX Spark across the board"; "The system stayed largely quiet (though the fan can make itself known)". The cheapest M5 Ultra is $5,499 with 96 GB; the 36-core version adds $1,300; moving from 96 GB to 256 GB adds $4,000. 512 GB configuration "coming in late October". https://www.tomshardware.com/desktops/mini-pcs/apple-mac-studio-m5-ultra-review

## Strix Halo

- **Framework Desktop.** Recommended models measured on Framework Desktop: Ryzen AI Max+ 395 with 64 GB runs Qwen3.5-122B-A10B at Q3_K_S using 52.5 GB; Ryzen AI Max+ 395 with 128 GB runs DeepSeek V4 Flash 0731 at UD-IQ2_XXS using 90.9 GB. https://frame.work/desktop
- **Framework Desktop DIY configurator.** Max+ 395 with 128 GB listed at 3,449 (the configurator served in GBP from this location) and marked out of stock. https://frame.work/products/desktop-diy-amd-aimax300/configuration/new
- **ServeTheHome, Acemagic M1A PRO+ review.** In the 140 W Performance mode the system drew 163 W at the wall with a GPT-OSS model on the GPU, a CPU stress test and a roughly 10 W portable monitor; Silent mode brought that to 87 W. About 43 dBA in Performance mode and 36 to 38 dBA in Silent mode, against a 34 dBA lab noise floor. https://www.servethehome.com/acemagic-m1a-pro-review-an-amd-powered-128gb-ai-mini-pc/4/
- **PC Watch, Minisforum MS-S1 MAX.** Noise at 50 cm: Quiet mode 32 dB idle and 41.6 dB at full load; Performance mode 37 dB idle and 48 dB at full load. https://pc.watch.impress.co.jp/docs/column/hothot/2050899.html

## RTX 5090

- **NVIDIA, GeForce RTX 5090.** 32 GB of GDDR7. https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/
- **GamersNexus, RTX 5090 Founders Edition review.** A two slot cooler "capable of handling 575W or more"; about 32.5 dBA at 1 m on the passive test bench. https://gamersnexus.net/gpus/nvidia-geforce-rtx-5090-founders-edition-review-benchmarks-gaming-thermals-power

## Not checked, or stated differently by the source

- The opening's "ninety billion parameter model" is, in Framework's own table, a 90.9 GB DeepSeek V4 Flash at about 2 bit; the table gives memory used, not a parameter count.
- The 21 W, 182 W and sone figures for the M5 Max Mac Studio are from COMPUTER BILD, not ComputerBase.
- Tom's Hardware prices 256 GB on the M5 Ultra at $4,000 over the $5,499 base; $6,799 is the price of the 36-core M5 Ultra at 96 GB.
- "Ninety one gigabytes for a roughly hundred twenty B mixture of experts": Framework's 90.9 GB row is DeepSeek V4 Flash; its roughly 120B mixture of experts row (Qwen3.5-122B-A10B) uses 52.5 GB.
- Apple's acoustic figures (4 dB and 7 dB) come from the configurations Apple tested (M5 Pro 48 GB; M5 Ultra 96 GB), not every model.
- The Framework 128 GB price was read in GBP; the US dollar price was not re-checked.
{% endraw %}

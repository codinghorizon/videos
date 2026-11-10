---
layout: default
title: "External GPU vs Desktop Tower For Local AI"
permalink: /external-gpu-vs-desktop-tower-local-ai/
date: 2026-11-10
---

# External GPU vs Desktop Tower For Local AI

{% raw %}
Every figure, price and benchmark on screen, with where it comes from. We did not test these
machines ourselves: every speed is a published run, linked here. Prices are live listings
checked on 9 November 2026 (PRICES.md holds the day's table).

## How OCuLink connects

- OCuLink on these boxes is PCIe 4.0 x4 in a cable: the card is a PCIe device of the mini PC,
  like a slot, with 4 lanes instead of 16.
  - GMKtec EVO-X3 128GB, OCuLink PCIe Gen4 x4, $3,799.99:
    https://www.gmktec.com/products/gmktec-evo-x3-ai-mini-pc-amd-ryzen-ai-max-395
  - Acemagic F9A 128GB, OCuLink PCIe 4.0 x4, $3,299 pre-order:
    https://acemagic.com/products/acemagic-f9a-395-minipc
  - GMKtec EVO-X2 128GB 2TB, USB4 only (no OCuLink), $3,649.99:
    https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc
  - Minisforum MS-S1 Max, x16 slot wired PCIe 4.0 x4, $3,959:
    https://store.minisforum.com/products/minisforum-ms-s1-max-mini-pc
- Link bandwidth: PCIe 4.0 is about 1.97 GB/s per lane per direction, so x4 is about 7.9 GB/s
  and x16 about 31.5 GB/s (PCI-SIG PCIe 4.0 rate, 16 GT/s with 128b/130b encoding).
- Minisforum DEG1 dock: needs its own ATX or SFX power supply; power both machines off before
  connecting or disconnecting OCuLink. Manual: https://manuals.plus/asin/B0DHGSG9PZ
  - $109 on Newegg: https://www.newegg.com/p/1DN-0432-00001
- Boot with the screen on the iGPU, move it after POST (Framework community thread):
  https://community.frame.work/t/external-gpus/84700

## What the 128GB box does alone

- Strix Halo memory bandwidth about 215 GB/s measured of 256 GB/s:
  https://community.frame.work/t/amd-strix-halo-ryzen-ai-max-395-gpu-llm-performance-tests/72521
- GPT-OSS 120B on Strix Halo, 33.06 tok/s tg128 (Vulkan):
  https://community.frame.work/t/will-the-ai-max-395-128gb-be-able-to-run-gpt-oss-120b/73280
- Strix Halo llama.cpp results by model: https://github.com/visorcraft/strix-halo-llm-perf
- Tower comparison: dual-channel DDR5-6000 is 2 x 8 bytes x 6,000 MT/s = 96 GB/s (our maths).

## What a 16GB external card adds (Reddit r/LocalLLaMA, MS-S1 Max + RTX 5070 Ti over OCuLink)

Source: https://reddit.com/r/LocalLLaMA/comments/1sfzrdv/ (quiet power mode, PCIe 4.0 x4 to
OCuLink, F9G-BK7 dock, 850W PSU, llama.cpp Vulkan tensor splits)

- Qwen3.5 27B Q4_K_XL: 11.89 tok/s box alone; 30.25 tok/s with 90% on the card; prompt reading
  268 to 989 tok/s; all on the card ran out of memory.
- Qwen3.5 122B-A10B Q4_K_XL: 19.46 tok/s alone, 21.79 with 20% on the card (+12%, our maths);
  more on the card ran out of memory.
- The owner's note: OCuLink was not a bottleneck for prompt processing or generation.
- Same setup, llama-2-7B Q4_0: card alone 179 tok/s on CUDA vs 168 on Vulkan:
  https://reddit.com/r/LocalLLaMA/comments/1sf9i82/
- Viewer comment on our video -9_VkRUZPAA: "combine the two with Vulkan to run larger models
  than either could support alone".

## What the cable does and doesn't limit

- Jeff Geerling, RTX 4090 on a Raspberry Pi 5 (PCIe Gen 3 x1), Qwen3 30B under 5% slower:
  https://jeffgeerling.com/blog/2025/big-gpus-dont-need-big-pcs
- llama.cpp copies CPU-held weights to the GPU for prompt batches of 32+ tokens
  (GGML_OP_OFFLOAD_MIN_BATCH): https://huggingface.co/blog/Doctor-Shotgun/llamacpp-moe-offload-guide
  and https://github.com/ggml-org/llama.cpp/issues/17026
- RTX 3090, GPT-OSS 120B with 12 layers on the GPU and the rest in system RAM, PCIe 3.0 x4
  (Thunderbolt 3) vs x16: prompt 140.46 vs 303.84 tok/s, generation 2.27 vs 2.33 tok/s:
  https://gist.github.com/slewsys/da27a118587b6a50abe1218c55f215a0

## Card speeds in a slot (Hardware Corner)

- RTX 3090, Qwen3.5 27B Q4: 33.5 tok/s, 1,104 tok/s prompt at 4K:
  https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-3090/
- RTX 5090, Qwen3.5 27B Q4: 58.8 tok/s at 4K:
  https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-5090/

## Prices (live listings, 9 November 2026)

| Part | Price | Source |
|---|---|---|
| GMKtec EVO-X3 128GB | $3,799.99 | gmktec.com (above) |
| Minisforum DEG1 dock | $109 | newegg.com/p/1DN-0432-00001 |
| ASRock PRO-850G 850W PSU | $54.99 | https://www.newegg.com/asrock-pro-series-atx-3-1-compatible-850-w-80-plus-gold-certified-power-supply-black-pro-850g/p/N82E16817955022 |
| Used RTX 3090 24GB | about $1,800 median asking | https://rigprice.com/gpu/rtx-3090/ |
| AMD Ryzen 5 8500G (cooler included) | $149.99 | https://www.newegg.com/amd-ryzen-5-8000-g-series-ryzen-5-8500g-phoenix-socket-am5-desktop-cpu-processor/p/N82E16819113815 |
| Gigabyte B650M DS3H | $216.76 | https://www.newegg.com/gigabyte-b650m-ds3h-micro-atx-motherboards-amd-amd-b650-am5/p/N82E16813145414 |
| 64GB DDR5-6000 kit | $1,039.99 | https://www.newegg.com/corsair-vengeance-64gb-2-x-32gb-ddr5-6000-pc5-48000-cas-latency-cl40-desktop-memory-gray/p/N82E16820982288 |
| 128GB DDR5-6000 kit | $2,804.99 | https://www.newegg.com/corsair-vengeance-rgb-128gb-2-x-64gb-ddr5-6000-pc5-48000-cas-latency-cl40-desktop-memory-black/p/N82E16820982280 |
| WD Blue SN5000 1TB | $169.70 | https://www.newegg.com/western-digital-1tb-blue-sn5000-nvme/p/N82E16820250268 |
| DIYPC DIY-S05-BK case | $34.98 | https://www.newegg.com/diypc-atx-mid-tower-steel-cases-black-diy-s05-bk/p/N82E16811353265 |
| RTX 5070 Ti 16GB | $1,499.99 | https://www.newegg.com/pny-technologies-inc-oc-geforce-rtx-5070-ti-16gb-graphics-card-triple-fans/p/N82E16814133900 |
| RTX 5090 32GB | $6,549.99 | https://www.newegg.com/gigabyte-gv-n5090gaming-oc-32gd-geforce-rtx-5090-32gb-graphics-card-triple-fans/p/N82E16814932761 |
| AOOSTAR AG02 (does not support RTX 5090) | $412.99 | https://www.newegg.com/p/2VH-02RP-00VK0 |

## Our maths (derived, shown only beside the figures they come from)

- External build: 3,799.99 + 109 + 54.99 + 1,800 = $5,764 (rounded).
- Tower without card: 149.99 + 216.76 + 1,039.99 + 169.70 + 54.99 + 34.98 = $1,666; with the
  3090, $3,466.
- Gap: 5,764 - 3,466 = $2,298.
- Dock plus power supply: 109 + 54.99 = $164.
- $ per tok/s at 33.5 tok/s (Qwen3.5 27B Q4, card speed): tower 3,466 / 33.5 = $103; external
  5,764 / 33.5 = $172.

### Not checked

- The external build's 3090 speed is taken as the card's x16 figure (33.5 tok/s), on the
  published evidence that the link barely matters once the model fits on the card; no run of a
  3090 over OCuLink on Qwen3.5 27B was found.
{% endraw %}

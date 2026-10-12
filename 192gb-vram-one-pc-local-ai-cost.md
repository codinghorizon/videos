---
layout: default
title: "Six MI50s Hit 192GB Of VRAM For $3,774 With One Catch"
permalink: /192gb-vram-one-pc-local-ai-cost/
date: 2026-10-12
---

# Six MI50s Hit 192GB Of VRAM For $3,774 With One Catch

{% raw %}
Every figure the video puts on screen or says, with where it comes from. Prices were read on the
live pages on 2026-10-12; listings change, so treat every price as that day's.

## The cheapest stack: six AMD Instinct MI50 32GB

- **$629 per card, "More than 10 available", 109 sold**, used, located in Hays, Kansas, United
  States (seller CloudStorageCorp).
  [eBay listing 205802298789](https://www.ebay.com/itm/205802298789). The cheapest result in the
  same search that day was $597.18 plus $50 delivery; we quote the $629 listing because it shows the
  quantity for a six-card stack.
- **Six cards: $3,774** (6 × $629). **About $20 per GB** (3,774 / 192 = 19.66). Our arithmetic.
- The MI50 is a 2018 datacenter card with passive cooling (no fan of its own).

## The documented MI50 builds

- [Completed 8xAMD MI50 - 256GB VRAM + 256GB RAM rig for $3k](https://www.reddit.com/r/LocalLLaMA/comments/1nhd5ks/completed_8xamd_mi50_256gb_vram_256gb_ram_rig_for/)
  (r/LocalLLaMA, 2025): six MI50s and two MI60s ($1,500 for the eight cards), ASRock ROMED8-2T
  board (seven full x16 slots), AMD EPYC 7532 (32 cores), 1300W PSU plus an 850W PSU the builder
  already had, ten blower fans, about $3k in total. **Qwen3 235B Q4_1 at about 21 tok/s** (llama.cpp),
  **idle about 400W**, **llama.cpp inference about 750W at the wall**.
- [8x AMD MI50 32GB at 26 t/s with MiniMax-M2.1](https://www.reddit.com/r/LocalLLaMA/comments/1qjaxfy/8x_amd_mi50_32gb_at_26_ts_tg_with_minimaxm21_and/):
  runs on vllm-gfx906, a community fork of vLLM for this chip (gfx906).
- Yearly power, our arithmetic at $0.15/kWh: 750W all year = 6,570 kWh = **$986**; 400W idle all
  year = 3,504 kWh = **$526**.

## Four MAXSUN Intel Arc Pro B60 Dual 48GB

- **$1,939** on Newegg's marketplace, sold and shipped by WEELIAO, free shipping from China, 30-day
  returns. [Newegg listing](https://www.newegg.com/p/3GM-0003-00003). The listing describes two GPUs
  on one board on PCIe 5.0 x8 + x8, with full bandwidth "on consumer motherboards with x16 lane
  bifurcation".
- **Four cards: $7,756**, **about $40 per GB**, **$3,982 more than six MI50s**. Our arithmetic.
- A single Arc Pro B60 has 24GB, so 192GB from single cards needs eight slots.
- No matched Qwen3 235B benchmark was found for four of these cards.

## Eight used RTX 3090s

- **$1,622**: RigPrice's going rate (median asking price) for a used RTX 3090 24GB on its
  2026-10-12 snapshot, 82 active listings. [RigPrice](https://rigprice.com/)
- **Eight cards: $12,976**, **about $68 per GB**. Our arithmetic.
- NVIDIA rates the reference RTX 3090 at **350W** total board power; eight are 2,800W.
  [NVIDIA RTX 3090 specifications](https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090-3090ti/)
- [LYTH: Eight RTX 3090s, Seven Slots, and an Awful Lot of Cables](https://www.lyth.de/en/8x3090-inference-rig/):
  seven RTX 3090s and one 3090 Ti, AMD EPYC 7443P, Supermicro H12SSL-i (seven slots; the eighth card
  through a bifurcation card), 256GB DDR4, eight PCIe 4.0 risers, a homemade wooden frame, four power
  supplies whose nameplates add up to **4,750 watts** ("not the real sustained consumption"),
  **450 watts idle**, **spikes up to 3.1 kilowatts**. Used 3090s "mostly went for around 650 to 700
  euros" in December 2025.
- Idle all year at $0.15/kWh, our arithmetic: 450W = 3,942 kWh = **$591**.

## Speed reports for Qwen3 235B

- [What do we need for Qwen 3 235?](https://www.reddit.com/r/LocalLLaMA/comments/1lcz8lg/what_do_we_need_for_qwen_3_235/)
  (r/LocalLLaMA): four RTX A6000s (192GB) run Qwen3 235B A22B **Q5_K_M at 31 tok/s**; a reply with
  eight RTX 3090s and the same quant reports **25-30 tok/s**, about 20 at 20k tokens.
- These runs differ in quant and context and are reports, not one matched benchmark.

## Radeon RX 7900 XTX (a viewer question)

- **$1,200**: RigPrice's going rate for a used RX 7900 XTX 24GB, 2026-10-12. Eight: **$9,600**,
  **$50 per GB**. Our arithmetic.

## Two RTX PRO 6000 Blackwell Max-Q 96GB

- **$16,499.99**, sold and shipped by Newegg, list $17,999.99 (save $1,500), 2x slot, 300W.
  [Newegg listing](https://www.newegg.com/nvidia-900-5g153-2200-000-rtx-pro-6000-96gb-graphics-card/p/N82E16814132105?item=N82E16814132105)
- **Two: $32,999.98 (about $33,000)**, **about $172 per GB**, about $20,024 more than eight 3090s,
  600W of board rating. Our arithmetic.

## Modified RTX 4090 48GB

- **$4,597** each, new, 5 available, located in Changsha, China; the cheapest 48GB RTX 4090 in an
  eBay search sorted by price on 2026-10-12. [eBay listing 318742251131](https://www.ebay.com/itm/318742251131)
- **Four: $18,388**, **about $96 per GB**, $5,412 more than eight 3090s. Our arithmetic.

## Mac Studio M5 Ultra 256GB

- **$9,499**: the M5 Ultra Mac Studio is $5,499 with 96GB; the 256GB option is +$4,000. The 512GB
  option is "coming late October". [Apple configurator](https://www.apple.com/shop/buy-mac/mac-studio/m5-ultra-chip-30-core-cpu-64-core-gpu-96gb-memory-1tb-storage),
  [Apple newsroom](https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/)

## What 192GB holds

- Qwen3 235B A22B Instruct 2507 **Q4_K_M is 142.65GB**.
  [bartowski's GGUF files](https://huggingface.co/bartowski/Qwen_Qwen3-235B-A22B-Instruct-2507-GGUF)
  It does not fit 96GB or 128GB; 192GB leaves about 49GB for cache and runtime.
- A 400B dense model at four bits needs about 200GB for weights alone (400 billion × 0.5 byte).
- llama.cpp splits one model across several GPUs by layer.
  [llama.cpp multi-GPU guide](https://github.com/ggml-org/llama.cpp/blob/master/docs/multi-gpu.md)

### Not checked

- No source publishes a complete current build total for any of these routes; host costs (board,
  CPU, risers, power supplies, cooling) are not included in any card subtotal.
- Power and speed for a six-card MI50 build and for four B60 Dual cards are not published.
- The 3090 and A6000 speeds are forum reports at different contexts, not a matched benchmark.
{% endraw %}

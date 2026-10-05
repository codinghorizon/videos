---
layout: default
title: "Your 12GB GPU Can Run 125B AI, If You Own This"
permalink: /qwen-125b-on-12gb-gpu/
date: 2026-10-05
---

# Your 12GB GPU Can Run 125B AI, If You Own This

{% raw %}
Checked 5 October 2026. Benchmark figures are one person's published measurements on their
own machine; none is an independent reproduction. Prices are retail listings on the day
checked and move daily.

## The model: Qwen3.8 Flash Next

- [Qwen3.8-Flash-Next model card](https://huggingface.co/Qwen/Qwen3.8-Flash-Next):
  "Number of Parameters: 125B with 6B activated, plus 51B n-gram embedding and 4B MTP".
  "N-gram Embedding: 20,000,000 (bigrams/trigrams at layer 2)". "Number of Layers: 48".
  "Number of Experts: 512", activated experts 10 routed plus 1 shared, which is the 11 of
  512 drawn per token. Licence: qwen-community-1.0.
- [On the Design of Qwen3.8-Next Architecture: Evaluation, Efficiency, and Training Stability](https://arxiv.org/abs/2608.30320),
  Qiu et al., submitted 31 August 2026. Abstract: "additional 51B parameters of n-gram
  embedding tables held off the accelerator" and "Capacity is added outside the backbone by
  a single n-gram embedding layer whose tables are prefetched from host memory."

## Memory: what Unsloth recommends

- [Unsloth: Qwen3.8-Next](https://unsloth.ai/docs/models/qwen3.8-next):
  "The smallest quant works on 75GB RAM so it's best to have a 96GB RAM/unified memory
  device." On the lookup layers: "these are not quantized that heavily (4-bit minimum) since
  they have random access pattern, and quantizing them heavily will damage the model."
  MTP hardware requirements (total memory, RAM plus VRAM or unified): 1-bit 76 GB, 2-bit
  80 GB, 3-bit 91 GB, 4-bit 97-115 GB, 5-bit 164 GB, 8-bit 200 GB, BF16 355 GB.
  GGUF sizes: UD-IQ1_S 72.5 GB, UD-IQ1_M 74.5 GB, UD-Q2_K_XL 78.9 GB, UD-IQ3_XXS 82.0 GB,
  UD-Q3_K_XL 90.0 GB, UD-IQ4_XS 93.7 GB, UD-Q4_K_XL 111.3 GB, UD-Q5_K_XL 158.3 GB,
  UD-Q6_K_XL 169.2 GB, Q8_0 188.2 GB. Runs through llama.cpp or Unsloth Desktop.

## Speed: the 12 GB RTX 5070 report

- [holden093/llama.cpp-qwen3.8-flash-next](https://github.com/holden093/llama.cpp-qwen3.8-flash-next),
  a customised llama.cpp branch. Hardware: "i5-13500 VM (6 P-cores with SMT as 12 vCPUs),
  91 GiB RAM, RTX 5070 12 GiB (PCIe 4.0 x16), model on NVMe". Model: "the Q2 with Q8_0
  hyper-connection mixers". Results: "about 23-24 tok/s decode at short context and 21-23
  tok/s at 23K, 855-877 tok/s prefill of a 23K prompt; peak VRAM 11.3 GB."
  The short context midpoint used for the arithmetic is 23.5 tokens per second.

## Speed: the RTX PRO 6000 placement benchmark

- [lukaLLM/Qwen3.8-Flash-Next-VRAM-Benchmark](https://github.com/lukaLLM/Qwen3.8-Flash-Next-VRAM-Benchmark),
  NVIDIA RTX PRO 6000 Blackwell, 96 GB VRAM, with VRAM capped per tier. "51.2B of its
  176.94B parameters are a lookup table, not matrix-multiply weights. Put that table in
  system RAM and the model runs on an 8 GB card, or on no GPU at all." "The model reaches
  36 tok/s on an 8 GB card and 8.5 tok/s with no GPU." "At a 2K prompt the 96 GiB tier
  processes prompts 8.4x faster than 8 GiB, against 3.1x for decode."

## Prices

- [Newegg, 96 GB DDR5 desktop memory, sorted by lowest price](https://www.newegg.com/p/pl?d=96gb+ddr5+desktop+memory&Order=1),
  5 October 2026: the cheapest 96 GB (2 x 48 GB) DDR5 desktop kit listed was the G.Skill
  Ripjaws S5 DDR5-5200 at $1,419.99. Laptop SODIMM kits started at $1,410.99.
- [Tom's Hardware: resurrected RTX 3060 12GB price jumps 45 percent](https://www.tomshardware.com/pc-components/gpus/resurrected-rtx-3060-12gb-price-jumps-45-percent-in-the-two-months-since-it-was-revived-2021-era-gpu-now-costs-nearly-usd500-across-most-retailers):
  MSI's Ventus 2X OC RTX 3060 12GB "launched at just $300 on its online store and $340 on
  Newegg. It's now listed for $480 in both places."
- [GMKtec EVO-X3](https://www.gmktec.com/products/gmktec-evo-x3-ai-mini-pc-amd-ryzen-ai-max-395):
  $3,799.99 for 128 GB RAM and a 2 TB SSD (list $4,100). AMD Ryzen AI Max+ 395, 16 cores
  and 32 threads; Radeon 8060S, 40 compute units; 128 GB onboard LPDDR5X at up to
  8000 MT/s; dual M.2 slots; DC power input.

## Strix Halo speed

- [Qwen3.8-Flash-Next on Strix Halo, Vulkan only: 33 tok/s decode, 500 tok/s prefill](https://github.com/ggml-org/llama.cpp/discussions/28512),
  llama.cpp discussion #28512. A Bosgame M5 (Ryzen AI Max+ 395, Radeon 8060S, 128 GB) on
  Vulkan; on ten replayed agent conversations "the median went from 25 to 33 tok/s".

## Arithmetic shown on screen

- Cheapest 96 GB DDR5 desktop kit, Newegg, 5 October 2026: $1,419.99, said as about $1,420.
- Card plus RAM subtotal: $480 + $1,420 = $1,900.
- $1,900 / 23.5 tokens per second = $80.85, about $81 per token per second.
- $3,799 / 33 tokens per second = $115.12, about $115 per token per second.
- $3,799 - $1,900 = $1,899.
- A 23K token prompt read at 855 to 877 tokens per second: 23,000 / 877 = 26.2 s to 23,000 / 855 = 26.9 s, about 27 s.

## Caveats

- Retail prices move daily. The RAM, card and Strix Halo prices are the listings found on 5 October 2026.
- The narration mentions one Windows setup with a practical floor around 24 GB using a very
  small 2 bit model. No public source for that report was found, and no figure for it is
  shown.
- The model card places the n gram embedding at layer 2 and the paper describes a single
  n gram embedding layer; the narration's "each layer can use it as a lookup" is not drawn
  as a per layer lookup.
- How the 12 GB report's runtime split the file between VRAM and system RAM is not
  published beyond its 11.3 GB peak VRAM, so every drawing of that split is labelled
  illustrative.
- The RTX 5070 and RTX PRO 6000 results come from different machines, runtimes and
  quantisations and are not combined.
{% endraw %}

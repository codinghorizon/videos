---
layout: default
title: "Fine Tune 8B AI On A $480 RTX 3060 (One Catch)"
permalink: /fine-tune-your-own-ai-model-at-home-the-hardware/
date: 2026-10-10
---

# Fine Tune 8B AI On A $480 RTX 3060 (One Catch)

{% raw %}
Sources for every figure on screen, checked on 2026-10-10.

## The Hugging Face demo

- **Qwen3-0.6B on open-r1/codeforces-cots, SFT.** Hugging Face's post shows the agent proposing
  "fine-tune Qwen/Qwen3-0.6B on open-r1/codeforces-cots using SFT".
- **t4-small, ~$0.75/hour, ~20 minutes, ~$0.30.** The configuration block in the same post: "Hardware:
  t4-small (~$0.75/hour)", "Estimated time: ~20 minutes", "Estimated cost: ~$0.30". All three are marked
  as estimates. The post gives no row count for the dataset and no production run's GPU hours.
- **A 100 example test run.** The post suggests "Do a quick test run on 100 examples" before a full job.
- **Jobs need a paid plan.** The post: "Jobs require a paid plan."
- **Budget ranges by model size.** The post's hardware guide: under 1B "expect $1-2 for a full run";
  1-3B "costs $5-15"; 3-7B "Budget $15-40 for production".
  https://huggingface.co/blog/hf-skills-training

## Hugging Face Jobs prices (per hour, billed by the minute)

- Nvidia A100 large (80 GB): $2.50. Nvidia H200 (141 GB): $5.00. Nvidia RTX PRO 6000 (96 GB): $2.75.
- The same table lists T4 small at $0.40 an hour today; the video quotes the tutorial's ~$0.75.
  https://huggingface.co/docs/hub/main/en/jobs-pricing

## Minimum VRAM for fine tuning (Unsloth)

| model | QLoRA (4-bit) | LoRA (16-bit) |
|---|---|---|
| 3B | 3.5 GB | 8 GB |
| 7B | 5 GB | 19 GB |
| 8B | 6 GB | 22 GB |
| 9B | 6.5 GB | 24 GB |
| 11B | 7.5 GB | 29 GB |
| 14B | 8.5 GB | 33 GB |
| 32B | 26 GB | 76 GB |

Unsloth calls these the "absolute minimum", notes more VRAM is sometimes needed depending on the
model, and recommends a batch size of 1, 2 or 3 when memory runs out.
https://unsloth.ai/docs/get-started/fine-tuning-for-beginners/unsloth-requirements

Unsloth's Intel GPU guide fine tunes Qwen3-32B in 4-bit (unsloth/Qwen3-32B-bnb-4bit) on Intel GPUs
(Data Center GPU Max, Arc series, Core Ultra AI PCs).
https://unsloth.ai/docs/get-started/install/intel

## Hardware prices, checked 2026-10-10

- **RTX 3060 12GB, $479.99.** MSI RTX 3060 Ventus 2X 12G OC, sold by Newegg. The cheapest Newegg-sold
  RTX 3060 12GB that day was a Gigabyte Windforce OC at $459.99.
  https://www.newegg.com/p/pl?d=rtx+3060+12gb&N=8000%204131&Order=1
- **Used RTX 3090 24GB, about $1,600.** RigPrice median asking price: $1,600 on its 2026-10-07 snapshot,
  $1,619 on 2026-10-10 (77 active used listings). https://rigprice.com/gpu/rtx-3090/
- **Intel Arc Pro B60 24GB, $649.99.** ASRock B60 CT 24G, sold and shipped by Newegg.
  https://www.newegg.com/p/N82E16814930148
- **Framework Desktop, Ryzen AI Max+ 395, 128GB: $3,449** (DIY edition, before storage and OS; out of
  stock on 2026-10-10). https://frame.work/products/desktop-diy-amd-aimax300/body/new
- **Mac Studio.** M5 Max from $2,499, configurable to 128GB; M5 Ultra from $5,499, up to 512GB (the 512GB
  configuration arrives late October). Apple names MLX for fine tuning on a Mac.
  https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/
- AMD Ryzen AI Max+ 395 specifications:
  https://www.amd.com/en/products/processors/desktops/ryzen/ryzen-ai-halo/ryzen-ai-max-plus-395.html

## Fine tuning on Strix Halo and Mac

- kyuz0's Strix Halo fine tuning toolbox (Fedora toolbox, ROCm) has notebooks for full fine tuning,
  LoRA, 8-bit LoRA and QLoRA on Gemma 3 and Qwen 3, with memory use and wall-clock time per run. It
  reports no tokens per second, so its times cannot be set against a rented GPU's.
  https://github.com/kyuz0/amd-strix-halo-llm-finetuning
- MLX LM supports LoRA and QLoRA fine tuning on Apple silicon. https://github.com/ml-explore/mlx-lm
- Apple, WWDC 2026 session 233, MLX training and fine tuning across devices.
  https://developer.apple.com/videos/play/wwdc2026/233/

## Derived figures (our arithmetic)

| figure | working |
|---|---|
| about 38 cents | half an hour at $0.75 = 0.375 |
| $1.25 | half an hour at $2.50 |
| 32 to 96 jobs | 480 / 15 = 32; 480 / 5 = 96 |
| about 16 runs | 650 / 40 = 16.25 |
| 40 runs | 1,600 / 40 |
| about 43 and 107 runs | 650 / 15 = 43.3; 1,600 / 15 = 106.7 |
| $10 to $11 | 4 hours at $2.50 and at $2.75 |
| $120 a year | 12 × $10 |
| over 5 years | 650 / 120 = 5.4 |
| over 13 years | 1,600 / 120 = 13.3 |
| 260 hours | 650 / 2.50 |
| 640 hours | 1,600 / 2.50 |
| 2 GB short | 26 − 24 |
{% endraw %}

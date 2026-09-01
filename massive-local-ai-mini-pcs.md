---
layout: default
title: "Tiny AI PCs Are Running Models They Should Not"
permalink: /massive-local-ai-mini-pcs/
date: 2026-09-01
---

# Tiny AI PCs Are Running Models They Should Not

{% raw %}
Every figure, price, spec and benchmark this video puts on screen, chased to a source.
Anything that could not be chased is listed at the end and is deliberately absent from
the picture.

## DeepSeek V4 Flash

| Claim | Finding | Source |
| --- | --- | --- |
| 284 billion total parameters | 284B total | https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash |
| About 13 billion active per token | 13B activated per token | https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash |
| Mixture of experts | Routed MoE, 256 experts | https://www.spheron.network/blog/deploy-deepseek-v4-flash-gpu-cloud/ |
| One million token context | One million tokens | https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash |
| Open weights, permissive licence | MIT License | https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash |

Active share is 13 / 284, which is 4.6 per cent. The expert grid on screen lights that
fraction and no other.

## The AMD Strix Halo mini PC

| Claim | Finding | Source |
| --- | --- | --- |
| Ryzen AI Max+ 395, up to 128 GB | 128 GB LPDDR5X-8000, shared | https://www.amd.com/en/products/processors/desktops/ryzen/ryzen-ai-halo/ryzen-ai-max-plus-395.html |
| 16 Zen 5 CPU cores | 16 cores, 32 threads, 5.1 GHz boost, 64 MB L3 | https://www.amd.com/en/products/processors/desktops/ryzen/ryzen-ai-halo/ryzen-ai-max-plus-395.html |
| Radeon 8060S integrated GPU | Radeon 8060S, 40 CU, RDNA 3.5 | https://datahardware.ai/blog/amd-ai-max-395-explained |
| 256 bit memory interface | 256-bit bus, 256 GB/s theoretical, about 215 GB/s real | https://datahardware.ai/blog/amd-ai-max-395-explained |
| BOSGAME M5 at 2,999 dollars | 2,999 dollars, Ryzen AI MAX+ 395, 128 GB, 2 TB SSD | https://wccftech.com/review/bosgame-m5-review-the-cheapest-128-gb-strix-halo-mini-pc/ |
| DeepSeek V4 Flash at roughly 12 tokens per second on it | About 12 tok/s generation at Q3, inside about 120 GB of GPU addressable memory | https://wccftech.com/review/bosgame-m5-review-the-cheapest-128-gb-strix-halo-mini-pc/ |

That 120 GB addressable figure is why the shot draws the model sitting inside the pool
rather than beside it: the whole expert set is resident, quantised, before a token moves.

## The rest of the Strix Halo class

| Machine | Finding | Source |
| --- | --- | --- |
| GMKtec EVO-X2 128 GB | About 3,299 to 3,649 dollars depending on storage | https://computingforgeeks.com/ryzen-ai-max-395-mini-pc-comparison/ |
| Framework Desktop | About 3,449 dollars, mini ITX board, PCIe slot, Linux first | https://localaimaster.com/blog/best-strix-halo-mini-pc |
| Beelink GTR9 Pro 128 GB | 1,985 dollars at launch, moved well above that since; dual 10GbE, vapour chamber | https://www.servethehome.com/beelink-gtr9-pro-review-amd-ryzen-ai-max-395-system-with-128gb-and-dual-10gbe/ |
| Beelink GTR9 Pro on GPT OSS 120B | About 31 tok/s at roughly 120 W | https://www.notebookcheck.net/Strix-Halo-Beelink-GTR9-Pro-teardown-reveals-a-vapor-chamber-dual-fan-design-filling-most-of-the-chassis-delivering-silent-120B-LLM-performance-at-120-W.1137263.0.html |

The price ladder on screen uses the ladder the script names (2,000 / 3,000 / 3,500) and
marks where this class actually sits today, which is at or above the top rung.

## Speeds, by model class, on Strix Halo

| Claim | Finding | Source |
| --- | --- | --- |
| GPT OSS 120B around 30 tokens per second | About 30 to 31 tok/s, llama.cpp Vulkan or ROCm | https://datahardware.ai/blog/strix-halo-tokens-per-second-2026 |
| Qwen3 235B single digit to low double digit | About 11 tok/s on a quantised 235B | https://www.popularai.org/p/strix-halo-mini-pc-local-ai |
| Dense 70B around 5 to 10 tokens per second | About 5 tok/s at Q4 on a GMKtec EVO-X2 with llama.cpp Vulkan; 5 tok/s at Q8 rising to about 15 at aggressive 4 bit | https://datahardware.ai/blog/strix-halo-tokens-per-second-2026 |
| Why dense is slower than sparse | A dense 70B reads about 40 GB of weights per token; at about 215 GB/s that caps out near 5 tok/s | https://datahardware.ai/blog/strix-halo-tokens-per-second-2026 |
| Small dense models are the fast ones | 7B to 13B dense at about 30 to 45 tok/s; Qwen3 30B A3B at about 70 to 100 tok/s | https://datahardware.ai/blog/strix-halo-tokens-per-second-2026 |

## The CPU only test

| Claim | Finding | Source |
| --- | --- | --- |
| Generation about 5.6 tokens per second | 5.61 tok/s | https://computingforgeeks.com/run-deepseek-v4-flash-locally/ |
| Prompt processing about 12.3 tokens per second | 12.33 tok/s | https://computingforgeeks.com/run-deepseek-v4-flash-locally/ |
| On a 128 GB class machine | AWS r7i.4xlarge, Xeon Platinum 8488C, 8 physical cores, 16 threads, 123 GiB usable RAM, no accelerator | https://computingforgeeks.com/run-deepseek-v4-flash-locally/ |
| It fit | UD-IQ3_XXS, 104 GB on disk, 104.4 GiB peak resident | https://computingforgeeks.com/run-deepseek-v4-flash-locally/ |
| Ten thousand prompt tokens is a coffee break | About 13.5 minutes before the first output token at that prefill rate | https://computingforgeeks.com/run-deepseek-v4-flash-locally/ |

The waiting figures the shot draws are that arithmetic and nothing else: 10,000 / 12.33
and 100,000 / 12.33.

## Apple

| Claim | Finding | Source |
| --- | --- | --- |
| M5 Max, 128 GB, up to 614 GB/s | Up to 128 GB unified memory, up to 614 GB/s | https://www.apple.com/mac-studio/specs/ |
| M4 Max, 128 GB, over half a terabyte per second | Up to 546 GB/s | https://9to5mac.com/2026/08/25/apple-unveils-next-generation-mac-studio-with-m5-max-and-m5-ultra/ |
| M3 Ultra, up to 512 GB, over 800 GB/s | 819 GB/s, up to 512 GB; M5 Ultra is 1.2 TB/s, a 50 per cent increase over M3 Ultra | https://www.macrumors.com/2026/08/25/apple-announces-new-mac-studio-with-m5-ultra-chip/ |
| DeepSeek V4 Flash on a 128 GB M5 Max MacBook Pro | 39.35 tok/s generation with short prompts, falling to 27.64 tok/s at 65,536 tokens of context; prefill 790.18 tok/s | https://modelfit.io/blog/deepseek-v4-flash-0731-128gb-macbook/ |
| Mac Studio results in the mid twenties to mid thirties | M3 Ultra 512 GB at 35.50 tok/s, q4, 2,048 token context; M3 Max 128 GB at 26.68 tok/s | https://modelfit.io/blog/deepseek-v4-flash-0731-128gb-macbook/ |
| It fits under the 128 GB ceiling | 2 bit DQ MLX build 96.5 GB, UD-Q2_K_XL GGUF 96.8 GB | https://modelfit.io/blog/deepseek-v4-flash-0731-128gb-macbook/ |

Those Apple decode figures are single run, greedy decoding, from one engine, which is why
the shot draws them as two measured points on a prompt length curve rather than as a
headline rate.

## Nvidia

| Claim | Finding | Source |
| --- | --- | --- |
| RTX 3090, 24 GB GDDR6X, about 936 GB/s | 24 GB GDDR6X, 936 GB/s | https://www.club386.com/nvidia-geforce-rtx-5090-vs-rtx-3090/ |
| RTX 4090, same 24 GB, much more compute | 24 GB GDDR6X, 1,008 GB/s headline | https://gigagpu.com/rtx-4090-24gb-gddr6x-vram-bandwidth/ |
| RTX 5090 raises the consumer ceiling to 32 GB | 32 GB GDDR7, 512 bit, 1,792 GB/s | https://www.spheron.network/blog/nvidia-rtx-5090-specs/ |
| DGX Spark, 128 GB unified memory | 128 GB coherent unified memory, models up to about 200B | https://intuitionlabs.ai/articles/nvidia-dgx-spark-review |
| The price moved upward after memory supply problems | Founders Edition raised 18 per cent from 3,999 to 4,699 dollars in February 2026, citing memory supply | https://overclock3d.net/news/systems/nvidia-raises-dgx-spark-price-by-700-due-to-memory-supply-constraints/ |
| DGX Spark on DeepSeek V4 Flash | 459 to 462 tok/s prompt processing, about 19.1 tok/s generation, 2 bit quant | https://computingforgeeks.com/run-deepseek-v4-flash-locally/ |

## Not chased to a source, and therefore not on screen

- **The Vulkan report of 12.2 tokens per second on short generation and 11.6 after context
  depth.** Published Strix Halo Vulkan runs of DeepSeek V4 Flash that could be found sit
  well above that: 18.90 tok/s shallow and 16.30 tok/s at 24,576 context on a matched
  Vulkan build, and higher again on other hosts. The shape of the claim, that generation
  barely drops as context deepens, is well supported; the two figures are not. The shot
  for that beat draws the shape and prints no absolute rate.
  https://www.soothill.io/blog/2026/08/09/deepseek-v4-flash-vulkan-rocm-strix-halo/
- **"Around thirty one to thirty six" tokens per second for MLX DeepSeek V4 Flash on a
  128 GB M5 Max.** The measured points found are 39.35 short prompt and 27.64 at 64K
  context, which brackets that band rather than confirming it. The shot draws the two
  measured points and the curve between them.
- **Behaviour problems at aggressive quantisation.** Widely reported by users rather than
  measured in a published benchmark, so the shot shows quantisation levels and the size
  they buy, and makes no claim on screen about reasoning quality at each level.
- **The Mac Studio generation named in the script.** A new Mac Studio with M5 Max and
  M5 Ultra was announced on 25 August 2026, with up to 512 GB and up to 1.2 TB/s. The
  M4 Max and M3 Ultra figures the script quotes are correct for those machines, but they
  are no longer the top of the Mac range.
  https://www.macrumors.com/2026/08/25/apple-announces-new-mac-studio-with-m5-ultra-chip/
{% endraw %}

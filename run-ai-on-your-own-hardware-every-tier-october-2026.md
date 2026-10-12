---
layout: default
title: "Run Qwen 27B For $350, Or Fit 284B In A Mini PC"
permalink: /run-ai-on-your-own-hardware-every-tier-october-2026/
date: 2026-10-12
---

# Run Qwen 27B For $350, Or Fit 284B In A Mini PC

{% raw %}
Research for every figure the video puts on screen or says, checked 2026-10-12 against the live pages
(read through a real browser on the day).

## Prices

| Machine | Memory | Price | Source |
|---|---|---|---|
| Used RTX 3060 12GB, cheapest screened pick (RigPrice; asking prices, not sales) | 12 GB | $350 | https://rigprice.com/gpu/rtx-3060-12gb/ |
| Used RTX 3060 12GB, going rate (RigPrice, 55 active listings) | 12 GB | $370 | https://rigprice.com/gpu/rtx-3060-12gb/ |
| ASRock Challenger Arc B580 12GB, cheapest new at Newegg (sorted by lowest price) | 12 GB | $329.99 | https://www.newegg.com/p/N82E16814930131 |
| MSI RTX 5060 Ti 16G Gaming Trio OC, sold by Newegg | 16 GB | $799.99 | https://www.newegg.com/p/N82E16814137954 |
| Used RTX 3090, going rate (RigPrice, 74 active listings) | 24 GB | $1,622 | https://rigprice.com/gpu/rtx-3090/ |
| Used RTX 3090, cheapest screened pick (refurbished) | 24 GB | $1,520 | https://rigprice.com/gpu/rtx-3090/ |
| Gigabyte RX 7900 XTX Gaming OC 24G, Newegg marketplace, ships from Hong Kong | 24 GB | $1,169.55 used, $1,364.36 new (not said) | https://www.newegg.com/p/27N-0022-000R8?Item=9SIBTK0KGJ1754 |
| PowerColor Radeon AI PRO R9700 32GB, Newegg (sold out on Oct 12 at the same price; ASRock Creator R9700 in stock at $1,699.99) | 32 GB | $1,699.99 | https://www.newegg.com/p/N82E16814131885 |
| Apple Mac Studio, M5 Max 18-core CPU, 32-core GPU, 36GB, 512GB | 36 GB unified | $2,499.00 | https://www.apple.com/shop/buy-mac/mac-studio/m5-max-chip-18-core-cpu-32-core-gpu-36gb-memory-512gb-storage |
| GMKtec EVO-X2, Ryzen AI Max+ 395, 128GB RAM + 1TB SSD (Add To Cart live, Oct 12) | 128 GB unified | $3,499.99 | https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc?variant=48746069262490 |
| Claude Pro, monthly (US; usage limits apply) | | $20 a month | https://claude.com/pricing |

Derived (our arithmetic): $800 / 16 GB = $50 per GB; $1,622 / 24 GB = about $68 per GB, so the 5060 Ti is the
cheaper card per gigabyte at about half the price ($800 / $1,622 = 0.49) for two thirds of the memory. The
R9700 ($1,700) sits $78 above the used 3090 going rate with 8 GB more. $1,622 / $20 = 81 months, nearly 7
years; $3,500 / $20 = 175 months, more than 14 years. Power and repairs not included.

Memory bandwidth: RTX 5060 Ti 448 GB/s, RTX 3090 936 GB/s (rigprice.com spec line), so the 5060 Ti's memory
is less than half as fast (0.48).

## Speed

| Machine | Model, setup | Result | Source |
|---|---|---|---|
| RTX 3060 12GB (one owner) | Qwen3.8 27B, Unsloth UD-IQ3_XXS, experimental llama.cpp patch, MTP depth 6, 65,536 token context | 29.65-29.69 tok/s fixed C++ workload; 33.21 peak ("a narrow, disclosed record-candidate result") | https://www.reddit.com/r/Qwen_AI/comments/1vzz4m4/qwen3827b_30_toks_at_64k_on_one_rtx_3060_12_gb/ |
| RTX 5060 Ti 16GB (community post) | Qwen3.8 27B, custom IQ4_XS, 32K context, llama.cpp CUDA | no MTP ~25.7 tok/s; MTP-1 ~40.0; MTP-2 ~47.4-47.6 | https://www.reddit.com/r/LocalLLM/comments/1voygm9/running_qwen3827b_dense_fully_on_a_single_rtx/ |
| RTX 3090 (Hardware Corner) | Qwen3.8 27B Q4_K Small (16.68 GiB), llama.cpp, MTP disabled, full CUDA offload | 4K 40.31 tok/s; 32K 37.02; 64K 33.95; 22 GB VRAM at 64K | https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/ |
| Radeon AI PRO R9700 (github rahlquist) | Qwen3.8 27B Q4_K_M, ROCm/HIP, 65k context server | decode ~256 26.4 tok/s; ~2.5k 26.2; ~40k 23.7; ~60k 22.5 | https://github.com/rahlquist/qwen38-r9700 |
| M5 Max 36GB (Rapid-MLX community run, 2026-08-21) | qwen3.8-27b-mixed-3.5bpw | 26.5 tok/s decode, 16.7 GB peak memory | https://rapidmlx.com/benchmarks/qwen3.8-27b-mixed-3.5bpw/apple-m5-max |
| Strix Halo, Ryzen AI Max+ 395 128GB (Lucebox) | DeepSeek V4 Flash, 284B mixture of experts, target + draft in the shared pool | up to 32.0 tok/s decode | https://www.lucebox.com/blog/deepseek-v4-strix-halo |
| Strix Halo (independent reproduction, MikeVeerman) | DeepSeek V4 Flash, 12 configurations | best sustained 24.8 tok/s on a real code prompt; highest 29.98 tok/s on a degenerate counting prompt | https://github.com/MikeVeerman/Strix-Halo-bench/blob/main/Deepseek-v4-flash-bench/README.md |

The R9700 and 3090 runs use different quants (Q4_K_M vs Q4_K_S), runtimes and context points; the video
says so ("the sources use different conditions").

## The 7900 XTX

The only live listing verified on Oct 12 was a Newegg marketplace seller shipping from Hong Kong (link above).
No price is said or shown for it.

## Not checked

- The Mac Studio enclosure itself was not benchmarked: the 26.5 tok/s run is an M5 Max with 36 GB on Rapid-MLX,
  enclosure not stated (the video says so).
- The 3060 result is one owner's tuned setup with an experimental patch; an ordinary install will be slower (said).
- "CUDA has the broadest set of tutorials and ready made configurations" and "ROCm support has improved" are
  judgement calls, not measured.
- Whether the EVO-X2 holds DeepSeek V4 Flash with the exact runtimes cited (Lucebox measured an AMD Ryzen AI MAX+ 395
  with 128 GB; the EVO-X2 is that chip and memory).
{% endraw %}

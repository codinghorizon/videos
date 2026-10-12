---
layout: default
title: "Your 16GB GPU Has a 27B Model Hiding Inside Today"
permalink: /your-16gb-gpu-runs-bigger-models-than-you-think/
date: 2026-10-12
---

# Your 16GB GPU Has a 27B Model Hiding Inside Today

{% raw %}
Every figure the video puts on screen or says, with where it comes from. Pages were read on
2026-10-12; listings and community results change, so treat every price as that day's.

## The model file: Qwen 3.8 27B

- **Qwen3.8-27B is a dense 27B model** (64 layers; 16 full attention layers, the rest Gated
  DeltaNet linear attention). [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B)
- **The official Q4_K_M GGUF is 19 GB.** [ggml-org/Qwen3.8-27B-GGUF](https://huggingface.co/ggml-org/Qwen3.8-27B-GGUF).
  Other Q4_K_M builds of the same model are smaller (an LM Studio build lists 16.5 GB), so "about
  nineteen gigabytes" holds for this file.

## RTX 5060 Ti 16GB: 29.2 tok/s

- **29.2 tokens/s generation** (29.18 tok/s decode), Qwen 3.8 27B, **UD-IQ3_XXS**, llama.cpp,
  **4,096 context**, **K/V cache q4_0**, **full GPU offload, flash attention**, one parallel slot,
  without speculation; reported by a user on Oct 3, 2026.
  [llamaperf: RTX 5060 Ti 16GB](https://llamaperf.com/gpu/rtx-5060-ti-16gb)

## RTX 4060 Ti 16GB: 17.6 and 10.7 tok/s

- **17.6 tok/s decode** with speculative decoding (draft-mtp) and **10.7 tok/s** with none: the same
  user, the same build, UD-Q3_K_XL, KV q4_0, **32K context**.
  [llamabench: RTX 4060 Ti 16GB, Qwen3.8 27B, Q3](https://llamabench.ai/browse/rtx4060ti16gb/qwen3-8-27b?quant=Q3)
- 32K is eight times the 5060 Ti run's 4K context (our arithmetic).

## The quant ladder

- One page swept the whole Qwen 3.8 27B quant ladder on an RTX 3090. **Task accuracy on 75 paired
  items is flat from 4.22 bits per weight through 2.91** and still a tie at 2.48; UD-Q2_K_XL (2.91
  bpw) is "the last rung that still performs like the full-quality file". Perplexity worsens a little
  with every step; below that rung the perplexity cost per gigabyte jumps about fivefold, and the
  accuracy boundary lies **between 2.48 and 2.15 bits per weight**.
- **Q4_K_M perplexity 6.535, UD-IQ4_XS 6.596: a gap of 0.061 inside a ±0.063 combined error bar**, so
  a tie. The same page sets aside an earlier GSM8K comparison (94.0% vs 93.0%) because of a grading
  bug, so the video does not use it.
- The page also cites a long multi-turn test where UD-Q2_K_XL and UD-Q3_K_XL both failed a Godot
  coding task, which is why the video says long reasoning and code can shift in ways a small
  benchmark misses.
  [Qwen3.8-27B measured settings, speeds and energy](https://chinkeong.github.io/qwen-27b/)

## RX 9060 XT 16GB: a memory placement fix

- An owner's generation speed went **from 6.5 to 18.9 tok/s (about 3x)** after fixing weights that sat
  in host visible memory over PCIe. A later llama.cpp update plus MTP speculative decoding took it to
  about 24 to 26 tok/s for coding; the video quotes only the fix.
  [r/unsloth: Qwen3.8 27B generation speed from 6.5 to ...](https://www.reddit.com/r/unsloth/comments/1vv7fva/increased_qwen38_27b_generation_speed_from_65_to/)

## Arc A770 16GB

- **14.4 t/s**, llama.cpp, "Qwen3.6 27B · Q4_K_M" (the listing also labels it "3B active", which a
  dense 27B model is not; the row is quoted as listed). [llamaperf: llama.cpp](https://llamaperf.com/engine/llama-cpp)
- An Arc tuned Qwen 3.8 27B file, **Qwen3.8-27B-GSQ-RCO-Intel-Arc-Tuned-MTP-3.2BPW.gguf, 10.45 GiB**,
  "Profile B (Ultra-Compact for 12–16GB Cards)", built from 52 Q4_K, 181 Q3_K, 169 Q2_K and 8 Q6_K
  tensors. [Greatjedi/Qwen3.8-27B-Intel-Arc-Tuned-GGUF](https://huggingface.co/Greatjedi/Qwen3.8-27B-Intel-Arc-Tuned-GGUF)

## A smaller KV cache

- Qwen 3.8 27B (UD-Q4_K_M) at **65.5K context**: the **f16 cache is 5.9 GB**; measured VRAM drops by
  1.6 GB at q8_0 and **2.6 GB at q4_0**; medians over **13 runs**, every range overlaps. The test ran on
  an RX 7900 XTX (24 GB). [r/LocalLLM: KV cache quantization test](https://www.reddit.com/r/LocalLLM/comments/1wq5on8/kv_cache_quantization_test_up_to_26_gb_less_kv/)
- A 4 bit cache stores about a quarter of the bits of a 16 bit one (q4_0 is about 4.5 bits per value
  with its scales, about 28%). The ideal saving at 5.9 GB would be about 4.2 GB; the measured 2.6 GB is
  below it. The reason given in the video (runtime buffers) is our reading, not the tester's.

## Mixture of experts: Qwen 3.6 35B A3B

- **Qwen3.6-35B-A3B-NVFP4 on an RTX 5060 Ti 16GB with 32GB system RAM (WSL2, capped at 23 GB):
  stable decode 22 ~ 24 tok/s**; expert layers NVFP4, attention FP8; 16.9 GB of expert weights in
  system RAM, peak VRAM ~5.9 GB.
  [FreeToken: Qwen3.6 35B deploy report](https://zhimayuandi.com/en/blog/freetoken-qwen36-deploy-report/)
- **RX 9060 XT 16GB: Qwen3.6 35B · 3B active · UD-Q4_K_XL, 66.0 t/s (speculative, part in system
  RAM).** [llamaperf: llama.cpp](https://llamaperf.com/engine/llama-cpp)

## Prices (US, Newegg, 2026-10-12)

- **64GB (2 x 32GB) desktop DDR5: $919.99**, the cheapest new kit when the search is sorted by lowest
  price (Team T-Force Delta RGB DDR5-5200, FF3D564G5200HC40CDC01). A $825 G.Skill kit on the same page
  is refurbished and a $865.55 offer is used. Most new kits on the page are $949 to $1,100.
  [Newegg search](https://www.newegg.com/p/pl?d=64gb+ddr5+desktop+memory+288-pin+2x32gb&Order=1)
- **$14.38 per GB** = 920 / 64 (our arithmetic).
- **Radeon RX 7900 XTX 24GB: $1,364.36 new**, the lowest of four marketplace sellers (Gigabyte Gaming
  OC; the video says "about $1,385", within 2%).
  [Newegg listing](https://www.newegg.com/p/27N-0022-000R8?Item=9SIBTK0KGJ1754)

## Corrections made before recording

The supplied script was corrected against these sources before anything was recorded: the 64GB kit
price ($866 was a used offer; the cheapest new kit is $920), the quant ladder (the 94%/93% figures
were withdrawn by their own page; the hard drop is below the largest Q2 file, not at Q2), and the
RX 9060 XT figure (the fix alone gave 18.9 tok/s, about 3x; 26 needed further changes).

### Not checked

- The video's explanation that the 2.6 GB KV saving falls short of the theoretical maximum because of
  runtime buffers is our inference; the tester did not explain the gap.
- The Arc A770 14.4 t/s row is listed as "Qwen3.6 27B · 3B active"; which file it really was could not
  be confirmed beyond that listing.
- "Card generation explains only part of the gap" and "the operating system would love one" are the
  narration's judgement, not measurements.
{% endraw %}

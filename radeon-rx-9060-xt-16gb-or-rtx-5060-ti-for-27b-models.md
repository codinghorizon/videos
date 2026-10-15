---
layout: default
title: "RX 9060 XT Runs 27B AI For $270 Less Than Nvidia"
permalink: /radeon-rx-9060-xt-16gb-or-rtx-5060-ti-for-27b-models/
date: 2026-10-15
---

# RX 9060 XT Runs 27B AI For $270 Less Than Nvidia

{% raw %}
Every figure the video puts on screen, with the page it came from. Checked on 15 October 2026.
Prices move daily; the dated listings are in PRICES.md.

## Prices (15 October 2026)

- **RX 9060 XT 16GB, $519.99 new** (Sapphire PULSE, the cheapest 16GB listing at Newegg; the same
  price at Best Buy). https://www.newegg.com/sapphire-tech-pulse-11350-03-20g-radeon-rx-9060-xt-16gb-graphics-card-double-fans/p/N82E16814202457
- **RTX 5060 Ti 16GB, $789.99 new** (MSI Ventus 2X OC, the cheapest 16GB listing at Newegg).
  https://www.newegg.com/p/pl?d=rtx+5060+ti+16gb&Order=1
- **The gap: $270** (789.99 − 519.99). Per gigabyte: $32.50 for the Radeon, $49.37 for the Nvidia.
- **Intel Arc A770 16GB, used, $310 market average** (40 listings; asking range $299 to $321).
  https://resaleprices.com/gpu/intel-arc-a770-16gb
- **RTX 4060 Ti 16GB, used, $639 market average** (17 listings; range $620 to $680).
  https://resaleprices.com/gpu/nvidia-rtx-4060-ti-16gb
- **RTX 3090, used, $1,649 going rate** (median asking price; 77 active listings).
  https://rigprice.com/gpu/rtx-3090/

## Memory and bandwidth

- **Qwen 3.8 27B at Q4_K Small is 16.68 GiB** (27.32 billion parameters), already over 16 GB before
  any cache; Q4_K_M is larger still. https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/
- **Qwen3.8-27B-UD-IQ4_XS.gguf is 14.25 GB** (UD-IQ3_XXS 10.9 GB).
  https://github.com/L4TN/qwen3.8-27B-MTP-rtx5060ti/blob/master/docs/tutorial.md
- **Memory bandwidth:** RX 9060 XT up to 320 GB/s (AMD specifications); RTX 5060 Ti 448 GB/s and
  RTX 4060 Ti 16GB 288 GB/s (128 bit GDDR7 at 28 Gbps and GDDR6 at 18 Gbps; NVIDIA's spec pages give
  the bus width, the figure is the product); Arc A770 16GB 560 GB/s, 256 bit
  (https://www.intel.com/content/www/us/en/products/sku/229151/intel-arc-a770-graphics-16gb/specifications.html);
  RTX 3090 936 GB/s, 24 GB.

## Published Qwen 3.8 27B speeds

- **RTX 5060 Ti, 29.2 tok/s generation**, UD-IQ3_XXS, q4_0 KV cache, 4,096 context; no prompt
  processing figure on that row. https://llamaperf.com/gpu/rtx-5060-ti-16gb
- **RTX 5060 Ti tuned: 92.73 prompt tok/s and 52.68 generation tok/s** at 32K context, UD-IQ4_XS
  with multi token prediction (draft), Q8_0 KV cache, on its chat workload.
  https://github.com/L4TN/qwen3.8-27B-MTP-rtx5060ti/blob/master/docs/tutorial.md
- **RX 9060 XT: about 21.4 tok/s generation without MTP, prompt processing ~74.5 to ~148.9 tok/s**,
  UD-IQ3_XXS, llama.cpp with Vulkan. A second user in the same thread reports 23 tok/s on the same
  file, about 32 with MTP. https://www.reddit.com/r/LocalLLM/comments/1welwcx/qwen3827b_on_rx_9060_xt_16gb/
- **RX 9060 XT, Qwen 2.5 Coder 14B Q4_K_M:** Vulkan 33.51 tok/s, ROCm 30.79 tok/s generation;
  prompt (pp512) 1,210 and 1,211 tok/s. https://github.com/parsapp/rx9060xt-llm-benchmarks
- **RTX 4060 Ti 16GB: 10.7 and 17.6 tok/s**, UD-Q3_K_XL at 32K context, the faster with draft MTP;
  prefill 289 to 291 tok/s. https://llamabench.ai/browse/rtx4060ti16gb/qwen3-8-27b?quant=Q3
- **Arc A770: about 9 tok/s**, IQ4_XS on Vulkan; the poster reports a SYCL backend build error and
  gives no prompt processing figure (they later mention 10 to 11 tok/s after changing settings).
  https://www.reddit.com/r/IntelArc/comments/1wdlyt6/i_want_to_use_qwen38_27b_a_bit_faster_on_the_a770/
- **RTX 3090: 39.7 to 40.0 tok/s** at Q4_K_M. https://chinkeong.github.io/qwen-27b/index.html

## Corrections made to the supplied script before recording

The supplied script said $789 "at Best Buy" from an October 8 snapshot, an A770 bandwidth of 512
GB/s (the 8GB card's figure), a tuned 5060 Ti run of 36 prompt and 70 generation tok/s (those are
the test's token counts, not its speeds), Radeon prompt processing of 300 to 500 tok/s (another
user's MTP build), a used RTX 4060 Ti at $330 (a mixed 8GB/16GB figure) and a used RTX 3090 at
$1,700. Each was corrected to the figures above with the fewest changed words.

### Not checked

- The video compares results from different quantisations, contexts, backends and MTP settings;
  no single controlled test ranks the four cards.
- Used prices are trackers' averages of asking prices, not completed sales.
- The RTX 5060 Ti and RTX 4060 Ti bandwidth figures are derived from bus width and memory speed;
  NVIDIA's own pages list only the bus width.
{% endraw %}

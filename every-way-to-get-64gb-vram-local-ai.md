---
layout: default
title: "The Cheapest Ways To Get 64GB VRAM For Local AI"
permalink: /every-way-to-get-64gb-vram-local-ai/
date: 2026-10-24
---

# The Cheapest Ways To Get 64GB VRAM For Local AI

{% raw %}
Every figure the video says or shows, with where it comes from. Prices were read live on
24 October 2026, the day of the recording; PRICES.md has each listing and each sum. Speeds are
other people's published runs, credited by name. We did not test or run anything ourselves.
Figures marked "by our maths" are our arithmetic on the sources below.

## The models and what 64GB holds

- **Llama 3.3 70B at 4 bit, about 42.5GB.** Q4_K_M file size on bartowski's GGUF page:
  https://huggingface.co/bartowski/Llama-3.3-70B-Instruct-GGUF
- **Qwen 3.8 27B in full precision, about 54GB.** BF16 file on ggml-org's GGUF page:
  https://huggingface.co/ggml-org/Qwen3.8-27B-GGUF
- **Qwen 3.5 122B at 3 bit, about 47GB.** Unsloth's 3 bit file:
  https://huggingface.co/unsloth/Qwen3.5-122B-A10B-GGUF
- **gpt-oss-120b, about 63GB (63.4GB listed).** https://huggingface.co/ggml-org/gpt-oss-120b-GGUF
- **Qwen3 Coder Next: 80B parameters, about 3B active per token.** Qwen's model card.
- **About a third of a megabyte of memory per token for Llama 3.3 70B.** By our maths from its
  published layout (80 layers, 8 key/value heads of 128 dimensions, 16 bit cache):
  2 x 80 x 8 x 128 x 2 bytes = 327,680 bytes per token.
- **16,000 tokens on 48GB, 65,000 on 64GB.** By our maths: (48 - 42.5)GB and (64 - 42.5)GB over
  327,680 bytes, rounded down, leaving a little for the computer.

## GMKtec EVO-X2 (AMD Ryzen AI Max+ 395), 64GB

- **$2,199.99 on sale, with a price increase warning.** https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc
- **$34 per GB; $46 per usable GB on 48GB.** By our maths.
- **Up to 48GB for graphics on a 64GB system, after changing a setting.** AMD's Variable Graphics
  Memory FAQ: https://www.amd.com/en/blogs/2025/faqs-amd-variable-graphics-memory-vram-ai-model-sizes-quantization-mcp-more.html
- **Llama 3.1 70B about 5 tok/s (5.06) and Qwen3 Coder Next about 43 tok/s (42.70), on the 128GB
  version with the same chip.** One owner's benchmarks:
  https://github.com/visorcraft/strix-halo-llm-perf/blob/main/BENCHMARKS.md
- **$431 per token a second on the 70B.** By our maths: 2,199.99 / 5.1.

## Mac mini M5 Pro and Mac Studio M5 Max, 64GB

- **$2,699 (mini) and $3,499 (Studio); $42 and $55 per GB; $800 apart.** Apple Store, 24 Oct 2026
  (links in PRICES.md).
- **macOS gives graphics about three quarters by default; one terminal command
  (iogpu.wired_limit_mb) raises it.** https://github.com/ivanopcode/devnote-override-macos-metal-vram-cap
- **M5 Max has twice the M5 Pro's memory speed.** Apple's specs pages:
  https://www.apple.com/mac-mini/specs/ and https://www.apple.com/mac-studio/specs/
- **Qwen 3.8 27B 4 bit in llama.cpp on an M5 Pro, about 18.5 tok/s; Qwen 3.8 Flash Next streamed
  with Slipstream, about 41 tok/s (40.8); oMLX Qwen 3.8 27B about 23 tok/s.** Owner reports on
  llamaperf: https://llamaperf.com/gpu/m5-pro-64gb
- **oMLX Qwen 3.8 27B on an M5 Max, about 33 tok/s (32.8, an 8 bit copy).**
  https://llamaperf.com/report/d5aa9148-da63-41f7-9dfb-1b227110c533

## Two Intel Arc Pro B70s

- **$1,299.99 each, sold by Newegg; $2,600 the pair; $41 per GB.**
  https://www.newegg.com/asrock-b70-ct-intel-arc-pro-b70-32gb-graphics-card/p/N82E16814930149
- **About $1,600 for the rest of the desktop; about $4,200 whole; $66 per GB.** Newegg parts on
  24 Oct 2026, itemised in PRICES.md.
- **Llama 3.3 70B 4 bit about 11.5 tok/s across the pair (llama.cpp), about 186W; Qwen3 Coder Next
  43.4 tok/s across both at about 79W.** Published benchmarks:
  https://github.com/PMZFX/intel-arc-pro-b70-benchmarks
- **$367 per token a second on the 70B.** By our maths: 4,216.83 / 11.5.

## Two AMD Radeon AI PRO R9700s

- **XFX R9700 $1,999.99, the cheapest on Newegg; the pair $1,400 more than the B70 pair; $88 per
  GB for the desktop.** https://www.newegg.com/p/pl?d=radeon+ai+pro+r9700&Order=1, our maths.
- **One R9700, Qwen 3.8 27B 4 bit about 26 tok/s (26.4).** https://github.com/rahlquist/qwen38-r9700
- **"One of you says you already run a pair of these on an older desktop board".** A viewer,
  @JasonTaylor-po5xc, on our channel, 21 Oct 2026: "dual R9700 - which provides me 64 GB of VRAM
  on my existing AM4 platform".
- **A second card roughly doubled long-prompt reading; writing slightly slower.**
  https://github.com/truelies444/amd-radeon-ai-pro-r9700-llama-cpp-rocm-benchmarks

## Three used RTX 3090s

- **About $1,700 used ($1,707 on rigprice); three about $5,100; 72GB; $71 per GB.**
  https://rigprice.com/gpu/rtx-3090/
- **Llama 3 70B 4 bit: two cards about 16 tok/s, four about 17 (16.89).** Older llama.cpp
  benchmark: https://github.com/XiongjieDai/GPU-Benchmarks-on-LLM-Inference
- **350W each.** NVIDIA's rated board power for the RTX 3090.

## Four 16GB cards

- **AMD RX 9060 XT 16GB from $639.99 on Newegg; four about $40 per GB.**
  https://www.newegg.com/p/pl?d=rx+9060+xt+16gb&Order=1
- **No published 70B run on four.** None found on 24 Oct 2026.

## The 64GB DGX Spark partners

- **Gigabyte AI TOP ATOM 64GB, $4,499, request a quote only; $70 per GB; $1,800 more than the Mac
  mini.** https://www.newegg.com/p/pl?d=gb10+64gb&Order=1
- **Same memory speed as the 128GB Spark.** https://gpusmith.com/hardware/systems/asus-ascent-gx10
- **Qwen 3.8 27B 4 bit about 12 tok/s (11.6) on the 128GB Spark.**
  https://blog.kubesimplify.com/qwen3-8-27b-on-dgx-spark

## Two RTX 5090s

- **NVIDIA lists from $1,999.** https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/
- **Cheapest on Newegg this week a refurbished one at $8,899; a pair $278 per GB.**
  https://www.newegg.com/p/pl?d=rtx+5090&Order=1
- **About 75 tok/s (74.83) on a 4 bit 27B with a short prompt, about 26 with a long document.**
  https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/

## Running costs

- **US average electricity 18.16 cents per kWh.** EIA Electric Power Monthly, Table 5.6.A:
  https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_5_6_a
- **The AMD chip in that benchmark was set to 120W.** The visorcraft page's "120W TDP Run"
  (it also has an 85W run): https://github.com/visorcraft/strix-halo-llm-perf/blob/main/BENCHMARKS.md
- **Close to half a fourth card.** By our maths: $740 against about $1,700 used, 44%.
- **4 hours a day, chips and cards only: AMD chip at 120W about $32 a year; the B70 pair at 186W
  about $50; three 3090s at 350W each up to $278; over three years about $740 more for the 3090s
  than the AMD chip.** By our maths (sums in PRICES.md).

### Not checked

- Whole-computer power draw (only the chips and cards are counted, as the video says).
{% endraw %}

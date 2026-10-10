---
layout: default
title: "An 8GB Mac Is The Wrong Buy For Local AI Today"
permalink: /your-old-mac-local-ai-m1-m6/
date: 2026-10-10
---

# An 8GB Mac Is The Wrong Buy For Local AI Today

{% raw %}
Every figure the video says or shows, with the page it was read from on 2026-10-10.
Benchmarks are community and published runs, not our own; each stays attached to its chip,
memory size, model, quant and runtime.

## Memory bandwidth and capacity (Apple)

| Chip | Bandwidth | Max memory said | Source |
|---|---|---|---|
| M1 | 68 GB/s | | llama.cpp discussion #4167 table: https://github.com/ggml-org/llama.cpp/discussions/4167 |
| M1 Pro | 200 GB/s | 32 GB | https://www.apple.com/uk/newsroom/2021/10/introducing-m1-pro-and-m1-max-the-most-powerful-chips-apple-has-ever-built/ |
| M1 Max | 400 GB/s | 64 GB | same |
| M1 Ultra | 800 GB/s (two M1 Max dies) | 128 GB | https://www.apple.com/newsroom/2022/03/apple-unveils-m1-ultra-the-worlds-most-powerful-chip-for-a-personal-computer/ |
| M2 | 100 GB/s | | https://www.apple.com/au/newsroom/2022/06/apple-unveils-m2-with-breakthrough-performance-and-capabilities/ |
| M2 Pro / M2 Max | 200 / 400 GB/s | | https://www.apple.com/newsroom/2023/01/apple-unveils-m2-pro-and-m2-max-next-generation-chips-for-next-level-workflows/ |
| M2 Ultra | 800 GB/s | | https://www.apple.com/newsroom/2023/06/apple-introduces-m2-ultra/ |
| M3 | 100 GB/s | | https://support.apple.com/en-gb/118552 |
| M3 Pro / M3 Max | 150 / 300 (30-core GPU) to 400 (40-core GPU) GB/s | | https://support.apple.com/en-gb/117736 |
| M3 Ultra | over 800 GB/s | 512 GB | https://www.apple.com/newsroom/2025/03/apple-reveals-m3-ultra-taking-apple-silicon-to-a-new-extreme/ |
| M4 / M4 Pro | 120 / 273 GB/s | | https://www.apple.com/newsroom/2024/10/apple-introduces-m4-pro-and-m4-max/ |
| M4 Max | 410 (32-core GPU) to 546 (40-core GPU) GB/s | 128 GB (laptops) | same, and https://support.apple.com/en-gb/121553 |
| M5 | over 150 GB/s | | https://www.apple.com/newsroom/2025/10/apple-unveils-new-14-inch-macbook-pro-powered-by-the-m5-chip/ |
| M5 Pro | 307 GB/s | | https://www.apple.com/newsroom/2026/03/apple-introduces-macbook-pro-with-all-new-m5-pro-and-m5-max/ |
| M5 Max | 460 (32-core GPU) / 614 (40-core GPU) GB/s | | https://support.apple.com/en-asia/128107 |
| M5 Ultra | 1.2 TB/s | 512 GB (top configuration) | same |
| M6 (Mac mini, 16 GB) | 153 GB/s | | https://www.apple.com/mac-mini/specs/ (24/32 GB configurations list 170 GB/s) |

## Model files and the GPU cap

- Llama 3.1 8B Instruct Q4_K_M: 4.92 GB (4,920,739,232 bytes): https://huggingface.co/bartowski/Meta-Llama-3.1-8B-Instruct-GGUF
- Llama 3.3 70B Instruct Q4_K_M: 42.5 GB (42,520,398,816 bytes): https://huggingface.co/bartowski/Llama-3.3-70B-Instruct-GGUF
- "By default, you can use ~75% of the total RAM with the GPU" (Georgi Gerganov, llama.cpp):
  https://github.com/ggml-org/llama.cpp/discussions/4167#discussioncomment-7661644. 16 -> ~12,
  32 -> ~24, 64 -> ~48 GB are that ratio, as the video says: working estimates.
- Weights read per generated token at 4 bits (8B ~4 GB, 27B ~14 GB, 70B ~35 GB) are parameters
  x 0.5 bytes, our arithmetic. Real Q4_K_M files are larger (the 70B file is 42.5 GB).

## Speeds (tokens per second, generation)

| Machine | Model, quant, runtime | tok/s | Source |
|---|---|---|---|
| base M1 | 7B Q4_0, llama.cpp | 14 (14.19 / 14.15) | llama.cpp #4167 |
| M1 Pro | 7B Q4_0, llama.cpp | 36.4 (16-core GPU 36.41) | llama.cpp #4167 |
| M2 mini, 24 GB | 7B Q4_0, llama.cpp | ~22 (21.91) | llama.cpp #4167 |
| M2 Pro / M2 Max / M2 Ultra | 7B Q4_0, llama.cpp | 38 / 66 (65.95, 38-core) / 89 (88.64, 60-core) | llama.cpp #4167 |
| M3 Max | 7B Q4_0, llama.cpp | 66 (66.31, 40-core) | llama.cpp #4167 |
| M1 Pro 16 GB | Gemma 4 E4B (QAT build), Ollama | 33 | https://llamaperf.com/gpu/m1-pro-16gb |
| M1 Pro 32 GB vs M4 Max 128 GB (2025) | Qwen 2.5 7B Q4, Ollama | 26.9 vs 72.5 | https://www.reddit.com/r/LocalLLaMA/comments/1j0c53c/inference_speed_comparisons_between_m1_pro_and/ |
| same | Qwen 2.5 14B, Ollama / LM Studio MLX | 14.7 vs 38.2 / 18.9 vs 52.2 | same |
| M4 Max 128 GB | Qwen 2.5 72B, Ollama / LM Studio | 8.8 / 10.9 (M1 Pro not tested) | same |
| M1 Max 64 GB | Qwen 3.8 27B, 4-bit MLX, 8-bit KV cache, speculative decoding | 33 (33.1) | https://llamaperf.com/mac/m1 |
| M2 Pro 32 GB | Qwen 2.5 14B Q4_K_M, Ollama | 14 | https://www.kunalganglani.com/llm-benchmarks |
| base M3 (16 GB / 24 GB rows) | Llama 3.1 8B Q4 / Qwen 2.5 14B | 20 / 7 | same |
| M4 mini 16 GB | Llama 3.1 8B Q4_K_M / Qwen 2.5 14B Q4_K_M, Ollama 0.31.2, fixed prompt, median of 3 | 21.2 / 11.7 | https://macyou.co/benchmarks (captured, dark) |
| M5 Pro 64 GB | Qwen 3.8 27B (MLX), Ollama 0.32.13 | 33.8 | https://github.com/daniel29348679/m5pro-llm-bench |
| M1 Max 64 GB | Llama 3.1 70B Q4_K_M | 4.5 | kunalganglani |
| M2 Max / M3 Max / M4 Max (48 GB) | Qwen 2.5 32B Q4_K_M | 11 / 14 / 22 | kunalganglani |
| M1 Ultra 128 GB | Llama 3.1 70B Q4_K_M | 8.5 | kunalganglani |

Tom's Hardware (M4 Max ahead of DGX Spark (GB10) and Strix Halo on decode at every depth; the
lead is largest on dense Gemma 4 12B and smallest on the Qwen 3.6 35B-A3B mixture of experts):
https://www.tomshardware.com/desktops/exploring-apple-silicons-local-ai-performance-with-the-mac-studio-and-m4-max-m4-max-beats-gb10-and-strix-halo-in-decode-throughput-but-memory-bandwidth-isnt-everything

## Our arithmetic

- Ceiling for 27B on an M1 Max: 400 GB/s / 14 GB per token = 28.6, "about twenty nine" tok/s,
  before overhead. A tuned community run with speculative decoding reached 33.1.
- Dollars per reported tok/s, 16 GB M4 mini: $643 / 21.2 = $30.3.

## Prices (Swappa, checked 2026-10-10; PRICES.md has the table)

| Listing | Price | URL |
|---|---|---|
| Mac mini 2020, M1, 8 GB, 256 GB (cheapest live) | $389 | https://swappa.com/listing/view/LAKT78373 |
| Mac mini 2023, M2, 8 GB, 256 GB (cheapest live) | $510 | https://swappa.com/listing/view/LAKG70018 |
| Mac mini 2024, M4, 16 GB, 256 GB (cheapest live) | $643 | https://swappa.com/listing/view/LAKL12649 |
| MacBook Pro 14 late 2023, M3 Max, 36 GB, 1 TB | $2,060 | https://swappa.com/listing/view/LAJS86002 |
| Mac Studio 2022, M1 Max, 64 GB, 2 TB (cheapest 64 GB) | $2,097 | https://swappa.com/listing/view/LAKH70981 |
| Mac Studio 2025, M4 Max, 64 GB, 512 GB (cheapest 64 GB) | $3,193 | https://swappa.com/listing/view/LAKB45343 |

Asking prices on single listings, not a market average. The script's original listings
($426, $464, $670, $2,040 M3 Max, $3,090 M4 Max) had sold or been withdrawn by 2026-10-10.

## Not checked / caveats

- Community figures (llamaperf, kunalganglani, Reddit, the M5 Pro repo) are single users' runs on
  their own settings, not matched tests; model versions and runtimes differ between rows.
- The Gemma 4 E4B 33 tok/s is the QAT build (27 tok/s without it, same page).
- Base M3 rows come from two memory sizes (8B on 16 GB, 14B on 24 GB).
- Qwen 2.5 32B on M4 Max was a 48 GB machine.
- "llama.cpp's ~75% cap" is the default the maintainer describes; macOS versions and runtimes
  (Ollama, LM Studio) set their own working limits.
{% endraw %}

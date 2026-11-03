---
layout: default
title: "RTX 5090 vs RTX 4090 vs RTX 3090 (Local AI)"
permalink: /rtx-5090-vs-4090-vs-3090-local-ai/
date: 2026-11-03
---

# RTX 5090 vs RTX 4090 vs RTX 3090 (Local AI)

{% raw %}
Every figure the script says, and where it came from. Read on 2026-11-02. Prices are in
PRICES.md (checked the same day by check-prices.mjs). Speeds are GPU Battle's: each card run on its
own in llama.cpp `llama-bench`, Q4_K_M, all layers on the GPU, batch 1, 512 prompt tokens and 128
generated. GPU Battle does not state a context length.

## Specs

| | RTX 5090 | RTX 4090 | RTX 3090 | Source |
|---|---|---|---|---|
| Memory | 32 GB GDDR7 | 24 GB GDDR6X | 24 GB GDDR6X | NVIDIA product pages [a][b][c] |
| Bandwidth | 1,792 GB/s | 1,008 GB/s | 936 GB/s | Wikipedia RTX 50 / 30 series [d][f], Notebookcheck [e] |
| Board power | 575 W | 450 W | 350 W | NVIDIA [a][b][c] |
| Required system power | 1,000 W | 850 W | 750 W | NVIDIA [a][b][c] |
| Launch MSRP | $1,999 | $1,599 | $1,499 | Wikipedia [d][g][f] |
| Launched | Jan 2025 | Oct 2022 | Sep 2020 | Wikipedia [d][g][f] |

- 4090 bandwidth is 8% over the 3090's (1008 / 936 = 1.077). The 5090's is 1.91x the 3090's
  ("nearly double").
- "Far more compute": CUDA cores 16,384 (4090) against 10,496 (3090).

[a] https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/
[b] https://www.nvidia.com/en-us/geforce/graphics-cards/40-series/rtx-4090/
[c] https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090-3090ti/
[d] https://en.wikipedia.org/wiki/GeForce_RTX_50_series
[e] https://www.notebookcheck.net/NVIDIA-GeForce-RTX-4090-GPU-Benchmarks-and-Specs.674574.0.html
[f] https://en.wikipedia.org/wiki/GeForce_RTX_30_series
[g] https://en.wikipedia.org/wiki/GeForce_RTX_40_series

## Speed per model size (GPU Battle, generation / prompt reading, tok/s)

| Model (Q4_K_M) | RTX 5090 | RTX 4090 | RTX 3090 | Page |
|---|---|---|---|---|
| Qwen3 8B | 243.9 / 13,393 | 164.3 / 11,240 | 137.6 / 5,036 | https://gpubattle.com/guides/qwen3-8b-gpu-benchmarks |
| Qwen3 14B | 143.1 / 8,106 | 96.37 / 6,183 | 81.11 / 2,992 | https://gpubattle.com/guides/qwen3-14b-gpu-benchmarks |
| Qwen3.8 27B | 75.74 / 3,980.8 | 48.01 / 2,889.6 | 41.93 / 1,324.7 | https://gpubattle.com/guides/qwen3-8-27b-gpu-benchmarks |
| Qwen3 30B-A3B | 344.7 / 10,737 | 259.6 / 9,208 | 202.3 / 4,413 | https://gpubattle.com/guides/qwen3-30b-a3b-gpu-benchmarks |
| gpt-oss-20b | 415.1 / 20,023 | 286.2 / 12,051 | 232 / 6,271 | https://gpubattle.com/guides/gpt-oss-20b-gpu-benchmarks |
| Llama 3.3 70B | won't fit (needs 44GB) | same | same | https://gpubattle.com/guides/llama-3-3-70b-gpu-benchmarks |

Spoken as: 8B "a hundred thirty eight" (137.6) and "two hundred forty four" (243.9); 27B exact;
30B-A3B "two hundred two" and "three hundred forty five"; prompt reading on 27B "thirteen hundred
twenty five" and "three thousand nine hundred eighty one" (3.0x, "three times faster").

Derived on the 27B: 4090 / 3090 = 1.145 ("fifteen percent faster"); 5090 / 3090 = 1.806 ("eighty
one percent"). Ten thousand token prompt: 10000 / 1324.7 = 7.5 s, 10000 / 3980.8 = 2.5 s.
"Fifteen pages" for 10,000 tokens is about 750 words a page at ~0.75 words per token, rounded.

- 24 GB runs Qwen3 32B "comfortably", the largest in GPU Battle's ladder that 24 GB runs:
  https://gpubattle.com/guides/what-can-you-run-on-24gb-vram
- 32 GB: https://gpubattle.com/guides/what-can-you-run-on-32gb-vram

## A 70B on 32 GB

Llama 3.3 70B GGUF sizes, https://huggingface.co/bartowski/Llama-3.3-70B-Instruct-GGUF :
Q4_K_M 42.52GB ("forty two point five"), Q3_K_M 34.27GB labelled "Low quality", Q2_K 26.38GB.
Squeezing a 70B onto 32 GB means three bits or lower, where the file list labels the quality low.

Two RTX 3090s (48 GB) run Llama 3 70B Q4_K_M at 16.29 tok/s in llama.cpp:
https://github.com/XiongjieDai/GPU-Benchmarks-on-LLM-Inference ("sixteen tokens a second").

## Power

GPU Battle's 27B run, average draw: 5090 412.6 W, 4090 258.9 W, 3090 295.2 W (the 4090 the least).
At 4 hours a day for a year at 18.16 c/kWh (EIA Electric Power Monthly table 5.6.a, US residential,
August 2026: https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_5_6_a):
4090 $69, 3090 $78, 5090 $109; 5090 minus 3090 $31 ("thirty dollars"). Card alone.

NVIDIA: the 5090 is rated 575 W with 1,000 W required system power; the 3090 asks for 750 W [a][c].
Two 3090s: 2 x 350 W = "seven hundred watts of GPU".

## Caveats

- 5090 connector melting: Tom's Hardware,
  https://www.tomshardware.com/pc-components/gpus/nvidia-rtx-5090-power-wire-reportedly-caught-fire-despite-using-the-original-cable
- 3090 back-side memory reaches 100 °C under load and stays there: Igor'sLAB, 2021-04-15 ("the
  memory also reaches the 100 °C mark after a short time in 3DMark Port Royal and stays there"),
  https://www.igorslab.de/en/hot-headed-unicorn-under-water-alphacool-eisblock-aurora-acryl-gpx-n-for-nvidia-rtx-3090-founders-edition-installation-and-test/
- 4090 production end reported (not NVIDIA-confirmed; traced to China's Board Channels forum,
  October 2024): Guru3D,
  https://www.guru3d.com/story/nvidia-seems-to-discontinue-rtx-4090-series-to-make-room-for-rtx-50-series/ .
  Digital Trends carried it too but answers automated reads with a browser check. RigPrice has 3 new listings.
- 1,000 W and 750 W required system power, 575 W total graphics power: NVIDIA's series compare
  table, https://www.nvidia.com/en-us/geforce/graphics-cards/compare/ (the product pages hold them
  in a collapsed panel that does not render as text).

## Prices (detail in PRICES.md)

RigPrice going rates from screened eBay asking prices, 2026-11-02: new 5090 $7,599; used 4090
$3,650; used 3090 $1,792. Cheapest used 3090 listings that day: $1,470 (Alienware, "HDMI Port
Issue", rusting) and $1,580 ("Missing Fan Screws"); a refurbished Founders Edition at $1,699,
https://www.ebay.com/itm/287633516722 .

## The viewer comment

Under "How Much VRAM Qwen 3.8 27B Really Needs (Local AI)" (Iu1E3q_kIEc), the real comment reads:
"I would never run this model on anything less than 20GB. Weird that you skipped that card, and
there is no 3090 final sale for anywhere near $950 currently. Just sayin'." The card on screen
prints "there is no 3090 final sale for anywhere near $950 currently".
{% endraw %}

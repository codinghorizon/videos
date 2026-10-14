---
layout: default
title: "Bonsai 2 Packs 27B AI Into a File Smaller Than 6GB"
permalink: /bonsai-2-gpu-mac-card-by-card/
date: 2026-10-14
---

# Bonsai 2 Packs 27B AI Into a File Smaller Than 6GB

{% raw %}
Every figure the video shows or says, with where it came from. Prices were checked on 14 October 2026
(the script's October 10 figures were re-checked that day; the ones that moved were corrected) and move
often; check the live listing before buying.

## The model (Prism ML's Bonsai 2 27B model card)

Source: [Hugging Face, prism-ml/Ternary-Bonsai-2-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-2-27B-gguf), read 14 October 2026.

| Figure | Source text |
|---|---|
| PTQ1_0 file 5.95 GB; PQ2_0 file 7.21 GB | "PTQ1_0 packs trits densely (1.75 bits/weight, 5.95 GB), PQ2_0 stores each trit in a 2-bit slot (2.13 bits/weight, 7.21 GB)" |
| Vision projector 0.63 GB, optional | "Vision tower mmproj (Q8_0) 0.63 GB optional — multimodal input only" |
| 262,144-token context ceiling | "262K-token context"; "-c sets the context, up to 262144" |
| Stock llama.cpp cannot run the files | "Stock llama.cpp will not run these files. It rejects PQ2_0 and PTQ1_0 as unknown types, and it loads Q2_0 without any warning and produces garbage" |
| M5 Pro laptop, 28.1 tok/s, PQ2_0 | Cross-Platform Throughput table: "Laptop (Apple M5 Pro, Metal) 28.1" (tg128, batch 1, depth 0, no vision tower) |
| RTX 5090, 129.9 tok/s, PQ2_0 | Same table: "RTX 5090 (32 GB) 129.9" ("measured with llama-bench on these GGUF packs") |
| 14-benchmark average: Bonsai 2 84.78, FP16 Qwen3.8-27B 86.32 (98.2%) | Benchmarks table: "Qwen3.8-27B FP16 ... 86.32 100%", "Bonsai 2 27B ... 5.95 GB 84.78 98.2%" |
| 2-bit Qwen (IQ2_XXS): 7.27 GB, 72.59 | "Qwen3.8-27B IQ2_XXS ("2-bit") 2.16 7.27 GB 72.59 84.1%" |
| LiveCodeBench: 90.07 Bonsai 2, 90.05 FP16 | Full per-benchmark results: "LiveCodeBench 90.05 87.96 56.40 90.07" |
| OCRBench v2: 56.88 Bonsai 2, 65.45 four-bit Qwen (UD-Q4_K_XL) | "OCR Bench v2 60.99 65.45 61.70 56.88" |

No RTX 5060, RTX 3060, RTX 5060 Ti, RTX 3090 or Mac mini row exists on the model card's throughput table.

## The demo (runtime and defaults)

Source: [PrismML-Eng/Bonsai-demo README](https://github.com/PrismML-Eng/Bonsai-demo).

| Claim | Source text |
|---|---|
| The demo downloads PQ2_0 by default | "A second packing, PQ2_0, trades 1.3 GB for faster prompt processing and is what this demo downloads by default" |
| Needs the PrismML llama.cpp fork | "Bonsai 2 needs this demo's llama.cpp binaries, from the PrismML fork; stock llama.cpp cannot run these files" |
| Vision projector can stay in system RAM | "BONSAI_MMPROJ_CPU=1 keeps the 27B's vision projector in system RAM instead of VRAM ... The cost is a slower image prompt" |
| Apple Silicon: MLX build | Model card: "MLX companion: also available as Ternary-Bonsai-2-27B-mlx-2bit for native Apple Silicon inference" |

## Prices (checked 14 October 2026)

| Figure | What it is | Source |
|---|---|---|
| $460 | Cheapest new RTX 5060 8GB (Gigabyte Windforce Max OC V2, $459.99) | [Newegg search, lowest price first](https://www.newegg.com/p/pl?d=rtx+5060+8gb&N=100007709%204131&Order=1) |
| $350 | RTX 3060 12GB, cheapest screened used pick | [RigPrice RTX 3060 12GB](https://rigprice.com/gpu/rtx-3060-12gb/) ("Cheapest screened pick $350 used") |
| about $370 | RTX 3060 12GB used going rate ($375 on the day) | RigPrice |
| $460 | RTX 3060 12GB new (Gigabyte Windforce OC rev 2.0, "Buy New $459.99") | [Newegg](https://www.newegg.com/gigabyte-windforce-oc-gv-n3060wf2oc-12gd-rev2-0-geforce-rtx-3060-12gb-graphics-card-double-fans/p/N82E16814932658) |
| $800 | MSI RTX 5060 Ti 16G Gaming Trio OC, sold by Newegg ($799.99) | [Newegg](https://www.newegg.com/p/N82E16814137954) |
| $1,590 | RTX 3090 24GB, cheapest screened pick, refurbished | [RigPrice RTX 3090](https://rigprice.com/gpu/rtx-3090/) |
| $1,600 | RTX 3090 used-condition listing (EVGA FTW3 Ultra, $1,599) | RigPrice |
| about $1,649 | RTX 3090 used going rate | RigPrice |
| $6,886 | Gigabyte RTX 5090 Windforce OC 32G, sold by a marketplace seller (Slava computers), condition not stated ($6,885.90) | [Newegg](https://www.newegg.com/p/1FT-000A-00930?Item=9SIAGBAM219504) |
| $899 | Mac mini M6, 16GB, 256GB | [Apple](https://www.apple.com/shop/buy-mac/mac-mini/m6-chip-12-core-cpu-12-core-gpu-16gb-memory-256gb-storage) |
| $1,699 | Mac mini M5 Pro, 24GB, 512GB | [Apple](https://www.apple.com/shop/buy-mac/mac-mini/m5-pro-chip-15-core-cpu-16-core-gpu-24gb-memory-512gb-storage) |
| $2,699 | The same Mac mini with the 64GB option (+$1,000) | Apple configurator, our arithmetic: $1,699 + $1,000 |

## Our arithmetic

- Room left before cache and runtime (card minus language file): 8 - 5.95 = 2.05 GB; 12 - 7.21 = 4.79; 16 - 7.21 = 8.79;
  24 - 7.21 = 16.79; 32 - 7.21 = 24.79; Mac mini 16 - 5.95 = 10.05; Mac mini 24 - 7.21 = 16.79. Upper bounds only:
  the cache, the runtime and the operating system come out of these.
- 84.78 / 86.32 = 98.2%.
- 5.95 / 8 = 74%; 5.95 / 12 = 50%.
- 1,000 tokens / 28.1 tok/s = 35.6 s of generation (prompt reading, reasoning and tool calls not included).
- 129.9 / 28.1 = 4.6.
- Choosing PTQ1_0 over PQ2_0 gives back 7.21 - 5.95 = 1.26 GB.
- OCRBench v2 gap: 65.45 - 56.88 = 8.57 points.
- Dollars per GB of VRAM: used RTX 3060 $350 / 12 = $29; RTX 3090 $1,590 / 24 = $66.

## Not checked

- "Newegg's own listing was out of stock" for the RTX 5090 (the writer's October 10 check; the page read on 14 October
  showed only the marketplace seller's offer).
- The 64GB Mac mini's "two to three weeks" delivery estimate (October 10 check; not shown without a delivery address).
- No published Bonsai 2 speed exists for the RTX 5060, RTX 3060, RTX 5060 Ti, RTX 3090 or any Mac mini: the video
  says so and draws no speed for them.
{% endraw %}

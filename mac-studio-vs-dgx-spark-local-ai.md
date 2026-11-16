---
layout: default
title: "Mac Studio vs DGX Spark (Local AI)"
permalink: /mac-studio-vs-dgx-spark-local-ai/
date: 2026-11-16
---

# Mac Studio vs DGX Spark (Local AI)

{% raw %}
Every figure on screen comes from this table, PRICES.md, or the narration. Checked 2026-11-15.

## Machines

| what | figure | source |
|---|---|---|
| DGX Spark memory | 128GB unified, CPU and GPU share it | https://docs.nvidia.com/dgx/dgx-spark/hardware.html |
| DGX Spark bandwidth | 273 GB/s | same |
| DGX Spark storage (Founders Edition) | 4TB | NVIDIA Marketplace |
| DGX Spark compute | "a petaflop" (1 PFLOP FP4, sparse) | NVIDIA product page |
| Mac Studio M5 Max (40-core GPU) | 128GB, 614 GB/s | https://support.apple.com/128107 |
| Mac Studio M5 Ultra from | 96GB, $5,499 | Apple store |
| Mac Studio M5 Ultra 256GB / 1TB | $9,499 | Apple store |
| 614 / 273 | 2.25x ("two and a quarter") | derived |
| ASUS Ascent GX10 | GB10, 128GB, 1TB, $5,999 | NVIDIA Marketplace |
| 64GB Spark | partners from $4,999 (from 2026-10-23) | implicator.ai |
| Spark price history | $3,999 launch (Oct 2025), $4,699 Feb 2026, $6,950 Oct 2026; +74% | implicator.ai, NVIDIA forum |
| Ultra ship wait | three to four months | Tom's Hardware deep dive |

## Speeds (GPT OSS 120B unless noted)

| run | read (prefill) tok/s | write (decode) tok/s | source |
|---|---|---|---|
| Spark, llama.cpp, 4K | 2,310 (2,309.84) | 55.7 (55.67) | llama.cpp benches/dgx-spark |
| Spark, llama.cpp, 32K | 1,567 | 42.8 (42.76) | same |
| M5 Max (MacBook Pro, 40-core, 128GB), MLX, 4K | 1,325 | 87.9 | Hardware Corner |
| M5 Max, MLX, 32K | 2,537 | 64.5 | same |
| 87.9 / 55.67 | 1.58x ("one and a half times") | | derived |
| Spark, llama.cpp batched | 1 request 57 (57.14) → 32 requests 353 (353.31) total; 11 each | | llama.cpp benches |
| M2 Ultra, llama.cpp batched | 88.6 → 279.4 total | | llama.cpp benches/mac-m2-ultra |
| vllm-mlx on M4 Max | 299 → 613 with 5 requests ("doubled") | | vllm-mlx docs |
| M5 Ultra vs Spark, Qwen 3.8 27B, llama.cpp | Ultra reads faster, writes close to 4x | | Tom's Hardware review |
| A person reads | 5 to 10 tok/s | | narration |

## Batching

- vLLM's Spark recipe sets max-num-seqs 4 and warns that above it bandwidth cost can outweigh the gain: https://vllm.ai/blog/2026-06-01-vllm-dgx-spark
- Viewer comment (under SdXAkMr_ugI, our biggest-model-on-the-Spark video): Dell version, vLLM, 95GB, huge context, "a maximum of four concurrent sessions".

## Setup

- Mac: Ollama or LM Studio, drag to Applications, pick a model.
- Spark: DGX OS (Ubuntu), NVIDIA playbooks (build.nvidia.com/spark); vLLM playbook "intermediate", 15 to 30 minutes.
- NVIDIA developer forum, January 2026: "SM121 software support is fundamentally incomplete" (thread: dgx-spark-sm121-software-support-is-severely-lacking).
- PyTorch had no CUDA 13 ARM builds on the standard index (separate index); a common speed-up library (flash-attention) would not compile.
- vLLM now publishes its own Spark recipe; it runs from a nightly container.

## Owning both (EXO Labs)

- https://blog.exolabs.net/nvidia-dgx-spark/ : Llama 3.1 8B, 8K prompt. Mac Studio (M3 Ultra) alone 6.42 s end to end; Sparks prefill + Mac decode 2.32 s; 2.8x. Spark prefill ~3.8x faster than the Mac; Mac decode ~3.4x faster than the Spark.
- One Mac + one Spark = $12,049 (PRICES.md); more than the 256GB M5 Ultra at $9,499.
{% endraw %}

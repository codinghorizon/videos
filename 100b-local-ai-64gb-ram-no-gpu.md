---
layout: default
title: "64GB Of RAM Runs A 100B Local AI Model Without A GPU"
permalink: /100b-local-ai-64gb-ram-no-gpu/
date: 2026-11-16
---

# 64GB Of RAM Runs A 100B Local AI Model Without A GPU

{% raw %}
What the shots put on screen, and where each figure comes from. Every figure was checked on
2026-11-15 (the verify stage). Prices live in PRICES.md; this file holds everything else.

## The model

| figure on screen | said | source |
|---|---|---|
| 117B total parameters | 024 | GPT-OSS-120B model card, https://huggingface.co/openai/gpt-oss-120b |
| 128 experts per layer, 4 active per token | 025, 026 | same model card |
| 5.1B active parameters | 027 | same model card |
| ships at about 4 bits per weight (MXFP4) | 039 | same model card |
| about 64GB, model plus a short conversation | 040-041 | llama.cpp guide, https://github.com/ggml-org/llama.cpp/discussions/15396 (64.0GB at 8K) |
| full context 131,072 tokens (68.5GB) | 073-074 | same guide |
| at least 66GB recommended | 043 | Unsloth guide, https://docs.unsloth.ai/basics/gpt-oss-how-to-run-and-fine-tune |
| files 62.6GB (Q2_K) to 65.4GB (F16) | 046-047 | https://huggingface.co/unsloth/gpt-oss-120b-GGUF |

## Quantization

| figure | said | source |
|---|---|---|
| KL divergence a "gold standard"; perplexity lets errors cancel out | 053-057 | Unsloth Dynamic 2.0, https://unsloth.ai/docs/basics/unsloth-dynamic-2.0-ggufs |
| Qwen 35B: KLD 0.0137 at 4-bit, 0.1846 at smallest 2-bit (13.5x) | 058-059 | https://unsloth.ai/docs/models/qwen3.5/gguf-benchmarks |
| Gemma 3 MMLU 71.47 at Q4_K_XL, 41.87 at IQ1_S (said 71 and 42) | 060-061 | Unsloth Dynamic 2.0 |
| some 4-bit models fell up to 59% on long tasks | 063-064 | https://arxiv.org/abs/2505.20276 |
| Qwen3 235B Q2_K 85.7GB | 069 | https://huggingface.co/unsloth/Qwen3-235B-A22B-GGUF |

Unsloth's own words used on screen: "gold standard" (KL divergence).

## 96GB

| figure | said | source |
|---|---|---|
| Qwen3.5 122B, 10B active | 076 | https://huggingface.co/Qwen/Qwen3.5-122B-A10B |
| smallest 4-bit (UD-IQ4_XS) 60.2GB; standard Q4_K_M 76.5GB | 077-078 | https://huggingface.co/unsloth/Qwen3.5-122B-A10B-GGUF |
| SWE-bench Verified 72 vs 62 for GPT-OSS | 079-080 | Qwen3.5-122B-A10B model card |
| about half as fast, 4 or 5 tok/s | 081-083 | our maths: 10B vs 5.1B active, from the 9 tok/s estimate |
| 4 sticks of DDR5 drop 5600 to 3600 | 091 | Puget Systems, https://pugetsystems.com/parts/CPU/AMD-Ryzen-9-9950X-4-3GHz-16-Core-170W-15647 |

## Speeds

| figure | said | source |
|---|---|---|
| RTX PRO 6000 writes 196 tok/s | 013 | llama.cpp guide (196.31) |
| 3x RTX 3090, 73 tok/s at about 13,000 tokens of context | 017 | Hardware Corner, https://www.hardware-corner.net/guides/3x-rtx-3090-gpt-oss-120b-test/ (73.26 at 12,788) |
| desktop about 9 tok/s | 019, 136 | our maths: EPYC 18.6 x (96 / 204.8 GB/s) = 8.7 |
| Ryzen AI Max scaled lands at 11 | 137 | our maths from ik_llama.cpp's ~29 tok/s writing |
| EPYC 7F52 CPU-only: 2-page prompt reads 63, writes 18.6 | 101-102 | https://llocalhost-web.pages.dev/speed-bench/all-results |
| 16K prompt: writes 4.3, run 9.5 minutes | 103-105 | same results page |
| EPYC 7F52: 16 cores, 8 channels DDR4 | 101, 121, 134 | AMD specifications |
| Ryzen AI Max+ 395 CPU-only reads 475 tok/s | 119-120 | https://github.com/ikawrakow/ik_llama.cpp/discussions/758 |
| AVX-512 makes the 9950X 56% faster on average | 126-127 | Tom's Hardware on Phoronix's tests |
| Zen 5 full width, Zen 4 half | 125 | Phoronix, https://www.phoronix.com/review/amd-zen5-avx-512-9950x |
| Core Ultra 9 285K: AVX2 only | 129-130 | Intel specifications |
| desktop 2 channels DDR5 = 96 GB/s on paper | 133 | 2 x 8 bytes x 6000 MT/s |
| XMP: stuck at 2000, writing nearly tripled to 28 tok/s | 138-141 | gpuwerk, https://gpuwerk.com/blog/moe-cpu-offload-llama-cpp/ (about 10 to about 28, GPU attention) |
| Xeon Gold 6152: 6 channels DDR4-2666 = 128 GB/s per socket, a third over 96 | 166-167 | Intel ARK; our maths |

## Viewer comment (108-111)

Under our own no-GPU video (local-ai-your-pc-can-run-with-no-gpu). Card quotes the comment's own
words only, as fetched with the YouTube comments tool; otherwise it carries the video name only.

Fetched 2026-11-15, video uZ5l8bGDcdg ("The Best Local AI You Can Run Without A GPU"), @5idi,
2026-10-21: "You're forgetting the KV cache. ... I ran Qwen3.5 35b A3b on an i7-1255U with 32gb of
ddr4 RAM with 128k context window, and... it worked! Prompt read started at around 22
tokens/second and went down to 10 as the context grew, and it answered at around 2 tokens/second."
On screen: the handle, the video title, and the two quoted sentences (laptop line; speeds line).

## API

| figure | said | source |
|---|---|---|
| cheapest provider $0.075 per million written tokens; plenty at $0.15 | 145-146 | https://openrouter.ai/openai/gpt-oss-120b |
| $1,000 buys over 13 billion tokens | 148 | 1000 / 0.075 x 1e6 = 13.3B |
| about 47 years nonstop at 9 tok/s | 149 | 13.3e9 / 9 / 31,557,600 s = 46.9 |

## Servers

| figure | said | source |
|---|---|---|
| older Xeon 6 channels per socket; EPYC Rome 8 | 159 | Intel / AMD specifications |
| R740, 2x Xeon Gold 6152, 256GB, $2,700 | 161-162 | TechMikeNY (PRICES.md) |
| single-socket EPYC server idles 110 W, 310 W under load | 171-172 | ServeTheHome DL325 Gen10, https://www.servethehome.com/hpe-proliant-dl325-gen10-review-amd-epyc-7002-power/4/ |
| US average 18.16 c/kWh | 174 | EIA |

## Photos and captures planned

- RTX PRO 6000 Blackwell (photo), used RTX 3090 (Commons photo), DDR5 kit (photo), Ryzen 9 9950X
  (photo), Dell PowerEdge R740 (photo).
- Captures: OpenRouter provider table ($0.075), Unsloth GGUF file list (62.6GB), Hardware Corner
  73 tok/s, Unsloth Dynamic 2.0 MMLU table, TechMikeNY R740 listing ($2,707.95), DataCenterDisk
  96GB ($1,529.99), llama.cpp guide (64), ServeTheHome power table.
{% endraw %}

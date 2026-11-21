---
layout: default
title: "Qwen 3.8 Flash Next At 190 Tok/s: The Fastest Way To Run It"
permalink: /qwen-3-8-flash-next-fastest-way-to-run/
date: 2026-11-21
---

# Qwen 3.8 Flash Next At 190 Tok/s: The Fastest Way To Run It

{% raw %}
Every figure the narration and the picture use, with the page it came from. Pages read and captured
21 November 2026 (captures in public/qwen-3-8-flash-next-fastest-way-to-run/web/, 2x, figure box in
each .json). Prices: PRICES.md.

## The model
- Qwen3.8-Flash-Next: 125B parameters, 6B active per token, 512 experts, 10 routed plus 1 shared per
  token, a 51B n-gram (word pair) embedding table, an MTP layer. Hugging Face model card,
  https://huggingface.co/Qwen/Qwen3.8-Flash-Next (capture hf-card, "512").
- Strata and Basalt keep the most called experts on the card and fetch the rest from system RAM; Basalt is
  a fork of Strata for Blackwell cards with MTP on by default. https://github.com/jesdga95/basalt
  (capture basalt-repo, "MTP").
- The n-gram table can sit in system RAM because only a few rows are read per token. Unsloth guide,
  https://unsloth.ai/docs/models/qwen3.8-next

## Runs
| figure | setup | source | capture |
|---|---|---|---|
| 193.2 tok/s (said 190 and 193.2) | RTX 5080, Basalt 0.5.0, IQ2_XS with drafter, 65,536 ctx, median of three | llamaperf.com/model/qwen3-8 | lp-5080-basalt |
| 155.6 tok/s | same card and owner, Strata 0.1.55 | llamaperf (same entry) | lp-5080-strata |
| +24% | 193.2 / 155.6 = 1.24 | derived | |
| 153 tok/s average | RTX 5080, Basalt, IQ3_S, ~130K ctx, 100+ requests; 15.7GB VRAM, 54.1GB RAM | remio.ai (German) | remio-153, remio-ram |
| 79.1 tok/s | RTX 5090, Strata, UD-Q5_K_XL, MTP on; fell from ~80 to 40-55 when free RAM ran low | dev.to/seppegadeyne | devto-79 |
| 1.3x to 1.7x, no accuracy loss | MTP, Unsloth's own claim; llama.cpp needs Unsloth's MTP branch and an MTP file | unsloth.ai docs | unsloth-mtp |
| 43.8 vs 73.5 tok/s (+68%) | M5 Max, MTPLX, same coding task, MTP off/on | mtplx.com/models/qwen3.8-flash-next | mtplx-735 |
| 125.8 tok/s | one cached OpenCode request, M5 Max 128GB (best case) | mtplx.com | mtplx-1258 |
| 39.2 tok/s | Ollama, M5 Max 128GB | note.com/jujube | note-392 |
| 53 vs 94 tok/s (+77%) | Strata team, RTX 5070 12GB, IQ3_S vs Q2_0 (vendor figures) | aiweekly.co | aiweekly-94 |
| 40.0 tok/s median | RTX 5090, 4 bit, part in system RAM | llamaperf | lp-5090-median |
| 17.0 tok/s median | RTX 3060, 4 bit | llamaperf | lp-3060-median |
| 42.9 tok/s | RTX 3060 12GB, 64GB RAM, Strata Q2_0, 4,096 token prompt | github.com/Niko1221/Strata bench-results | strata-3060 |
| 102.4 tok/s; 104 at 124K | two RTX 5060 Ti 16GB, Basalt, 64GB DDR4, 4 bit | llamaperf | lp-5060ti-pair |
| 72 to 86 tok/s | two RTX 3090, Strata, 300W cap, 256GB RAM, 6 bit, 120K ctx | llamaperf | (none) |
| 94.3 tok/s | Strix Halo, Halogen, short single request | llamaperf | lp-halo |
| 4.8 tok/s | CPU only, 16 vCPU, 128GB RAM, llama.cpp, smallest file; MTP 5.2 vs 5.4 | computingforgeeks.com | cfg-cpu |
| Ollama split pull failed, merged by hand | reviewer | computingforgeeks.com | |

## Viewer question
"Why not comparing against RTX5080 16GB" — a real comment under nYvnQ1-xZAg (our RTX 4090 vs Mac video),
read from the channel's comment store on 21 November 2026.

## Captures not taken
Apple's store page ($5,099) and TweakTown ($6,199.99) refuse a headless capture (shadow DOM; Cloudflare).
Both prices are in PRICES.md with their URLs and are shown as drawn tags with a source credit.
{% endraw %}

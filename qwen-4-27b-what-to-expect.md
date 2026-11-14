---
layout: default
title: "What To Expect From Qwen 4 27B For Local AI"
permalink: /qwen-4-27b-what-to-expect/
date: 2026-11-14
---

# What To Expect From Qwen 4 27B For Local AI

{% raw %}
Format: figure | exact context | URL | what the page literally says (as fetched today).
OFFICIAL = Alibaba/Qwen-owned page or post. AGG = aggregator/third party only. CALC = our maths.
UNVERIFIED = could not be opened or the page does not state it.

## 1. Qwen 4 status today

- 2026-09-22, Apsara Conference, Hangzhou | Qwen 4 announced, "currently in training" | https://rits.shanghai.nyu.edu/ai/alibaba-at-apsara-2026-qwen-4-in-training-10t-models-next/ | "The conference release says Qwen 4 is 'currently in training.' No release date is given." (AGG summary of Alibaba release; the Alizila keynote https://www.alizila.com/aliviews-eddie-wu-shares-alibabas-strategic-full-stack-ai-roadmap-at-the-2026-apsara-conference/ and the Media OutReach release https://macaubusiness.com/alibaba-unveils-roadmap-on-full-stack-ai-strategy-from-chips-cloud-infrastructure-models-to-agents/ both returned 403 today: UNVERIFIED first-hand)
- Four names Max / Flash / Plus / 27B | shown at Apsara | https://pasqualepillitteri.it/en/news/17552/qwen-4-alibaba-apsara-en and https://www.orcarouter.ai/blog/qwen-4-max-lineup-announced-apsara-2026 | "Alibaba showed off four new names ... Qwen 4 Max, Qwen 4 Flash, Qwen 4 Plus and Qwen 4 27B." (AGG). CONFLICT: NYU RITS says the four names came from "an unconfirmed X post" and "Alibaba's materials do not name these variants", and that the 27B Eddie Wu discussed "is the current open-source Qwen-27B, not a Qwen 4 model". Treat "Qwen 4 27B" as reported, not officially confirmed.
- 5 to 10 trillion params | applies to Qwen 4.5 / Qwen 5, NOT Qwen 4 | https://www.thestandard.com.hk/innovation/article/343438/Alibaba-plans-AI-model-with-5-trillion-to-10-trillion-parameters-unveils-new-chip (Reuters, 22-09-2026) | "plans to train a new artificial intelligence model with between 5 trillion and 10 trillion parameters"; "Alibaba's current flagship model, Qwen 3.8 Max, has 2.4 trillion parameters". Reuters piece does not mention Qwen 4 or 27B.
- No Qwen 4 weights on Hugging Face | huggingface.co/Qwen, checked 2026-11-12 | https://huggingface.co/Qwen | newest models: Qwen3.8-2.4T-A95B(-FP8), Qwen3.8-Flash-Next(-FP8), Qwen3.8-27B(-FP8), Qwen3.6-35B-A3B, Qwen3.6-27B. "No Qwen4 or Qwen 4 model appears on the page."
- Teaser 2026-11-06 | @Alibaba_Qwen post "The becoming begins." (does not name Qwen4) | https://x.com/Alibaba_Qwen/status/2118674834632978755 via https://pasqualepillitteri.it/en/news/30987/qwen4-teaser-the-becoming-begins-en | X itself not openable (402); text via AGG.
- Qwen4-Max preview opened 2026-11-11 | OFFICIAL @Alibaba_Qwen post, created_at "Wed Nov 11 02:01:09 +0000 2026" | https://x.com/Alibaba_Qwen/status/2120335993643684315 (read via https://api.fxtwitter.com/Alibaba_Qwen/status/2120335993643684315) | "Qwen4 is coming. Deeper knowledge. Richer world understanding. Stronger coding and agentic capabilities. Built for real-world tasks ... Qwen4-Max is now in preview on Alibaba's Token Plan." Early access on QwenWork, Qoder, Qwen APP, QwenStudio.
- Model ID qwen4-max-preview; preview ends 2026-11-25 (Beijing); Token Plan from $3/month new users | AGG only | https://pasqualepillitteri.it/en/news/31971/qwen4-max-preview-alibaba-token-plan-from-3-dollars | "available from today, November 11, 2026"; closes November 25. Official https://qwencloud.com/pricing/token-plan does NOT mention Qwen4-Max today and shows no plan amounts: price UNVERIFIED.
- Qwen4-Max benchmarks | NONE published by Alibaba | same AGG page: "no model card and no benchmarks". 
- Qwen4-Max 1M context | AGG only, client-side setting in Qwen Code repo per AlphaSignal | https://pasqualepillitteri.it/en/news/31971/qwen4-max-preview-alibaba-token-plan-from-3-dollars | "a client-side setting, not a server-confirmed limit". UNVERIFIED officially.
- Qwen 4 27B release date | none | https://www.yottalabs.ai/post/qwen-4-27b-release-date-specs-hardware-what-is-known-2026 (updated 2026-11-11) | "Qwen 4 27B is announced, not released." Dense/context/params/licence all "Unknown". (AGG)
- Rumours (all AGG, unconfirmed by Alibaba): anonymous r/LocalLLaMA "end of October" (Oct 7); Arena aliases kibitz/kalmia (Oct 23); Apsara Amsterdam attendee "could launch next week" (Oct 29) | https://pasqualepillitteri.it/en/news/17552/qwen-4-alibaba-apsara-en
- "Qwen4-27B dense" in vllm-xpu-kernels | cited by AGG | https://github.com/analytics-zoo/vllm-xpu-kernels/pull/22 | 404 today: DROP / UNVERIFIED.

## 2. Qwen 3.8 27B (the model it replaces)

- Release ~2026-08-14 | weights published | https://the-decoder.com/alibabas-qwen-team-releases-qwen-3-8-models-with-open-weights-under-the-apache-2-0-license/ (dated Aug 14, 2026) | "Alibaba's AI team Qwen has released the open model weights for Qwen3.8." HF API: repo createdAt 2026-08-05 (private creation), lastModified 2026-11-07, 7,094,218 downloads, 19,705 likes | https://huggingface.co/api/models/Qwen/Qwen3.8-27B
- Dense, 27B (27,781,427,952 params BF16) | model card | https://huggingface.co/Qwen/Qwen3.8-27B | "compact, deployment-friendly dense model"; HF API safetensors total 27,781,427,952.
- Layout | 64 layers, 16 x (3 x Gated DeltaNet -> FFN, 1 x Gated Attention -> FFN) = 48 linear + 16 full attention | same card
- Context | 262,144 native, to 1,000,000 with YaRN | same card
- Licence | Apache 2.0 | same card + HF API "apache-2.0"
- Inputs | text, image, video; thinking on by default, reasoning_effort xhigh/medium/low | same card
- Benchmarks (official card): SWE-bench Pro 61.7 | Terminal Bench 2.1 (Terminus) 73.0 | LiveCodeBench v6 90.3 | GPQA Diamond 89.2 | HLE 30.8 | https://huggingface.co/Qwen/Qwen3.8-27B | Qwen3.6-27B on same table: 53.5 / 63.4 / 83.9 / 87.8 / 24.0. Card does NOT list SWE-bench Verified, AIME or MMLU-Pro.
- GGUF sizes (Unsloth, live) | https://huggingface.co/unsloth/Qwen3.8-27B-GGUF/tree/main | UD-IQ4_XS 14.4 GB; UD-Q4_K_M 16.6 GB; UD-Q4_K_XL 17.7 GB; UD-Q5_K_M 19.9 GB; UD-Q6_K 22 GB; Q8_0 29 GB; Q4_0 16.1 GB; UD-IQ3_XXS 10.9 GB; UD-IQ2_XXS 7.21 GB; mmproj-BF16 931 MB. No plain (non-UD) Q4_K_M/Q5_K_M/Q6_K files in this repo.
- BF16 | 54.7 GB (50 GB + 4.67 GB) | https://huggingface.co/unsloth/Qwen3.8-27B-GGUF/tree/main/BF16
- Other Q4_K_M size | 17.1 GB | https://github.com/karginb/blackwell-qwen-3.8-bench | "Q4_K_M: 17.1 GB", "BF16 (original) 54.7 GB". Channel prices page uses 16.8 GB (https://locallyexplains.site/prices/).
- bartowski repo | https://huggingface.co/bartowski/Qwen_Qwen3.8-27B-GGUF returned 401: UNVERIFIED.

## 3. Gemma 4 31B (rival)

- Dense, 30.7B, 256K context, Apache 2.0 | https://huggingface.co/google/gemma-4-31B-it
- Benchmarks (official card): LiveCodeBench v6 80.0% | GPQA Diamond 84.3% | HLE 19.5% no tools / 26.5% with search | AIME 2026 no tools 89.2% | MMLU Pro 85.2% | same URL. No SWE-bench or Terminal Bench listed.
- Head-to-head overlaps (CALC from the two cards): LiveCodeBench v6 90.3 vs 80.0; GPQA Diamond 89.2 vs 84.3; HLE 30.8 vs 19.5.
- Q4_K_M 18.3 GB; UD-Q4_K_XL 18.8 GB; Q8_0 32.6 GB | https://huggingface.co/unsloth/gemma-4-31B-it-GGUF/tree/main

## 4. Published tok/s, Qwen 3.8 27B (+ bandwidth)

Bandwidths: RTX 5060 Ti 16GB 448 GB/s, RTX 5090 1792 GB/s (https://en.wikipedia.org/wiki/GeForce_RTX_50_series); RTX 3090 936 GB/s (https://en.wikipedia.org/wiki/GeForce_RTX_30_series). NVIDIA product pages list only 128-bit / 512-bit / 384-bit, 16/32/24 GB, not bandwidth. RTX 4090: Wikipedia row lacks it (4090 D row 1008 GB/s); NVIDIA page 384-bit GDDR6X 24GB, no bandwidth: 4090 bandwidth UNVERIFIED today (techpowerup 403). Apple M5 Pro 307 GB/s, M5 Max 32-core 460 GB/s, M5 Max 40-core 614 GB/s, M6 153/170 GB/s (https://www.apple.com/macbook-pro/specs/, https://www.apple.com/mac-mini/specs/). Ryzen AI Max+ 395: "256-bit LPDDR5x", "LPDDR5x-8000" (https://www.amd.com/en/products/processors/laptop/ryzen/ai-300-series/amd-ryzen-ai-max-plus-395.html) -> 256 GB/s CALC (8000 MT/s x 32 bytes); sleepingrobots states "about 218 GB/s" for its box.

- RTX 5060 Ti 16GB | plain median 28.8 tok/s at 3-bit, 2 runs; PP 400.0 t/s | https://llamaperf.com/gpu/rtx-5060-ti-16gb | "28.8gen t/s at 3-bit · 2 runs". Also Oct 26 report: IQ3_S, 81,920 ctx, llama.cpp, MTP on, 40.0 tok/s.
- Used RTX 3090 | plain median 37.4 tok/s at 4-bit, 6 runs; prefill 561.0 (2 runs) | https://llamaperf.com/gpu/rtx-3090 | Also Nov 2: UD-Q4_K_XL, q8_0 KV, 11,600 ctx: megakernel fork 109.2, "llama.cpp reached 54.4 at its best setting" (MTP). Gemma 4 31B 4-bit 36.5 (1 run) on same page. (GPU Battle 41.93 Q4_K_M from earlier research: page now behind a captcha, UNVERIFIED today.)
- RTX 4090 | plain median 40.0 tok/s 4-bit, 3 runs; prefill 1,949.3 | https://llamaperf.com/gpu/rtx-4090 | Oct 21: UD-Q4_K_XL, 8,192 ctx F16 KV, llama.cpp b11200, MTP off 47.0 / MTP on 109.4; 47.0 at 64K; 46.6 at 131K (q8_0 KV); 46.5 at 262K (q4_0 KV) (third-party write-up).
- RTX 5090 32GB | plain median 80.0 tok/s at 4-bit, 7 runs; 6-bit 69.1 (2 runs) | https://llamaperf.com/gpu/rtx-5090 | Nov 2: Q4_K_M, 120,000 ctx, LM Studio, 80-90 tok/s; Nov 9 same with MTP 110-120.
- Apple M5 Max 40-core GPU, 128GB | MLX-4bit, oMLX 0.6.4, no MTP: 24.1 tok/s (code answers); built-in bench 30.6 / 27.3 / 25.0 / 23.5 at 1k/4k/16k/32k; with VLM MTP 34.5; Oct 27 oQ4e-mtp Lightning MTP 70.8 | https://jacar.es/?p=8613 | peak memory MLX-4bit 21.7 GiB up to 32k prompt.
- Apple M5 Pro 64GB | 10 community reports; computed median of single figures 36.0 tok/s (mixed engines/MTP); plain llama.cpp UD-IQ4_XS llama-bench 18.5 tok/s, PP 381.6 (Oct 12); oMLX 4-bit 16,384 ctx 23.0 (Sep 27) | https://llamaperf.com/gpu/m5-pro-64gb
- Apple M5 Pro 48GB | 16.5 tok/s 4-bit llama.cpp, attributed to frandroid | https://llmcheck.net/models/qwen38-27b-on-m5-pro/ | frandroid source page refused fetch: secondary only.
- M4 Pro / M4 Max | no measured figure found; llmcheck values 13 (M4 Pro) / 26 (M4 Max) are labelled "estimated" | https://llmcheck.net/models/qwen38-27b-on-m5-pro/ | UNVERIFIED as measurements. Note Apple no longer sells M4 Pro Mac mini (current: M6 and M5 Pro).
- Strix Halo (Ryzen AI Max+ 395, 128GB) | Q6_K, Vulkan RADV, 131,072 ctx: 9.6 tok/s baseline, 18 tok/s with MTP (draft-n-max 2), Aug 15 2026 | https://sleepingrobots.com/dreams/qwen38-mtp-strix-halo/ | "9.6 t/s baseline", "hits 18 t/s via MTP".
- Strix Halo | UD-Q4_K_XL, 262,144 ctx, Gufo + DFLASH speculative: 24.0 tok/s, PP 450 (Nov 6) | https://llamaperf.com/gpu/strix-halo-128gb
- Strix Halo | AMD "up to 24.5 tokens per second", llama.cpp Vulkan, MTP=4, Windows, quant not named | https://amd.com/en/blogs/2026/run-qwen-3-8-27b-on-amd-ryzen-ai-max-and-radeon-graphics-cards-day-0.html | page timed out today: from search snippet only, UNVERIFIED.
- Intel Arc B580/B60 | no Qwen 3.8 27B measurement found (B580 12GB cannot fit Q4); https://bentech.substack.com/p/running-local-llms-on-intel-arc-pro covers Qwen3.5-27B only. NONE.
- 8GB laptop footnote | RTX 5070 Laptop, UD-IQ2_XXS, 4096 ctx: "13.1 tok/s steady state, 4096 context, 7669 / 8151 MiB VRAM" | https://github.com/karginb/blackwell-qwen-3.8-bench

## 5. KV cache, Qwen 3.8 27B

- config.json | https://huggingface.co/Qwen/Qwen3.8-27B/raw/main/config.json | num_hidden_layers 64; full_attention_interval 4 (16 full-attention layers); num_attention_heads 24; num_key_value_heads 4; head_dim 256; linear_num_key_heads 16; linear_num_value_heads 48; linear_key/value_head_dim 128; hidden_size 5120; max_position_embeddings 262144; dtype bfloat16; architectures Qwen3_5ForConditionalGeneration.
- Per token (CALC) | 2 (K,V) x 16 layers x 4 heads x 256 x 2 bytes = 65,536 B = 64 KiB at FP16 | matches karginb "KV cache 64 KiB/token — a quarter of what a full-attention 27B would cost" (https://github.com/karginb/blackwell-qwen-3.8-bench)
- 32,768 tokens = 2 GiB; 65,536 = 4 GiB; 131,072 = 8 GiB; 262,144 = 16 GiB at FP16 (CALC). q8_0 cache roughly half, q4_0 roughly a quarter + overhead (CALC, approximate).
- Plus a fixed linear-attention state (CALC, approximate): 48 layers x 48 value heads x 128 x 128 = ~37.7M values per sequence = ~75 MB in 16-bit (~150 MB in FP32), independent of context.

## 6. Prices

Live today (2026-11-12):
- Used RTX 3090 | going rate $1,825 median asking, 81 used listings, range $1,740-$2,000; cheapest screened pick $1,560 (ZOTAC Trinity, "smoke/herbal odor"); delisted at $1,655 "(assumed sold)" | https://rigprice.com/gpu/rtx-3090/ | "UPDATED 2026-11-12"
- Used RTX 3090 sold | average sale $1,203 on 2026-11-07 | https://www.getpcparts.com/market-prices/gpu-graphics-cards/rtx-3090 (eBay sold search 403: UNVERIFIED)
- RTX 5060 Ti 16GB | new going rate $925 median of 54 new listings, range $872-$1,000; lowest screened new $838 (PNY, free shipping) | https://rigprice.com/gpu/rtx-5060-ti-16gb/ | "UPDATED 2026-11-12". gpupoet "starting at $773" across 82 deals, Nov 2026, retailer not named, 16GB not distinguished (https://gpupoet.com/gpu/learn/price/november-2026/nvidia-geforce-rtx-5060-ti). Newegg blocked (403) today.
- RTX 5090 | new going rate $7,350 median ask, range $6,900-$7,900; used $7,000; 113 listings | https://rigprice.com/gpu/rtx-5090/ | "UPDATED 2026-11-12". Newegg 403 today.
- Mac mini M5 Pro | from $1,699 (15-core CPU/16-core GPU, 24GB/512GB); from $1,899 (18/20-core) ; M6 from $899 | https://www.apple.com/shop/buy-mac/mac-mini (store JSON: "From $1699", "From $1899"); configured 48GB/64GB price not exposed in page data: UNVERIFIED at Apple. M5 Pro offers 48GB or 64GB (https://www.apple.com/mac-mini/specs/).
- Mac mini M5 Pro 64GB / 1TB (18-core) | $3,299 at Abt ("Notify me" shown, stock unclear) | https://www.abt.com/Apple-Mac-mini-Compact-Desktop-M5-Pro-64GB-Unified-Memory-1TB-SSD-in-Silver-Z1UD00082/p/252371.html
- Framework Desktop Max+ 395 128GB | £3,449 (page geo-served in GBP), all configs "Out of stock" | https://frame.work/products/desktop-diy-amd-aimax300 | USD not shown to us.
- GMKtec EVO-X2 128GB | 429 rate-limited all session: UNVERIFIED today.

Channel's latest checked rows:
- https://locallyexplains.site/prices/ : RTX 5060 Ti 16GB $799.99 Newegg MSI Ventus 3X OC (9 Nov); RTX 3090 used $1,800 rigprice (9 Nov); RTX 4090 used $3,611 rigprice (10 Nov); RTX 5090 $6,549.99 Newegg Gigabyte Gaming OC (9 Nov); Mac mini M6 16GB $899 (9 Nov); Mac Studio M5 Max 128GB $5,099 (9 Nov); Mac Studio M5 Ultra 256GB $9,499 (7 Nov); GMKtec EVO-X2 128GB+1TB $3,499.99 (9 Nov); Framework Desktop 64GB $1,959 (25 Oct). Qwen 3.8 27B Q4_K_M listed as 16.8 GB.
- channels/locallyexplains/videos/external-gpu-vs-desktop-tower-local-ai/PRICES.md (2026-11-09): GMKtec EVO-X2 128GB 2TB $3,649.99; GMKtec EVO-X3 128GB $3,799.99; RTX 3090 $1,800; RTX 5090 $6,549.99.
- channels/locallyexplains/videos/is-16gb-enough-for-local-ai/PRICES.md (2026-11-09): RTX 5060 Ti $800 (gpuprix lowest new); Mac mini M6 24GB $1,099 / 32GB $1,499 at Abt.
- channels/locallyexplains/videos/local-ai-hardware-resale-value/PRICES.md (2026-11-10): RTX 3090 average sale $1,203 (Nov 7, getpcparts); Framework Desktop 128GB $3,449.

## 7. Official architecture hints for Qwen 4

- OFFICIAL | Qwen3.8-Flash-Next model card | https://huggingface.co/Qwen/Qwen3.8-Flash-Next | "This experimental preview of the architecture that will underpin Qwen4 is built around a fundamental rethinking of how the core components of modern large language models (LLMs) interact at scale." "The first open-weight release under this architecture is Qwen3.8-Flash-Next."
- That architecture (same card): 48 layers = 12 x (3 x (Gated DeltaNet -> MoE) -> 1 x (Qwen Sparse Attention -> MoE)); 512 experts, 10 routed + 1 shared; n-gram embedding 20,000,000 entries (bigrams/trigrams at layer 2), 51B n-gram params; MTP 1 layer trained multi-step; 125B total / 6B active; 262,144 native context, to 1,000,000; vision encoder (image + video in); thinking on by default, reasoning_effort xhigh/medium/low; licence Qwen Community License 1.0 (NOT Apache).
- OFFICIAL @Alibaba_Qwen 2026-11-11: "Deeper knowledge. Richer world understanding. Stronger coding and agentic capabilities." No specs.
- llama.cpp PR #30965 "qwen4exp : build the QSA selection without the kq_mask", merged 2026-10-23: "In `qwen4exp` all 12 attention layers are QSA" | https://github.com/ggml-org/llama.cpp/pull/30965 | community code, not Alibaba; 12 QSA layers matches the Flash-Next layout.
- Whether Qwen 4 27B is dense, its context or licence: NOT stated by any official source.
{% endraw %}

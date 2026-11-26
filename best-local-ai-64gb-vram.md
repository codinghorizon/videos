---
layout: default
title: "The Best Local AI On 64GB VRAM"
permalink: /best-local-ai-64gb-vram/
date: 2026-11-26
---

# The Best Local AI On 64GB VRAM

{% raw %}
Researched 2026-11-26. Every figure below was read on 2026-11-26 from the page cited. The question (different from
the 2026-10-27 video, which asked which hardware gives you 64GB): with 64GB of VRAM already on your desk (two 32GB
cards, a 64GB Mac or a 64GB Strix Halo mini PC), which MODEL do you run for each of seven jobs, how many GB does it
really take at a stated context, and what has someone measured it at on a named 64GB setup?
The finding: one 27B dense model (Qwen3.8 27B) wins three of the seven jobs, each at its own squeeze, and the biggest
model that fits, Qwen3.5 122B A10B in a 52.5 GB file, only fits a Mac or a Strix Halo after you raise its graphics
memory limit (both default to about 75%, 48GB of 64).

## Sources

R1: https://huggingface.co/unsloth/Qwen3.8-27B-GGUF/tree/main (accessed 2026-11-26) unsloth file list: "Qwen3.8-27B-Q8_0.gguf 29 GB"; "Qwen3.8-27B-UD-Q4_K_XL.gguf 17.7 GB"; "Qwen3.8-27B-UD-Q8_K_XL.gguf 31.5 GB"; "mmproj-BF16.gguf 931 MB"
R2: https://unsloth.ai/docs/models/qwen3.8.md (accessed 2026-11-26) unsloth docs: "Qwen3.8-27B is a 27B parameter dense model"; 27B benchmarks GPQA Diamond 89.2, IFBench 79.5, LiveCodeBench v6 90.3; context 262,144 "can be extended to 1M via YaRN"; "8-bit | 31 GB" total memory
R3: https://huggingface.co/evsinlb/Qwen3.8-27B-oQ8e-mtp (accessed 2026-11-26) evsinlb model card: "M5 Pro MacBook Pro (20-core GPU, 64 GB), oMLX 0.6.4, built-in benchmark (Code/Python context), Lightning MTP on, ANE off": pp1024/tg128 tg 14.0 tok/s, peak 33.7 GB; pp4096/tg128 tg 10.9, peak 35.2 GB; pp16384/tg128 tg 18.6 tok/s, peak 37.2 GB; "30 GB on disk" (8-bit MLX build); benchmark undated
R4: https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF (accessed 2026-11-26) unsloth: Qwen3.8-Flash-Next 125B total / 6B active; smallest file "UD-IQ1_S" 66.4 GB; GPQA Diamond 91.7 vs 27B 89.2; context "262,144 natively and extensible up to 1,000,000 tokens"
R5: https://huggingface.co/Qwen/Qwen3.8-27B (accessed 2026-11-26) Qwen model card (citation August 2026): GPQA Diamond "89.2" (Qwen3.6-27B 87.8); HLE "30.8"; native context "262,144 tokens, extensible to 1,000,000"; thinking mode on by default; OmniDocBench 1.5 "91.1"
R6: https://ollama.com/library/qwen3.8/tags (accessed 2026-11-26) Ollama: "qwen3.8:27b-nvfp4 · 18GB · 256K" (MLX); qwen3.8:27b-q8_0 30GB
R7: https://modelfit.io/r/2o2trs4va4/ (accessed 2026-11-26) ModelFit run by @sgeggie, 2026-11-12: "Qwen3.8 27B on Apple M5 Max", "Apple M5 Max 40-core GPU · 64GB", "nvfp4 MLX · 18.5 GB · spec. decoding", Ollama 0.40.16 MLX runner, Generation "70.9 tok/s", prompt 902 tok/s, 4k context, median of 3 runs, 256 generated tokens
R8: https://huggingface.co/unsloth/Qwen3.8-27B-GGUF/blob/main/config.json (accessed 2026-11-26) "num_hidden_layers": 64, "full_attention_interval": 4 (48 "linear_attention" and 16 "full_attention" in layer_types), "num_key_value_heads": 4, "head_dim": 256, "max_position_embeddings": 262144
R9: https://huggingface.co/AtomicChat/Ripple-65B-Preview-GGUF/tree/main (accessed 2026-11-26) AtomicChat file list: "Ripple-65B-Preview-Q4_K_M.gguf 38.8 GB"; Ollama https://ollama.com/library/ripple-preview:65b-q4_K_M "39GB", 64.8B, Q4_K_M
R10: https://huggingface.co/ricursiveai/Ripple-65B-Preview (accessed 2026-11-26) Ricursive model card: "65B dense Transformer"; "up to 1Mi (1,048,576 tokens) of context"; SWE-bench Verified 76.5; Terminal-Bench 2.1 80.5 (Terminus 2); self-reported
R11: https://www.oflight.co.jp/en/columns/ripple-65b-preview-requirements-vram-2026 (accessed 2026-11-26) oflight, estimate read from config.json: 80 layers, 8 KV heads, head_dim 128, 16 full-attention layers, 64 with a 1,024-token sliding window; "64 KiB per token"; KV "~8.3 GiB" at 128K; an engine that keeps a full cache on every layer needs 320 KiB per token; measured runs only on a 96GB GH200 (40.6 tok/s) and 2x B200
R12: https://modelfit.io/models/ripple-65b/ (accessed 2026-11-26) ModelFit: "No speed test run for this model yet."
R13: https://letsdatascience.com/news/ricursive-releases-ripple-65b-preview-apache-20-open-coding-7e90be63 (accessed 2026-11-26) Nov 6, 2026: Ripple-65B Preview released under Apache 2.0, a "Preview" with light post-training, scores self-reported
R14: https://huggingface.co/google/gemma-4-31B-it (accessed 2026-11-26) Google model card: vision MMMU Pro "76.9%" (26B A4B 73.8%); OmniDocBench 1.5 edit distance "0.131" (lower is better); GPQA Diamond 84.3%; context 256K
R15: https://huggingface.co/unsloth/gemma-4-31B-it-GGUF/tree/main (accessed 2026-11-26) unsloth: "gemma-4-31B-it-Q4_K_M.gguf 18.3 GB", "mmproj-BF16.gguf 1.2 GB", "gemma-4-31B-it-Q8_0.gguf 32.6 GB"
R16: https://omlx.ai/benchmarks/9ltxbslg (accessed 2026-11-26) oMLX community benchmark, 2026-05-19, gemma-4-31B-it 4-bit, "M4 Max (40-core GPU)", "64 GB", oMLX v0.3.8: TG tok/s 1k "15.5", 4k "14.4", 8k "12.8", 16k "7.3"; Peak Mem 1k "27.3 GB", 16k "31.6 GB"; submitter not named
R17: https://ollama.com/library/gemma4/tags (accessed 2026-11-26) Ollama: "gemma4:31b-it-q4_K_M · 20GB · 256K"; gemma4:31b-mlx 19GB
R18: https://omlx.ai/benchmarks/64qjueqz (accessed 2026-11-26) oMLX community benchmark, submitted 2026-05-12: "Qwen3.6-35B-A3B", "8bit", "M5 Max (40c)", "64 GB", oMLX v0.3.8; rows "1k | 2,198 | 100.8 | 35.4 GB", "4k | 3,653 | 97.8 | 36.2 GB", "32k | 3,234 | 84.2 | 38.9 GB" (PP tok/s | TG tok/s | Peak Mem)
R19: https://huggingface.co/api/models/mlx-community/Qwen3.6-35B-A3B-8bit/tree/main (accessed 2026-11-26) 8 shards summing to 37,721,403,002 bytes = 37.72 GB
R20: https://huggingface.co/Qwen/Qwen3.6-35B-A3B (accessed 2026-11-26) Qwen model card: "35B in total and 3B activated"; native context 262,144; SWE-bench Verified 73.4 (Gemma4-26B-A4B 17.4)
R21: https://frame.work/blog/choosing-a-framwork-desktop-for-local-ai (accessed 2026-11-26) Framework, Donato Capitella, 02 Sep 2026: "You can also run a larger model such as Qwen3.5-122B-A10B. Its 52.5GB Q3 file fits, but leaves less memory for context than the smaller models."
R22: https://huggingface.co/unsloth/Qwen3.5-122B-A10B-GGUF (accessed 2026-11-26) unsloth: "Q3_K_S 52.5 GB"; UD-IQ3_XXS 44.7 GB; Q4_K_M 76.5 GB
R23: https://huggingface.co/Qwen/Qwen3.5-122B-A10B/raw/main/config.json (accessed 2026-11-26) "num_hidden_layers": 48, "full_attention_interval": 4 (12 full_attention layers), "num_key_value_heads": 2, "head_dim": 256, "max_position_embeddings": 262144, "num_experts": 256, "num_experts_per_tok": 8; 122B total, 10B active (model name A10B)
R24: https://runaihome.com/blog/strix-halo-64gb-vs-128gb-local-ai-2026/ (accessed 2026-11-26) RunAIHome, 28 Sep 2026: Windows VGM "converts up to 75% of total RAM into 'dedicated' graphics memory" (48GB on 64GB); Linux amdgpu.gttsize=57344 gives "roughly 56GB"; gpt-oss-120b "does not fit" on 64GB
R25: https://github.com/ml-explore/mlx-lm/issues/883 (accessed 2026-11-26) BrunoCerberus, 12 Feb 2026: "`mlx_lm.server` starts by wiring ~75% of RAM" (the reporter's analysis; Apple does not document the default); the limit is raised with sysctl iogpu.wired_limit_mb
R26: https://omlx.ai/benchmarks/mkl5f0ho (accessed 2026-11-26) Qwen3.5-122B-A10B 3-bit MLX on an M3 Max 128GB: 47.6 TG tok/s at 1k, peak 53.6 GB (a 128GB machine: not a 64GB run)
R27: https://github.com/Niko1221/Strata (accessed 2026-11-26) Strata: "Free, open source, and yours to run."; MIT license; hardware: NVIDIA GeForce RTX 20 / 30 / 40 / 50 series; AMD Radeon RX 7700-7900, RX 9060 / 9070, AI PRO R9700; Intel Arc (Linux); Apple Silicon M1 or newer; AMD Ryzen AI Max (Strix Halo); NVIDIA DGX Spark (Linux)
R28: https://github.com/Niko1221/Strata/releases (accessed 2026-11-26) Strata 0.2.22 released 25 Nov 2026; v0.2.20: "Unified 4-tier GPU + RAM + CPU + SSD Mixture-of-Experts execution across Qwen3.8-Flash-Next, HY-4 Flash, and Inkling 2 Mini"; "hot experts in remaining VRAM"; "cold experts in pageable RAM"
R29: https://www.newegg.com/gigabyte-gv-n5090aorusm-ice-32gd-geforce-rtx-5090-32gb-graphics-card-triple-fans/p/N82E16814932765 (accessed 2026-11-26) Newegg, GIGABYTE AORUS RTX 5090 Master ICE 32GB, $6,799.99, in stock, sold by Newegg (cheapest new RTX 5090 in stock sold by Newegg; the $6,499.99 Gaming OC is out of stock)
R30: https://www.apple.com/shop/buy-mac/mac-mini/m5-pro-chip-15-core-cpu-16-core-gpu-64gb-memory-512gb-storage (accessed 2026-11-26) Apple, Mac mini M5 Pro 64GB 512GB, "price":2699.00, available
R31: https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc (accessed 2026-11-26) GMKtec EVO-X2, Ryzen AI Max+ 395, 64GB RAM + 1TB SSD: "Sale price $2,199.99 Regular price $2,599.99"; stock unclear
R32: https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/ (accessed 2026-11-26) Hardware Corner, updated August 17, 2026: Qwen3.8 27B Q4_K Small (16.68 GiB) measured VRAM "18 GB at 4k ... 20 GB at 32k ... 26 GB at 128k, and 34 GB at 256k"

## The evidence kit

HERO: R21 R22 Qwen3.5 122B A10B, a 122-billion-parameter model, fits in 64GB as a 52.5 GB Q3_K_S file (Framework: "Its 52.5GB Q3 file fits"), and with a 32K chat it needs 53.31 GB, leaving 10.69 GB of 64
COUNTER: R24 R25 on a 64GB Strix Halo under Windows the GPU gets up to 75% of RAM, 48GB, and MLX on a Mac starts by wiring ~75%, so the 52.5 GB file does not fit either out of the box; Linux raises the Strix Halo pool to roughly 56GB (2.69 GB left), and only two 32GB cards give the full 64GB
STEELMAN: R4 R2 the case for a bigger model: Qwen3.8 Flash Next scores 91.7 on GPQA Diamond against the 27B's 89.2, but its smallest file is 66.4 GB, more than 64GB
UNIT-CHAIN: R1 R8 64GB -> Qwen3.8 27B Q8_0 file 29 GB -> 16 of 64 layers keep a KV cache at 65,536 bytes a token -> 17.18 GB at 262,144 tokens -> 46.18 GB in all -> a full-length document fits with 17.82 GB left
MONEY-OBJECT: R29 R30 R31 the 64GB the viewer already paid for: two RTX 5090s ($6,799.99 each at Newegg), a 64GB Mac mini M5 Pro ($2,699.00) or a 64GB GMKtec EVO-X2 ($2,199.99)
PRICES: R29 R30 as of 2026-11-26: RTX 5090 32GB $6,799.99 (Newegg, in stock, so $13,599.98 for two); Mac mini M5 Pro 64GB 512GB $2,699.00 (apple.com). Not spoken: GMKtec EVO-X2 64GB $2,199.99 sale price, but the 64GB option shows "Variant sold out or unavailable" (R31)
BENCH: R18 Qwen3.6 35B A3B 8-bit MLX on an M5 Max 40-core 64GB, oMLX v0.3.8: 97.8 tok/s at 4k (100.8 at 1k, 84.2 at 32k), peak 38.9 GB at 32k; R3 Qwen3.8 27B 8-bit MLX on an M5 Pro 64GB, MTP on: 18.6 tok/s at 16K, peak 37.2 GB; R7 Qwen3.8 27B nvfp4 on an M5 Max 64GB with speculative decoding: 70.9 tok/s at 4k; R16 Gemma 4 31B 4-bit on an M4 Max 64GB: 7.3 tok/s at 16k, peak 31.6 GB
STRATA: R27 R28 Strata, free and open source (MIT), splits a mixture-of-experts model across VRAM and system RAM ("hot experts in remaining VRAM", "cold experts in pageable RAM") and names Qwen3.8-Flash-Next, the 66.4 GB model that does not fit 64GB; it runs on RTX 20 series and newer, Apple Silicon M1 or newer, and Strix Halo
VIRAL: NONE: no single widely shared post about running models on exactly 64GB of VRAM in November 2026 with measurable reach was found
COMMUNITY: R3 R16 R18 R7 every speed here is a community measurement: evsinlb's own model card (M5 Pro 64GB), oMLX community benchmark submissions (M5 Max 64GB, M4 Max 64GB) and @sgeggie's ModelFit run (M5 Max 64GB)
UNMEASURED: R12 R26 R11 no measured speed on any 64GB setup was found for Ripple-65B Preview (ModelFit: "No speed test run for this model yet"), for Qwen3.5 122B A10B (the published runs are on 128GB machines), or for Qwen3.8 27B at its full 262,144-token length; no measured run on two 32GB cards or a 64GB Strix Halo was found for any of the seven picks
PATTERN: R18 R3 R20 R2 on 64GB the active parameters set the speed: Qwen3.6 35B A3B works 3B parameters a word and writes 97.8 tok/s on an M5 Max, while the dense Qwen3.8 27B works all 27B and writes 18.6 tok/s on an M5 Pro with MTP on
SPONSOR: none (no paid sponsor; the ZoneBlade house ad, and one Amazon affiliate link for the 64GB Mac mini from channel.json affiliate)
ARTEFACT: 2026-11-26 headroom against the 48GB default pool per pick (48 - GB), seconds for a 500-token answer per measured speed (500 / tok/s), two-pick totals (sum of GB), and two RTX 5090s against the Mac mini (13599.98 / 2699 = 5.04)
ARTEFACT: 2026-11-26 read the file lists, config files and model cards of seven models and five community benchmark pages, and worked the memory numbers: Qwen3.8 27B cache 16 x 4 x 256 x 2 x 2 = 65,536 bytes a token, x 262,144 = 17.18 GB, + 29 = 46.18 GB; Qwen3.5 122B cache 12 x 2 x 2 x 256 x 2 = 24,576 bytes a token, x 32,768 = 0.81 GB, + 52.5 = 53.31 GB, 64 - 53.31 = 10.69 GB; Ripple 38.8 + 8.59 + 0.27 = 47.66 GB at 128K

## The seven picks (three facts each)

1. All-rounder: Qwen3.8 27B, 8-bit MLX (evsinlb oQ8e build, 30 GB on disk, R3) / Q8_0 GGUF 29 GB (R1). 37.2 GB peak at 16,384 tokens (R3, measured). 18.6 tok/s on an M5 Pro MacBook Pro 64GB, MTP on, at 16K (R3). Why: IFBench 79.5 (R2).
2. Coding: Ripple-65B Preview, Q4_K_M 38.8 GB (R9). 47.7 GB at 131,072 tokens (derived: 38.8 + 8.59 + 0.27, R11). No measured figure on a 64GB setup (R12). Why: SWE-bench Verified 76.5, self-reported (R10, R13).
3. Reasoning: Qwen3.8 27B, nvfp4 MLX 18.5 GB in the measured run (R7; Ollama's tag rounds it to 18GB, R6). 22.79 GB at 65,536 tokens (derived: 65,536 bytes x 65,536 = 4.29 GB + 18.5, R8). 70.9 tok/s on an M5 Max 64GB with speculative decoding at 4k (R7). Why: GPQA Diamond 89.2, HLE 30.8, thinking on by default (R5).
4. Vision: Gemma 4 31B, 4-bit (Q4_K_M 18.3 GB + 1.2 GB vision file, R15). 31.6 GB peak at 16,384 tokens (R16, measured, text run). 7.3 tok/s on an M4 Max 64GB at 16k (R16). Why: MMMU Pro 76.9% (R14).
5. Long documents: Qwen3.8 27B, Q8_0 29 GB (R1). 46.18 GB at 262,144 tokens (derived, R8). No measured figure at that length on a 64GB setup. Why: only 16 of 64 layers keep a cache (R8).
6. Fastest: Qwen3.6 35B A3B, 8-bit MLX 37.72 GB (R19). 38.9 GB peak at 32k (R18). 97.8 tok/s on an M5 Max 64GB at 4k (R18). Why: 3B active, SWE-bench Verified 73.4 (R20).
7. Biggest that fits: Qwen3.5 122B A10B, Q3_K_S 52.5 GB (R22). 53.31 GB at 32,768 tokens (derived, R23). No measured figure on a 64GB setup (R26 is 128GB). Why: Framework says the 52.5GB Q3 file fits (R21).
{% endraw %}

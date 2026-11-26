---
layout: default
title: "Best Local AI With 0GB Of VRAM (No GPU Needed)"
permalink: /best-local-ai-0gb-vram/
date: 2026-11-26
---

# Best Local AI With 0GB Of VRAM (No GPU Needed)

{% raw %}
Researched 2026-11-26. Every figure below was read on 2026-11-26 from the page cited. The question (different from
the 2026-11-17 video, which asked how big a model 64GB of RAM holds): with no graphics card at all, which model is
best on the ordinary 8GB, 16GB and 32GB PCs and laptops people already own, ranked by measured CPU-only speed?
The finding: a mixture-of-experts model reads only its active slice per word, so on a CPU a 30B MoE in a 10.3 GB file
runs faster than dense 8B-9B models, and it fits a 16GB PC.

## Sources

R1: https://byteshape.com/blogs/Qwen3-30B-A3B-Instruct-2507 (accessed 2026-11-26) ByteShape Team, January 5, 2026, Qwen3-30B-A3B-Instruct-2507 quants measured on CPU (llama.cpp GGUF): "Intel i7 with 64GB RAM": ByteShape CPU-2 "Q3_K_S-2.70bpw [KQ-2]" 27.57 TPS at accuracy 0.9418; CPU-5 "Q3_K_S-3.25bpw [KQ-5]" 23.09 TPS at 0.9797 ("combines ~98% accuracy with 23.1 TPS"); Unsloth Q4_K_M 18.32 TPS; Unsloth Q8_0 12.73 TPS. "On a Pi 5 (16GB), Q3_K_S-2.70bpw [KQ-2] hits 8.03 TPS at 2.70 BPW and maintains 94.18% of BF16 quality"; Pi KQ-7 (Q4_K_S-3.92bpw) 5.30 TPS. No exact i7 model or llama.cpp version given.
R2: https://huggingface.co/byteshape/Qwen3-30B-A3B-Instruct-2507-GGUF/tree/main (accessed 2026-11-26) file sizes: Qwen3-30B-A3B-Instruct-2507-Q3_K_S-2.70bpw.gguf 10.3 GB; Q3_K_S-3.25bpw 12.4 GB; Q4_K_S-3.92bpw 14.9 GB
R3: https://bkataru.github.io/igllama/showcase/qwen35-small/ (accessed 2026-11-26) igllama v0.3.7 (llama.cpp gguf-v0.18.0), "AMD EPYC-Rome (16 cores / 32 threads @ 2.0 GHz)", "30 GB DDR4", GPU "None (CPU-only)", 8 threads generation, Q4_K_XL: Qwen3.5-0.8B 0.53 GB 23.01 tok/s; Qwen3.5-2B 1.28 GB 18.38 tok/s; Qwen3.5-4B 2.71 GB 8.48 tok/s; Qwen3.5-9B 5.56 GB 6.45 tok/s; page undated
R4: https://bkataru.github.io/igllama/showcase/qwen35-35b/ (accessed 2026-11-26) same machine and runtime: Qwen3.5-35B-A3B UD-Q4_K_XL 19.17 GB, "5.56 tok/s @ 8 threads", RAM usage "~22 GB" with an 8K KV cache; 4.40 tok/s at 4 threads, 2.86 at 16 threads; page undated
R5: https://huggingface.co/ubergarm/Qwen3-30B-A3B-GGUF/discussions/2 (accessed 2026-11-26) ubergarm, Jun 30, 2025: "tuned AMD 9950x rig with 2x48GB DDR5@6400MT/s (~88GB/s RAM bandwidth)", Qwen3-30B-A3B mix-IQ4_K, ik_llama.cpp llama-sweep-bench, CPU only, TG 33.93 t/s at N_KV 0, 32.92 at 1024
R6: https://ollama.com/library/qwen3/tags (accessed 2026-11-26) qwen3:30b-a3b-q4_K_M 19GB; qwen3:4b 2.5GB; qwen3:8b 5.2GB; qwen3:14b 9.3GB
R7: https://ollama.com/library/qwen3.5/tags (accessed 2026-11-26) qwen3.5:0.8b-q8_0 1.0GB; qwen3.5:2b-q4_K_M 1.9GB; qwen3.5:4b-q4_K_M 3.3GB; qwen3.5:9b-q4_K_M 6.6GB; qwen3.5:35b-a3b-q4_K_M 22GB
R8: https://ollama.com/library/gemma4/tags (accessed 2026-11-26) gemma4:e2b-it-q4_K_M 4.6GB; gemma4:e4b-it-q4_K_M 6.6GB; gemma4:12b-it-q4_K_M 8.0GB
R9: https://raw.githubusercontent.com/geerlingguy/ai-benchmarks/master/README.md (accessed 2026-11-26) Jeff Geerling's ai-benchmarks (no dates or quants per row): Pi 5 16GB CPU Llama 3.2:3b 4.88 tok/s at 11.9W peak; Pi 5 8GB CPU Llama 3.2:3b 4.61 tok/s; GMKtec G3 Plus (Intel N150) 16GB CPU Llama 3.2:3b 9.06 tok/s; Dell Optiplex 780 (Q8400) 1.09 tok/s
R10: https://www.mgroeber.de/benchmarking-llamacpp-on-legacy-hardware-2.html (accessed 2026-11-26) Marcus Groeber, 2 Feb 2026 updated 20 Aug 2026, llama-bench -p 512 -n 128, Llama 2 7B Q4_0: Lenovo Yoga 730 (i7-8550U, 16 GB, 2018) 6.37 ± 0.08 tok/s at 8 threads (5.64 at 4); Samsung S22 Ultra (8 GB, Q3_K - Small) 1.73 ± 0.53; ZOTAC i5-3470T 2.46
R11: https://kreier.github.io/benchmark/llm (accessed 2026-11-26) kreier's Ollama benchmark, CPU only (num_gpu 0): i7-8700 llama3.1:8b 5.9 tok/s, llama3.2:3b 12.1 tok/s; i3-10100 llama3.1:8b 5.4
R12: https://ollama.com/library/llama3.2/tags (accessed 2026-11-26) llama3.2:3b 2.0GB; llama3.2:1b 1.3GB
R13: https://github.com/Niko1221/Strata (accessed 2026-11-26) Strata, free, open source; supports "NVIDIA GeForce RTX 20 / 30 / 40 / 50 series", recent Radeon, Intel Arc (Linux), Apple Silicon, Strix Halo, DGX Spark; no CPU-only build listed; Inkling 2 Mini: "A 4 GiB card is enough to start"
R14: https://github.com/Niko1221/Strata/releases (accessed 2026-11-26) Strata 0.2.22 released 25 Nov 2026; 0.2.21: "RTX 3060 Ti 8 GB, SQ-10: 43 instead of 11 tok/s" (Inkling 2 Mini)
R15: https://resaleprices.com/gpu/nvidia-rtx-2060 (accessed 2026-11-26) used RTX 2060 6GB market average $164, fair range $150-$170, 159 listings, updated Nov 25, 2026
R16: https://www.pishop.us/product/raspberry-pi-5-16gb/ (accessed 2026-11-26) Raspberry Pi 5 16GB, $385.00, out of stock
R19: https://www.raspberrypi.com/news/price-rises-for-some-16gb-raspberry-pi-products/ (accessed 2026-11-26) Eben Upton, 2 Nov 2026: Raspberry Pi 5 16GB rises by $80 "to $385"; cause "a lack of alternative supply for 16GB DRAM"
R17: https://github.com/ggml-org/llama.cpp/blob/master/tools/server/README.md (accessed 2026-11-26) llama.cpp server options: "-m, --model FNAME" "model path to load"; "-t, --threads N" "number of CPU threads to use during generation (default: -1)"; "-c, --ctx-size N" "size of the prompt context (default: 0, 0 = loaded from model)"; "-cmoe, --cpu-moe" "keep all Mixture of Experts (MoE) weights in the CPU"; "-ncmoe, --n-cpu-moe N" "keep the Mixture of Experts (MoE) weights of the first N layers in the CPU"; "-ngl, --gpu-layers, --n-gpu-layers N"
R18: https://github.com/ggml-org/llama.cpp/discussions/28248 (accessed 2026-11-26) MichaelDietzel, comment dated Sep 9, 2026: "CPU + RAM: EPYC 7401P + 8 channel DDR4 @ 136GB/s", model "Qwen3.6-35B-A3B-UD-Q6_K_XL", llama-bench token generation: "Baseline CPU-only speed: 14.97 ± 0.06"; with a 2080 Ti 22GiB and --n-cpu-moe 40: 38.20, 30: 44.34, 20: 49.57, 13: 54.25 ± 3.29 tok/s

## The evidence kit

HERO: R1 R2 Qwen3 30B A3B in ByteShape's Q3_K_S-2.70bpw quant (a 10.3 GB file) writes 27.57 tok/s on an Intel i7 with no graphics card, keeping 94.18% of the full model's accuracy score, so a 30B model runs on a 16GB PC with no GPU
COUNTER: R3 R4 dense models don't get that lift: on one CPU-only EPYC box with DDR4, Qwen3.5 9B (5.56 GB) writes 6.45 tok/s and Qwen3.5 4B 8.48 tok/s, so a bigger dense model slows down in step with its file size
STEELMAN: R10 R11 R9 the "it's too slow" case: an ordinary 2018 laptop (i7-8550U, 16 GB) writes 6.37 tok/s on Llama 2 7B, an i7-8700 desktop 5.9 tok/s on Llama 3.1 8B, a Pi 5 4.88 tok/s on Llama 3.2 3B: dense 7B-8B models on everyday CPUs sit around 6 tok/s
UNIT-CHAIN: R2 R1 16GB of RAM -> the 10.3 GB Qwen3 30B A3B file fits with 5.7 GB left -> only about 3B of its 30B parameters work on each word -> 27.57 tok/s on the i7 -> a 500-token answer in about 18.14 s (500 / 27.57); the same file on a Pi 5 at 8.03 tok/s takes about 62.27 s
MONEY-OBJECT: R13 R15 the next step up is a used graphics card: Strata runs on RTX 20 series and newer, and the cheapest one in the used data is an RTX 2060 6GB at $164
PRICES: R15 R16 as of 2026-11-26: used RTX 2060 6GB $164 average (159 listings); Raspberry Pi 5 16GB $385.00 out of stock (PiShop)
BENCH: R1 Qwen3 30B A3B Instruct 2507, ByteShape Q3_K_S-2.70bpw, Intel i7 64GB, CPU only: 27.57 TPS (accuracy 0.9418); Q3_K_S-3.25bpw 23.09 TPS (0.9797); Unsloth Q4_K_M 18.32; Unsloth Q8_0 12.73; Pi 5 16GB: 8.03 TPS; R3 Qwen3.5 0.8B/2B/4B/9B 23.01/18.38/8.48/6.45 tok/s CPU only; R4 Qwen3.5 35B A3B 5.56 tok/s CPU only
STRATA: R13 R14 R15 Strata needs a graphics card (RTX 20 series or newer, recent Radeon, Arc, Apple Silicon): no CPU-only build. Say it as the step up: a used RTX 2060 6GB at $164 runs it, "A 4 GiB card is enough to start" for Inkling 2 Mini, and 0.2.21 took an RTX 3060 Ti 8GB from 11 to 43 tok/s on it
VIRAL: NONE: no single widely shared post on CPU-only local AI in 2026 with measurable reach was found
COMMUNITY: R5 R10 R11 ubergarm measured Qwen3 30B A3B at 33.93 t/s on a Ryzen 9 9950X with DDR5-6400 and no GPU (ik_llama.cpp, June 2025); Marcus Groeber ran llama-bench on his own 2018 laptop (6.37 tok/s) and phone (1.73 tok/s); kreier timed an i7-8700 at 5.9 tok/s on Llama 3.1 8B
UNMEASURED: R1 R4 no one has published a CPU-only run of a 2026 MoE (Qwen3.5 35B A3B) on an ordinary 16GB or 32GB home PC: R4 is a 2.0 GHz EPYC server with DDR4; ByteShape does not name its i7 model or its memory speed; no Gemma 4 CPU-only run was found
PATTERN: R3 R4 R1 on the same machine, size stops deciding speed once a model is a mixture of experts: on the EPYC box the 35B A3B (19.17 GB) writes 5.56 tok/s against the dense 4B's 8.48 (65.57% of its speed at 7.07x the file); on the i7 the 30B A3B at 2.70 bpw writes 27.57 tok/s
SPONSOR: none (no paid sponsor; the ending discloses our own Amazon affiliate links for the used RTX 2060 and the Raspberry Pi 5 16GB, from channel.json affiliate, per check-script's link-line rule)
HYBRID: R18 R17 on an EPYC 7401P with 8-channel DDR4 (136GB/s), Qwen3.6 35B A3B at Q6 writes 14.97 tok/s CPU only; with a 2080 Ti 22GiB holding the rest and the experts of the first 13 layers kept in RAM (--n-cpu-moe 13) it writes 54.25 tok/s, 3.62x (54.25 / 14.97)
READ-VS-WRITE: R5 ubergarm's CPU-only run reads a prompt at 576.96 tok/s and writes at 33.93 tok/s: reading is 17.00x faster than writing (576.96 / 33.93)
CONTEXT-MEMORY: R4 the 35B A3B file is 19.17 GB and uses about 22 GB with an 8K KV cache: about 2.83 GB for the chat (22 - 19.17)
ARTEFACT: 2026-11-26 read ByteShape's CPU tables and file list, igllama's CPU-only Qwen3.5 tables, ubergarm's sweep, Geerling's, Groeber's and kreier's tables and Ollama's tag pages, and worked the numbers: 16 - 10.3 = 5.7 GB; 500 / 27.57 = 18.14 s; 500 / 8.03 = 62.27 s; 5.56 / 8.48 = 0.6557; 19.17 / 2.71 = 7.07; 27.57 / 12.73 = 2.17

## By RAM size: the best model with no GPU

- **8GB PC or laptop.** Qwen3.5 4B (Ollama q4_K_M 3.3GB, R7): 8.48 tok/s CPU only on the EPYC box (R3). Llama 3.2 3B
  (2.0GB, R12) 12.1 tok/s on an i7-8700 (R11), 9.06 on an N150 mini PC (R9). Gemma 4 E2B (4.6GB, R8): no CPU run found.
- **16GB.** Qwen3 30B A3B, ByteShape Q3_K_S-2.70bpw 10.3 GB (R2): 27.57 tok/s on the i7 (R1), 8.03 on a Pi 5 16GB (R1).
  The dense alternatives: Qwen3.5 9B 6.6GB (R7) at 6.45 tok/s (R3); qwen3:14b 9.3GB (R6).
- **32GB.** Qwen3.5 35B A3B, 19.17 GB at Q4 (R4), about 22 GB in use with an 8K context: 5.56 tok/s on the 2.0 GHz
  EPYC box; the Ollama q4_K_M is 22GB (R7). Qwen3 30B A3B at Q4_K_M (Ollama 19GB, R6): 18.32 tok/s on the i7 (R1).
- **The old laptop and the phone.** 2018 i7-8550U laptop 6.37 tok/s on Llama 2 7B (R10); S22 Ultra phone 1.73 (R10).
- **The step up:** a GPU. Strata (R13) starts at RTX 20 series; used RTX 2060 6GB $164 (R15).

## Verdict (for the script to prove, not to open with)

With 16GB and no GPU, run Qwen3 30B A3B in a 3-bit quant: a mixture of experts reads about 3B parameters a word, so it
beats every dense 8B-9B model on speed while being far bigger. With 8GB, Qwen3.5 4B. With 32GB, the 30B A3B at 4-bit
(18.32 tok/s on the i7) beats Qwen3.5 35B A3B on speed. A GPU is the next step, and that's where Strata starts.
{% endraw %}

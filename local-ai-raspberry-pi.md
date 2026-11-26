---
layout: default
title: "What Local AI Actually Runs On A Raspberry Pi"
permalink: /local-ai-raspberry-pi/
date: 2026-11-26
---

# What Local AI Actually Runs On A Raspberry Pi

{% raw %}
Researched 2026-11-26. Every price below was read on 2026-11-26 from the page cited. US prices, before tax and shipping.
The question (different from the 0GB-VRAM video, which picked models for CPU-only PCs, and the 24/7 video, which compared
whole always-on machines on power): with the Raspberry Pi 5 as the box, which Pi and how much memory, what is the biggest
model that really fits, which model for each job with a measured Pi speed, is the AI HAT+ 2 worth it, and does a used
mini PC at the same price beat the Pi?
The finding: a 30B model (Qwen3 30B A3B, ByteShape's 10.3 GB 2.70bpw file) runs at 8.03 tok/s on a Pi 5 16GB, but the
16GB board is $385 since 2 Nov 2026; the $200 AI HAT+ 2 is slower than the Pi's own CPU on every model CNX measured;
and a refurbished 16GB office mini PC costs $199.99, $12.04 more than an 8GB Pi with its power supply.

## Sources

R1: https://www.pishop.us/product/raspberry-pi-5-16gb/ (accessed 2026-11-26) PiShop US (official reseller), Raspberry Pi 5 16GB, price "385", availability InStock
R2: https://www.pishop.us/product/raspberry-pi-5-8gb/ (accessed 2026-11-26) PiShop US, Raspberry Pi 5 8GB, price "175", availability OutOfStock
R3: https://www.pishop.us/product/raspberry-pi-5-4gb/ (accessed 2026-11-26) PiShop US, Raspberry Pi 5 4GB, price "110", availability InStock
R4: https://www.pishop.us/product/raspberry-pi-5-2gb/ (accessed 2026-11-26) PiShop US, Raspberry Pi 5 2GB, price "77.5", availability OutOfStock
R5: https://www.raspberrypi.com/news/price-rises-for-some-16gb-raspberry-pi-products/ (accessed 2026-11-26) Eben Upton, 2 Nov 2026: Raspberry Pi 5 16GB rises by $80 "to $385"; cause "a lack of alternative supply for 16GB DRAM"
R6: https://www.techradar.com/pro/raspberry-pi-5-price-hike-means-the-16gb-model-now-costs-three-times-what-it-did-at-launch-and-of-course-the-global-ram-shortage-is-to-blame (accessed 2026-11-26) TechRadar, 7 Nov 2026: Pi 5 16GB launched at $120 (January 2025), now $385
R7: https://www.pishop.us/product/raspberry-pi-27w-usb-c-power-supply-white-us/ (accessed 2026-11-26) PiShop US, Raspberry Pi 27W USB-C Power Supply White US (SC1153), price "12.95", InStock
R8: https://byteshape.com/blogs/Qwen3-30B-A3B-Instruct-2507/ (accessed 2026-11-26) ByteShape, 5 Jan 2026: "On a Pi 5 (16GB), Q3_K_S-2.70bpw [KQ-2] hits 8.03 TPS at 2.70 BPW and maintains 94.18% of BF16 quality"; "generation feels real-time once it reaches roughly 8 TPS"; Q4_K_S-3.92bpw 5.30 TPS; context not stated
R9: https://huggingface.co/byteshape/Qwen3-30B-A3B-Instruct-2507-GGUF/tree/main (accessed 2026-11-26) file "Qwen3-30B-A3B-Instruct-2507-Q3_K_S-2.70bpw.gguf" 10.3 GB (Hugging Face file list); the 2.66bpw file is 10.18 GB, the 3.92bpw file 14.95 GB
R10: https://huggingface.co/Qwen/Qwen3-30B-A3B-Instruct-2507/raw/main/config.json (accessed 2026-11-26) "num_hidden_layers": 48, "num_key_value_heads": 4, "head_dim": 128
R11: https://www.raspberrypi.com/news/mastering-edge-ai-on-raspberry-pi-with-litert-and-gemma/ (accessed 2026-11-26) Raspberry Pi / Google: Gemma 4 E2B, LiteRT-LM (QAT): prefill 99 tok/s, decode 9 tok/s, peak memory 1432 MB; llama.cpp (Q4_0): prefill 24, decode 4, peak 4406 MB; "Hardware: Raspberry Pi 5 (8 GB RAM variant)"; "1024 prefill tokens and 256 decode tokens; the CPU runs with four threads"; LiteRT-LM model size 2468 MB
R12: https://raw.githubusercontent.com/geerlingguy/ai-benchmarks/master/README.md (accessed 2026-11-26) Jeff Geerling's ai-benchmarks, Llama 3.2:3b table: Pi 5 16GB CPU 4.88 Tokens/s, 11.9W peak; Pi 5 8GB CPU 4.61, 13.9W; GMKtec G3 Plus (Intel N150) 16GB CPU 9.06, 26.4W; DeepSeek R1 14b table: Pi 5 16GB CPU 1.20 Tokens/s, 13.0W; GMKtek G3 Plus (Intel N150) 16GB CPU 2.13 Tokens/s, 30.3W; context not stated
R23: https://www.raspberrypi.com/products/raspberry-pi-5/ (accessed 2026-11-26) Raspberry Pi 5 specification: "Broadcom BCM2712 2.4GHz quad-core 64-bit Arm Cortex-A76 CPU"
R13: https://ollama.com/library/llama3.2/tags (accessed 2026-11-26) llama3.2:latest (3b) 2.0GB
R14: https://huggingface.co/unsloth/Llama-3.2-3B-Instruct/raw/main/config.json (accessed 2026-11-26) "num_hidden_layers": 28, "num_key_value_heads": 8, "head_dim": 128
R15: https://www.cnx-software.com/2026/01/20/raspberry-pi-ai-hat-2-review-a-40-tops-ai-accelerator-tested-with-computer-vision-llm-and-vlm-workloads/ (accessed 2026-11-26) CNX Software, 20 Jan 2026: AI HAT+ 2 on a Raspberry Pi 5 2GB against "the Raspberry Pi development kit for CM5 using the Broadcom BCM2712 CPU cores, 4GB RAM" (Ollama 0.14.2): Qwen 2.5 instruct 1.5B 11.73 tokens/s CPU vs 6.74 HAT; Qwen 2.5 Coder 1.5B 10.26 vs 8.06; Llama3.2 3B 4.78 vs 2.60; Deepseek R1 1.5B 9.04 vs 6.72; Qwen2 1.5B 11.29 vs 5.89; the CPU Qwen 2.5 1.5B instruct run: "prompt eval count: 40 token(s)", "prompt eval rate: 21.39 tokens/s", "eval count: 8 token(s)", "eval rate: 11.73 tokens/s"; HAT results "might include the prompt evaluation time"; HAT runs through hailo-ollama; "feels more like an AI decelerator than an AI accelerator"
R16: https://www.raspberrypi.com/products/ai-hat-plus-2/ (accessed 2026-11-26) Raspberry Pi product page: "Available now for $200."; "Hailo-10H AI accelerator delivering 40 TOPS (INT4) inferencing performance"; "8GB on-board RAM"
R17: https://www.jeffgeerling.com/blog/2026/raspberry-pi-ai-hat-2/ (accessed 2026-11-26) Jeff Geerling, 15 Jan 2026: launched as the "$130 AI HAT+ 2"; tested on an 8 gig Pi 5: "The Pi's built-in CPU trounces the Hailo 10H"; "the 8 gigs of RAM holds back the LLM use case (vs just running on the Pi's CPU) the most"; vision models "10x faster than on the Pi's CPU"; the Hailo runs at 3W against the Pi SoC's 10W; "not quite enough to give this HAT an advantage over just paying for the bigger 16GB Pi"
R18: https://ollama.com/library/qwen2.5-coder/tags (accessed 2026-11-26) qwen2.5-coder:1.5b 986MB
R19: https://ollama.com/library/qwen2.5/tags (accessed 2026-11-26) qwen2.5:1.5b 986MB
R20: https://huggingface.co/Qwen/Qwen2.5-1.5B-Instruct/raw/main/config.json (accessed 2026-11-26) "num_hidden_layers": 28, "num_key_value_heads": 2, "hidden_size": 1536, "num_attention_heads": 12 (head_dim 128), "max_position_embeddings": 32768; Qwen2.5-Coder-1.5B-Instruct config identical on these keys
R21: https://shop.pcworld.com/sales/lenovo-thinkcentre-m710q-tiny-intel-core-i5-6500t-16gb-ram-512gb-solid-state-drive-windows-10-pro-refurbished (accessed 2026-11-26) Lenovo ThinkCentre M710Q Tiny (2017, refurbished), i5-6500T, 16GB RAM, 512GB SSD, $199.99 (was $249.00), "Selling Fast", Add To Cart
R22: https://github.com/Niko1221/Strata (accessed 2026-11-26) Strata, free and open source; downloads "Strata-0.2.22-windows-x64-setup.exe", "Strata-0.2.22-linux-x86_64.AppImage", "Strata-0.2.22-macos-arm64.dmg" (no ARM Linux or Raspberry Pi build); supported hardware: "NVIDIA GeForce RTX 20 / 30 / 40 / 50 series", AMD Radeon RX 7700-7900 / 9060 / 9070 / AI PRO R9700, Intel Arc (Linux), Apple Silicon M1 or newer, Strix Halo

## The evidence kit

HERO: R8 R9 R1 a 30-billion-parameter model, Qwen3 30B A3B (ByteShape Q3_K_S-2.70bpw, a 10.3 GB file), writes 8.03 tok/s on a Raspberry Pi 5 16GB, which ByteShape calls real time; the board is $385
COUNTER: R5 R6 R1 the 16GB Pi 5 launched at $120 in January 2025 and is $385 since 2 Nov 2026 (3.21 times), because of the 16GB DRAM shortage, so the board that holds the big model costs more than a refurbished 16GB mini PC ($199.99, R21)
STEELMAN: R12 R11 the Pi's case: a Pi 5 16GB drew 11.9W peak running Llama 3.2 3B against 26.4W for the N150 mini PC in the same table, and Gemma 4 E2B runs in 1432 MB on an 8GB Pi at 9 tok/s
UNIT-CHAIN: R9 R10 R1 16GB Pi 5 -> Qwen3 30B A3B 2.70bpw file 10.3 GB -> its cache is 2 x 48 x 4 x 128 x 2 = 98,304 bytes a token -> 0.40 GB at 4,096 tokens -> 10.70 GB in all -> 5.30 GB left of 16 for the system; on an 8GB Pi it does not fit
MONEY-OBJECT: R1 R2 R3 R4 the Pi 5 boards: 2GB $77.50 (out of stock), 4GB $110, 8GB $175 (out of stock), 16GB $385 (PiShop)
PRICES: R1 R2 R3 R4 R7 R16 R21 as of 2026-11-26: Pi 5 16GB $385 in stock; 8GB $175 out of stock; 4GB $110 in stock; 2GB $77.50 out of stock (PiShop US); 27W USB-C power supply $12.95 (PiShop); AI HAT+ 2 $200 (raspberrypi.com, "Available now"); refurbished ThinkCentre M710Q i5-6500T 16GB 512GB $199.99 (PCWorld Shop)
BENCH: R8 Qwen3 30B A3B 2.70bpw 8.03 tok/s on a Pi 5 16GB (ByteShape); R11 Gemma 4 E2B LiteRT-LM 9 tok/s decode, 99 prefill, 1432 MB peak, Pi 5 8GB, 1,024 + 256 tokens (Raspberry Pi / Google); R12 Llama 3.2 3B 4.88 tok/s Pi 5 16GB, 9.06 GMKtec G3 Plus N150 16GB (Geerling); R15 Qwen 2.5 Coder 1.5B 10.26 tok/s and Qwen 2.5 1.5B 11.73 tok/s on a CM5 4GB CPU, 8.06 and 6.74 on the AI HAT+ 2 (CNX)
STRATA: R22 Strata, the free open source engine for speeding up and fitting models, ships for Windows x64, Linux x86_64 and Apple Silicon Macs, starting at RTX 20 series cards: there is no Raspberry Pi build, so it is the step up after a Pi, not something to install on one
VIRAL: NONE: Zero to MVP's "Gemma 4 on Raspberry Pi 5" video (435k views) is a creator test, not a written post with figures we can cite
COMMUNITY: R12 R15 R17 Jeff Geerling's own benchmark table and AI HAT+ 2 review, and Jean-Luc Aufranc's CNX Software review, are individual measurements
UNMEASURED: R21 R12 no measured tok/s for the ThinkCentre M710Q (i5-6500T) on any model; the only mini PC in Geerling's table is the N150 GMKtec G3 Plus, which has no live price here; no source states the context for ByteShape's 8.03 tok/s or Geerling's 4.88 tok/s
PATTERN: R15 R17 the AI HAT+ 2 lost to the Pi's own CPU on all five models CNX ran (Qwen 2.5 1.5B 6.74 against 11.73), and Geerling: "The Pi's built-in CPU trounces the Hailo 10H"; the 3W NPU cannot keep up with the 10W CPU
SPONSOR: none (no paid sponsor; the ZoneBlade house ad, and one Amazon affiliate link for the Raspberry Pi 5 from channel.json affiliate)
ARTEFACT: 2026-11-26 worked each pick's memory at a stated context from its config (2 x layers x KV heads x head_dim x 2 bytes a token): Qwen3 30B 98,304 bytes x 4,096 = 0.40 GB + 10.3 = 10.70 GB; Llama 3.2 3B 114,688 x 4,096 = 0.47 GB + 2.0 = 2.47 GB; Qwen 2.5 Coder 1.5B 28,672 x 4,096 = 0.12 GB + 0.986 = 1.10 GB; Qwen 2.5 1.5B 28,672 x 32,768 = 0.94 GB + 0.986 = 1.93 GB at 32,768 tokens
ARTEFACT: 2026-11-26 the Pi against a refurbished mini PC at the same money: Pi 5 8GB $175 + $12.95 power supply = $187.95, against the 16GB M710Q at $199.99, $12.04 more for twice the memory and a 512GB SSD; the 16GB Pi at $385 costs $185.01 more than the M710Q; a 500-token answer takes 62.27 s at 8.03 tok/s, 55.56 s at 9, 102.46 s at 4.88; HAT vs CPU 11.73 / 6.74 = 1.74 times

## The six sections (three facts per model)

1. Which Pi: 2GB $77.50 (out of stock), 4GB $110, 8GB $175 (out of stock), 16GB $385 (R1-R4), up from $120 in January 2025 (R6). Power supply $12.95 (R7).
2. Biggest that fits: Qwen3 30B A3B Instruct 2507, ByteShape Q3_K_S-2.70bpw, 10.3 GB file (R9). 10.70 GB at 4,096 tokens (derived, R10). 8.03 tok/s on a Pi 5 16GB (ByteShape, R8). Needs the 16GB board.
3. Picks per job:
   - Chat: Gemma 4 E2B, LiteRT-LM QAT build (2468 MB model, R11). 1432 MB peak at 1,024 + 256 tokens (R11, measured). 9 tok/s on a Pi 5 8GB (Raspberry Pi / Google, R11).
   - Coding help: Qwen 2.5 Coder 1.5B, Ollama default Q4_K_M 986MB (R18). 1.10 GB at 4,096 tokens (derived, R20). 10.26 tok/s on a CM5 4GB, the Pi 5's chip (CNX, R15).
   - Home assistant: Llama 3.2 3B, Ollama default Q4_K_M 2.0GB (R13). 2.47 GB at 4,096 tokens (derived, R14). 4.88 tok/s on a Pi 5 16GB (Geerling, R12).
   - Summaries: Qwen 2.5 1.5B Instruct, Q4_K_M 986MB (R19). 1.93 GB at 32,768 tokens, its full length (derived, R20). 11.73 tok/s on a CM5 4GB (CNX, R15).
4. Accelerator: AI HAT+ 2, $200, available now (R16), launched at $130 (R17); slower than the CPU on all five CNX models (R15); Geerling: CPU "trounces" it (R17). Verdict: skip it for chat models.
5. Pi vs mini PC: $187.95 Pi 5 8GB + PSU vs $199.99 refurbished M710Q 16GB (R21); M710Q no measured figure; the measured mini PC row is the N150 G3 Plus 9.06 vs Pi 5 16GB 4.88 tok/s at 26.4W vs 11.9W (R12).
6. Verdict per buyer.
{% endraw %}

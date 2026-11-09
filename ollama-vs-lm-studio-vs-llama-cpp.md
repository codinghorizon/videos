---
layout: default
title: "Ollama vs LM Studio vs llama.cpp (Local AI Speed)"
permalink: /ollama-vs-lm-studio-vs-llama-cpp/
date: 2026-11-09
---

# Ollama vs LM Studio vs llama.cpp (Local AI Speed)

{% raw %}
Compiled 2026-11-09 from pages opened that day. Format: figure — exact context — URL.
Nothing here was tested by us. Every number is the named source's own.
[FLAG] = unconfirmed, contradictory, or weak source.

## 1. Head-to-head speed runs (same model, same card)

### A. InventiveHQ: all three apps, RTX 5060 Ti 16GB (strongest three-way)
- llama.cpp direct 77.0 tok/s, LM Studio 76.8 (-0.3%), Ollama 69.1 (-10.3%) — Qwen2.5-Coder-7B Q4, identical across runners, RTX 5060 Ti 16GB in an i7-8700 Alienware Aurora R7 (PCIe 3.0 x8), Windows Server 2025. 12-prompt suite, temp 0, 256 tokens per prompt, wall-clock completion_tokens/elapsed (end-to-end, not separate prompt processing). Published 2026-06-26, modified 2026-08-13 — https://inventivehq.com/blog/ollama-vs-llama-cpp-vs-lm-studio-benchmark
- Per task (llama.cpp / LM Studio / Ollama): code 76.9/77.5/70.5, math 76.8/77.1/69.6, reasoning 77.1/77.0/69.3, summarisation 76.4/75.0/65.3, chat 78.2/77.1/69.8 — same page.
- Quote: "one engine wearing three different costumes"; "a flat ~10% gap across the board is the signature of a *structural* cost". Ollama causes given as likely (daemon layer, template engine, older bundled llama.cpp or different defaults), not confirmed — same page.
- On Apple M3 Max the order changes: llama.cpp 53.5, Ollama 46.2 (-14%), LM Studio 38.2 (-29%), blamed on LM Studio's bundled llama.cpp lagging upstream b9430 — same page (Mac, off-topic but shows "platform-dependent").
- [FLAG] App versions and context length not stated.

### B. computingforgeeks: Ollama vs llama.cpp vs vLLM on RTX 4090 and RTX 5090 (rented cards)
- Qwen3.8-27B, Q4_K_M (Ollama library qwen3.8:27b; llama.cpp unsloth UD-Q4_K_M), 474-token prompt, 256 output, temp 0. Versions: llama.cpp "v0.6.0", Ollama 0.35.1, vLLM 0.31.0. Measured October 2026, updated 2026-10-06 — https://computingforgeeks.com/ollama-vs-vllm-vs-llama-cpp/
- RTX 4090, single user decode: vLLM 54.3, llama.cpp 49.5, Ollama (draft off) 39.9 (19% slower than llama.cpp), Ollama with MTP draft 76.2 — same page.
- RTX 5090, single user decode: vLLM 85.7, llama.cpp 77.8, Ollama (draft off) 76.8 (within 2%), Ollama MTP 129.7 — same page.
- 32 concurrent users, aggregate tok/s: RTX 4090 llama.cpp 306, vLLM 300, Ollama 39 (flat, no gain). RTX 5090 vLLM 936, llama.cpp 369, Ollama 74. Time to first token at 32 users on 4090: llama.cpp 6.5 s, Ollama 101.7 s — same page.
- Quote: "Ollama runs one request at a time on the newest Qwen models" — it classes Qwen3.8 as `qwen35`, refuses parallel slots and launches its runner with `-np 1`; importing the identical GGUF into Ollama gave the same result — same page.
- Ollama enables MTP speculative decoding by default (1.7-1.9x single user on 4090/5090); vLLM needs a flag and could not start it on the 24GB card — same page.
- 4090 gap "likely, but not proven" to be the llama.cpp build Ollama bundles — same page.
- [FLAG] "llama.cpp v0.6.0" is not llama.cpp's own b-number scheme; the page's naming, not ours.

### C. techfuelhq: Ollama vs llama-server, RTX 5080 (author-measured)
- Ollama 0.32.1 vs llama.cpp b10507, 4096 context both, full GPU offload, temp 0, 256-token generations, median of 5. Measured 2026-08-20, updated 2026-09-28 — https://techfuelhq.com/self-hosted/ollama-vs-llamacpp-rtx-5080-2026/
- Decode tok/s (Ollama / llama.cpp): Llama 3.2 3B 319 / 338 (~6%); Qwen 2.5 14B 99.4 / 101.4 (~2%); gpt-oss 20B 195.8 / 222-238 (~13-22%, different GGUF conversions) — same page.
- Prompt processing (~420 tokens) is the other way: Llama 3.2 3B 17,444 vs 16,809 (Ollama ~4% faster); Qwen 2.5 14B 5,004 vs 4,697 (Ollama ~7% faster) — same page.
- Overhead ladder, Llama 3.2 3B: llama-bench 367, llama-server 338, Ollama 319 tok/s — same page.
- [FLAG] Quant not named (same GGUF bytes both sides). RTX 5080 not on the brief's card list.

### D. dev.to (maruhana): the 15% gap was the defaults
- Out of the box Ollama 101.89 / 104.12 / 100.11 tok/s vs llama.cpp (Llama-Windows) 87.97 / 86.19 / 85.70 — Qwen3.6-35B-A3B Q4_K_M, 262,144 context both, Ollama 0.40.7 vs llama.cpp b11706, Nvidia RTX Spark N1X laptop on Windows 11 Arm64, dated Nov 9 — https://dev.to/maruhana/ollama-vs-llamacpp-on-the-same-gguf-the-15-speed-gap-was-the-defaults-not-the-engine-3hcl
- Causes quoted: "Ollama uses MTP speculative decoding (2 draft tokens) by default"; "The sampling defaults did not match either" (Ollama temp 1.0, top_k 20, min_p 0, presence_penalty 1.5 vs llama.cpp 0.8 / 40 / 0.05 / 0) — same page.
- Matched settings: no draft, greedy 81.69 vs 80.44; MTP 2 tokens greedy 104.04 vs 110.85 (llama.cpp ahead) — same page.
- [FLAG] Laptop Arm chip with Nvidia GPU, not a desktop RTX card. One prompt, one PC. Here Ollama won by default, which contradicts A and B.

### E. dev.to (sysoft): Qwen3.6-27B on one RTX 3090
- Ollama Q4_K_M 35.7 tok/s using 23.2 GB VRAM; ik_llama.cpp same Q4_K_M 41.9 tok/s (1.17x) using 17.3 GB; + IQ4_XS 47.5; + MTP ~75 (about 2.1x Ollama). Ollama num_ctx 8192, llama.cpp -c 4096, flash attention on. Posted 2026-06-09, corrected 2026-06-10 — https://dev.to/sysoft/doubling-qwen36-27b-on-one-rtx-3090-ollama-llamacpp-mtp-lever-by-lever-357-802-toks-4i8
- Mainline llama.cpp MTP effect 45.1 -> 74.6 (1.65x) — same page.
- [FLAG] Engine step is ik_llama.cpp (a fork), not mainline; contexts differ (8192 vs 4096); Ollama version not stated; WSL2.

### F. praveentechworld: Ollama vs LM Studio vs vLLM, RTX 4090, Windows 11
- Llama-3.1-8B-Instruct Q4_K_M: Ollama 88.4, LM Studio 86.1, vLLM (AWQ, WSL2) 85.7 tok/s. Active VRAM 5.62 / 5.78 / 6.84 GB; idle VRAM 0.0 / 1.2 / 21.6 GB. Published 2026-09-06, updated 2026-10-16 — https://www.praveentechworld.com/blog/ollama-vs-vllm-vs-lm-studio-windows-11-wsl2-benchmark/
- Aggregate at 16 streams: Ollama 102.1, LM Studio 98.4, vLLM 326.4 tok/s — same page.
- [FLAG] Versions listed are Ollama v0.3.12, LM Studio v0.3.2, vLLM 0.6.1 (2024 builds) in a 2026 article; headline numbers inconsistent with its own table. Weak.

### G. Ollama's own claim
- "up to 20% faster" on NVIDIA with Ollama 0.30, chart only, Gemma 4 26B Q4_K_M on RTX 5090; GGUF support "through llama.cpp". Blog dated 2026-06-05 — https://ollama.com/blog/gguf
- [FLAG] Vendor claim, no absolute tok/s, faster than its own previous version, not than llama.cpp.

### Weak/unusable roundups (do not quote as measurements)
- [FLAG] tech-insider.org: "[Tested]" headline but no method; dated April 19, 2026 yet cites late-October events; "5x memory gap" is 500 MB / 100 MB of claimed overhead; cites Olud.ai Llama 3.3 70B on one 4090 Ollama 48 vs LM Studio 44 — https://tech-insider.org/lm-studio-vs-ollama-2026/
- [FLAG] promptquorum: Llama 3.3 70B Q4_K_M on an RTX 4090 at "39 GB VRAM" (impossible on a 24 GB card), llama.cpp 38 / Ollama 36 — https://www.promptquorum.com/local-llms/llamacpp-vs-ollama-vs-vllm
- [FLAG] markaicode: withdrew its own in-house numbers; cites "llama.cpp is 3-10% faster than Ollama on NVIDIA GPUs" (Ajit Singh roundup) — https://markaicode.com/benchmarks/ollama-vs-llamacpp-benchmark/
- singhajit roundup: "3-10%" llama.cpp advantage attributed to Ollama's Go server layer, no absolute Ollama NVIDIA numbers — https://singhajit.com/llm-inference-speed-comparison/
- r/LLMDevs (u/deepu105, ~Dec 2025, snapshot 2026-06-05): "At matched flags, Ollama and llama.cpp converge on most cells"; no tok/s in captured text — https://reddit.sentinel-team.org/posts/1tvtmd5/snapshots/2026-06-05T21%3A16%3A39.776657Z
- [FLAG] No clean r/LocalLLaMA thread with three-app numbers on a named RTX card was found.

Summary of who wins: llama-server wins single-user decode in A, B, C, E (2-19%, up to ~17% engine-only in E); LM Studio within 0.3% of llama-server on Nvidia (A); Ollama wins only where its defaults turn on MTP drafting (B, D) or on prompt processing (C, 4-7%).

## 2. Why they differ: the defaults (official docs, as of 2026-11-09)

### Ollama
- Context default by VRAM: "< 24 GiB VRAM: 4k context", "24-48 GiB VRAM: 32k context", ">= 48 GiB VRAM: 256k context"; change with app slider or `OLLAMA_CONTEXT_LENGTH=64000 ollama serve` — https://docs.ollama.com/context-length
- [FLAG] FAQ still says "By default, Ollama uses a context window size of 4096 tokens" (no VRAM tiers) — docs contradict each other — https://docs.ollama.com/faq
- keep_alive: "By default models are kept in memory for 5 minutes before being unloaded" — https://docs.ollama.com/faq
- OLLAMA_NUM_PARALLEL: "default 1"; RAM scales with parallel x context — https://docs.ollama.com/faq
- OLLAMA_MAX_LOADED_MODELS: "3 * the number of GPUs or 3 for CPU inference"; OLLAMA_MAX_QUEUE 512, then 503 — https://docs.ollama.com/faq
- Flash attention: used "automatically when the selected backend and devices support it"; OLLAMA_FLASH_ATTENTION=1 forces on, 0 off — https://docs.ollama.com/faq
- OLLAMA_KV_CACHE_TYPE: default f16; q8_0 about half memory; q4_0 about a quarter; global to all models; needs flash attention — https://docs.ollama.com/faq
- Offload: model loads on one GPU if it fits, else spread; `ollama ps` PROCESSOR column shows e.g. "48%/52% CPU/GPU" when spilled — https://docs.ollama.com/faq
- [FLAG] The FAQ does not document per-layer num_gpu estimation; no 2026 official source found for "estimator leaves layers on CPU".
- MTP speculative decoding on by default (2 draft tokens) and Ollama sampling defaults temp 1.0 / top_k 20 / presence_penalty 1.5 — reported by D (dev.to maruhana) and B (computingforgeeks), not found in Ollama docs [FLAG].
- Bundled llama.cpp lag: Ollama 0.35.1 bundles "llama.cpp 0.5.0-dev"; half-speed L40S result traced to the bundled build — computingforgeeks (B). dev.to D found Ollama's bundled llama-server 32 commits newer than b11706 at 0.40.7 — so lag varies by release.

### LM Studio
- Context default: 0.3.2 "reduced default context size from 8K to 4K tokens" to cut out-of-memory errors — https://lmstudio.ai/blog/lmstudio-v0.3.2 (via search result; text matched in search snippet)
- 0.4.16: "Updated default context length to 8k tokens" (page shows no date; search snippet says June 8, 2026) — https://lmstudio.ai/changelog/lmstudio/lmstudio-v0.4.16
- 0.3.24 added an app-wide default context length setting (App Settings > General) — https://lmstudio.ai/changelog/lmstudio-v0.3.24 [FLAG: from search snippet, page not opened]
- Flash attention: "Flash Attention is now enabled by default for CUDA engines" (0.3.31, no date on page) — https://lmstudio.ai/changelog/lmstudio-v0.3.31
- GPU offload: "If not specified, LM Studio will automatically determine optimal GPU usage"; `--gpu 0.5 | max | off` — https://lmstudio.ai/docs/cli/load
- Guardrails: only mentioned as "This model may be loaded based on your resource guardrails settings" in the load estimator; estimator accounts for "context length, flash attention, and whether the model is vision-enabled" — https://lmstudio.ai/docs/cli/load
- Per-model saved defaults for GPU offload, context size and flash attention — https://lmstudio.ai/docs/app/advanced/per-model
- REST load params (no defaults stated): context_length, flash_attention, offload_kv_cache_to_gpu (false = KV in system RAM), eval_batch_size, num_experts — https://lmstudio.ai/docs/developer/rest/load
- [FLAG] CUDA 12 vs Vulkan runtime default and KV cache quant default not stated in docs opened.

### llama.cpp llama-server (README on master, 2026-11-09)
- `-c/--ctx-size` "(default: 0, 0 = loaded from model)" — https://github.com/ggml-org/llama.cpp/blob/master/tools/server/README.md
- `-ngl/--gpu-layers` "either an exact number, 'auto', or 'all' (default: auto)" — same
- `--fit` "whether to adjust unset arguments to fit in device memory ('on' or 'off', default: 'on')"; `--fit-ctx` "minimum ctx size that can be set by --fit option, default: 4096"; `--fit-target` default 1024 (MiB margin) — same
- `-fa/--flash-attn` "default: 'auto'" — same
- `-np/--parallel` "(default: -1, -1 = auto)"; `--kv-unified` "enabled if number of slots is auto" — same
- Auto = 4 slots: PR #23694 says when -np is omitted the server "auto-sets n_parallel=4 and kv_unified=true" — https://github.com/ggml-org/llama.cpp/pull/23694 [FLAG: from search snippet; merge status unconfirmed]
- `-cb/--cont-batching` "(default: enabled)"; `--jinja` "(default: enabled)"; `-ctk` "(default: f16)"; `-b` 2048; `-ub` 512 — README
- `--spec-type` default "none" (draft-mtp available, off by default) — README
- Router mode: `--models-dir`, `--models-max` "(default: 4, 0 = unlimited)", `--models-autoload` enabled, `--sleep-idle-seconds` default -1 (disabled) — README

## 3. Versions, dates, licence
- Ollama latest: v0.40.15, 03 Nov (2026) — https://github.com/ollama/ollama/releases (v0.40.14 03 Nov, v0.40.13 28 Oct)
- llama.cpp latest: b12229, 09 Nov (2026) 16:41 — https://github.com/ggml-org/llama.cpp/releases
- LM Studio latest: 0.4.28, October 31, 2026 (0.4.27 Oct 29) — https://releasebot.io/updates/lm-studio/lmstudio ; notes page shows 0.4.28 without a date — https://lmstudio.ai/changelog/lmstudio-v0.4.28
- LM Studio 0.4.0 (Jan 28, 2026) added llmster headless daemon and parallel requests with continuous batching — https://lmstudio.ai/blog/0.4.0
- LM Studio also now ships "LM Studio Bionic" agent app (introduced Jul 16, 2026); lmstudio.ai/changelog currently shows Bionic 1.2.0 (Nov 5, 2026) — https://lmstudio.ai/blog , https://lmstudio.ai/changelog
- Licence: Ollama "MIT license" — https://github.com/ollama/ollama ; llama.cpp "MIT license", ~134k stars — https://github.com/ggml-org/llama.cpp
- LM Studio: "Starting today, LM Studio is free to use both at home and at work" (2025-07-08), previous separate commercial licence removed — https://lmstudio.ai/blog/free-for-work
- [FLAG] LM Studio closed source: not stated on pages opened (widely known; app is proprietary, its SDK/CLI are open). Confirm before saying on air.

## 4. Server-side / concurrency
- Ollama OLLAMA_NUM_PARALLEL default 1 — https://docs.ollama.com/faq
- Ollama at 32 users on RTX 4090 stayed at 39 tok/s aggregate vs llama.cpp 306 (Qwen3.8 architecture forced to -np 1) — https://computingforgeeks.com/ollama-vs-vllm-vs-llama-cpp/
- Ollama v0.40.15 note: recurrent and vision GGUF models "can now handle more than one request at a time" — https://github.com/ollama/ollama/releases
- llama-server: continuous batching on by default, slots auto (4 per PR #23694) — README / PR above
- LM Studio: "By default, Max Concurrent Predictions is set to 4"; continuous batching "allows the LM Studio server to dynamically combine multiple requests"; requires llama.cpp runtime v2.0.0 — https://lmstudio.ai/docs/app/advanced/parallel-requests
- LM Studio 0.4.0: unified KV cache on by default; "Parallel requests work thanks to llama.cpp's open-source continuous batching implementation"; not on MLX; no throughput numbers given — https://lmstudio.ai/blog/0.4.0
- [FLAG] praveentechworld multi-stream table (Ollama 102.1, LM Studio 98.4, vLLM 326.4 at 16 streams, RTX 4090) uses 2024 app versions — weak.
- vLLM side mention: RTX 5090 vLLM 936 tok/s at 32 users vs llama.cpp 369 — computingforgeeks.

## 5. Memory / VRAM differences
- Same Qwen3.6-27B Q4_K_M on RTX 3090: Ollama 23.2 GB VRAM (num_ctx 8192) vs ik_llama.cpp 17.3 GB (-c 4096) — https://dev.to/sysoft/doubling-qwen36-27b-on-one-rtx-3090-ollama-llamacpp-mtp-lever-by-lever-357-802-toks-4i8 [FLAG: contexts differ]
- RTX 5080 GPU memory, Ollama vs llama.cpp: Llama 3.2 3B 4,343 vs 4,339 MiB; Qwen 2.5 14B 10,941 vs 10,942; gpt-oss 20B 14,152 vs 13,037 (different conversions) — https://techfuelhq.com/self-hosted/ollama-vs-llamacpp-rtx-5080-2026/
- Context spill: DeepSeek-R1 14B Q4 on RTX 3060 12GB in Ollama: num_ctx 4096 = 35.3 tok/s, 8192 = 27.2, 16384 = 4.8 tok/s (7x drop) — author-measured, published 2026-03-03, updated 2026-11-04 — https://insiderllm.com/guides/num-ctx-vram-overflow-slow-inference/
- Speed vs context on llama.cpp, Qwen3 8B Q4_K_XL RTX 3060 12GB: 16K 42.0 tok/s, 32K 31.9 (Hardware Corner via) — https://singhajit.com/llm-inference-speed-comparison/
- Ollama idle VRAM 0.0 GB (keep_alive unload) vs LM Studio 1.2 GB idle — praveentechworld [FLAG weak]

## 6. Ollama / llama.cpp attribution (sourced only)
- Ollama May 15, 2025: "We set out to support a new engine that makes multimodal models first-class citizens"; Ollama had depended on llama.cpp; credits GGML as "the tensor library that powers Ollama's inference" — https://ollama.com/blog/multimodal-models
- Ollama June 5, 2026 (0.30): GGUF compatibility "through llama.cpp"; thanks "the work done by Georgi Gerganov and the llama.cpp maintainer teams"; Vulkan on by default — https://ollama.com/blog/gguf
- Ollama README lists llama.cpp under "Supported backends" as a "project founded by Georgi Gerganov" — https://github.com/ollama/ollama
- Ollama's own blobs not always reusable in llama.cpp: gpt-oss tagged "gptoss" which upstream refuses (techfuelhq); Qwen3.6 blob refused with `expected 4, got 3` (dev.to sysoft).
- [FLAG] No sourced community controversy quotes collected; only the above.

## 7. Prices (US, 2026-11)
- RTX 5060 Ti 16GB, the price said in the video: cheapest new listing $800 (PNY), read 2026-11-09 — https://rigprice.com/gpu/rtx-5060-ti-16gb/ . $800 / 77 tok/s = about $10.40 per token a second (llama.cpp); $800 / 69 = about $11.60 (Ollama); 10% of $800 = $80.
- Trackers and news (other cards, not said as prices in the video):
- RTX 5060 Ti 16GB: PNY $799.99 on NVIDIA marketplace (Nov 2) vs $429 MSRP — https://tech-insider.org/nvidia-rtx-50-prices-rise-november-2026-rtx-5090-3340/ [weak source]
- RTX 5070 Ti 16GB: PNY $1,269.99 NVIDIA marketplace (Nov 2) vs $749 MSRP — same page; search snippet says Notebookcheck saw Newegg cheapest at $1,339.99 — https://notebookcheck.net/Another-Nvidia-GPU-nears-twice-its-MSRP-as-RTX-5070-Ti-prices-skyrocket.1444219.0.html (not opened)
- RTX 5090: Founders Edition $1,999 out of stock; Gigabyte Aorus $3,340 Walmart Nov 2 — tech-insider above; gpupoet tracker "93 deals ... starting at $6,080" — https://gpupoet.com/gpu/learn/price/november-2026/nvidia-geforce-rtx-5090
- RTX 4090 used: gpupoet "84 ... deals ... starting at $3,370"; November lowest average of three cheapest eBay listings $3,540 — https://gpupoet.com/gpu/learn/price/november-2026/nvidia-geforce-rtx-4090
- RTX 3090 used: gpupoet "71 ... deals ... starting at $1,643"; November lowest average (three cheapest eBay listings/day) $1,541, range $1,492-1,608 — https://gpupoet.com/gpu/learn/price/november-2026/nvidia-geforce-rtx-3090
- These are eBay asking-price averages, not sold prices.

## 8. The viewer comment quoted
- "Friends don't let friends use ollama.." — @rivencarrymeriven1624, 2026-10-03, under https://youtu.be/OxIt69PyWjk ; the same comment ranks "self compiled llama.cpp > llama.cpp > unsloth studio = lm studio > ollama".
{% endraw %}

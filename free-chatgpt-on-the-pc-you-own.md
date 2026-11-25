---
layout: default
title: "Run AI Like ChatGPT At Home For Free (Local AI)"
permalink: /free-chatgpt-on-the-pc-you-own/
date: 2026-11-25
---

# Run AI Like ChatGPT At Home For Free (Local AI)

{% raw %}
R1: https://openai.com/index/introducing-gpt-oss/ (accessed 2026-11-24) dated August 5, 2025: "The gpt-oss-20b model delivers similar results to OpenAI o3-mini on common benchmarks and can run on edge devices with just 16 GB of memory"; "making it ideal for on-device use cases, local inference, or rapid iteration without costly infrastructure"; "come natively quantized in MXFP4. This allows for the gpt-oss-120B model to run within 80GB of memory, while gpt-oss-20b only requires 16GB"; "designed to be used within agentic workflows with exceptional instruction following, tool use like web search or Python code execution"; gpt-oss-120b "near-parity with OpenAI o4-mini" "on a single 80 GB GPU"; 20b is 21B total, 3.6B active, 32 experts with 4 active; 120b is 117B total, 5.1B active; natively quantized in MXFP4; Apache 2.0; built for agentic workflows with tool use such as web search and Python code execution
R2: https://arxiv.org/html/2508.10925 (accessed 2026-11-24) gpt-oss model card: "Our model has a knowledge cutoff of June 2024"; gpt-oss-20b checkpoint size 12.8GiB; "the smaller model to run on systems with as little as 16GB memory"; SWE-Bench Verified for gpt-oss-20b 37.4 low, 53.2 medium, 60.7 high
R3: https://store.steampowered.com/hwsurvey/ (accessed 2026-11-24) Steam Hardware & Software Survey: October 2026. System RAM: 4 GB 1.35%, 8 GB 7.52%, 12 GB 2.45%, 16 GB 41.42% (+3.60 points on September), 24 GB 2.31%, 28 GB 0.53%, 32 GB 37.06%, 48 GB 1.19%, 60 GB 0.99%, 64 GB 3.94%, more than 64 GB 0.60%. VRAM: 8 GB 26.92%, 10 GB 1.84%, 11 GB 0.94%, 12 GB 12.91%, 16 GB 26.35%, 20 GB 1.28%, 22 GB 0.97%, 24 GB 5.40%, 32 GB 1.40%, 64 GB 0.52% (8 GB is the most common VRAM size)
R4: https://lmstudio.ai/models/gpt-oss (accessed 2026-11-24) "To run the smallest gpt-oss, you need at least 12 GB of RAM. The largest one may require up to 65 GB."; openai/gpt-oss-20b download 12.00 GB
R5: https://lmstudio.ai/blog/free-for-work (accessed 2026-11-24) published 2025-07-08: "Starting today, LM Studio is free to use both at home and at work."
R6: https://lmstudio.ai/docs/app/system-requirements (accessed 2026-11-24) Mac: Apple Silicon (M1/M2/M3/M4), macOS 14.0 or newer, "16GB+ RAM recommended", may still work on 8GB Macs with smaller models and modest context; Intel Macs not supported. Windows: x64 and ARM (Snapdragon X Elite), AVX2 required on x64, at least 16GB RAM recommended, at least 4GB dedicated VRAM recommended. Linux: x64 and ARM64 AppImage, Ubuntu 20.04 or newer
R7: https://ollama.com/blog/new-app (accessed 2026-11-24) July 30, 2025: "Ollama's new app is now available for macOS and Windows"; "supports file drag and drop, making it easier to reason with text or PDFs"; "images can be sent to models that support them"; context length can be increased in settings, "this will require more memory"
R8: https://github.com/Niko1221/Strata (accessed 2026-11-24) "Run powerful AI on your own computer. Chat, code and work with images, locally." "Free, open source", MIT; one-click install for Windows / Linux, installers for Windows x64, Linux and macOS arm64 (Strata 0.2.21); runs Qwen3.8-Flash-Next, Hy4-Flash, Qwen3.6-35B-A3B and Inkling 2 Mini; supports RTX 20/30/40/50, Radeon RX 7000/9000, Apple Silicon M1 or newer
R9: https://github.com/Niko1221/Strata/blob/main/docs/bench-results/2026-10-09-community-rtx-3060-0141/README.md (accessed 2026-11-24) community benchmark, Strata 0.1.41, measured 2026-10-09 on Windows: one RTX 3060 12GB (with 64GB of system RAM), Qwen3.8-Flash-Next Q2_0: 42.9 tok/s decode at a 4,096-token prompt, 38.6 at 127,999, 37.4 at 260,000 (medians of three)
R10: https://github.com/Niko1221/Strata/releases (accessed 2026-11-24) Strata 0.2.21, released 2026-11-24: "RTX 3060 Ti 8 GB, SQ-10: 43 instead of 11 tok/s" (Inkling 2 Mini, against 0.2.20)
R11: https://github.com/janhq/jan (accessed 2026-11-24) "Jan is an open source alternative to ChatGPT that runs 100% offline on your computer."; Apache 2.0; 46.1k stars; latest release v0.8.8, 2026-10-28 (https://github.com/janhq/jan/releases)
R12: https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-5060-ti-16gb/ (accessed 2026-11-24) updated March 2026, RTX 5060 Ti 16GB, gpt-oss 20B (MXFP4) generation: 92.1 t/s at 4k context, 82.4 at 16k, 73.2 at 32k, 58.1 at 64k, 43.8 at 128k
R13: https://blog.google/innovation-and-ai/technology/developers-tools/gemma-4/ (accessed 2026-11-24) Apr 02, 2026: Gemma 4 in Effective 2B (E2B), Effective 4B (E4B), 26B MoE and 31B Dense; E2B and E4B "run completely offline with near-zero latency across edge devices like phones"; Apache 2.0
R14: https://developers.google.com/edge/litert-lm/models/gemma-4 (accessed 2026-11-24) E2B model size 2.58 GB, E4B 3.65 GB. Windows (Intel LunarLake) laptop: E2B 30 decode tk/s on CPU, 48 on GPU; E4B 17 on CPU, 25 on GPU; peak memory E2B 3,505 MB (CPU) and 3,540 MB (GPU), E4B 9,372 MB (CPU) and 7,147 MB (GPU). MacBook Pro M4: E2B 160 decode tk/s on GPU
R15: https://help.openai.com/en/articles/6950777-what-is-chatgpt-plus (accessed 2026-11-24) "ChatGPT Plus is a subscription plan that provides enhanced access to the ChatGPT web app for $20/month."
R16: https://ollama.com/download (accessed 2026-11-24) downloads for macOS, Linux and Windows
R17: https://help.openai.com/en/articles/9237897-chatgpt-search (accessed 2026-11-24) "ChatGPT can search the web to answer questions with current information and links to relevant sources." "Web search is available on ChatGPT Free, Go, Plus, Pro, Business, Enterprise, and Edu."
R18: https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them (accessed 2026-11-24) "1 token is approximately three-quarters of a word."; "100 tokens are approximately 75 words."; "These are estimates, not exact counts."
R19: https://github.com/ollama/ollama (accessed 2026-11-24) MIT license; "Start building with open models. Access the latest releases locally or in the cloud with complete privacy."
R20: https://lmstudio.ai/models/gemma-4 (accessed 2026-11-24) "google/gemma-4-e2b" 4.20 GB; "To run the smallest Gemma 4, you need at least 4 GB of RAM. The largest one may require up to 19 GB."; sizes E2B, E4B, 26B A4B and 31B

HERO: R1 16 GB of memory: OpenAI's own words for what gpt-oss-20b needs
COUNTER: R3 41.42% of Steam PCs have exactly 16 GB of RAM, and 88.04% have 16 GB or more (our sum of the table)
STEELMAN: R15 R1 "enhanced access to the ChatGPT web app for $20/month", and OpenAI's bigger free model, gpt-oss-120b, needs "a single 80 GB GPU"
UNIT-CHAIN: R1 R2 R4 R12 16 GB of memory -> gpt-oss-20b, 12.8 GiB checkpoint, 12.00 GB download -> 92.1 tok/s on an RTX 5060 Ti 16GB at 4k context, 58.1 at 64k
MONEY-OBJECT: R3 the 16 GB of memory in the computer the viewer already owns (and the $20 a month plan, R15)
PRICES: R15 as of 2026-11-24 ChatGPT Plus $20/month on OpenAI's own help page; no hardware is priced (the video is about the computer the viewer already owns)
BENCH: R12 gpt-oss 20B (MXFP4) on an RTX 5060 Ti 16GB, 92.1 t/s generation at 4k context, 58.1 at 64k (Hardware Corner, llama.cpp)
STRATA: R8 R9 R10 the free desktop app for Windows, Linux and Mac; a community RTX 3060 12GB run of Qwen3.8-Flash-Next at 42.9 tok/s (Strata 0.1.41); 0.2.21 takes an RTX 3060 Ti 8GB from 11 to 43 tok/s on Inkling 2 Mini
VIRAL: NONE: no single viral post drives this topic; the subject is an evergreen newcomer question
COMMUNITY: R9 a community RTX 3060 12GB owner's Strata benchmark, Windows, medians of three runs, 2026-10-09
UNMEASURED: R14 R2 nobody we could find has published a gpt-oss-20b speed for an ordinary 16GB Windows laptop with no graphics card; the laptop figures that exist are Google's own for Gemma 4 E2B and E4B
SPONSOR: none paid; the channel's own Amazon affiliate link for the RTX 5060 Ti 16GB (the link line, channel.json affiliate)
PATTERN: NONE: the video is a setup primer with no earlier comparable event to set it against
ARTEFACT: 2026-11-24 we did the math on the Steam October 2026 RAM table (16 GB and above sums to 88.04%) and the VRAM table, worked out gpt-oss-20b's active share (3.6 of 21 billion), the speed kept from 4k to 64k context (58.1 of 92.1), and the months since the June 2024 cutoff; I read the 16 source pages listed here
{% endraw %}

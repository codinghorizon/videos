---
layout: default
title: "How To Start Running Local AI The Correct Way (2026)"
permalink: /start-running-local-ai-the-correct-way/
date: 2026-10-20
---

# How To Start Running Local AI The Correct Way (2026)

{% raw %}
Every price was checked on its page on 2026-10-20 (see PRICES.md). Every speed is a named
public run, labelled with who ran it on screen. Estimates are labelled "our maths". We ran no
tests of our own.

## Prices

- ChatGPT Plus $20 a month: https://learn.chatgpt.com/docs/pricing
- LM Studio plans: Free $0, Bionic+ $20 a month, Pro $100 a month: https://lmstudio.ai/pricing
- Used RTX 3090 24GB going rate about $1,700 (rigprice, October 20): https://rigprice.com/gpu/rtx-3090/
- Used RTX 3060 12GB going rate about $370 (rigprice, October 20): https://rigprice.com/gpu/rtx-3060-12gb/
- ASUS Dual RTX 5060 8GB $469.99, sold by Newegg: https://www.newegg.com/asus-dual-rtx5060-o8g-geforce-rtx-5060-8gb-graphics-card-double-fans/p/N82E16814126807
- Sapphire Pulse RX 9060 XT 16GB $519.99, sold by Newegg: https://www.newegg.com/sapphire-tech-pulse-11350-03-20g-radeon-rx-9060-xt-16gb-graphics-card-double-fans/p/N82E16814202457
- Our maths: $71/GB (1700/24), $59/GB (469.99/8), $31/GB (370/12), $50 gap, $240 a year,
  18.5 months (370/20), 85 months (1700/20).

## Apps

- LM Studio offline: "Nothing you enter into LM Studio when chatting with LLMs leaves your device": https://lmstudio.ai/docs/app/offline
- LM Studio free for home and work (July 2025): https://lmstudio.ai/blog/free-for-work
- LM Studio system requirements (AVX2 on Windows, Apple Silicon only on Mac, 16GB recommended): https://lmstudio.ai/docs/app/system-requirements
- LM Studio quant advice ("Choose a 4-bit option or higher"): https://lmstudio.ai/docs/app/basics/download-model
- LM Studio changelog 0.4.26 (October 13, 2026): https://lmstudio.ai/changelog/lmstudio
- Ollama free and unlimited on your own hardware: https://ollama.com/pricing ; MIT licence: https://github.com/ollama/ollama ; desktop app: https://ollama.com/blog/new-app
- Ollama default context 4K under 24GB of VRAM: https://docs.ollama.com/context-length
- Jan (Apache 2.0) fit labels "Fits", "May be slow", "Won't fit": https://docs.jan.ai/desktop/manage-models
- Jan Mac guide, 8GB runs up to about 3B: https://docs.jan.ai/desktop/install/mac
- Jan v0.8.7 (October 20, 2026): https://github.com/janhq/jan/releases/latest

## Finding your memory

- Windows Settings > System > About: https://support.microsoft.com/en-us/windows/find-information-about-your-windows-device-a66d52c8-3323-44fd-8f34-a9497bb935e1
- Task Manager Dedicated GPU memory: https://devblogs.microsoft.com/directx/gpus-in-the-task-manager/
- Mac About This Mac: https://support.apple.com/en-us/102767
- Unsloth's rule (memory about equal to the file size, or it runs much slower): https://unsloth.ai/docs/models/qwen3.8
- Steam survey September 2026: 16GB VRAM 27.2%, 8GB 26.7%: https://store.steampowered.com/hwsurvey/

## Models and file sizes (Q4)

- Qwen3.5 4B about 2.7GB: https://huggingface.co/unsloth/Qwen3.5-4B-GGUF
- Qwen3.5 9B about 5.7GB (Q8 about 9.5GB): https://huggingface.co/unsloth/Qwen3.5-9B-GGUF
- Gemma 4 12B about 7GB: https://huggingface.co/unsloth/gemma-4-12b-it-GGUF
- gpt-oss-20b about 11.6GB file, about 15GB running, 21B parameters, 3.6B active: https://huggingface.co/unsloth/gpt-oss-20b-GGUF and https://huggingface.co/openai/gpt-oss-20b
- Qwen 3.8 27B: https://huggingface.co/unsloth/Qwen3.8-27B-GGUF
- A token is about 3/4 of a word: https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them

## Speeds (named runs)

- LocalScore, Llama 3.1 8B Q4_K_M: Ryzen 7 4800H about 7 tok/s and about 50 s to first token;
  M5 16GB about 20; M1 16GB about 9; M4 16GB about 7 s to first token; RTX 4060 about 38;
  RTX 3060 12GB about 51 and under 1 s to first token: https://www.localscore.ai/model/1
- LocalScore, Qwen2.5 14B Q4_K_M: RTX 4060 Ti 8GB about 3.5 tok/s, RTX 3060 12GB about 27: https://www.localscore.ai/model/2
- Dell E6420 (2011) 8GB, Llama 2 7B Q4_0 on the CPU, 1.90 tok/s: https://www.mgroeber.de/benchmarking-llamacpp-on-legacy-hardware-2.html
- gpt-oss-20b on an RTX 5060 Ti 16GB, 111.51 tok/s; 8K to 131K context adds about 3GB; Mac GPU memory limit: https://github.com/ggml-org/llama.cpp/discussions/15396
- Qwen 3.8 27B on a used RTX 3090, 40.31 tok/s at 4K (Hardware Corner, llama.cpp, flash attention): https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/

## Captures (public/<slug>/web)

Each source above that is shown on screen is captured with scripts/capture-receipt.mjs; the
box around the quoted figure is in its json.
{% endraw %}

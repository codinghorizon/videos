---
layout: default
title: "How Much VRAM Local AI Really Needs At Full Context"
permalink: /how-much-vram-local-ai-full-context/
date: 2026-11-14
---

# How Much VRAM Local AI Really Needs At Full Context

{% raw %}
Every figure on screen, and where it comes from. Prices checked on the day; see PRICES.md.
No figure here is our own test: all are published by the sources named.

## Memory at context length
- Qwen 3.8 27B VRAM at 4K to 256K; RTX 3090 40.31 / 37.02 / 33.95 tok/s; RTX 5090 74.83 at 4K, 22.79 at 128K
  https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/ (capture web/hc-27b.png)
- RTX 5060 Ti 16GB: Qwen3 14B 41.1 at 4K, 25.9 at 32K; gpt-oss 20B 43.8 at 128K
  https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-5060-ti-16gb/ (capture web/hc-5060.png)
- Offload cliff on an RTX 5060 Ti, 43.18 to 12.5 tok/s
  https://inventivehq.com/blog/vram-offload-cliff-gpu-layers-benchmark

## Model files and configs (the notes per token)
- Qwen 3.8 27B Q4_K_M, 16.8GB: https://huggingface.co/lmstudio-community/Qwen3.8-27B-GGUF
- Qwen 3.8 27B config: https://huggingface.co/Qwen/Qwen3.8-27B
- Llama 3.3 70B Q4_K_M, 42.5GB: https://huggingface.co/bartowski/Llama-3.3-70B-Instruct-GGUF
- Llama 3.3 70B config (80 layers, 8 KV heads, head 128): https://huggingface.co/unsloth/Llama-3.3-70B-Instruct
- gpt-oss-120b: https://huggingface.co/unsloth/gpt-oss-120b-GGUF
- Qwen 3.8 Flash Next config: https://huggingface.co/Qwen/Qwen3.8-Flash-Next (capture web/flashnext.png)
- Gemma 4 and other GGUF sizes: https://huggingface.co/unsloth

## Shrinking the notes
- llama.cpp KV quantization perplexity f16 6.2322, q8_0 6.2344, q4_0 6.4384
  https://github.com/ggml-org/llama.cpp/pull/7412 (capture web/lcpp-pr.png)
- Ollama FAQ, q8_0 half, q4_0 a quarter: https://docs.ollama.com/faq
- Ollama context defaults (4K under 24GB, 64K for agents): https://docs.ollama.com/context-length
  (captures web/ollama-ctx.png, web/ollama-4096.png)

## Jobs and tokens
- Coding agent prompt sizes (Claude Code almost 20K tokens):
  https://dev.to/larsderidder/five-clis-walk-into-a-context-window-1c5a (capture web/devto.png)
- Tokens about 3/4 of a word: https://help.openai.com/en/articles/4936856

## Hardware and prices (see PRICES.md for the day's checks)
- RTX 5060 Ti 16GB $799.99, Newegg: https://www.newegg.com/msi-rtx-5060-ti-16g-ventus-3x-oc-geforce-rtx-5060-ti-16gb-graphics-card-triple-fans/p/N82E16814137957
- Used RTX 3090 going rate $1,825, rigprice 2026-11-12: https://rigprice.com/gpu/rtx-3090/
  (page showed $1,800 later the same evening; spoken figure kept, not captured on screen)
- RTX 5090 $6,549.99, Newegg: https://www.newegg.com/gigabyte-gv-n5090gaming-oc-32gd-geforce-rtx-5090-32gb-graphics-card-triple-fans/p/N82E16814932761
- Mac mini M5 Pro 64GB 1TB $3,299, Abt: https://www.abt.com/Apple-Mac-mini-Compact-Desktop-M5-Pro-64GB-Unified-Memory-1TB-SSD-in-Silver-Z1UD00082/p/252371.html
- Mac mini specs, M5 Pro 307 GB/s: https://www.apple.com/mac-mini/specs/
- macOS GPU memory cap about 75%: https://github.com/ivanopcode/devnote-override-macos-metal-vram-cap
- GMKtec EVO-X2 128GB $3,499.99: https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc
- Strix Halo gpt-oss-120b 51.81, 36.32 at 32K, 26.11 at 64K; prompt 371.47 at 64K
  https://kyuz0.github.io/amd-strix-halo-toolboxes/ (figure sits behind a page toggle; drawn, not captured)
- Qwen 3.8 Flash Next on Strix Halo, 111GB, crashes at 32K:
  https://sleepingrobots.com/dreams/qwen38-flash-next-strix-halo/
{% endraw %}

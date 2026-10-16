---
layout: default
title: "The VRAM You Need For Every Local AI Model (October 2026)"
permalink: /vram-you-need-for-every-local-ai-model/
date: 2026-10-16
---

# The VRAM You Need For Every Local AI Model (October 2026)

{% raw %}
Every figure in the video, where it came from. Prices were checked on 16 October 2026 and move
weekly; speeds are other people's published measurements, never our own.

## Model sizes and memory maths
- Qwen3.5 9B card and config: https://huggingface.co/Qwen/Qwen3.5-9B
- Qwen3.5 9B GGUF sizes: https://huggingface.co/unsloth/Qwen3.5-9B-GGUF
- Qwen3 8B config: https://huggingface.co/Qwen/Qwen3-8B
- Qwen3 14B card and config: https://huggingface.co/Qwen/Qwen3-14B
- Qwen3 14B GGUF sizes: https://huggingface.co/unsloth/Qwen3-14B-GGUF
- Qwen 3.8 27B card and config: https://huggingface.co/Qwen/Qwen3.8-27B
- Qwen 3.8 27B Q4_K_M files: https://huggingface.co/lmstudio-community/Qwen3.8-27B-GGUF, https://huggingface.co/ggml-org/Qwen3.8-27B-GGUF and https://huggingface.co/unsloth/Qwen3.8-27B-GGUF
- Qwen 3.8 27B KV cache maths: https://www.techplained.com/run-qwen-3-8-27b-locally
- Ternary Bonsai 2 27B (5.95 GB, 98.2%): https://huggingface.co/prism-ml/Ternary-Bonsai-2-27B-gguf
- Bonsai 2 needs Prism's llama.cpp fork; Ollama cannot load it: https://huggingface.co/prism-ml/Ternary-Bonsai-2-27B-gguf/blob/main/KNOWN_ISSUES.md
- Llama 3.3 70B GGUF sizes: https://huggingface.co/bartowski/Llama-3.3-70B-Instruct-GGUF
- Llama 3.3 70B config: https://huggingface.co/unsloth/Llama-3.3-70B-Instruct
- Llama 70B KV cache in a llama.cpp log (160 MiB at 512 tokens): https://huggingface.co/legraphista/Meta-Llama-3.1-70B-Instruct-IMat-GGUF/blob/252373a45c3345bde22d5be01b45bff696b0ad9f/imatrix.log
- Qwen 3.8 Flash Next card: https://huggingface.co/Qwen/Qwen3.8-Flash-Next
- Qwen 3.8 Flash Next GGUF sizes: https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF
- gpt-oss-120b GGUF sizes: https://huggingface.co/unsloth/gpt-oss-120b-GGUF
- GLM-5.3-Flash card and config: https://huggingface.co/zai-org/GLM-5.3-Flash
- GLM-5.3-Flash GGUF sizes: https://huggingface.co/unsloth/GLM-5.3-Flash-GGUF
- Qwen3.5 397B GGUF sizes: https://huggingface.co/unsloth/Qwen3.5-397B-A17B-GGUF
- Downloads per model (last 30 days): https://huggingface.co/models?sort=downloads

## Speeds
- RTX 3060 12GB (Qwen3 8B 55.2, Qwen3 14B 31.2 tok/s): https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-3060-12gb/
- Qwen 3.8 27B measured VRAM and RTX 3090 speed: https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/
- Strix Halo, Llama 70B: https://github.com/visorcraft/strix-halo-llm-perf
- Strix Halo, Flash Next: https://llamaperf.com/gpu/strix-halo-128gb and https://github.com/Niko1221/Strata/releases/tag/v0.1.40
- Flash Next on Strix Halo (111 GB file crashes at 32K): https://sleepingrobots.com/dreams/qwen38-flash-next-strix-halo/
- Strata (RTX 5070 12GB + 64GB, SSD streaming): https://github.com/Niko1221/Strata
- RTX 5090 in VRAM vs spilled to RAM, Qwen 3.8 27B: https://www.macstories.net/stories/m5-ultra-mac-studio-review-the-dream-mac-for-local-ai-agents/
- Qwen3 235B on M3 Ultra: https://omlx.ai/benchmarks/dn0dqucy
- Usable speed by task: https://openclawdc.com/blog/usable-tokens-per-second-by-task/

## Prices (16 October 2026)
- RTX 5060 8GB, $469.99 at Newegg: https://www.newegg.com/zotac-rtx-5060-amp-geforce-rtx-5060-8gb-graphics-card-double-fans/p/N82E16814500658
- Used RTX 3060 12GB, about $370: https://rigprice.com/gpu/rtx-3060-12gb/
- RX 9060 XT 16GB, $499.99 at Newegg: https://www.newegg.com/powercolor-reaper-rx9060xt-16g-a-radeon-rx-9060-xt-16gb-video-card-double-fans/p/N82E16814131880
- Intel Arc Pro B60 24GB, $649.99 at Newegg: https://www.newegg.com/asrock-intel-arc-pro-b60-24gb-graphics/p/N82E16814930148
- Used RTX 3090, about $1,740: https://rigprice.com/gpu/rtx-3090/
- RTX 5070 12GB, $859.99 at Newegg: https://www.newegg.com/gigabyte-gv-n5070eagleoc-ice-12gd-geforce-rtx-5070-12gb-graphics-card-triple-fans/p/N82E16814932775
- 64GB DDR5-5200 kit, $919.99 at Newegg: https://www.newegg.com/team-group-t-force-delta-rgb-64gb-ddr5-5200-cas-latency-cl40-desktop-memory-black/p/N82E16820331982
- GMKtec EVO-X2 64GB $2,199.99 and 128GB $3,499.99: https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc
- Bosgame M5 128GB, $3,099.76 pre-order: https://www.bosgamepc.com/products/bosgame-m5-ai-mini-desktop-ryzen-ai-max-395
- Mac Studio M5 Ultra 256GB, $9,499: https://www.apple.com/shop/buy-mac/mac-studio/m5-ultra-chip-30-core-cpu-64-core-gpu-256gb-memory-1tb-storage
- Mac Studio M5 Ultra 512GB option "coming late October", no price: https://www.apple.com/shop/buy-mac/mac-studio
{% endraw %}

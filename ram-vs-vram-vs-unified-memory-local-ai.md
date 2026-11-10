---
layout: default
title: "RAM vs VRAM vs Unified Memory (Local AI)"
permalink: /ram-vs-vram-vs-unified-memory-local-ai/
date: 2026-11-10
---

# RAM vs VRAM vs Unified Memory (Local AI)

{% raw %}
Checked 2026-11-09. Every speed is a published result, not our own run.

## Memory bandwidth
- Dual-channel DDR5-6000: 96 GB/s; DDR5-5200: 83 GB/s. https://www.hardware-corner.net/memory-bandwidth-llm-speed/
- RTX 3090 24GB: 936 GB/s. RTX 5060 Ti 16GB: 448 GB/s. RTX 5090 32GB: 1,792 GB/s. (same source)
- Strix Halo (Ryzen AI Max+ 395): 256 GB/s. (same source)
- Mac Studio M5 Max 40-core GPU: 614 GB/s; M5 Ultra: 1.2 TB/s; M5 Ultra base memory 96GB. https://www.apple.com/mac-studio/specs/

## Speed limit = bandwidth / bytes read per token
- Decode is memory-bound: each token reads the whole (active) weights once; prefill is compute-bound. https://akash.network/the-bid/what-actually-determines-llm-inference-speed-2026/
- Dense 27B at 4-bit is about 17GB. Our maths: 96/17 = 5.6 tok/s; 936/17 = 55; 1,792/17 = 105; 614/17 = 36; 256/17 = 15.
- Hardware Corner, Qwen3.5 27B Q4_K: RTX 3090 33.5 tok/s generation, 1,104 tok/s prompt at 4K; RTX 5090 58.8 tok/s; Strix Halo Q8 270 tok/s prompt. https://www.hardware-corner.net/qwen35-27b-35b-hardware-requirements/
- 33.5/55 = 61%; 58.8/105 = 56%. At ~57%, DDR5 lands near 3 tok/s (our maths).

## Mixture of experts
- gpt-oss-120b: about 63GB file, 5.1B active parameters per token. https://openai.com/index/introducing-gpt-oss/

## Spilling out of VRAM
- InventiveHQ, Qwen2.5-Coder 14B on RTX 5060 Ti 16GB: 43.18 tok/s all 48 layers on GPU; 12.5 tok/s at 40/48; 2.89 tok/s CPU only; calls partial offload "a cliff". https://inventivehq.com/blog/vram-offload-cliff-gpu-layers-benchmark
- Nvidia Windows driver falls back to shared system memory; CUDA Sysmem Fallback Policy "Prefer No Sysmem Fallback" in Nvidia Control Panel, per app. https://llmconfigurator.com/en/guides/troubleshooting/windows-shared-gpu-memory-slow
- carteakey, gpt-oss-120b on RTX 4070 12GB + 64GB DDR5-6000 with experts on CPU: 23.7-24.0 tok/s; 9.72 tok/s at 2000 MT/s on an older llama.cpp build. https://carteakey.dev/blog/local-inference/optimizing-gpt-oss-120b-local-inference/

## Unified memory
- oMLX, Mac Studio M5 Max 40-core 128GB, gpt-oss-120b: 79.7 tok/s at 1K context, 41.4 at 32K. https://omlx.ai/benchmarks/d8dnhh1k
- Level1Techs, Strix Halo gpt-oss-120b on ROCm: 51.8 tok/s at depth 0, 19.8 at 32K. https://forum.level1techs.com/t/one-spark-two-spark-red-strix-blue-arc/240937
- macOS lets the GPU wire about 75% of memory by default; iogpu.wired_limit_mb raises it. https://github.com/ivanopcode/devnote-override-macos-metal-vram-cap
- AMD Variable Graphics Memory: up to 96GB on a 128GB Ryzen AI Max+ 395 (Windows). https://www.amd.com/en/blogs/2025/faqs-amd-variable-graphics-memory-vram-ai-model-sizes-quantization-mcp-more.html
- ROCm on Linux: GTT default about half of system RAM, adjustable. https://rocmdocs.amd.com/en/develop/how-to/system-optimization/strixhalo.html

## Prompt reading (llama.cpp scoreboards, Llama 2 7B Q4_0, pp512)
- RTX 3090: 5,175 tok/s. https://github.com/ggml-org/llama.cpp/discussions/15013
- M5 Max 40-core: 3,220 tok/s. https://github.com/ggml-org/llama.cpp/discussions/4167
- Ryzen AI Max+ 300 (Vulkan): 1,487 tok/s; ~1,704 with flash attention. https://github.com/ggml-org/llama.cpp/discussions/10879
- 20,000-token document, our maths: 20,000/1,104 = 18 s (RTX 3090); 20,000/270 = 74 s (Strix Halo, Q8).

## Prices (2026-11-09, see PRICES.md)
- 64GB (2x32GB) T-Force Delta RGB DDR5-5200, Newegg: $999.99 ($15.62/GB). https://www.newegg.com/p/N82E16820331982
- RTX 5060 Ti 16GB MSI Ventus 3X OC, Newegg: $799.99 ($50/GB).
- RTX 3090 used asking price: $1,800 ($75/GB). https://rigprice.com/gpu/rtx-3090/
- RTX 5090 Gigabyte Gaming OC, Newegg: $6,549.99 ($205/GB).
- Mac Studio M5 Max 40-core 128GB: $5,099 ($40/GB); 48GB config $3,099. https://www.apple.com/shop/buy-mac/mac-studio
- GMKtec EVO-X2 128GB: $3,499.99 ($27/GB). https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc
- 128GB (2x64GB) Corsair Vengeance RGB DDR5-6000, Newegg: $2,804.99.

### Not checked
- Exact tok/s for a dense 27B on desktop DDR5 alone (only derived from the ceiling ratio).
- Whether every 2-card split mode alternates per token (true for llama.cpp's default layer split; tensor split differs).
- The Strix Halo and Studio gpt-oss-120b runs used different apps (ROCm llama.cpp vs oMLX), so the gap is not like for like.
{% endraw %}

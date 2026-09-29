---
layout: default
title: "Strix halo vs mac studio: the 128GB buying trap"
permalink: /strix-halo-vs-mac-studio-local-ai/
date: 2026-09-29
---

# Strix halo vs mac studio: the 128GB buying trap

{% raw %}
Every figure in the video, with the page it comes from. Checked on 28 September 2026.

## Intro

- **RTX 5090 has 32GB.** NVIDIA: "equipped with 32 GB of super-fast GDDR7 memory"; spec table "Standard Memory Config 32 GB GDDR7".
  https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/

## Chapter 1: The memory number that matters

- **Ryzen AI Max+ 395 supports 128GB.** AMD product page: "Max. Memory 128 GB", "System Memory Type 256-bit LPDDR5x", "Former Codename Strix Halo".
  https://www.amd.com/en/products/processors/laptop/ryzen/ai-300-series/amd-ryzen-ai-max-plus-395.html
- **Framework Desktop uses it.** Framework spec page: "AMD Ryzen AI Max+ 395 - 128GB … 128GB LPDDR5x-8000 memory (soldered)".
  https://frame.work/desktop?tab=specs
- **GMKtec EVO-X2 uses it.** Product page title: "GMKtec EVO-X2 AMD Ryzen AI Max+ 395 AI Mini PC", sold in 64GB and 128GB versions.
  https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc
- **The new Mac Studio has M5 Max and M5 Ultra, replacing M4 Max and M3 Ultra.** Apple announced it on **August 25, 2026**. Pre-orders opened that day. It went on sale on **September 22, 2026** ("The new Mac mini and Mac Studio are available today"). Apple compares the new chips with M4 Max and M3 Ultra.
  https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/
  https://www.apple.com/newsroom/2026/09/the-new-mac-mini-and-mac-studio-are-available-today/
- **AMD: up to 96GB of 128GB can go to graphics.** AMD: "system memory options ranging from 32GB all the way up to 128GB of unified memory – out of which up to 96GB can be converted to VRAM through AMD Variable Graphics Memory." The AMD LM Studio playbook's screenshot shows "Dedicated Graphics Memory 96 GB / Remaining System Memory 32 GB".
  https://www.amd.com/en/blogs/2025/amd-ryzen-ai-max-395-processor-breakthrough-ai-.html
  https://developer.amd.com/playbooks/lmstudio-rocm-llms/
- **GMKtec: 64GB default on the 128GB EVO-X2, adjustable to 96GB.** GMKtec support FAQ, "How can I configure the GFX memory on my EVO-X2?": "For units shipped with 128GB RAM, the default GFX memory is 64GB, and the maximum adjustable is 96GB." The setting is changed in the BIOS. For 64GB units the FAQ gives a 32GB default and a 48GB maximum.
  https://www.gmktec.com/pages/guides-how-to-tutorial
- **M5 Max goes up to 128GB. M5 Ultra starts at 96GB, with 256GB and 512GB options.** Apple tech specs, M5 Max: "36GB unified memory. Configurable to: 48GB, 64GB, or 128GB (M5 Max with 18-core CPU and 40-core GPU)". M5 Ultra: "96GB unified memory. Configurable to: 256GB or 512GB (M5 Ultra with 36-core CPU and 80-core GPU)". The larger memory options need the top chip configuration.
  https://www.apple.com/mac-studio/specs/
- **512GB arrives in late October.** Apple: "Mac Studio with 512GB of unified memory is coming in late October." The Mac Studio page's footnote reads: "512GB memory option for M5 Ultra coming late October."
  https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/
  https://www.apple.com/mac-studio/

## Chapter 2: What actually fits

- **Four-bit arithmetic.** At 4 bits, or half a byte, per parameter: 8B × 0.5 = 4GB, 32B × 0.5 = 16GB, 70B × 0.5 = 35GB. At 8 bits the same model takes twice the space. This counts weights only; real files carry some overhead on top.
- **The community 4-bit MLX build of Qwen 3.8 27B is 16.1GB.** Hugging Face lists `mlx-community/Qwen3.8-27B-4bit` at 16.1 GB (16,081,490,933 bytes).
  https://huggingface.co/mlx-community/Qwen3.8-27B-4bit/tree/main
- **Qwen3-Coder-Next has about 80B parameters, about 3B active.** Qwen: "Number of Parameters: 80B in total and 3B activated"; "With only 3B activated parameters (80B total parameters)".
  https://huggingface.co/Qwen/Qwen3-Coder-Next
- **A published 4-bit package is about 45 GiB, roughly 49GB.** Visorcraft's benchmark lists "Qwen3-Coder-Next 80B-A3B Q4_K_M | 45.17 GiB". Qwen's own Q4_K_M GGUF is shown as 48.4 GB (48,410,992,032 bytes, or 45.09 GiB). 45.17 GiB is about 48.5 decimal GB, so "roughly 49" is a round-up of 48.4 to 48.5GB. Unsloth's UD-Q4_K_M build is 49.3 GB.
  https://github.com/visorcraft/strix-halo-llm-perf/blob/main/BENCHMARKS.md
  https://huggingface.co/Qwen/Qwen3-Coder-Next-GGUF/tree/main/Qwen3-Coder-Next-Q4_K_M

## Chapter 3: Bigger doesn't automatically fix the bug

- **Qwen3-Coder-Next targets coding agents and tool use.** Visorcraft describes it as "Designed specifically for coding agents and tool calling". The Qwen model card describes it as built for agent deployment.
  https://huggingface.co/Qwen/Qwen3-Coder-Next
- **Qwen 3.8 27B has vision.** Qwen model card: "Type: Causal Language Model with Vision Encoder". The pipeline tag is image-text-to-text.
  https://huggingface.co/Qwen/Qwen3.8-27B
- **Qwen 3.8 27B scores 61.7 on SWE-bench Pro, against 53.5 for Qwen 3.6 27B.** From the model card's benchmark table, row "Agentic coding / SWE-bench Pro". Qwen's footnote says it ran with the Claude Code harness at temperature 1.0 and a 256K context, on a benchmark with corrected tasks, and that all baselines were re-evaluated.
  https://huggingface.co/Qwen/Qwen3.8-27B
- **Gemma 4 includes a 31B vision model and a 26B mixture of experts with about 4B active.** Google model cards. The 31B Dense has "Total Parameters 30.7B" and "Supported Modalities Text, Image". The 26B A4B MoE has "Total Parameters 25.2B" and "Active Parameters 3.8B" ("activating a 4B subset of parameters").
  https://huggingface.co/google/gemma-4-31B
  https://huggingface.co/google/gemma-4-26B-A4B
- **GLM 5.3 Flash has 320B total and 18B active parameters.** Z.ai: "With 320B total parameters and just 18B active parameters". At four bits that is 320B × 0.5 = 160GB of weights.
  https://huggingface.co/zai-org/GLM-5.3-Flash
- **A 4-bit MLX build of Qwen 3.5 397B is 224GB.** Hugging Face lists `mlx-community/Qwen3.5-397B-A17B-4bit` at 224 GB (223,888,201,461 bytes).
  https://huggingface.co/mlx-community/Qwen3.5-397B-A17B-4bit/tree/main

## Chapter 4: The speed trap

- **Visorcraft's Strix Halo tests.** Visorcraft's `strix-halo-llm-perf` repository: "All tests run on GMKtec EVO-X2, Ryzen AI Max+ 395, 128 GB LPDDR5X-8000". The runs used Vulkan RADV (Mesa) with llama.cpp build `05a6f0e89` (b8038), dated February 13, 2026. The command was `llama-bench … -p 512 -n 128`, meaning a 512-token prompt and 128 generated tokens.
  - 120W run: "Llama 3.1 70B Q4_K_M … tg128 5.10 ± 0.00" tokens per second.
  - "Qwen3-Coder-Next 80B-A3B (Q4_K_M) — Vulkan RADV, 120W": "tg128 42.70 ± 0.04" tokens per second.
  - At those rates, 300 tokens take 300 / 5.10 ≈ 59 seconds and 300 / 42.7 ≈ 7 seconds.
  https://github.com/visorcraft/strix-halo-llm-perf/blob/main/BENCHMARKS.md
- **Strix Halo memory bandwidth is about 256 GB/s.** AMD Ryzen AI Halo spec page (Ryzen AI Max+ 395, 128GB): "Memory Bandwidth 256GB/s". AMD's launch blog also refers to "the 256 GB/s bandwidth".
  https://www.amd.com/en/products/processors/desktops/ryzen/ryzen-ai-halo/ryzen-ai-max-plus-395.html
- **M5 Max reaches 614 GB/s in its higher GPU configuration.** Apple tech specs: the 32-core GPU M5 Max has "460GB/s memory bandwidth". The configurable "M5 Max with 18-core CPU, 40-core GPU … (614GB/s memory bandwidth)".
  https://www.apple.com/mac-studio/specs/
- **M5 Ultra reaches about 1,200 GB/s.** Apple: "1.2TB/s memory bandwidth" on both M5 Ultra configurations, and "1.2TB/s of memory bandwidth, 50 percent higher than before". Apple gives no more precise figure.
  https://www.apple.com/mac-studio/specs/
- **Tom's Hardware: M5 Ultra generates nearly 4x as fast as DGX Spark on Qwen 3.8 27B at 4 bits.** "Apple Mac Studio (M5 Ultra) review: Local model citizen outpaces DGX Spark and Threadripper", by Andrew E. Freedman, published 21 September 2026: "its tokens-per-second throughput is double that of the M4 Max and almost four times higher than the DGX Spark across the board." The chart is titled "Throughput (tokens per second) - Qwen 3.8 27B Q4_K_M, llama.cpp, No MTP", with input length 2048 and output length 512. At zero context: M5 Ultra 46.27, M4 Max 22.7, DGX Spark 11.8. The ratio to Spark is about 3.9x at most context depths and about 3.5x at 65,536. The review unit was an M5 Ultra with 256GB and 4TB, priced at $12,299.
  https://www.tomshardware.com/desktops/mini-pcs/apple-mac-studio-m5-ultra-review

## Chapter 5: Your codebase changes the race

- **Apple: up to 4x faster prompt processing on M5 Ultra than M3 Ultra in LM Studio.** Apple newsroom: "Up to 9.8x faster LLM prompt processing in LM Studio when compared to Mac Studio with M1 Ultra, and up to 4x faster than M3 Ultra." Apple measured it as time to first token. Apple's test note: "Time to first token measured with an 8K-token prompt using a 14-billion parameter model with 4-bit quantization, and LM Studio v0.4.19+2", using preproduction M5 Ultra systems in July 2026.
  https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/
  https://www.apple.com/mac-studio/

## Chapter 6: The software you live with

- **LM Studio offers local chat and an API, and works offline once models are downloaded.** LM Studio docs: "Use a simple and flexible chat interface"; "Serve local models on OpenAI-like endpoints, locally and on the network"; "LM Studio can operate entirely offline, just make sure to get some model files first." The docs say chatting with models, chatting with documents and running a local server work without internet.
  https://lmstudio.ai/docs/app
  https://lmstudio.ai/docs/app/offline
- **On Mac, LM Studio runs MLX and llama.cpp.** "LM Studio supports running LLMs on Mac, Windows, and Linux using llama.cpp. On Apple Silicon Macs, LM Studio also supports running LLMs using Apple's MLX."
  https://lmstudio.ai/docs/app
- **AMD's August 2026 playbook documents Vulkan and ROCm runtimes for LM Studio.** AMD AI Playbooks, "Running and Serving LLMs with LM Studio", marked "Last validated: August 2026", with the platform set to Ryzen AI Max+: "LM Studio offers both Vulkan and AMD ROCm software backends (called runtimes) for AMD users." August 2026 is the validation date the page shows; the page gives no publication date.
  https://developer.amd.com/playbooks/lmstudio-rocm-llms/

## Chapter 7: The machines trying to steal the sale

- **Mac mini with M5 Pro: up to 64GB and 307 GB/s.** Apple tech specs: "Apple M5 Pro chip … 307GB/s memory bandwidth"; "24GB unified memory, Configurable to: 48GB or 64GB". The September 22 newsroom post says "support for up to 64GB of unified memory with 307GB/s of memory bandwidth".
  https://www.apple.com/mac-mini/specs/
  https://www.apple.com/newsroom/2026/09/the-new-mac-mini-and-mac-studio-are-available-today/
- **DGX Spark: 128GB unified memory and 273 GB/s.** NVIDIA specifications: "System Memory 128 GB LPDDR5x, coherent unified system memory"; "Memory Bandwidth 273 GB/s".
  https://www.nvidia.com/en-us/products/workstations/dgx-spark/
- **Framework lists a 192GB Ryzen AI Max+ PRO 495 desktop as coming soon, at 273 GB/s.** Framework: "The most powerful Framework Desktop yet is coming soon with an AMD Ryzen AI Max+ PRO 495 processor and 192GB of LPDDR5X memory." Its spec strip reads "192GB Unified memory | 273GB/s Memory bandwidth". No price or date is given. 192 / 128 = 1.5, which is 50% more capacity. 273 / 256 ≈ 1.07, which is about 7% more bandwidth.
  https://frame.work/desktop?tab=192gb-coming-soon
- **Framework's RAM is soldered, and its storage can be swapped.** Framework spec page: "128GB LPDDR5x-8000 memory (soldered)". Storage: "2x NVMe PCIe 4.0 x4 M.2 2280 sockets with heatspreaders, up to 8TB each". GMKtec also describes the EVO-X2's memory as "Onboard LPDDR5X (non-upgradeable)".
  https://frame.work/desktop?tab=specs

## Chapter 8: The bill and the choice

- **Apple US starting prices: $2,499 for M5 Max with 36GB, $5,499 for M5 Ultra with 96GB.** Apple newsroom: "Mac Studio with M5 Max starts at $2,499 (U.S.)"; "Mac Studio with M5 Ultra starts at $5,499 (U.S.)". The tech specs page lists base memory as 36GB for M5 Max and 96GB for M5 Ultra.
  https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/
  https://www.apple.com/mac-studio/specs/
- **GMKtec lists the EVO-X2 from about $2,200, with 64GB and 1TB as the displayed configuration.** The GMKtec product page shows "$2,199.99" (was $2,599.99) with "64GB RAM + 1TB SSD" selected. The store's product data prices the 128GB + 1TB version at $3,499.99 and 128GB + 2TB at $3,649.99. These are prices as listed on 28 September 2026, and the page says prices are about to rise.
  https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc

### Not checked

- The Mac Studio's timing. "The September 2026 M5 Max and M5 Ultra" describes when it went on sale (September 22). Apple announced it on August 25, 2026.
- Qwen3-Coder-Next's size. No published 4-bit package is exactly "roughly 49 decimal gigabytes": the 45 GiB packages are 48.4 to 48.5GB. Only Unsloth's UD-Q4_K_M, at 45.9 GiB, comes to 49.3GB.
- That MLX offers "maintained conversions of popular releases". This is a general description of the mlx-community organisation on Hugging Face and was not checked against a specific source.
- The NPU's AI rating not predicting GPU inference speed. This is an explanation, not a published figure.
- General statements about KV cache growth, offloading slowdowns, concurrent requests, CUDA-only tutorials, enclosure power settings and fan noise. These are explanatory and cite no figure.
- Complete 128GB prices across sellers, beyond GMKtec's own listing.
{% endraw %}

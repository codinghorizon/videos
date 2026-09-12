---
layout: default
title: "128GB vs 192GB: The Local AI Upgrade You Might Regret"
permalink: /128gb-vs-192gb-local-ai/
date: 2026-09-12
---

# 128GB vs 192GB: The Local AI Upgrade You Might Regret

{% raw %}
Checked 11 September 2026. Prices are US dollars before tax. File sizes are the decimal
gigabytes the hosting service reports for the download, not the memory a running model
needs; every fit shown on screen leaves that overhead as a separate, labelled block.

## The machines

| On screen | Source |
| --- | --- |
| DGX Spark: GB10 Grace Blackwell, 128 GB unified LPDDR5x, 4 TB self encrypting NVMe, 273 GB/s | [Nvidia, DGX Spark specifications](https://www.nvidia.com/en-us/products/workstations/dgx-spark/) |
| Spark US list price raised from $3,999 to $4,699 with no hardware change; Nvidia cites memory supply constraints | [Nvidia developer forum, price change announcement, 23 Feb 2026](https://forums.developer.nvidia.com/t/2-23-2026-price-change-announcement/361713) |
| Dell Pro Max with GB10, built on the same chip | [Jeff Geerling, ai-benchmarks](https://github.com/geerlingguy/ai-benchmarks/blob/main/README.md) lists the Dell Pro Max with GB10 beside the Framework and Apple results |
| Ryzen AI Max+ 395: 16 Zen 5 cores, 32 threads, Radeon 8060S with 40 RDNA 3.5 compute units, XDNA 2 NPU | [AMD, Ryzen AI Max+ 395 blog](https://www.amd.com/en/blogs/2025/amd-ryzen-ai-max-395-processor-breakthrough-ai-.html); [cpu-monkey spec listing](https://www.cpu-monkey.com/en/cpu-amd_ryzen_ai_max_plus_395) |
| Framework Desktop, 128 GB Ryzen AI Max+ 395: $3,449 before storage and other options; memory listed as non upgradeable; storage priced separately from +$135 | [Framework configurator](https://frame.work/products/desktop-diy-amd-aimax300/configuration/new) |
| Framework 395 theoretical bandwidth 256 GB/s | LPDDR5X-8000 on a 256 bit bus: 8000 MT/s × 256 bits ÷ 8 = 256 GB/s. [Framework Desktop specifications](https://frame.work/desktop) |
| Beelink GTR9 Pro: Ryzen AI Max+ 395, Radeon 8060S, 128 GB LPDDR5X-8000 | [Beelink, GTR9 Pro](https://www.bee-link.com/products/beelink-gtr9-pro-amd-ryzen-ai-max-395) |
| Minisforum MS S1 Max: Ryzen AI Max+ 395, up to 128 GB unified memory | [Minisforum, MS-S1 Max](https://www.minisforum.com/products/ms-s1-max) |
| BOSGAME M5: Ryzen AI Max+ 395, 96 GB and 128 GB variants | [BOSGAME, M5](https://www.bosgamepc.com/products/bosgame-m5-ai-mini-desktop-ryzen-ai-max-395) |
| GMKtec EVO X2: $2,199.99 sale price applies to the 64 GB / 1 TB configuration; 128 GB configurations exist without a distinct price on the page | [GMKtec, EVO X2 product page](https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc) |
| Mac Studio M2 Ultra: up to 192 GB unified memory, 800 GB/s, 60 or 76 GPU cores, 24 CPU cores, announced 5 June 2023 | [Apple Newsroom, M2 Ultra](https://www.apple.com/newsroom/2023/06/apple-introduces-m2-ultra/) |
| Reseller listing: Mac Studio M2 Ultra, 76 core GPU, 192 GB, 1 TB, $5,095.02, marked currently unavailable | [iPowerResale listing](https://ipowerresale.com/products/apple-mac-studio-m2-ultra-192gb-ram-1tb-ssd-76-core-gpu-grade-a). One indexed listing, not an in stock offer or a market price |
| AMD Variable Graphics Memory allows up to 96 GB for graphics on a 128 GB system | [AMD, Ryzen AI Max+ 395 blog](https://www.amd.com/en/blogs/2025/amd-ryzen-ai-max-395-processor-breakthrough-ai-.html); [AMD, VGM FAQ](https://www.amd.com/en/blogs/2025/faqs-amd-variable-graphics-memory-vram-ai-model-sizes-quantization-mcp-more.html). A driver setting, not a hardware ceiling; Linux runtimes draw the line differently |
| Framework 192 GB desktop, coming: Ryzen AI Max+ PRO 495, 40 CU Radeon 8065S, 192 GB LPDDR5X, 273 GB/s, no price, no measured model speed | [Framework, 192 GB coming soon](https://frame.work/desktop?tab=192gb-coming-soon). 192 ÷ 128 = 1.5; 273 ÷ 256 = 1.066 |
| H100: 80 GB | [OpenAI, gpt-oss-120b model card](https://huggingface.co/openai/gpt-oss-120b) names "a single 80GB GPU (like NVIDIA H100 or AMD MI300X)" |

## The models

| On screen | Source |
| --- | --- |
| Qwen3 Coder 30B A3B Instruct, Q4_K_M: 18.56 GB | [Unsloth, Qwen3-Coder-30B-A3B-Instruct-GGUF](https://huggingface.co/unsloth/Qwen3-Coder-30B-A3B-Instruct-GGUF), file size from the repository tree |
| Llama 70B class at four bit: about 40 to 45 GB | [Ollama, llama3.1:70b](https://ollama.com/library/llama3.1:70b) lists the Q4 tag at about 43 GB; drawn as a range |
| GPT OSS 120B: 117B total, 5.1B active, MoE weights post trained in MXFP4, runs on a single 80 GB GPU; text only | [OpenAI, gpt-oss-120b model card](https://huggingface.co/openai/gpt-oss-120b); [OpenAI developer docs](https://developers.openai.com/api/docs/models/gpt-oss-120b) |
| Qwen3.5 122B A10B: 122B total, 10B active, vision language model (image, text, video input) | [Qwen, Qwen3.5-122B-A10B model card](https://huggingface.co/Qwen/Qwen3.5-122B-A10B) |
| Qwen3.5 122B A10B, bartowski Q4_K_M: 77.62 GB (shown as 78); Q8_0: 132.60 GB (shown as 133) | [bartowski, Qwen_Qwen3.5-122B-A10B-GGUF](https://huggingface.co/bartowski/Qwen_Qwen3.5-122B-A10B-GGUF), shard sizes summed from the repository tree |
| Qwen3 235B A22B, official Q4_K_M: 142.15 GB (shown as 142) | [Qwen, Qwen3-235B-A22B-GGUF](https://huggingface.co/Qwen/Qwen3-235B-A22B-GGUF), five shards summed |
| DeepSeek V4 Flash: 284B total, 13B active per token | [DeepSeek, DeepSeek-V4-Flash model card](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) |
| Unsloth DeepSeek V4 Flash GGUF: UD-IQ3_XXS 103.0 GB, UD-Q4_K_XL 155.1 GB | [Unsloth, DeepSeek-V4-Flash-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-GGUF), folder sizes summed from the repository tree |

## Speed and bandwidth

| On screen | Source |
| --- | --- |
| Llama 3.1 70B generation: Framework Desktop mainboard (395+) 4.97 tokens/s (GPU/CPU); Dell Pro Max GB10 4.71 tokens/s (GPU); M1 Ultra 64 GPU core 128 GB 9.84 tokens/s (GPU) | [Jeff Geerling, ai-benchmarks README](https://github.com/geerlingguy/ai-benchmarks/blob/main/README.md). Collected submissions with different software versions and settings, not one controlled run; the M2 Ultra is not in the table |
| 1,000 tokens at 5 tokens/s is 200 s; at 10 tokens/s is 100 s | Arithmetic. Excludes loading, prompt processing and any reasoning tokens |
| Bandwidth: M2 Ultra 800 GB/s, DGX Spark 273 GB/s, Framework 395 256 GB/s theoretical, Framework 495 273 GB/s | Apple, Nvidia and Framework pages above |
| 800 ÷ 273 ≈ 2.9, shown only to be struck out | Arithmetic; bandwidth ratios are not measured speedups |

## Benchmarks

| On screen | Source |
| --- | --- |
| SWE-bench Verified: Qwen3.5 122B A10B 72.0, Qwen3.5 27B 72.4. Terminal Bench 2: 49.4 against 41.6 | [Qwen, Qwen3.5-122B-A10B model card, benchmark table](https://huggingface.co/Qwen/Qwen3.5-122B-A10B#benchmark-results). Developer reported evaluations of the full precision models |

## Illustrative, not measured

These frames draw an idea rather than a published number, and print no figure for it:

- The size of the GPT OSS 120B block inside the 80 GB card and the 128 GB tank is drawn to
  suggest a fit with room, not to a measured file size.
- The 2.5 tokens per second reply in the local chat window, the "feels like" dials, the
  thirty task grid, the two rows of mistakes, the ten task tally and its 7 successes and
  4:12 of correction time, the 148 GB download in the 140 to 155 band, and the value dial
  are all hypothetical illustrations of the argument.
- The $1,500 premium in the verdict is the script's own hypothetical, not a market difference; the hours saved bars under it are illustrative.
- The split of the Spark's $4,699 into memory and platform is illustrative, not a bill of materials.
- Blocks labelled system, apps, working space, context, conversation, vision model,
  embeddings and speech are proportioned to make the stacking legible, not measured.

## Not checked

- No current price was checked for the Beelink GTR9 Pro, Minisforum MS S1 Max or BOSGAME M5; the script names them as alternatives, not as bargains.

- Whether any current GMKtec EVO X2 128 GB configuration undercuts the Framework 395 by a
  margin that matters; the page did not expose a distinct 128 GB price.
- Whether the iPowerResale listing has returned to stock or moved in price since indexing.
- Any tokens per second figure for the M2 Ultra, the Framework 495 or the DGX Spark running
  the models named here under a current runtime.
- Whether the Qwen3.5 benchmark scores hold for four bit desktop copies.
{% endraw %}

---
layout: default
title: "Your Local AI Setup Needs More VRAM Than You Think"
permalink: /how-much-vram-do-you-actually-need-for-local-ai/
date: 2026-09-07
---

# Your Local AI Setup Needs More VRAM Than You Think

{% raw %}
Sources for every figure, price, capacity and benchmark this video puts on screen.
Checked 6 September 2026.

## Models

### Qwen3 Coder 480B A35B

- 480B total parameters, 35B active. Mixture of experts, 160 experts with 8 activated,
  62 layers.
- 262,144 tokens (256K) of context natively, extended to 1M with YaRN.
- Source: Qwen, model card. https://huggingface.co/Qwen/Qwen3-Coder-480B-A35B-Instruct
- Source: Qwen, launch post. https://qwenlm.github.io/blog/qwen3-coder/

### Qwen3 Coder 30B A3B

- 30.5B total parameters, 3.3B activated, on the same architecture as Qwen3 30B A3B.
- 256K native context (262,144 tokens).
- Source: Qwen, model card. https://huggingface.co/Qwen/Qwen3-Coder-30B-A3B-Instruct

**At four bit, around 19GB of weights with minimal context.** Community quantisations put
Q4_K_M between roughly 18.6GB and 21.9GB of weights, before runtime overhead and before
any KV cache. The video's "around nineteen gigabytes with minimal context, and the memory
need grows as the context grows" sits inside that range and is stated as an estimate,
which is what it is.

- Source: Unsloth GGUF quantisations, file sizes.
  https://huggingface.co/unsloth/Qwen3-Coder-30B-A3B-Instruct-GGUF
- Source: AWQ 4 bit build. https://huggingface.co/cyankiwi/Qwen3-Coder-30B-A3B-Instruct-AWQ-4bit

### Devstral Small 2 and Devstral 2

- Devstral Small 2: 24B parameters, 256K context window, **68.0%** on SWE bench Verified,
  Apache 2.0.
- Devstral 2: 123B parameters, 256K context window, **72.2%** on SWE bench Verified.
- Source: Mistral AI, launch post. https://mistral.ai/news/devstral-2-vibe-cli/
- Source: Mistral AI, model card.
  https://huggingface.co/mistralai/Devstral-Small-2-24B-Instruct-2512

### DeepSeek V4 Flash

- 284B total parameters, 13B active. Mixture of experts, 1M token context.
- Source: DeepSeek, model card. https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash

### GLM 4.5 Air

- 106B total parameters, 12B active.
- Source: Z.ai, model card. https://huggingface.co/zai-org/GLM-4.5-Air
- Source: Z.ai developer documentation. https://docs.z.ai/guides/llm/glm-4.5

### MiniMax M2.5

- **80.2%** on SWE bench Verified.
- Source: MiniMax, launch post. https://www.minimax.io/news/minimax-m25
- Source: MiniMax, model card. https://huggingface.co/MiniMaxAI/MiniMax-M2.5

## Graphics cards

### RTX 5090

- 32GB GDDR7, 512 bit bus, 1,792 GB/s of memory bandwidth, 21,760 CUDA cores.
- Nvidia's listed price is **$1,999**. Street pricing has run far above it through the
  memory shortage, with retail listings starting around $5,100 in September 2026.
- Source: Nvidia, product page and specifications.
  https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/

### RTX PRO 6000 Blackwell

- **96GB GDDR7 with ECC**, 24,064 CUDA cores, 600W.
- Launched March 2025 at an MSRP of $8,565. Nvidia's marketplace listed it at
  **$16,000** as of September 2026, after two increases attributed to GDDR7 supply.
  Retail sat between roughly $14,000 and $15,500 at the same time.
- Source: Tom's Hardware, on the MSRP doubling to $16,000.
  https://www.tomshardware.com/pc-components/gpus/nvidia-doubles-rtx-pro-6000-blackwells-msrp-to-a-staggering-usd16-000-96gb-card-started-pre-orders-below-usd8-000-last-year
- Source: Newegg listing, for the 96GB GDDR7 ECC specification.
  https://www.newegg.com/nvidia-blackwell-rtx-pro-6000-96gb-graphic-card/p/N82E16814132106

### RTX 3090, RTX 4090, RTX 3060 12GB

- RTX 3090 and RTX 4090: 24GB each. RTX 3060: a 12GB variant.
- The 3090 has commonly traded in the **$700 to $1,000** range on the used market
  through much of 2026, which is the range the video gives. By August and September 2026
  the same trackers put it higher, roughly $1,000 to $1,400, as memory prices rose. The
  video's "used prices move every week" is doing real work here.
- Source: XDA, on the used 3090 as the value pick for local AI in 2026.
  https://www.xda-developers.com/used-rtx-3090-still-best-for-local-ai-in-value/
- Source: GPUDojo used price tracker. https://gpudojo.com/rtx-3090

### AMD RX 7900 XTX

- 24GB GDDR6, RDNA 3.
- Source: AMD partner specifications, ASUS.
  https://www.asus.com/us/motherboards-components/graphics-cards/asus/rx7900xtx-24g/techspec/

## Macs

### M5 Max MacBook Pro

- Configurable to **128GB** of unified memory, with up to **614 GB/s** of memory
  bandwidth. 18 core CPU, up to 40 core GPU.
- Source: Apple Newsroom, M5 Pro and M5 Max announcement.
  https://www.apple.com/newsroom/2026/03/apple-debuts-m5-pro-and-m5-max-to-supercharge-the-most-demanding-pro-workflows/
- Source: Apple, MacBook Pro technical specifications.
  https://support.apple.com/en-us/126319

### Mac Studio with M3 Ultra

- Configurable to **512GB** of unified memory, with **819 GB/s** of memory bandwidth.
  32 core CPU, 80 core GPU.
- Source: Apple Newsroom, M3 Ultra announcement.
  https://www.apple.com/newsroom/2025/03/apple-reveals-m3-ultra-taking-apple-silicon-to-a-new-extreme/
- Source: Apple, Mac Studio technical specifications.
  https://support.apple.com/en-us/122211

## The AMD unified memory desktop

### Framework Desktop

- Uses AMD Ryzen AI Max chips and is configurable with **128GB of LPDDR5x**, soldered
  and not upgradeable. A 192GB configuration has since been announced.
- Source: Framework, product page. https://frame.work/desktop
- Source: Framework, launch post. https://frame.work/blog/introducing-the-framework-desktop

## Benchmarks

### SWE bench Verified

A 500 issue human validated subset of SWE bench, drawn from real GitHub issues in real
Python repositories. A run is scored on whether the model's patch makes the repository's
own tests pass.

- Source: OpenAI, introducing SWE bench Verified.
  https://openai.com/index/introducing-swe-bench-verified/

## Not confirmed at a primary source

**The Framework Desktop starting price of $1,269.** The narration gives this figure and
it could not be confirmed anywhere. Framework's own launch post prices the base Ryzen AI
Max 385 with 32GB at **$1,099**, the Max+ 395 with 64GB at $1,599 and the Max+ 395 with
128GB at $1,999, and the current product pages carry no price at all. Reporting through
2026 has the top configuration rising well above its launch price during the memory
shortage rather than falling. No configuration at $1,269 was found at any point.

Because of this the figure is **not drawn on screen anywhere in the video**. The beat that
covers Framework's pricing shows the configuration ladder and the fact that memory is
soldered, and prints no starting price.

**Current used RTX 3090 pricing.** The $700 to $1,000 range the narration gives was
accurate for much of 2026 and is now at the low end of what trackers report. The shot
draws the range as a historical band rather than as today's price, and labels it as a
zone that moves.
{% endraw %}

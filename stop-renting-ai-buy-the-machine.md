---
layout: default
title: "Stop Renting AI Before It Gets Much More Expensive"
permalink: /stop-renting-ai-buy-the-machine/
date: 2026-09-07
---

# Stop Renting AI Before It Gets Much More Expensive

{% raw %}
Every figure, price, capacity and benchmark this video puts on screen, chased to a
primary source. Checked 6 September 2026.

## Cloud GPU rental pricing

RunPod publishes per hour Pod pricing on its own pricing page, split between Community
Cloud and Secure Cloud.

| GPU | VRAM | Community Cloud | Secure Cloud |
| --- | --- | --- | --- |
| RTX 4090 | 24 GB | $0.34 / hr | $0.74 / hr |
| RTX 5090 | 32 GB | $0.69 / hr | $0.99 / hr |

Source: RunPod pricing, https://www.runpod.io/pricing

The three monthly figures the video draws are arithmetic on those rates, at a full
730 hour month (365 days / 12 months x 24 hours = 730.5 hours):

| Hourly | Per month at 730 hours |
| --- | --- |
| $0.99 | $722.70 |
| $0.74 | $540.20 |
| $0.70 | $511.00 |
| $0.34 | $248.20 |

The narration rounds these to "roughly seven hundred thirty", "roughly five hundred" and
"about two hundred fifty". A dollar an hour is exactly $730.50 a month, which is where the
first figure comes from. Storage and idle volume charges are additional and are not in
these numbers.

## Consumer GPU memory

| Card | Architecture | Memory | Bus |
| --- | --- | --- | --- |
| GeForce RTX 3090 | Ampere | 24 GB GDDR6X | 384 bit |
| GeForce RTX 4090 | Ada Lovelace | 24 GB GDDR6X | 384 bit |
| GeForce RTX 5090 | Blackwell | 32 GB GDDR7 | 512 bit |

Sources:
- https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/
- https://www.nvidia.com/en-us/geforce/graphics-cards/40-series/rtx-4090/

The 4090 did not increase memory capacity over the 3090; both are 24 GB. The 5090 is the
first of the three to move, to 32 GB.

## RTX 5090 local inference throughput

The llama.cpp project keeps a community CUDA performance thread. The RTX 5090 entry for
Llama 2 7B Q4_0, text generation of 128 tokens:

| Configuration | Tokens per second |
| --- | --- |
| Without flash attention | 290.02 +/- 1.10 |
| With flash attention | 300.40 +/- 0.28 |

Source: llama.cpp CUDA performance discussion,
https://github.com/ggml-org/llama.cpp/discussions/15013

That is a small four bit model on a single card, which is what makes it fast; it is not a
figure that carries over to a larger model or a longer context.

## Unified memory machines

**Mac Studio with M3 Ultra.** Configurable up to 512 GB of unified memory, with 800 GB/s
memory bandwidth, up to a 32 core CPU and an 80 core GPU.
Source: Apple Newsroom, "Apple reveals M3 Ultra, taking Apple silicon to a new extreme",
https://www.apple.com/newsroom/2025/03/apple-reveals-m3-ultra-taking-apple-silicon-to-a-new-extreme/
and Mac Studio (2025) tech specs, https://support.apple.com/en-us/122211

**NVIDIA DGX Spark.** 128 GB of unified LPDDR5x at 273 GB/s on a GB10 Grace Blackwell
Superchip. NVIDIA states it can fine tune models up to 70 billion parameters and run
inference on models up to 200 billion parameters, with two units connected reaching 405
billion.
Source: https://www.nvidia.com/en-us/products/workstations/dgx-spark/

## Open weight models

**Qwen3 Coder.** Qwen3-Coder-480B-A35B-Instruct is a 480 billion parameter mixture of
experts model with 35 billion active parameters, 160 experts with 8 activated per forward
pass, and a native context window of 262,144 tokens, extendable to about 1 million with
YaRN.
Sources: https://qwenlm.github.io/blog/qwen3-coder/ and
https://huggingface.co/Qwen/Qwen3-Coder-480B-A35B-Instruct

**Kimi K2.** A mixture of experts model with 1 trillion total parameters and 32 billion
activated, pre trained on 15.5 trillion tokens, released under a modified MIT licence and
built for tool use and agentic work. It reports 65.8 on SWE-bench Verified.
Sources: https://moonshotai.github.io/Kimi-K2/ and
https://huggingface.co/moonshotai/Kimi-K2-Instruct

**DeepSeek V3 and V3.1.** DeepSeek-V3.1 is 671 billion total parameters with 37 billion
active, extended through a two phase long context training process to a 128,000 token
context window, with post training aimed at tool calling and agent behaviour. Weights are
published on Hugging Face.
Sources: https://api-docs.deepseek.com/news/news250821/ and
https://huggingface.co/deepseek-ai/DeepSeek-V3.1

## Runtimes and formats named on screen

Ollama, LM Studio, vLLM, llama.cpp, Open WebUI, GGUF and MLX are all named in the
narration as pieces a first local setup has to choose between. GGUF is llama.cpp's model
container format; MLX is Apple's array framework for Apple silicon.

## Not verified

- The narration's "two thousand dollars on a GPU" is an illustrative purchase price
  rather than a quoted price for a specific card, so no retailer price is put on screen
  for it. What the video draws is the arithmetic of that figure across three years.
- H100 and B200 rental rates are not stated in the narration and are not put on screen.
- The claim that a used RTX 3090 box "might be the local AI bargain" is a judgement, not
  a measurement, and is drawn as its memory capacity rather than as a price.
{% endraw %}

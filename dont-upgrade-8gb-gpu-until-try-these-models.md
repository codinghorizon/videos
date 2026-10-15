---
layout: default
title: "Don't Upgrade Your 8GB GPU Until You Try These Models"
permalink: /dont-upgrade-8gb-gpu-until-try-these-models/
date: 2026-10-15
---

# Don't Upgrade Your 8GB GPU Until You Try These Models

{% raw %}
Checked 15 October 2026.

## Prices

| Figure | Value | Source |
|---|---|---|
| ChatGPT Plus | $20 per month | [OpenAI Help Center, What is ChatGPT Plus?](https://help.openai.com/en/articles/6950777-what-is-chatgpt-plus) |
| ChatGPT Plus over a year | $240 (20 × 12) | arithmetic |
| ASUS Dual GeForce RTX 5060 Ti 16GB (DUAL-RTX5060TI-O16G), new | $799.99, sold and shipped by Newegg | [Newegg](https://www.newegg.com/asus-dual-rtx5060ti-o16g-geforce-rtx-5060-ti-16gb-graphics-card-double-fans/p/N82E16814126798) |
| That card in months of ChatGPT Plus | 40 months (799.99 / 20 = 40.0) | arithmetic |

## Qwen3 8B on 8GB cards

| Machine and setup | Result | Source |
|---|---|---|
| RTX 4060 8GB, memory left for a model | about 7.2 GB once the operating system has taken its share | [localllmchecker, RTX 4060 · Qwen3 8B](https://localllmchecker.com/can-i-run/rtx-4060/qwen3-8b/) (an estimate, not a measured run) |
| RTX 4060, Qwen3 8B Q5_K_M, 8K context | 6.54 GB of the 7.2 GB, headroom 0.66 GB, about 32.6 tokens per second | same page |
| RTX 4060, Qwen3 8B Q4_K_M, 8K context | 5.79 GB total, 37.2 tokens per second; about 1.4 GB left of 7.2 (7.2 − 5.79 = 1.41) | same page |
| RTX 4060, Qwen3 8B Q5_K_M by context | 8K: 6.54 GB, fits; 16K: 7.67 GB, does not fit; 32K: 9.92 GB | same page |
| RTX 3060 Ti 8GB, qwen3:8b Q4_K_M, Ollama 0.34.1 | 59.5 tok/s, 8,192 token context, reported memory 6.1, measured 23 September 2026 | [llm-bench.io benchmark](https://llm-bench.io/benchmarks/cmudsddd5013m01o6aam7d2hq) (a community benchmark feed) |
| RTX 5060 8GB, qwen3 8b, Ollama 0.9.5 | 61.70 tok/s, on a server with a 24-core Platinum 8160 and 64GB RAM | [Database Mart, Ollama GPU benchmark RTX 5060](https://www.databasemart.com/blog/ollama-gpu-benchmark-rtx5060) |
| Qwen3 8B | 8B parameters, Apache 2.0 | [Qwen/Qwen3-8B model card](https://huggingface.co/Qwen/Qwen3-8B) |

## Larger models on 8GB cards

| Machine and setup | Result | Source |
|---|---|---|
| RTX 4060 8GB, 32GB DDR5, Windows 11, Qwen3.8 27B UD-Q4_K_XL (17.56 GB GGUF), llama.cpp CUDA, 32K context | about 5.99 tok/s with MTP, about 3.82 without (about 57% more); 6 to 7 GB VRAM used | [r/Qwen_AI owner report](https://www.reddit.com/r/Qwen_AI/comments/1x28tms/qwen3827b_q4_on_rtx_4060_8gb_32gb_ram_6_toks_with/) |
| RX 7600 8GB, Ryzen 5 5600, 64 GB DDR4, Ubuntu 26.04, Qwen3.8 Flash Next (about 125B) IQ2_XS on Strata | 24 tok/s decode; Strata splits the MoE experts across GPU, CPU and RAM | [r/LocalLLM owner report](https://www.reddit.com/r/LocalLLM/comments/1wynz8o/rx_7600_8_gb_on_linux_qwen38flashnext_125b_at_24/) |
| Same rig, caveats | Strata needs about 33 GB of pinned RAM for IQ2_XS, so 64 GB is the practical minimum; it reads prompts in 256-token chunks | same thread |
| Same rig, Qwen3.6 35B A3B on llama.cpp | 23.6 tok/s decode without MTP, 32.0 tok/s with MTP | same thread |
| Same rig, desktop reserve | `--vram-reserve-mib 2560`; the default 700 MiB left GNOME Shell crashing | same thread |
| RTX 4060 Laptop GPU 8GB, Qwen3.6-35B-A3B-class MoE (Rotary GPU) | 21.06 tok/s decode, about 6.3 GB VRAM, 2,048 output tokens | [Rotary GPU, arXiv 2605.29135](https://arxiv.org/abs/2605.29135) |

## Bonsai 2 (Prism ML)

| Figure | Value | Source |
|---|---|---|
| Base model | derived from Qwen3.8-27B, ternary {−1, 0, +1} weights with FP16 group scaling | [prism-ml/Ternary-Bonsai-2-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-2-27B-gguf) |
| Deployed size, language model | 5.95 GB (PTQ1_0) or 7.21 GB (PQ2_0) | same card |
| Thinking-mode average, 14 benchmarks | 84.78 for Bonsai 2 against 86.32 for Qwen3.8-27B FP16 (98.2%) | same card |
| LiveCodeBench | 90.07 for Bonsai 2, 90.05 for FP16 | same card |
| Qwen3.8-27B FP16 footprint | 54 GB; UD-Q4_K_XL 17.6 GB | same card |
| Throughput | an Apple M5 Pro laptop result (28.1 tok/s, PQ2_0) is listed; no RTX 4060 result | same card |
| Runtime | stock llama.cpp will not run PTQ1_0 or PQ2_0; Prism's llama.cpp fork is required; the demo downloads PQ2_0 by default | same card; [Prism ML announcement](https://prismml.com/news/bonsai-2-27b) |

## Image and voice

| Figure | Value | Source |
|---|---|---|
| Stable Diffusion 3.5 Medium | 9.9 GB of VRAM, excluding text encoders, for full performance | [Stability AI, Introducing Stable Diffusion 3.5](https://stability.ai/news/introducing-stable-diffusion-3-5) |
| Stable Diffusion XL | 1024x1024 base resolution | [ComfyUI examples, SDXL](https://github.com/comfyanonymous/ComfyUI_examples/blob/master/sdxl/README.md) |
| Kokoro | 82 million parameters, Apache-licensed weights, "lightweight architecture" | [hexgrad/Kokoro-82M](https://huggingface.co/hexgrad/Kokoro-82M) |
| Qwen3-TTS | 0.6B CustomVoice and 1.7B Base models among others; voice design and cloning; the example loads the model on `cuda:0` in `torch.bfloat16` | [QwenLM/Qwen3-TTS](https://github.com/QwenLM/Qwen3-TTS) |

## Derived figures in the narration

| Figure | Working |
|---|---|
| 1.4 GB headroom at Q4_K_M | 7.2 − 5.79 = 1.41 |
| 0.7 GB headroom at Q5_K_M | 7.2 − 6.54 = 0.66 |
| 2.05 GB left after the PTQ1_0 file | 8 − 5.95 |
| under 1 GB left after the PQ2_0 file | 8 − 7.21 = 0.79 |
| 98.2% of full precision | 84.78 / 86.32 = 0.982 |
| 57% more decode speed with MTP | 5.99 / 3.82 = 1.57 |
| 54 GB at full precision | 27B parameters × 2 bytes (and the card's own figure) |

## Not checked

- The RTX 4060 figures are a calculator's estimate, not a measured run on the card.
- The 3060 Ti and 5060 results are single community and vendor runs; drivers, background load and settings change them.
- The memory split of the 27B offload between the card and system RAM beyond the owner's "6 to 7 GB VRAM used" is not reported.
- No published RTX 4060 speed exists for Bonsai 2.
{% endraw %}

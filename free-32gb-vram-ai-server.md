---
layout: default
title: "Two Free Tesla T4s Run A 35B Local AI Model (32GB VRAM)"
permalink: /free-32gb-vram-ai-server/
date: 2026-10-22
---

# Two Free Tesla T4s Run A 35B Local AI Model (32GB VRAM)

{% raw %}
The sources the script cites, as listed with it. Every price was opened on 2026-10-22 (PRICES.md
has the table). Nothing in this video was benchmarked by us: every speed is a named public run.

## Kaggle: the machines, the quota and the rules
- Kaggle notebooks docs (T4 x2 specs, 12h GPU and 9h TPU sessions, 20 min idle, 20GB disk, internet setting, VS Code URL, GPU misuse): https://www.kaggle.com/docs/notebooks
- Kaggle GPU quota (30 hours a week, resets weekly): https://www.kaggle.com/docs/efficient-gpu-usage
- Kaggle TPU docs (20 hours a week, 9 hours a session, 128GB of high-speed memory): https://www.kaggle.com/docs/tpu
- Kaggle staff: 2x T4 uses the same quota as one GPU: https://www.kaggle.com/discussions/product-feedback/361104
- Kaggle staff: GPU needs a phone-verified account: https://www.kaggle.com/discussions/product-feedback/202584
- Kaggle Terms of Use (personal, non-commercial use): https://www.kaggle.com/terms
- Kaggle Acceptable Use Policy (server farming, circumvention tools): https://www.kaggle.com/aup
- remokaggle (archived 2021, SSH tunnel warning): https://github.com/lamhoangtung/remokaggle

## The cards
- NVIDIA Tesla T4 specifications (16GB GDDR6, 320+ GB/s, 70W, Turing): https://www.nvidia.com/en-us/data-center/tesla-t4/
- NVIDIA Tesla P100 PCIe datasheet (16GB HBM2, 732 GB/s): https://images.nvidia.com/content/tesla/pdf/nvidia-tesla-p100-PCIe-datasheet.pdf
- FlashAttention README (Turing support, bf16 needs Ampere or newer): https://github.com/Dao-AILab/flash-attention
- llama.cpp CUDA scoreboard (Llama 2 7B Q4_0: Tesla T4 46.38, Tesla P100 58.35 tok/s): https://github.com/ggml-org/llama.cpp/discussions/15013

## Speeds (public runs, not ours)
- Qwen 3.8 27B Q4_K_M on Kaggle 2x T4 with Ollama, 16.23 tok/s (October 14 2026), and about 30GB usable VRAM: https://imprasit.substack.com/p/how-to-build-a-free-ai-server-on
- t4q engine for Qwen3.8-27B on Kaggle 2x T4 (30.4 tok/s plain, 66 to 71 tok/s with MTP; llama.cpp baseline 21.2 tok/s; prefill about 512 tok/s): https://github.com/Zapdev-labs/kaggle-t4-kernels
- Gemma 4 26B-A4B on Kaggle 2x T4, about 51 tok/s: https://github.com/w-sliman/llama-server-cuda-t4
- Qwen3.6 35B-A3B on 2x T4, about 25 tok/s: https://turbollm.dev/guides/turbollm-on-kaggle
- MiniCPM-V 4.7 on Kaggle 2x T4, 57.5 tok/s: https://github.com/ajithvnr2001/minicpmv47-kaggle-dual-t4-server
- Qwen3 30B-A3B on one free Kaggle T4 with llama.cpp's MoE cache, 22.6 to 43.2 tok/s: https://dev.to/sampop3/llamacpps-moe-cache-nearly-doubled-30b-decode-speed-on-a-free-t4-15np
- kaggle-tpu-lab (Qwen3.8-27B bf16 about 130 tok/s with MTP, 78 without; GLM-5.3-Flash about 165 tok/s; Cloudflare 100 s timeout; ID check): https://github.com/ARahim3/kaggle-tpu-lab
- kaggle-tpu-lab Qwen3.8-27B details: https://github.com/ARahim3/kaggle-tpu-lab/tree/main/qwen38-27b
- kaggle-tpu-lab GLM-5.3-Flash details: https://github.com/ARahim3/kaggle-tpu-lab/tree/main/glm53-flash
- Qwen 3.8 27B on a used RTX 3090, about 40 tok/s at 4K context (Hardware Corner): https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/
- Qwen 3.8 27B Q4_K_M on an RTX 5090, about 78 tok/s: https://x.com/witcheer/status/2088316316205907970

## Model file sizes
- Qwen 3.8 27B GGUF (Q4 16.46GB, Q8 29.05GB): https://huggingface.co/unsloth/Qwen3.8-27B-GGUF
- Gemma 4 31B GGUF (Q4_K_M 18.32GB): https://huggingface.co/unsloth/gemma-4-31B-it-GGUF
- Qwen3.6 35B-A3B GGUF: https://huggingface.co/unsloth/Qwen3.6-35B-A3B-GGUF
- gpt-oss-20b GGUF (Q4_K_M 11.62GB): https://huggingface.co/unsloth/gpt-oss-20b-GGUF
- Llama 3.3 70B GGUF (Q4_K_M 42.52GB, UD-IQ2_M 24.3GB): https://huggingface.co/unsloth/Llama-3.3-70B-Instruct-GGUF

## Other free tiers
- Google Colab FAQ (free tier limits, 12 hours, disallowed activities): https://research.google.com/colaboratory/faq.html
- Modal pricing ($30 a month in free credits, per second GPU rates, T4 about $0.59 an hour): https://modal.com/pricing
- Lightning AI pricing (free credits, about 80 GPU hours, 4 hour restarts): https://lightning.ai/pricing
- Hugging Face ZeroGPU docs (half an RTX Pro 6000 Blackwell, 48GB, daily quota): https://huggingface.co/docs/hub/spaces-zerogpu
- Google Cloud free trial (no GPUs): https://docs.cloud.google.com/free/docs/free-cloud-features
- AWS EC2 free tier instance types: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-free-tier-usage.html
- Oracle Always Free resources: https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm

## Prices (October 22 2026)
- RTX 5090 32GB, new from $4,921 on eBay: https://gpudojo.com/rtx-5090
- Used RTX 3090, going rate about $1,700: https://rigprice.com/gpu/rtx-3090/
- Used Tesla T4 16GB, from about $430: https://gpudojo.com/t4
- Qwen3.8 27B on OpenRouter, $2.20 per million output tokens: https://openrouter.ai/qwen/qwen3.8-27b

## Our maths (labelled as ours in the video)
- Two T4s for 30 hours at Modal's T4 rate: 0.59 x 2 x 30 = about $35 a week; x 52 = about $1,840 a year.
- A week of nonstop output: 20 tok/s x 3,600 x 30 = about 2.2 million tokens; x $2.20 per million = at most about $5.
- Speed ceiling of the T4 pair for a 16.5GB file: about 320 GB/s per card, the layers split across both cards and read in turn, so about 320 / 16.5 = about 19 tok/s.
- Dollars per GB: RTX 5090 4,921 / 32 = $154; used RTX 3090 1,700 / 24 = $71; two used T4s 860 / 32 = $27.
{% endraw %}

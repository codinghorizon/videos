---
layout: default
title: "Nvidia GPUs Are Slower Than You Think (Local AI)"
permalink: /nvidia-gpus-slower-than-you-think-local-ai/
date: 2026-11-08
---

# Nvidia GPUs Are Slower Than You Think (Local AI)

{% raw %}
The sources the script cites, as listed with it.

- gpu-unlock repository, README, supported GPUs, benchmark chart, workload table and FAQ: https://github.com/Zagitta/gpu-unlock
- gpu-unlock benchmark discussion #238 (RTX 3090 Ollama, vLLM and ComfyUI results; RTX 3060, 3070, 4080, 4090 and 2080 Ti results): https://github.com/Zagitta/gpu-unlock/discussions/238
- gpu-unlock issue #290, RTX 4070 llama.cpp Q6_K, no change in prompt or generation speed up to 32K tokens: https://github.com/Zagitta/gpu-unlock/issues/290
- gpu-unlock issue #280, RTX 3070 Ti, one hard freeze in four unlocked boots: https://github.com/Zagitta/gpu-unlock/issues/280
- gpu-unlock issue #304, RTX 4090 with a 10% BF16 gain: https://github.com/Zagitta/gpu-unlock/issues/304
- gpu-unlock issue #258, RTX 3090 at 120.7 BF16 TFLOPS and clock readings: https://github.com/Zagitta/gpu-unlock/issues/258
- Windows-GPU-UNLOCK, experimental Windows port (Secure Boot and BitLocker off): https://github.com/impacifist/Windows-GPU-UNLOCK
- NVIDIA Ampere GA102 GPU architecture whitepaper (RTX 3090 and RTX A6000 tensor rates; RTX 3090 936 GB/s): https://www.nvidia.com/content/PDF/nvidia-ampere-ga-102-gpu-architecture-whitepaper-v2.pdf
- NVIDIA Ada GPU architecture whitepaper (RTX 4090 tensor rates): https://images.nvidia.com/aem-dam/Solutions/geforce/ada/nvidia-ada-gpu-architecture.pdf
- Notebookcheck on gpu-unlock, October 24, 2026: https://www.notebookcheck.net/Nvidia-RTX-3090-performance-nearly-doubles-with-free-GPU-unlock-but-there-s-a-catch.1432805.0.html
- jacar.es on gpu-unlock (Nvidia has not commented): https://jacar.es/en/gpu-unlock-geforce-fp16-bf16-tensor-unlock/
- Inside gpu-unlock (token generation is memory-bandwidth bound): https://dev.to/terminalchai/inside-zagittagpu-unlock-unlocking-full-rate-fp16-bf16-tensor-math-on-nvidia-rtx-30-series-gpus-l7j
- RTX 3090 used asking price, $1,800 (rigprice, November 7, 2026): https://rigprice.com/gpu/rtx-3090/
- RTX 3060 12GB used asking price, $380 (rigprice, November 7, 2026): https://rigprice.com/gpu/rtx-3060-12gb/
- RTX 4090 used asking price, $3,555 (rigprice, November 7, 2026): https://rigprice.com/gpu/rtx-4090/
- RTX A6000 used asking price, $5,000 (rigprice, November 7, 2026): https://rigprice.com/gpu/rtx-a6000/
{% endraw %}

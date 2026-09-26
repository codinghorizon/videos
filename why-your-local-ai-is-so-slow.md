---
layout: default
title: "Your Local AI Is Slow for a Reason You Can Fix"
permalink: /why-your-local-ai-is-so-slow/
date: 2026-09-26
---

# Your Local AI Is Slow for a Reason You Can Fix

{% raw %}
Sources for the claims and figures this video puts on screen. Every page below was read on
25 September 2026.

## The two clocks

- Ollama's generate endpoint reports the time spent loading the model (`load_duration`),
  evaluating the prompt (`prompt_eval_duration`, with `prompt_eval_count`) and generating
  tokens (`eval_duration`, with `eval_count`) as separate fields. Source: Ollama API
  reference, Generate a response, https://docs.ollama.com/api/generate

## Where the model runs

- llama.cpp describes itself as running on CPU and several GPU backends: Apple silicon via
  Metal, custom CUDA kernels for NVIDIA GPUs (with AMD GPUs supported via HIP), Vulkan and
  SYCL backends, and CPU plus GPU hybrid inference to partially accelerate models larger than
  the total VRAM capacity. Source: llama.cpp README, Description,
  https://github.com/ggml-org/llama.cpp
- `-ngl, --gpu-layers`: the maximum number of layers to store in VRAM. `-c, --ctx-size`:
  the size of the prompt context. `-b, --batch-size`: logical maximum batch size.
  `-fa, --flash-attn`: sets Flash Attention on, off or auto. Source: llama.cpp server README,
  common params, https://github.com/ggml-org/llama.cpp/blob/master/tools/server/README.md
- `ollama ps` shows which memory a model was loaded into: `100% GPU` means entirely on the
  GPU, `100% CPU` entirely in system memory, and a split such as `48%/52% CPU/GPU` means
  partly in each. Source: Ollama FAQ, "How can I tell if my model was loaded onto the GPU?",
  https://docs.ollama.com/faq
- Windows Task Manager shows GPU utilisation per engine, with separate graphs for engines
  such as 3D, copy, video and compute. Source: Microsoft DirectX Developer Blog, "GPUs in the
  Task Manager", 21 July 2017,
  https://devblogs.microsoft.com/directx/gpus-in-the-task-manager/
- Activity Monitor on macOS can show GPU activity. Source: Apple, Activity Monitor User
  Guide, https://support.apple.com/guide/activity-monitor/view-gpu-activity-actmntr1003/mac
- `nvidia-smi` is NVIDIA's System Management Interface for monitoring its GPUs on Linux and
  Windows. Source: https://docs.nvidia.com/deploy/nvidia-smi/index.html
- Ollama supports NVIDIA GPUs with compute capability 5.0+ and driver version 550 and newer;
  after a suspend/resume cycle on Linux Ollama can fail to discover the NVIDIA GPU and fall
  back to running on the CPU. Source: Ollama docs, Hardware support,
  https://docs.ollama.com/gpu (read 26 September 2026)
- `llama-server` takes `-dev, --device` (a list of devices to use for offloading) and
  `--list-devices`. Source: llama.cpp server README,
  https://github.com/ggml-org/llama.cpp/blob/master/tools/server/README.md
- Ollama's FAQ: models are kept in memory for 5 minutes by default before being unloaded;
  `keep_alive` sets how long a model stays loaded and `0` unloads it immediately; with
  insufficient memory, idle models are unloaded to make room for a new one; the default
  context window is 4096 tokens and is changed with `OLLAMA_CONTEXT_LENGTH` or `num_ctx`;
  Flash Attention is used automatically when the backend and devices support it.
  Source: https://docs.ollama.com/faq

## Model size and quantization

- GGUF quantization types as the Hugging Face documentation lists them: F16 is 16 bit half
  precision; Q6_K works out at 6.5625 bits per weight, Q5_K at 5.5 and Q4_K at 4.5.
  Source: Hugging Face Hub docs, GGUF, Quantization Types, https://huggingface.co/docs/hub/gguf
- File sizes for one 7B model's GGUF quantizations, as listed on the repository: F16
  15.24 GB, Q6_K 6.25 GB, Q5_K_M 5.44 GB, Q4_K_M 4.68 GB, Q4_K_S 4.46 GB. The same model
  in two Q4 files is two different sizes. Source: bartowski/Qwen2.5-7B-Instruct-GGUF,
  https://huggingface.co/bartowski/Qwen2.5-7B-Instruct-GGUF
- Qwen2.5-7B-Instruct: 7.61B parameters, 28 layers, 131,072 token context. Source: model
  card, https://huggingface.co/Qwen/Qwen2.5-7B-Instruct (read 26 September 2026)
- Ollama's qwen2.5 library page lists sizes from 0.5b (398MB) through 7b (4.7GB), 14b
  (9.0GB), 32b (20GB) and 72b (47GB). Source: https://ollama.com/library/qwen2.5 (read 26
  September 2026)
- The Qwen3-30B-A3B repository lists a model size of 31B params in its Safetensors panel.
  Source: https://huggingface.co/Qwen/Qwen3-30B-A3B
- Qwen3-30B-A3B is a mixture of experts model with 30.5B parameters in total and 3.3B
  activated, 128 experts with 8 activated. Source: model card,
  https://huggingface.co/Qwen/Qwen3-30B-A3B
- Mixtral 8x7B routes each token to two of eight experts per layer, so each token has access
  to 47B parameters but uses only 13B active parameters during inference. Source: Jiang et
  al., "Mixtral of Experts", arXiv:2401.04088, https://arxiv.org/abs/2401.04088

## Context

- Ollama sets a default context length from available VRAM: 4k below 24 GiB, 32k from 24 to
  48 GiB, 256k at 48 GiB and above; a larger context length increases the memory required
  to run a model. Source: Ollama docs, Context length, https://docs.ollama.com/context-length

## Extra work

- Ollama's FAQ: parallel request processing for a model increases the context size by the
  number of parallel requests, so a 2K context with 4 parallel requests results in an 8K
  context and additional memory; `OLLAMA_MAX_LOADED_MODELS` is the maximum number of models
  loaded concurrently, provided they fit in available memory. Source: Ollama FAQ, "How does
  Ollama handle concurrent requests?", https://docs.ollama.com/faq
- Ollama can quantize the K/V cache when Flash Attention is enabled: q8_0 uses about half the
  memory of f16 and q4_0 about a quarter. Source: Ollama FAQ, "How can I set the
  quantization type for the K/V cache?", https://docs.ollama.com/faq

## Hardware and power

- Apple's MacBook Pro tech specs list unified memory per configuration (16GB to 128GB) and
  memory bandwidth per chip, from 153GB/s (M5) to 460GB/s (M5 Max). Source:
  https://www.apple.com/macbook-pro/specs/ (read 26 September 2026)
- Activity Monitor's Memory pane shows how much memory is used and how often memory is
  swapped between RAM and the startup disk. Source: Apple, "Check if your Mac needs more
  RAM in Activity Monitor",
  https://support.apple.com/guide/activity-monitor/check-if-your-mac-needs-more-ram-actmntr34865/mac
  (read 26 September 2026)

- Low Power Mode on a Mac reduces energy use and can reduce performance. Source: Apple
  Support, https://support.apple.com/en-us/101613
- Windows power mode lets you choose between efficiency and performance. Source: Microsoft
  Support, "Change the power mode for your Windows PC",
  https://support.microsoft.com/en-us/windows/change-the-power-mode-for-your-windows-pc-c2aff038-22c9-f46d-5ca0-78696fdf2de8

## Downloads

- llama.cpp publishes its builds and release notes on its GitHub releases page. Source:
  https://github.com/ggml-org/llama.cpp/releases
- llama.cpp documents separate CPU, BLAS, Metal, SYCL, CUDA and other builds. Source:
  https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md
- CUDA toolkit releases state a minimum driver version. Source: NVIDIA CUDA Toolkit release
  notes, https://docs.nvidia.com/cuda/cuda-toolkit-release-notes/index.html
- Apple's GPU framework is Metal. Source: https://developer.apple.com/metal/
- AMD publishes a ROCm compatibility matrix of supported GPUs and operating systems.
  Source: https://rocm.docs.amd.com/projects/install-on-linux/en/latest/reference/system-requirements.html
- Speculative decoding: a smaller draft model generates drafts that the target model then
  checks. Source: llama.cpp, `docs/speculative.md`,
  https://github.com/ggml-org/llama.cpp/blob/master/docs/speculative.md, and Leviathan et
  al., "Fast Inference from Transformers via Speculative Decoding", arXiv:2211.17192
- FlashAttention is an IO aware exact attention algorithm that reduces memory reads and
  writes. Source: Dao et al., arXiv:2205.14135, https://arxiv.org/abs/2205.14135
- Jan is an open source desktop app for running models locally. Source:
  https://github.com/janhq/jan
- `llama-bench` reports tokens per second per model, test and batch size, and its
  measurements do not include tokenization and sampling. Source: llama.cpp,
  tools/llama-bench/README.md,
  https://github.com/ggml-org/llama.cpp/blob/master/tools/llama-bench/README.md (read 26
  September 2026)
- llama.cpp's CPU build is built with CMake and no GPU backend. Source: docs/build.md, CPU
  Build, https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md

## Front ends named

- Ollama, https://ollama.com · LM Studio, https://lmstudio.ai · Jan, https://jan.ai ·
  llama.cpp, https://github.com/ggml-org/llama.cpp

## Not checked

- The Activity Monitor capture shows the app's own user guide; the GPU History window itself
  is not captured on screen.
- The first token delays and token rates shown on the waiting timelines are illustrative,
  not measurements of any machine.
- Whether a given newer processor with fewer cores beats a given older many core processor
  depends on the model and runtime; the video states this as a possibility and its strips
  are illustrative.
- Unified memory being slower than "every dedicated graphics card" is a general statement;
  no specific pair of machines is compared on screen.
{% endraw %}

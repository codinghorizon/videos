---
layout: default
title: "Your OS is quietly choosing how good local AI feels"
permalink: /which-operating-system-for-local-ai/
date: 2026-10-01
---

# Your OS is quietly choosing how good local AI feels

{% raw %}
Sources checked 30 September 2026.

## Windows

**Ollama runs natively on Windows with NVIDIA and AMD Radeon GPU support.** Ollama's Windows
documentation: "Ollama runs as a native Windows application, including NVIDIA and AMD Radeon
GPU support." It lists NVIDIA 551.61 or newer drivers for NVIDIA cards, and an AMD ROCm v7 /
HIP7 driver stack or a Vulkan-capable Radeon driver for AMD. The local API is served on
`http://localhost:11434`.
Source: https://docs.ollama.com/windows

**Ollama 0.30 enabled Vulkan by default.** Released 5 June 2026: "Vulkan is now enabled by
default, extending Ollama's GPU acceleration to a wider range of hardware, including AMD and
Intel devices." The same post reports up to 20% faster performance on NVIDIA hardware and
wider GGUF model support through llama.cpp.
Source: https://ollama.com/blog/improved-performance-and-model-support-with-gguf

**Ollama's desktop app chats with models and files.** "Ollama's macOS and Windows now include
a way to download and chat with models", and "Ollama's new app supports file drag and drop,
making it easier to reason with text or PDFs." (30 July 2025)
Source: https://ollama.com/blog/new-app

**LM Studio** is a desktop app for running local models, with local APIs (REST, OpenAI
compatible and Anthropic compatible endpoints) and a headless daemon.
Sources: https://lmstudio.ai, https://lmstudio.ai/docs/developer

**WSL2 runs a Linux environment on Windows.** Microsoft: WSL "allows you to run a Linux
environment on your Windows machine, without the need for a separate virtual machine or dual
booting."
Source: https://learn.microsoft.com/en-us/windows/wsl/about

**CUDA on WSL goes through the Windows driver.** NVIDIA's CUDA on WSL User Guide: existing
Linux CUDA applications "can run unmodified within the WSL environment"; the Windows display
driver "is the only driver you need to install. Do not install any Linux display driver in
WSL." The Windows driver is exposed inside WSL 2 as `libcuda.so`.
Source: https://docs.nvidia.com/cuda/wsl-user-guide/index.html

**Where files live under WSL affects speed.** Microsoft recommends against working across
operating systems with your files, and says that for the fastest performance you store files
in the WSL file system when working from a Linux command line, and in the Windows file system
when working from a Windows command line.
Source: https://learn.microsoft.com/en-us/windows/wsl/filesystems

**WSL networking has its own considerations.** By default WSL uses a NAT based architecture,
and Microsoft recommends trying mirrored networking mode.
Source: https://learn.microsoft.com/en-us/windows/wsl/networking

## Linux

**llama.cpp's supported backends** include CUDA (NVIDIA GPU), HIP (AMD GPU), Metal (Apple
Silicon), SYCL (Intel GPU) and Vulkan (GPU), among others.
Source: https://github.com/ggml-org/llama.cpp (Supported backends table)

**AMD ROCm lists supported GPUs and Linux distributions.** ROCm's System requirements (Linux)
page: "If a GPU is not listed on this table, it's not officially supported by AMD." The
current ROCm documentation now presents support as a compatibility matrix per device family,
GPU and Linux distribution (ROCm 10.0.0).
Sources: https://rocm.docs.amd.com/projects/install-on-linux/en/docs-7.0.0/reference/system-requirements.html,
https://rocm.docs.amd.com/en/latest/compatibility/compatibility-matrix.html

**Ollama on AMD Radeon.** Ollama supports a listed set of AMD GPUs through ROCm, with additional
AMD support through the Vulkan library, and on Linux requires the AMD ROCm v7 driver.
Source: https://docs.ollama.com/gpu

**Containers on Linux with NVIDIA GPUs** are set up through the NVIDIA Container Toolkit,
installed from the distribution's package manager (apt for Ubuntu and Debian, dnf, zypper).
Source: https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html

**llama.cpp's HTTP server** (`llama-server`) provides OpenAI compatible chat completions and
other REST endpoints, for running a model as a service.
Source: https://github.com/ggml-org/llama.cpp/tree/master/tools/server

## macOS

**Apple silicon uses unified memory.** MLX documentation: "Apple silicon has a unified memory
architecture. The CPU and GPU have direct access to the same memory pool. MLX is designed to
take advantage of that." Arrays do not need to be moved between devices.
Source: https://ml-explore.github.io/mlx/build/html/usage/unified_memory.html

**MLX** is "an array framework for machine learning on Apple silicon, brought to you by Apple
machine learning research." **MLX LM** is a Python package for generating text and fine
tuning large language models on Apple silicon with MLX.
Sources: https://github.com/ml-explore/mlx, https://github.com/ml-explore/mlx-lm

**Mac Studio memory.** Apple's Mac Studio tech specs list 36GB and 96GB unified memory
configurations, configurable to 48GB, 64GB or 128GB (M5 Max) and 256GB or 512GB (M5 Ultra).
Source: https://www.apple.com/mac-studio/specs/

## Memory and context

**Context uses memory.** Ollama's context length documentation: context length is the maximum
number of tokens the model has access to in memory, and Ollama's default context depends on
available VRAM (under 24 GiB: 4k; 24 to 48 GiB: 32k; 48 GiB and over: 256k).
Source: https://docs.ollama.com/context-length

**GPU compatibility has to be checked per card.** Ollama supports NVIDIA GPUs with compute
capability 5.0+ and driver version 550 and newer, and points to NVIDIA's compute capability
list to check a card.
Source: https://docs.ollama.com/gpu

## Not checked

- The narration says ROCm's "current" documentation carries the unlisted GPU statement. The
  statement is on ROCm's System requirements (Linux) pages through 7.x; the current 10.0.0
  documentation is organised as a compatibility matrix, and the video shows the 7.0.0 page.
- That networking, permissions and containers under WSL "each have details" is a general
  statement; only networking is shown from Microsoft's own page.
- How much slower a model runs when it spills into system memory depends on the model,
  runtime and machine; the video states no figure.
{% endraw %}

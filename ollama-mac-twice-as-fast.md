---
layout: default
title: "Ollama On Your Mac Can Run Local AI Twice As Fast"
permalink: /ollama-mac-twice-as-fast/
date: 2026-11-08
---

# Ollama On Your Mac Can Run Local AI Twice As Fast

{% raw %}
Every figure this video puts on screen, with the page it came from. Nothing here is our own
benchmark: each number is someone else's published test, and the video says whose.

## Fix one: the app it runs in

- **Ollama's own test, 58 to 112 tokens a second decode** (prefill 1,154 to 1,810), Qwen 3.5
  35B-A3B, NVFP4 on Ollama 0.19 against Q4_K_M on 0.18; the preview needed a Mac with more than
  32GB. [Ollama blog: MLX](https://ollama.com/blog/mlx)
- **Models run on MLX on Apple Silicon by default** from Ollama v0.40.0.
  [Release notes](https://github.com/ollama/ollama/releases/tag/v0.40.0) ·
  [all releases](https://github.com/ollama/ollama/releases)
- **Ollama 0.18 slower than llama.cpp, about 32.5 against 53.5 tokens a second** (the issue's
  table reads 32.54 and 53.53), fixed in 0.31.2 per the maintainer.
  [ollama/ollama#14861](https://github.com/ollama/ollama/issues/14861)
- **M1 Max 64GB, LM Studio 0.4.5: MLX 57, GGUF 29, Ollama 18 tokens a second as the UI reports
  them**; prefill 6.9 s against 2.9 s at 655 tokens and 49.4 s at 8.5K.
  [famstack: MLX vs GGUF](https://famstack.dev/guides/mlx-vs-gguf-apple-silicon/) ·
  [part 2](https://famstack.dev/guides/mlx-vs-gguf-part-2-isolating-variables/)
- **M4 Max 128GB, Qwen 3.5 35B-A3B: mlx-lm 130.2, llama.cpp 71.0, Ollama 43.5 tokens a second.**
  [Antek Apetanovic](https://antekapetanovic.com/blog/qwen3.5-apple-silicon-benchmark/)
- **M3 Ultra, Qwen 3.5 9B: Ollama GGUF 77.7, Ollama MLX 90.5, mlx-lm 107.5 tokens a second.**
  [terminalbytes](https://terminalbytes.com/ollama-vs-llama-cpp-vs-mlx-mac-2026/)
- **"About 10~20% speed gain"** from GGUF to MLX, a reply on r/LocalLLaMA.
  [Reddit thread](https://www.reddit.com/r/LocalLLaMA/comments/1rezq19/)
- **Long context can flip it: MLX 5.95 against llama.cpp with flash attention 12.12 tokens a
  second at 146K** on an M3 Ultra. [ml-explore/mlx-lm#763](https://github.com/ml-explore/mlx-lm/issues/763)
- The M1 Max launched in October 2021.
  [Apple Newsroom](https://www.apple.com/newsroom/2021/10/introducing-m1-pro-and-m1-max-the-most-powerful-chips-apple-has-ever-built/)

## Fix two: the memory macOS gives the GPU

- **The GPU's share is capped by default and raised with `sudo sysctl iogpu.wired_limit_mb`**;
  the setting does not survive a reboot, and going past the default can mean slow, swapping
  loads. [llama.cpp discussion #2182](https://github.com/ggml-org/llama.cpp/discussions/2182)
- **Setting it to 0 restores the default; leave 8 to 16GB for the system.**
  [InsiderLLM](https://insiderllm.com/guides/ollama-mac-setup-optimization)
- **The wired limit must stay strictly below total memory.**
  [MLX docs](https://ml-explore.github.io/mlx/build/html/python/_autosummary/mlx.core.set_wired_limit.html) ·
  [mlx-lm README](https://github.com/ml-explore/mlx-lm)
- **Checking where a model runs: the PROCESSOR column of `ollama ps`** (100% GPU, or a CPU/GPU
  split). [Ollama FAQ](https://github.com/ollama/ollama/blob/main/docs/faq.mdx)

## Fix three: the context length setting

- **Ollama's default context by memory: 4K under 24GB, 32K from 24 to 48GB, 256K above; 64,000
  for agents and coding tools.** [Ollama docs: context length](https://docs.ollama.com/context-length)
- **A 16GB M4 Mac mini at 128K context: qwen3:4b needed 23GB, 51% ran on the CPU, 32 fell to
  19.4 tokens a second.** [creatos](https://creatos.io/tests/why-ollama-is-slow-on-mac-context-length)
- **The MLX runner does not reserve the whole context up front.**
  [ollama/ollama#16219](https://github.com/ollama/ollama/issues/16219)
- **M2 Ultra, Qwen3 30B-A3B: 79.0 tokens a second falls to 45.3 at 32K depth** (the table
  reads 78.97 and 45.26). [llama.cpp M2 Ultra benchmarks](https://github.com/ggml-org/llama.cpp/blob/master/benches/mac-m2-ultra/mac-m2-ultra.md)
- **KV cache size worked from Llama 3.1 8B's config** (32 layers, 8 KV heads, head dim 128).
  [config.json](https://huggingface.co/unsloth/Llama-3.1-8B-Instruct/blob/main/config.json)
- **The KV cache in 8 bits (`q8_0`)** is an Ollama option; some report slower generation with it
  on Macs. [Ollama FAQ](https://github.com/ollama/ollama/blob/main/docs/faq.mdx) ·
  [InsiderLLM](https://insiderllm.com/guides/ollama-mac-setup-optimization)
- **Plain M4, LLaMA 7B: Q4_0 24.11, Q8_0 13.54, F16 7.43 tokens a second at 120GB/s.**
  [llama.cpp discussion #4167](https://github.com/ggml-org/llama.cpp/discussions/4167)
{% endraw %}

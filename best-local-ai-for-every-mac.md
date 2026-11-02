---
layout: default
title: "The Best Local AI For Every Mac"
permalink: /best-local-ai-for-every-mac/
date: 2026-11-02
---

# The Best Local AI For Every Mac

{% raw %}
The sources the script cites, as listed with it.

VIEWER-COMMENT: HRLhJjaCu-E "I have MacBook Air M5 16 512 Which model can I run"
- llama.cpp Apple Silicon benchmark, Llama 2 7B Q4_0 tg128: M1 14.15, M4 24.11 tok/s: https://github.com/ggml-org/llama.cpp/discussions/4167
- Default GPU memory limit on Apple Silicon (two thirds up to 36GB, three quarters above) and raising it: https://techobsessed.net/2023/12/increasing-ram-available-to-gpu-on-apple-silicon-macs-for-running-large-language-models/
- llama.cpp discussion of the recommended max working set size on Apple Silicon: https://github.com/ggml-org/llama.cpp/discussions/2182
- mlx-lm, raising the wired limit with sysctl iogpu.wired_limit_mb: https://github.com/ml-explore/mlx-lm
- LM Studio system requirements (Apple Silicon, 16GB+ recommended, small models on 8GB): https://lmstudio.ai/docs/app/system-requirements
- MacBook Air specs, M5 153GB/s memory bandwidth, 24GB option: https://www.apple.com/macbook-air/specs/
- M1 Max 400GB/s memory bandwidth: https://www.apple.com/newsroom/2021/10/introducing-m1-pro-and-m1-max-the-most-powerful-chips-apple-has-ever-built/
- Gemma 4 E2B GGUF, Q4_K_M 3.11GB: https://huggingface.co/unsloth/gemma-4-E2B-it-GGUF
- Gemma 4 E4B GGUF, Q4_K_M 4.98GB: https://huggingface.co/unsloth/gemma-4-E4B-it-GGUF
- Gemma 4 12B GGUF, Q4_K_M 7.12GB: https://huggingface.co/unsloth/gemma-4-12b-it-GGUF
- Gemma 4 26B-A4B GGUF, 3.8B active: https://huggingface.co/unsloth/gemma-4-26B-A4B-it-GGUF
- Qwen 3.5 9B GGUF, Q4_K_M 5.68GB: https://huggingface.co/unsloth/Qwen3.5-9B-GGUF
- Qwen 3.8 27B GGUF, UD-Q4_K_M 16.46GB: https://huggingface.co/unsloth/Qwen3.8-27B-GGUF
- Qwen 3.6 35B-A3B MLX 4-bit, 20.40GB: https://huggingface.co/mlx-community/Qwen3.6-35B-A3B-4bit
- Qwen 3.8 Flash-Next GGUF, UD-Q4_K_XL 111.33GB, UD-IQ4_XS 93.7GB, smallest file 72.5GB: https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF
- gpt-oss-120b GGUF, Q4_K_M 62.8GB: https://huggingface.co/unsloth/gpt-oss-120b-GGUF
- M1 8GB, Gemma 4 E2B Q4 in Ollama, 15-20 tok/s (llamaperf user report): https://llamaperf.com/report/692c0506-b60f-4be8-8657-9f0adbabf67f
- M1 16GB, Gemma 4 E4B MLX 4-bit, 8.2 tok/s (llamaperf): https://llamaperf.com/report/0f3d1b2d-bcbc-406e-a445-15efd02d34d6
- M4 16GB Mac mini, Qwen 3.5 9B Q4_K_M, 17.7 tok/s (llamaperf): https://llamaperf.com/report/6d6bd1f8-e8f8-4c57-8efa-a8a72a6f4096
- M4 16GB Mac mini, Gemma 4 12B, 13.1 tok/s (llamaperf): https://llamaperf.com/report/0602ef2f-47d9-4942-923a-8e396ab52ad6
- M5 16GB MacBook Air, Qwen 3.5 9B, 25 tok/s with a custom MLX engine (llamaperf): https://llamaperf.com/report/841f288d-9dec-4c72-943d-8df639b19239
- M4 Pro 24GB, Gemma 4 26B-A4B QAT in Ollama, 36-38 tok/s, 9% memory free (llamaperf): https://llamaperf.com/report/1df21626-47ae-4913-86e9-819eae42c9f3
- M4 Pro 24GB, Qwen 3.8 27B Q4_K_M, 11.4 tok/s (llamaperf): https://llamaperf.com/report/2f013c70-7fcb-4549-b660-362c6b87eedf
- M6 32GB, Qwen 3.8 27B Q4_K_M in LM Studio, 11.8 tok/s (llamaperf): https://llamaperf.com/report/d2d9827b-7391-4fac-b51e-a7ac66743505
- M6 32GB, Qwen 3.6 35B-A3B MLX 4-bit in LM Studio, 63.8 tok/s (llamaperf): https://llamaperf.com/report/d1c23d37-16c6-43b0-8eab-fafa820be02f
- M1 Max 32GB, Qwen 3.8 27B MLX, 15.8 tok/s (llamaperf): https://llamaperf.com/report/26e1bb85-0ded-44f1-8e00-41a458f999a3
- M5 Max 48GB, Qwen 3.6 35B-A3B Q4_K_M in llama.cpp, 124.3 tok/s (llamaperf): https://llamaperf.com/report/fd5dcb77-032b-47dd-8e69-ba2ad96b6525
- M5 Max 48GB, Gemma 4 31B Q4_K_M, 25.2 tok/s (llamaperf): https://llamaperf.com/report/029a8867-3513-4bdc-a034-34d7f01a9af4
- M2 Max 64GB, Qwen 3.6 35B-A3B in LM Studio, 83.8 tok/s (llamaperf): https://llamaperf.com/report/91068037-4617-4a19-952e-487f49f12733
- M4 Max 64GB, Qwen 3.8 27B Q4_K_M, 23.9 tok/s (llamaperf): https://llamaperf.com/report/bd485d2a-b5d1-42a9-86e4-fb00a851e620
- M1 Max 64GB, Qwen 3.6 35B-A3B in MTPLX (speculative decoding), 62 tok/s (llamaperf): https://llamaperf.com/report/06fcd973-9372-4f7e-bc49-13b58a08669a
- M4 Max 128GB, Qwen 3.8 Flash-Next UD-Q3_K_XL in llama.cpp, 27.3 tok/s (llamaperf): https://llamaperf.com/report/4bd01db4-cfa9-490a-b1a1-edd624fd79a7
- M3 Ultra 512GB, Qwen 3.5 397B-A17B 6-bit, 29.2 tok/s (llamaperf): https://llamaperf.com/report/4b0a832d-1324-43d9-8c19-a60e46ef7ffc
- M5 Ultra 256GB, GLM-5.3-Flash 320B-A18B in oMLX, 61.7 tok/s (llamaperf): https://llamaperf.com/report/3622ad63-5fa5-4293-831e-7d60db9be6cf
- ChatGPT Plus, $20 a month: https://help.openai.com/en/articles/6950777
{% endraw %}

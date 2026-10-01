---
layout: default
title: "32GB VRAM Can Run These Models, But One Stands Out"
permalink: /best-local-ai-on-32gb-vram/
date: 2026-10-01
---

# 32GB VRAM Can Run These Models, But One Stands Out

{% raw %}
Sources checked on 30 September 2026.

## The cards

- **GeForce RTX 5090: 32 GB of GDDR7.** NVIDIA's specification: "Standard Memory Config 32 GB GDDR7".
  https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/
- **Radeon AI PRO R9700: 32 GB.** AMD's product page for the workstation card.
  https://www.amd.com/en/products/graphics/workstations/radeon-ai-pro/ai-9000-series/amd-radeon-ai-pro-r9700.html

## Qwen 3.5 27B

- **27 billion parameters, a causal language model with a vision encoder.** Model card, Model Overview:
  "Type: Causal Language Model with Vision Encoder", "Number of Parameters: 27B".
  https://huggingface.co/Qwen/Qwen3.5-27B
- **Context: 262,144 tokens natively, extensible to 1,010,000.** Same card: "Context Length: 262,144
  natively and extensible up to 1,010,000 tokens."
- **72.4 on SWE-bench Verified and 80.7 on LiveCodeBench v6.** Same card, Benchmark Results, Language,
  Coding rows, Qwen3.5-27B column. The card also reports reasoning and vision language results.
- **17 GB package in Ollama, 256K context, text and image input.** Ollama library, qwen3.5 tags:
  `qwen3.5:27b · 17GB · 256K · Text, Image`.
  https://ollama.com/library/qwen3.5

## Gemma 4 26B A4B

- **About four billion parameters active per token; all 26 billion must be loaded.** Google's Gemma 4
  overview, Key Considerations for Memory Planning: "While it only activates 4 billion parameters per
  token during generation, all 26 billion parameters must be loaded into memory".
  https://ai.google.dev/gemma/docs/core
- **Image input and a draft model for speculative decoding.** Same page, Capabilities: "Processes Text,
  Image with variable aspect ratio and resolution support (all models)" and "All Gemma 4 models (E2B,
  E4B, 12B, 31B, and 26B A4B) include a dedicated draft model for speculative decoding".
- **14.4 GB at Q4_0 just to load.** Same page, Table 1, Gemma 4 26B A4B row: BF16 57.7 GB, SFP8 28.8 GB,
  Q4_0 14.4 GB. The caption: "Approximate GPU or TPU memory required to load Gemma 4 models based on
  parameter count, quantization level and 20% overhead of loading additional things."
- **The table excludes context and supporting software.** Same page: "The estimates in the preceding
  table only account for the memory required to load the static model weights. They don't include the
  additional VRAM needed for supporting software or the context window."
- **256K context for the medium models.** Same page: "Small models feature a 128K context window, while
  the medium models support 256K." Model card on Hugging Face: 25.2B total, 3.8B active.
  https://huggingface.co/google/gemma-4-26B-A4B-it

## Qwen 3 Coder 30B

- **30.5 billion parameters in total, 3.3 billion activated, 262,144 token context.** Model card, Model
  Overview: "Number of Parameters: 30.5B in total and 3.3B activated", "Context Length: 262,144
  natively".
  https://huggingface.co/Qwen/Qwen3-Coder-30B-A3B-Instruct
- **Built for agentic coding.** Same card, Highlights: "Significant Performance among open models on
  Agentic Coding, Agentic Browser-Use, and other foundational coding tasks."
- **19 GB in Ollama, 256K, text input only.** Ollama library: `qwen3-coder:30b · 19GB · 256K · Text`.
  https://ollama.com/library/qwen3-coder

## Devstral Small 2

- **24B, image input, positioned for tools, codebases and multi file edits.** Model card: "Devstral
  Small 2 excels at using tools to explore codebases, editing multiple files and power software
  engineering agents", and under Updates, "Vision Capabilities: Enables the model to analyze images".
  https://huggingface.co/mistralai/Devstral-Small-2-24B-Instruct-2512
- **15 GB four bit package in Ollama, text and image input.** `devstral-small-2:24b · 15GB · 384K ·
  Text, Image`.
  https://ollama.com/library/devstral-small-2
- **65.8% on SWE-bench Verified and 32.0% on Terminal Bench.** Mistral's benchmark table as carried on
  the Ollama library page, beside larger systems (Devstral 2 at 123B, DeepSeek v3.2 at 671B, Kimi K2
  Thinking at 1000B and others). Mistral's own model card and announcement now report 68.0% on
  SWE-bench Verified and 22.5% on Terminal Bench 2 for the same model.
  https://mistral.ai/news/devstral-2-vibe-cli/

## gpt-oss 20B

- **14 GB in Ollama, 128K, text input.** `gpt-oss:20b · 14GB · 128K · Text`. Ollama's page describes the
  family as "designed for powerful reasoning, agentic tasks, and versatile developer use cases".
  https://ollama.com/library/gpt-oss
- **MXFP4 at 4.25 bits per parameter for the mixture of experts weights.** Same page: "The models are
  post-trained with quantization of the mixture-of-experts (MoE) weights to MXFP4 format, where the
  weights are quantized to 4.25 bits per parameter."
- **21 billion parameters with 3.6 billion active; configurable reasoning effort; function calling and
  structured outputs; Apache 2.0.** Model card.
  https://huggingface.co/openai/gpt-oss-20b

## Benchmarks

- **SWE-bench Verified** is "a human-filtered subset of 500 instances", and its leaderboard defaults to
  a bash only setting run with mini-SWE-agent.
  https://www.swebench.com/
- **LiveCodeBench** collects problems from periodic contests on LeetCode, AtCoder and Codeforces.
  https://livecodebench.github.io/

## Runners

- **LM Studio** runs open models locally with its own app.
  https://lmstudio.ai/
- **Ollama's local API** is served at `http://localhost:11434/api`; the same page lists `https://ollama.com/api`
  for cloud access.
  https://docs.ollama.com/api/introduction
{% endraw %}

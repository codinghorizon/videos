---
layout: default
title: "Your 8GB GPU Can Code Locally If You Pick Right"
permalink: /local-ai-coding-8gb-vram/
date: 2026-08-31
---

# Your 8GB GPU Can Code Locally If You Pick Right

{% raw %}
Every figure this video puts on screen, and where it comes from.

All model sizes are the **published GGUF blob sizes** taken from each repository's own file
listing, converted to gigabytes at 2^30 bytes. That is the unit local runners report memory
in, and it is the unit an "8 GB card" is sold in, so the card and the weights are compared
on the same scale throughout.

The two figures that are computed rather than quoted are the KV cache per token and the
cache at a given context length. Both are arithmetic over values taken from Qwen2.5 Coder
7B Instruct's own `config.json`, and the arithmetic is shown on screen so it can be checked.

---

## Qwen2.5 Coder 7B Instruct (the pick)

- 7.61 B total parameters, 6.53 B non embedding, 28 layers, Apache 2.0.
  <https://huggingface.co/Qwen/Qwen2.5-Coder-7B-Instruct>
- Long context support up to 128K tokens; the model card states a full context of 131,072
  tokens, while `config.json` gives `max_position_embeddings` 32,768.
  <https://huggingface.co/Qwen/Qwen2.5-Coder-7B-Instruct/raw/main/config.json>
- `num_hidden_layers` 28, `num_attention_heads` 28, `num_key_value_heads` 4,
  `hidden_size` 3584. Head dimension is therefore 3584 / 28 = 128.
- Published GGUF file sizes (bytes), from the repository listing:
  Q2_K 3,015,940,032 · Q3_K_M 3,808,391,104 · Q4_0 4,431,390,720 ·
  **Q4_K_M 4,683,073,536 (4.36 GB)** · Q5_K_M 5,444,831,232 · Q6_K 6,254,198,784 ·
  Q8_0 8,098,525,184 (7.54 GB).
  <https://huggingface.co/Qwen/Qwen2.5-Coder-7B-Instruct-GGUF>

### The KV cache figure, derived

Bytes held per token, at 16 bit:

    2 (a key and a value) x 28 layers x 4 kv heads x 128 head dim x 2 bytes = 57,344 bytes

which is **56 KB per token**. So the cache is 0.44 GB at 8,192 tokens, 0.88 GB at 16,384
and 1.75 GB at 32,768. Those are the numbers the trough segments are drawn from, and the
multiplication itself is on screen in the KV cache beat.

## Kimi K2 Thinking

- 1 T total parameters, 32 B activated, 384 experts with 8 selected per token plus 1 shared,
  256K context, native INT4 via quantisation aware training, modified MIT licence.
  <https://huggingface.co/moonshotai/Kimi-K2-Thinking>
- Weight shards total **594,283,168,582 bytes (553 GB)** across 62 safetensors files, at the
  INT4 format the model ships in. That is the figure the video compares against the card,
  and 553 / 8 is where the 69x on screen comes from.

## Qwen3 Coder 30B A3B Instruct

- 30.5 B total, 3.3 B activated, 128 experts with 8 activated, 48 layers, 262,144 native
  context, Apache 2.0. <https://huggingface.co/Qwen/Qwen3-Coder-30B-A3B-Instruct>
- Q4_K_M GGUF 18,556,689,568 bytes (17.28 GB).
  <https://huggingface.co/unsloth/Qwen3-Coder-30B-A3B-Instruct-GGUF>

## Mistral Small 24B Instruct 2501

- 24 B parameters, 32k context, Apache 2.0. The model card itself states it "fits in a
  single RTX 4090 or a 32GB RAM MacBook once quantized".
  <https://huggingface.co/mistralai/Mistral-Small-24B-Instruct-2501>
- Q4_K_M GGUF 14,333,909,248 bytes (13.35 GB).
  <https://huggingface.co/unsloth/Mistral-Small-24B-Instruct-2501-GGUF>

## Qwen3 8B

- 8.2 B total, 6.95 B non embedding, 36 layers, 32,768 native context (131,072 with YaRN),
  Apache 2.0, with switchable thinking and non thinking modes.
  <https://huggingface.co/Qwen/Qwen3-8B>
- Q4_K_M GGUF 5,027,783,488 bytes (4.68 GB).
  <https://huggingface.co/Qwen/Qwen3-8B-GGUF>

## The DeepSeek R1 distills

- R1 Distill Qwen 7B is built on Qwen2.5 Math 7B; R1 Distill Llama 8B on Llama 3.1 8B.
  Published scores: LiveCodeBench pass@1 37.6 and 39.6, Codeforces ratings 1189 and 1205,
  AIME 2024 pass@1 55.5 and 50.4.
  <https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Qwen-7B>
- R1 0528 Qwen3 8B distils DeepSeek R1 0528's chain of thought onto Qwen3 8B Base. MIT.
  AIME 2024 86.0, AIME 2025 76.3.
  <https://huggingface.co/deepseek-ai/DeepSeek-R1-0528-Qwen3-8B>
- Q4_K_M GGUF for R1 0528 Qwen3 8B is 5,027,785,216 bytes (4.68 GB).
  <https://huggingface.co/unsloth/DeepSeek-R1-0528-Qwen3-8B-GGUF>

## Llama 3.1 8B Instruct

- 8 B parameters, 128,000 context, over 15 trillion training tokens, Llama 3.1 Community
  License. <https://huggingface.co/meta-llama/Llama-3.1-8B-Instruct>
- Q4_K_M GGUF 4,920,739,168 bytes (4.58 GB).
  <https://huggingface.co/lmstudio-community/Meta-Llama-3.1-8B-Instruct-GGUF>

## Gemma 3 and Gemma 3n

- Gemma 3 ships at 1B, 4B, 12B and 27B. The **4B, 12B and 27B are the ones with vision**;
  the 1B is text only. Context up to 128k.
  <https://developers.googleblog.com/en/introducing-gemma3/>
  <https://huggingface.co/google/gemma-3-4b-it>
- Gemma 3n is the low resource line: E4B holds 8 B raw parameters but runs at an effective
  4 B "by offloading low-utilization matrices from the accelerator", E2B at an effective 2 B.
  Text, image, audio and video in, 32K context. <https://huggingface.co/google/gemma-3n-E4B-it>
- Gemma 3 4B Q4_K_M is 2,489,894,016 bytes (2.32 GB) and its vision projector is a separate
  851,251,328 byte file (0.79 GB), which is why the video draws the projector as its own
  segment of the memory budget. <https://huggingface.co/unsloth/gemma-3-4b-it-GGUF>

---

## Not verified

- The tokens per second figures, the prompt evaluation times and the layer offload counts
  shown in terminals and on dials are **illustrative of the behaviour being described**,
  not measurements from a particular machine. They depend on the card, the driver, the
  runner and the quantisation, and no single number would be true across them.
- The "runner and desktop" allowance of roughly half a gigabyte in the memory budget
  shots is an allowance for the CUDA context and compute buffers rather than a published
  figure.
- "Four runners" for mature local support counts Ollama, LM Studio, llama.cpp and vLLM,
  which all carry the model; it is a count of the runners named in the video rather than an
  exhaustive one.
- The narration's claim that Qwen2.5 Coder 7B Instruct is the model to start with on an 8 GB
  card is an editorial recommendation, not a benchmark result.
{% endraw %}

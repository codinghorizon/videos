---
layout: default
title: "9 Local AI models ranked: the biggest wastes your VRAM"
permalink: /local-ai-models-tier-list/
date: 2026-09-23
---

# 9 Local AI models ranked: the biggest wastes your VRAM

{% raw %}
Every figure, size, score and capability this video states, chased to a primary source.
Sizes are the ones the distributor's own page shows rather than calculated from a parameter
count, because the download is what is being compared.

Two kinds of number appear in this video and they are not sourced the same way. A
**published figure** is somebody's own number and is cited here. A **planning range** is the
script's own estimate of working memory, and the script says so itself; those are not
measurements and are not presented as any.

## The models, in ranking order

### Llama 3.1 8B instruct — B tier

- Ollama `llama3.1:8b` download **4.9GB**, quantisation **Q4_K_M**, **8.03B** parameters,
  context **128K**. <https://ollama.com/library/llama3.1:8b>
- Text in, text out. No image input.

### Gemma 4 26B A4B instruction tuned — A tier

- Ollama `gemma4:26b` download **19GB**, **25.2B** total parameters, **3.8B** active,
  context **256K**, multimodal text and image input with a **~550M** vision encoder,
  native function calling, configurable thinking modes.
  <https://ollama.com/library/gemma4:26b>
- The A4B appears in the name on Google's own card, `google/gemma-4-26B-A4B-it`:
  **26B params** in its safetensors box, licence **apache-2.0**. Ollama's tag for the same
  model is `gemma4:26b` and carries no A4B at all.
  <https://huggingface.co/google/gemma-4-26B-A4B-it>
- The dense sibling `gemma4:31b` is **30.7B** parameters, **20GB**.
  <https://ollama.com/library/gemma4>
- Ollama's family table puts the two side by side: `gemma4:26b` **19GB**, `gemma4:31b`
  **20GB**, both 256K context, both text and image. One gigabyte apart, which is why fewer
  active parameters does not mean a smaller download. <https://ollama.com/library/gemma4>
- Google's own reasoning comparison, 31B dense against 26B A4B:
  MMLU Pro **85.2%** against **82.6%**; AIME 2026 no tools **89.2%** against **88.3%**;
  GPQA Diamond **84.3%** against **82.3%**; Tau2 **76.9%** against **68.2%**;
  BigBench Extra Hard **74.4%** against **64.8%**.
  <https://huggingface.co/google/gemma-4-31b-it>

The script says "roughly 26 billion in total, but about four billion active". The
published figures are 25.2B and 3.8B.

### DeepSeek R1 distill qwen 7B — C tier

- Ollama `deepseek-r1:7b` download **4.7GB**, **Q4_K_M**, and the page names the tag as
  **DeepSeek-R1-Distill-Qwen-7B**. <https://ollama.com/library/deepseek-r1:7b>
- **55.5** pass@1 on **AIME 2024**, in the model card's "Distilled Model Evaluation" table.
  The base is **Qwen2.5-Math-7B** and the distillation uses DeepSeek R1's reasoning work,
  so the release is DeepSeek's and Qwen is the base it was built from.
  <https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Qwen-7B>
- The full model the name refers to, DeepSeek R1, is **684B params**, tensor types
  BF16, F8_E4M3 and F32. <https://huggingface.co/deepseek-ai/DeepSeek-R1>

### Ministral 3 8B instruct 2512 — A tier

- **8.4B** language model plus a **0.4B** vision encoder; "capable of fitting in 12GB of
  VRAM in FP8, and less if further quantized"; context **256k**; native function calling
  and JSON output; and the guidance to "limit their number to the minimum required for the
  use case". <https://huggingface.co/mistralai/Ministral-3-8B-Instruct-2512>
- Ollama `ministral-3:8b` download **6.0GB**, 256K context, text and image.
  <https://ollama.com/library/ministral-3>

### Llama 3.3 70B instruct — D tier

- Ollama `llama3.3:70b` download **43GB**, **Q4_K_M**, **70.6B** parameters, and Meta's own
  README line as Ollama carries it: "Llama 3.3 70B offers similar performance compared to
  the Llama 3.1 405B model." <https://ollama.com/library/llama3.3:70b>
- "optimized for multilingual dialogue use cases"; **text in/text out** only, so no image
  input; context **128k**. <https://huggingface.co/meta-llama/Llama-3.3-70B-Instruct>
- 43GB against llama 3.1 8B's 4.9GB is **8.8x**, which is the script's "nearly nine copies".
- The 64GB mac the script names is a real configuration rather than a round number: the
  Mac mini's M5 Pro column ships with 24GB unified memory and is **"Configurable to: 48GB
  or 64GB"**. <https://www.apple.com/uk/mac-mini/specs/>

### Phi 4 reasoning vision 15B — B tier

- Context **16,384 tokens**; **15B** parameters; tensor type **BF16**.
  <https://huggingface.co/microsoft/Phi-4-reasoning-vision-15B>
- What Microsoft says it targets, in the card's own words: "Scientific and mathematical
  reasoning over visual inputs", "Computer-use agent (CUA) tasks" including GUI
  interpretation and element localization, and "image captioning, visual question
  answering, optical character recognition, object localization, and grounding".
- Stated runtime requirements: **torch >= 2.7.1, transformers >= 4.57.1, vllm >= 0.15.2**,
  hosted "on a vLLM server using bf16 precision", tested on A6000, A100, H100 and B200.
- **7.5GB** is 15 billion parameters at 4 bits, which is arithmetic rather than a published
  package size, and the script calls it "raw four bit weight arithmetic" for that reason.
- **The custom model code is in config.json, not on the card.** The card states version
  floors and never says `trust_remote_code`. The config declares
  `"architectures": ["Phi4ForCausalLMV"]` and an `auto_map` naming
  `modeling_phi4_visionr.Phi4VisionR`, `modeling_phi4_visionr.Phi4ForCausalLMV` and
  `processing_phi4_visionr.Phi4VisionRProcessor`. An `auto_map` pointing at modelling and
  processing modules held in the repository is custom model code loaded through
  transformers.
  <https://huggingface.co/microsoft/Phi-4-reasoning-vision-15B/blob/main/config.json>
- **Two different context numbers.** The card states **Context Length: 16,384 tokens**;
  config.json reports `max_position_embeddings` **32768**, which is the positional table
  the backbone was built with rather than the supported window. 16,384 is the published
  context length and is the figure this video uses.

### Mistral 7B instruct version 0.3 — F tier

- Ollama `mistral:7b` download **4.4GB**, **Q4_K_M**, **7.25B** parameters, Apache License
  2.0, and v0.3 "supports function calling". <https://ollama.com/library/mistral:7b>
- The card's own change list against v0.2: **"Extended vocabulary to 32768"**,
  **"Supports v3 Tokenizer"**, **"Supports function calling"**. The vocabulary size and the
  context length are both 32768 and are not the same quantity.
  <https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.3>
- `max_position_embeddings` **32768**, licence **apache-2.0**, no image input.
  <https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.3>
  and <https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.3/raw/main/config.json>
- 6.0GB against 4.4GB is a **1.6GB** saving.

### Devstral small 2 24B instruct 2512 — A tier

- **68.0%** SWE-bench Verified; the larger **123B** Devstral 2 reaches **72.2%**;
  "a single RTX 4090 or a Mac with 32GB RAM"; vision capabilities; **24 billion**
  parameters; **256k** context; Apache 2.0.
  <https://huggingface.co/mistralai/Devstral-Small-2-24B-Instruct-2512>
- Ollama `devstral-small-2:24b` download **15GB**, **Q4_K_M**.
  <https://ollama.com/library/devstral-small-2:24b>
- 72.2 against 68.0 is **4.2 points** for **5.1x** the parameters, both derived from the
  two published figures.

### Qwen 3.8 27B — S tier

- Terminal-Bench 2.1 **73.0**, against **63.4** for Qwen3.6-27B, in the "Agentic terminal
  coding" row; **27B** parameters; "a native vision-language model that understands images
  and videos"; "Thinking mode is on by default and can be disabled per request; reasoning
  depth can be tuned with `reasoning_effort`", levels **xhigh (default), medium, low**;
  context **262,144** natively. Also SWE-bench Pro **61.7**, LiveCodeBench v6 **90.3**.
  <https://huggingface.co/Qwen/Qwen3.8-27B>
- 73.0 against 63.4 is **9.6 points**, computed from the two published figures.
- The llama.cpp team's own GGUF conversion: `Qwen3.8-27B-Q4_K_M.gguf` **19 GB**, with the
  separate vision projector `mmproj-Qwen3.8-27B-BF16.gguf` at **931 MB** in BF16 and
  **629 MB** at Q8_0. That 931 MB is the script's "roughly another gigabyte in its higher
  precision version". <https://huggingface.co/ggml-org/Qwen3.8-27B-GGUF>
- Qwen3.8-Flash-Next: "125B with 6B activated, plus 51B n-gram embedding and 4B MTP", and
  it does score higher on several evaluations than the 27B: SWE-bench Pro **62.5** against
  **61.7**, CoWorkBench **73.9** against **70.7**, DeepSWE 1.1 **58.7** against **42.2**,
  IFBench **81.3** against **79.5**. <https://huggingface.co/Qwen/Qwen3.8-Flash-Next>

## The local runner

- `llama.cpp` is the local runner the script refers to: "LLM inference in C/C++". Its own
  quick start fetches a quantised model by name into a local binary
  (`llama-cli -hf ggml-org/...-GGUF`, `llama-serve -hf ...`).
  <https://github.com/ggml-org/llama.cpp>
- Whether any given architecture loads is a property of the runner and its version rather
  than of the file, which is why the script says to check it before choosing a file on
  size alone. No source here settles it for a particular build.

## The worked example

The broken checkout is the script's own worked example and is nobody's product. Its
arithmetic holds both ways round: a $100 cart with a $10 coupon and 10% tax is $99 when the
coupon is applied before tax (90 x 1.10) and $100 when it is applied after (110 less 10).

## Not chased to a source

- **"document analysis"**, as one of three things Microsoft targets. The card names
  visual and mathematical reasoning, computer use with element localization, and OCR.
- **Every working memory range** (6 to 8, 22 to 26, 8 to 10, 12 to 16, 18 to 24, 48 to 56,
  22 to 26 GB). These are the script's planning estimates for one user at a modest context,
  which the script itself calls "planning ranges, not measured guarantees".
{% endraw %}

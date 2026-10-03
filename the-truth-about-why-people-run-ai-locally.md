---
layout: default
title: "The Real Reason Developers Keep Running AI Locally"
permalink: /the-truth-about-why-people-run-ai-locally/
date: 2026-10-03
---

# The Real Reason Developers Keep Running AI Locally

{% raw %}
Every figure this video states, and where it comes from. Pages were checked on 2 and 3 October 2026.

## LM Studio offline and on-device processing

- LM Studio docs, "Offline Operation".
  https://lmstudio.ai/docs/app/offline
  - "LM Studio can operate entirely offline, just make sure to get some model files first."
  - "In general, LM Studio does not require the internet in order to work. This includes core functions like chatting with models, chatting with documents, or running a local server, none of which require the internet."
  - Using downloaded LLMs: "Nothing you enter into LM Studio when chatting with LLMs leaves your device."
  - Chatting with documents (RAG): "All document processing is done locally, and nothing you upload into LM Studio leaves the application."
  - Running a local server: "Requests to LM Studio use OpenAI endpoints and return OpenAI-like response objects, but stay local."
- LM Studio docs, "LM Studio as a Local LLM API Server": local LLMs can be served "either on localhost or on the network", with OpenAI-compatible and Anthropic-compatible endpoints.
  https://lmstudio.ai/docs/developer/core/server

## Qwen 3.5 package sizes on Ollama

- Ollama library, qwen3.5, tags table (Size / Usage column):
  https://ollama.com/library/qwen3.5
  - qwen3.5:4b, 3.4GB
  - qwen3.5:9b (latest), 6.6GB
  - qwen3.5:27b, 17GB

## Ollama: context length and memory, prompt and generation timings, OpenAI compatibility

- Ollama docs, "Context length": "Setting a larger context length will increase the amount of memory required to run a model. Ensure you have enough VRAM available to increase the context length."
  https://docs.ollama.com/context-length
  - The same page shows the Ollama app settings, including "Airplane mode keeps data local, disabling cloud models and web search."
- Ollama API docs: responses report `prompt_eval_count`, `prompt_eval_duration` ("time spent in nanoseconds evaluating uncached prompt tokens"), `eval_count` and `eval_duration` ("time in nanoseconds spent generating the response") as separate fields.
  https://github.com/ollama/ollama/blob/main/docs/api.md
- Ollama docs, "OpenAI compatibility": "Connect OpenAI clients to Ollama. Ollama supports a subset of the OpenAI API."
  https://docs.ollama.com/api/openai-compatibility

## OpenAI API data controls

- OpenAI platform docs, "Data controls in the OpenAI platform".
  https://platform.openai.com/docs/guides/your-data
  - "As of March 1, 2023, data sent to the OpenAI API is not used to train or improve OpenAI models (unless you explicitly opt in to share data with us)."
  - "By default, abuse monitoring logs are generated for all API feature usage and retained for up to 30 days, unless longer retention is required by law, or is reasonably necessary to protect our services or any third party from harm."
  - "Eligible customers may have their customer content excluded from these abuse monitoring logs ... by getting approved for the Zero Data Retention or Modified Abuse Monitoring controls."

## Graphics cards

- NVIDIA GeForce RTX 4090: 24 GB GDDR6X.
  https://www.nvidia.com/en-us/geforce/graphics-cards/40-series/rtx-4090/
- NVIDIA GeForce RTX 5090: 32 GB GDDR7; Total Graphics Power 575 W.
  https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/

## The electricity arithmetic

- 575 W × 4 hours a day × 30 days = 69,000 Wh, which is 69 kWh.
- 69 kWh × $0.18 per kWh = $12.42 for the month.
- This is the card's rated total graphics power held for four hours a day, not a measurement of a whole computer. The $0.18 per kWh rate is the example rate the video uses.

## RTX 4090, about 150 tokens per second

- NVIDIA Technical Blog, "Accelerating LLMs with llama.cpp on NVIDIA RTX Systems", 2 October 2024.
  https://developer.nvidia.com/blog/accelerating-llms-with-llama-cpp-on-nvidia-rtx-systems/
  - "On the NVIDIA RTX 4090 GPU, users can expect ~150 tokens per second, with an input sequence length of 100 tokens and an output sequence length of 100 tokens."
  - The figure is NVIDIA internal measurement of a Llama 3 8B model on llama.cpp (Figure 1).

## Mac mini with M6

- Apple, Mac mini tech specs: M6 configurations start at 16GB unified memory, "Configurable to: 24GB or 32GB".
  https://www.apple.com/mac-mini/specs/
- Apple Newsroom, August 2026: "Apple's new Mac mini, featuring M6 and M5 Pro, delivers a massive leap in AI performance".
  https://www.apple.com/newsroom/2026/08/apple-unveils-a-more-powerful-mac-mini-featuring-the-all-new-m6-and-m5-pro/

## AMD Ryzen AI Max+ 395

- AMD blog, "AMD Ryzen AI MAX+ 395 Processor: Breakthrough AI Performance in Thin and Light", 17 March 2025: "available today with system memory options ranging from 32GB all the way up to 128GB of unified memory, out of which up to 96GB can be converted to VRAM through AMD Variable Graphics Memory."
  https://www.amd.com/en/blogs/2025/amd-ryzen-ai-max-395-processor-breakthrough-ai-.html
{% endraw %}

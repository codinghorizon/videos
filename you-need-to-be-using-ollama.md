---
layout: default
title: "Ollama's best trick isn't the chatbot you downloaded"
permalink: /you-need-to-be-using-ollama/
date: 2026-09-29
---

# Ollama's best trick isn't the chatbot you downloaded

{% raw %}
Every figure, name and setting the video states, with the primary source it comes from.
All pages were checked on 28 September 2026.

## Installing and running

- **Download options.** Ollama's download page offers macOS, Linux and Windows. On Linux the
  install command is `curl -fsSL https://ollama.com/install.sh | sh`.
  https://ollama.com/download
- **The Linux background service.** The Linux docs describe a systemd service whose
  `ExecStart` is `/usr/bin/ollama serve`, enabled with `sudo systemctl enable ollama`.
  https://docs.ollama.com/linux
- **Local or cloud at setup.** "Follow the setup prompts. Sign in to use cloud models, or
  choose a local model." Cloud requests need an API key; local requests do not.
  https://docs.ollama.com/quickstart · https://docs.ollama.com/api/introduction
- **qwen3.5:4b** is listed at 3.4GB, **qwen3.5:2b** at 2.7GB. Every qwen3.5 tag lists a 256K
  context window and Text and Image input.
  https://ollama.com/library/qwen3.5
- **The RTX 3060** is on Ollama's supported NVIDIA list (compute capability 8.6), and NVIDIA
  lists it with 12 GB or 8 GB of GDDR6.
  https://docs.ollama.com/gpu · https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3060-3060ti/
- **MacBook Air** with Apple M5 ships with 16GB unified memory, configurable higher.
  https://www.apple.com/macbook-air/specs/

## Choosing a model

- **gemma4:e2b** is listed at 7.2GB, 128K context, Text and Image input. The page's capability
  tags also include audio and thinking.
  https://ollama.com/library/gemma4
- **qwen3.8:27b** is listed at 18GB, 256K context.
  https://ollama.com/library/qwen3.8
- **LiveCodeBench v6**, from the Benchmark Results table on Ollama's gemma4 page: Gemma 4 E2B
  44.0%, Gemma 3 27B (no think) 29.1%. "Evaluation results marked in the table are for
  instruction-tuned models."
  https://ollama.com/library/gemma4

## The API

- **The local server** answers at `http://localhost:11434`. Chat is `POST /api/chat` with a
  `model` and a `messages` array; `stream` defaults to true; the reply text is
  `message.content`.
  https://docs.ollama.com/api/chat · https://docs.ollama.com/api/streaming
- **Structured outputs.** "Provide a JSON schema to the `format` field." The docs add that it
  is "ideal to also pass the JSON schema as a string in the prompt".
  https://docs.ollama.com/capabilities/structured-outputs
- **Official libraries** for Python and JavaScript.
  https://github.com/ollama/ollama-python · https://github.com/ollama/ollama-js
- **OpenAI compatibility** covers "a subset of the OpenAI API", including
  `/v1/chat/completions`, `/v1/completions`, `/v1/models`, `/v1/embeddings` and non-stateful
  `/v1/responses`.
  https://docs.ollama.com/api/openai-compatibility

## Performance and memory

- **`ollama ps`** shows NAME, ID, SIZE, PROCESSOR, CONTEXT and UNTIL. The documented example
  row is `gemma4:latest · 9.6 GB · 100% GPU · 131072`.
  https://docs.ollama.com/context-length
- **The PROCESSOR column.** "48%/52% CPU/GPU means the model was loaded partially onto both the
  GPU and into system memory."
  https://docs.ollama.com/faq
- **Hardware support.** NVIDIA GPUs from compute capability 5.0, AMD Radeon through ROCm, and
  Apple GPUs through Metal.
  https://docs.ollama.com/gpu
- **Default context length** depends on VRAM: 4k below 24 GiB, 32k from 24 to 48 GiB, 256k at
  48 GiB or more. It can be set with `OLLAMA_CONTEXT_LENGTH`, the app's context slider, or
  `num_ctx` per request.
  https://docs.ollama.com/context-length · https://docs.ollama.com/faq

## Interfaces, containers and exposure

- **The desktop app** for macOS and Windows includes a way to download and chat with models.
  https://ollama.com/blog/new-app
- **Open WebUI** connects to an Ollama server. For Ollama on the Docker host, its docs give
  `http://host.docker.internal:11434`.
  https://docs.openwebui.com/getting-started/quick-start/connect-a-provider/starting-with-ollama
- **The official image** is `ollama/ollama`. The basic command mounts a volume at
  `/root/.ollama` and maps port 11434. NVIDIA GPUs need the NVIDIA Container Toolkit and
  `--gpus=all`.
  https://docs.ollama.com/docker
- **Docker on a Mac.** Ollama's announcement of the Docker image says to run Ollama as a
  standalone app on the Mac, because Docker Desktop does not pass the GPU through.
  https://ollama.com/blog/ollama-is-now-available-as-an-official-docker-image
- **No login by default.** "The local API at http://localhost:11434 does not require
  authentication." Ollama binds 127.0.0.1 port 11434 unless `OLLAMA_HOST` changes it.
  https://docs.ollama.com/api/authentication · https://docs.ollama.com/faq
- **Cloud models** are processed by Ollama's cloud. Cloud features, including web search, can be
  turned off with `{"disable_ollama_cloud": true}` in `~/.ollama/server.json` or
  `OLLAMA_NO_CLOUD=1`.
  https://docs.ollama.com/cloud · https://docs.ollama.com/faq
- **Concurrency.** `OLLAMA_NUM_PARALLEL` sets parallel requests per model and defaults to 1;
  required memory scales with it.
  https://docs.ollama.com/faq

## The alternatives

- **LM Studio** serves local LLMs over a REST API and OpenAI compatible endpoints, has the `lms`
  CLI, and ships llmster, "a standalone daemon, no GUI required".
  https://lmstudio.ai/docs/developer/core/server · https://lmstudio.ai/docs/developer/core/headless
- **llama.cpp's HTTP server** lists OpenAI compatible routes, parallel decoding, continuous
  batching and schema constrained JSON.
  https://github.com/ggml-org/llama.cpp/blob/master/tools/server/README.md
- **Unsloth Studio** is "an open-source, no-code web UI for training, running and exporting open
  models in one unified local interface".
  https://unsloth.ai/docs/new/studio
- **vLLM** lists "Continuous batching of incoming requests, chunked prefill, prefix caching".
  https://github.com/vllm-project/vllm
- **`ollama launch`** configures external apps to use Ollama models. Its listed integrations
  are OpenCode, Claude Code, Codex, VS Code and Droid.
  https://docs.ollama.com/cli · https://docs.ollama.com/integrations/opencode

## Caveats

- The Mac and Docker statement comes from Ollama's 2023 announcement post; the current Docker
  docs page does not mention the Mac.
- `/bye` to leave a conversation comes from the CLI's own help text rather than a docs page.
- On a machine with 48 GiB of VRAM or more, the default allocated context does equal a 256K
  listing.
{% endraw %}

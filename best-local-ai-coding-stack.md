---
layout: default
title: "Your local coding AI can edit the wrong files confidently"
permalink: /best-local-ai-coding-stack/
date: 2026-09-29
---

# Your local coding AI can edit the wrong files confidently

{% raw %}
Every figure and product claim that appears on screen, with the page it comes from. Pages
were checked on 28 September 2026.

## Runner and launch integrations

- **Ollama can launch coding agents against local models.** "`ollama launch` is a new
  command which sets up and runs your favorite coding tools like Claude Code, OpenCode, and
  Codex with local or cloud models." Commands shown include `ollama launch claude` and
  `ollama launch opencode`. Supported integrations listed: Claude Code, OpenCode, Codex, Droid.
  https://ollama.com/blog/launch
- **Launch commands per model.** The Qwen3 Coder library page lists applications with
  commands such as `ollama launch claude --model qwen3-coder` and
  `ollama launch opencode --model qwen3-coder`.
  https://ollama.com/library/qwen3-coder
- **Tool calling in Ollama.** "Ollama supports tool calling (also known as function calling)
  which allows a model to invoke tools and incorporate their results into its replies."
  https://docs.ollama.com/capabilities/tool-calling
- **LM Studio.** Its documentation describes running models such as Llama, DeepSeek, Qwen and
  Phi locally, with a chat interface and model search and download ("Use a simple and
  flexible chat interface", "Search & download functionality").
  https://lmstudio.ai/docs/app

## Editor assistant

- **Continue runs in VS Code and JetBrains.** "Open source AI code assistant for VS Code and
  JetBrains." https://docs.continue.dev/
- **Model roles.** "Models in Continue can be configured to be used for various roles in the
  extension": `chat`, `autocomplete`, `edit`, `apply`, `embed` (and `rerank`).
  https://docs.continue.dev/customize/model-roles/00-intro
- **Autocomplete recommendation.** The autocomplete guide lists QwenCoder2.5 (1.5B) as a best
  open model for autocomplete and recommends `ollama run qwen2.5-coder:1.5b` for local use.
  https://docs.continue.dev/customize/deep-dives/autocomplete
- **Context length warning.** Under "Model requires more system memory to run": "Continue may
  use a higher default context length than other tools. Reduce `contextLength` in your config
  (e.g., to 2048), or try a smaller model."
  https://docs.continue.dev/guides/ollama-guide
- **Agent mode depends on tool support.** Under "Agent mode is not supported": add
  `capabilities: [tool_use]` to the model config, and "If still not working, the model may not
  actually support tools." The same guide shows an error reading "does not support tools".
  https://docs.continue.dev/guides/ollama-guide
- **`contextLength` in config.** The same guide's advanced settings example sets
  `contextLength: 8192`, which is the value used in the illustrative config on screen.

## Agent

- **OpenCode.** "The open source AI coding agent." Its built in tools include bash ("Execute
  shell commands"), edit ("Modify existing files"), grep and glob.
  https://opencode.ai/ and https://opencode.ai/docs/tools/

## Models

- **Qwen3 Coder 30B.** `qwen3-coder:30b` is listed at 19GB with a 256K context window, and the
  page states it "offers 30B total parameters with only 3.3B activated". It also lists long
  context support "optimized for repository-scale understanding" and agentic capabilities for
  software engineering tasks. https://ollama.com/library/qwen3-coder
- **Qwen3 Coder's design.** The Qwen team describes it as "our most agentic code model to
  date", with results on agentic coding and agentic tool use.
  https://qwenlm.github.io/blog/qwen3-coder/
- **Qwen 2.5 Coder sizes.** Tags 0.5b (398MB), 1.5b (986MB), 3b (1.9GB), 7b (4.7GB), 14b
  (9.0GB), 32b (20GB). https://ollama.com/library/qwen2.5-coder
- **GPT OSS 20B.** OpenAI describes gpt-oss-20b as "our medium-sized open-weight model for low
  latency, local, or specialized use-cases (21B parameters with 3.6B active parameters)", with
  configurable reasoning effort. https://developers.openai.com/api/docs/models/gpt-oss-20b
  Ollama lists `gpt-oss:20b` at 14GB with a 128K context window and describes the family as
  designed "for powerful reasoning, agentic tasks, and versatile developer use cases".
  https://ollama.com/library/gpt-oss
- **Devstral Small.** "Devstral excels at using tools to explore codebases, editing multiple
  files and power software engineering agents." Model size 24B parameters.
  https://huggingface.co/mistralai/Devstral-Small-2505
  Mistral's announcement and its SWE-Bench Verified chart:
  https://mistral.ai/news/devstral

## Hardware

- **A 16GB graphics card.** Current consumer cards with 16GB of graphics memory include the
  GeForce RTX 5070 Ti ("16 GB GDDR7").
  https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5070-family/
  The 19GB `qwen3-coder:30b` download is larger than 16GB before context and runtime memory
  are added. How much memory context, runtime overhead, the operating system and the editor
  take depends on the setup and is not stated by any of these pages.

## Not checked

- No model in this video was run against the invoice bug. The bug, the repository and every
  file name in it are an illustrative fixture, and the scorecard is shown unscored.
- The relative speed of a 1.5B and a 30B model for autocomplete is illustrated, not measured.
- The claim that some models advertising tool support still fail at it in practice rests on
  Continue's troubleshooting guidance, not on a test of any named model.
{% endraw %}

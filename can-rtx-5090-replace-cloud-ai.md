---
layout: default
title: "RTX 5090 Can Replace Claude. What Is The Catch?"
permalink: /can-rtx-5090-replace-cloud-ai/
date: 2026-10-03
---

# RTX 5090 Can Replace Claude. What Is The Catch?

{% raw %}
Checked 2 October 2026.

## The card

- **GeForce RTX 5090: 32 GB of GDDR7.** NVIDIA's product page: "equipped with 32 GB of super-fast GDDR7 memory". <https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/>
- **Sixteen 2 GB GDDR7 packages.** The card has a 512-bit memory interface (NVIDIA's specifications for the RTX 5090), and each GDDR7 package is 32 bits wide, so 32 GB is carried as sixteen 2 GB packages. Board photographs published before launch show them arranged around the GB202 die. <https://www.igorslab.de/en/?p=251836>
- **Launch price $1,999.** NVIDIA newsroom, CES 2025: "the GeForce RTX 5090 GPU with 3,352 AI TOPS and the GeForce RTX 5080 GPU with 1,801 AI TOPS will be available on Jan. 30 at $1,999 and $999, respectively." <https://nvidianews.nvidia.com/news/nvidia-blackwell-geforce-rtx-50-series-opens-new-world-of-ai-computer-graphics>

## Local models

- **Qwen3 Coder on Ollama.** "qwen3-coder:30b offers 30B total parameters with only 3.3B activated"; the `30b` tag is listed at 19 GB with a 256K context window; described as "Alibaba's performant long context models for agentic and coding tasks" and tagged `tools`. The same page lists launch commands for Claude Code and OpenCode. <https://ollama.com/library/qwen3-coder>
- **Devstral Small 2 and Devstral 2.** Mistral: "Devstral Small 2 scores 68.0% on SWE-bench Verified"; Devstral 2, a 123B parameter model, "reaches 72.2% on SWE-bench Verified"; Devstral Small 2 is a 24B model "capable of running locally on consumer hardware". Announced 9 December 2025. <https://mistral.ai/news/devstral-2-vibe-cli>
- **Devstral Small 2 on Ollama.** Listed at 15 GB: "24B model that excels at using tools to explore codebases, editing multiple files and power software engineering agents." <https://ollama.com/library/devstral-small-2>
- **gpt oss.** Ollama lists `gpt-oss:20b` at 14 GB with a 128K context: "OpenAI's open-weight models designed for powerful reasoning, agentic tasks, and versatile developer use cases." <https://ollama.com/library/gpt-oss> · <https://huggingface.co/openai/gpt-oss-20b>
- **Qwen3 Coder Next.** "Number of Parameters: 80B in total and 3B activated." <https://huggingface.co/Qwen/Qwen3-Coder-Next>
- **Qwen3.5.** The family runs from 0.8B to 397B parameters, published as image-text-to-text models. <https://huggingface.co/collections/Qwen/qwen35>

## Agents and integrations

- **Ollama and Claude Code.** "Ollama connects Claude Code to local and cloud models through its Anthropic-compatible API", launched with `ollama launch claude`. <https://docs.ollama.com/integrations/claude-code>
- **OpenCode.** "an open-source coding agent that runs in your terminal, reads your project, edits files, and runs commands." <https://docs.ollama.com/integrations/opencode> · <https://opencode.ai>
- **Where Claude Code's model runs.** "Claude Code runs locally. To interact with the LLM, Claude Code sends data over the network. This data includes all user prompts and model outputs." <https://code.claude.com/docs/en/data-usage>

## Hosted contenders

- **Claude Opus 4.8**, released 28 May 2026. "On our Super-Agent benchmark, Claude Opus 4.8 is the only model to complete every case end-to-end." "Claude Code with Opus 4.8 can now carry out codebase-scale migrations across hundreds of thousands of lines of code from kickoff to merge, with the existing test suite as its bar." "It builds on Opus 4.7 with improvements across benchmarks." Pricing for regular usage: "$5 per million input tokens and $25 per million output tokens." <https://www.anthropic.com/news/claude-opus-4-8>
- **OpenAI Codex.** Described by OpenAI as a coding agent for writing, reviewing and shipping code across local projects and cloud tasks; access follows the user's ChatGPT plan. <https://openai.com/codex/> · <https://github.com/openai/codex>

## Benchmarks

- **SWE-bench Verified.** "A human-validated subset of 500 SWE-bench instances for reliable evaluation of coding agents and language models." <https://www.swebench.com/verified.html>

## Not checked

- Ollama's own Devstral Small 2 page quotes 65.8% on SWE-bench Verified, against the 68.0% in Mistral's announcement. The video uses Mistral's figure and attributes it to Mistral.
- The narration attributes the local versus hosted processing statement to Claude Code's setup docs; the wording that says it is on the Claude Code data usage page.
- Codex plan allowances and usage limits were not checked against OpenAI's pricing page, which could not be retrieved.
- Memory used by runtimes, context, agent prompts and session state is not measured here and is shown only as a share the viewer has to size.
- No local model was run against the test job shown in the video; the settings fixture and its patches are illustrative.
{% endraw %}

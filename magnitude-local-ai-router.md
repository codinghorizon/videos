---
layout: default
title: "Your Local AI Is Probably Picking The Wrong Model"
permalink: /magnitude-local-ai-router/
date: 2026-09-08
---

# Your Local AI Is Probably Picking The Wrong Model

{% raw %}
Sources for every figure, date, name and claim the finished picture puts on screen.
Checked 7 September 2026.

## The repository

**`magnitudedev/magnitude`, 4,013 stars, created 12 June 2026, Apache 2.0.**
The GitHub REST API for the repository reports `stargazers_count: 4013`,
`created_at: 2026-06-12T09:06:26Z`, `pushed_at: 2026-09-07T20:32:48Z`,
`license: Apache License 2.0`, `open_issues_count: 20`.
Source: GitHub REST API, https://api.github.com/repos/magnitudedev/magnitude

**2,098 stars on 4 September 2026.**
A GitHub trending digest dated 4 September 2026 records the repository at 2,098 stars,
having gained 161 that day.
Source: https://startupcorners.com/digest/devtools-digest-2026-09-04

So the on screen growth figure is 2,098 on 4 September to 4,013 on 7 September: a rise of
1,915 in three days. That is the pair of dated, sourced numbers the shots use.

**First trended 8 August 2026.**
Trendshift records the repository's first appearance on its daily all languages list on
8 August 2026, and currently shows it at approximately 4k stars.
Source: https://trendshift.io/repositories/79752

## What Magnitude is

**"Open source inference server that runs the best local models for your hardware,
plugged into the agent you already use."**
The repository description, verbatim.
Source: https://github.com/magnitudedev/magnitude

**It profiles chip, memory and bandwidth.**
The documentation states it "profiles your chip, memory, and bandwidth".
Source: https://docs.magnitude.dev/introduction

**It recommends models with an estimated tokens per second figure.**
The documentation states it "recommends what fits: the best models for your machine, with
estimated tok/s".
Source: https://docs.magnitude.dev/introduction

**Models load on request and unload when idle or when memory fills.**
The README states "Models load just in time and unload when idle or memory gets tight".
Source: https://github.com/magnitudedev/magnitude

**Supported agents: Pi, OpenCode, Hermes, OpenClaw, Codex, Claude Code, Oh My Pi, Cline.**
The repository description and documentation both carry this list, verbatim and complete.
Source: https://github.com/magnitudedev/magnitude, https://docs.magnitude.dev/introduction

**Install is `npm i -g @magnitudedev/cli`.**
Source: https://github.com/magnitudedev/magnitude

**The site's own framing: "Run your agent on local models. Free, private, and offline."**
Source: https://magnitude.dev/

## How early the project is

**The CLI is on version 0.0.11.**
The npm registry metadata for `@magnitudedev/cli` reports `dist-tags.latest: 0.0.11`,
across 91 published versions including alpha and beta releases. A 0.0.x line is the
evidence for the script's "the CLI versions are still early".
Source: https://registry.npmjs.org/@magnitudedev/cli

## The tools it sits beside

**Ollama.** A local model runner whose pitch is a single command to pull and run a model.
Source: https://ollama.com/

**LM Studio.** A desktop application for discovering, downloading and running local models,
with a graphical model browser.
Source: https://lmstudio.ai/

**llama.cpp.** The C and C++ inference engine, from Georgi Gerganov, that most local model
runners are built on or beside, and the origin of the GGUF format and its quantisation
scheme.
Source: https://github.com/ggml-org/llama.cpp

## Quantisation naming

**`Q4_K_M` is a real llama.cpp quantisation type**, a four bit K quant at medium size.
The llama.cpp quantisation table lists the K quant family (`Q2_K` through `Q6_K`, in `_S`,
`_M` and `_L` sizes) alongside the legacy types, and `Q4_K_M` is the one most model
repository pages list first. A model page routinely publishes ten or more such files for a
single model, which is the "ten different quant files" the script describes.
Source: https://github.com/ggml-org/llama.cpp/blob/master/tools/quantize/README.md

## Model families named on screen

The families the script lists all publish open weights in sizes that run locally: Qwen
(Alibaba), DeepSeek, Kimi (Moonshot AI), GLM (Z.ai), Mistral, Llama (Meta) and Gemma
(Google). They are shown as marks and family names only; no benchmark score, parameter
count or release date for any of them is stated on screen, so none is asserted here.

## What is on screen and what is not

Numbers the picture states, all sourced above: 4,013 stars; 2,098 stars on 4 September;
the difference between the two, 1,915 new stars in three days; 12 June 2026 and the 87
days from it to 7 September; version 0.0.11; the eight agent names; chip, memory and
bandwidth; the `Q4_K_M` filename and the llama.cpp quant type names.

The script's line about "more than two thousand new stars in a week" could not be chased to
a tracker publishing that specific weekly figure. The measured rise from the two dated
sources above is 1,915 stars in three days, which is consistent with it but is not the same
statement. The shots therefore put the two dated star counts on screen and never render a
weekly figure.

The VRAM tiers the script discusses, eight gigabytes and sixteen gigabytes, are used as
categories of machine rather than as measurements, and the picture never states a model
size in gigabytes for a named model, because no primary source was chased for one.
{% endraw %}

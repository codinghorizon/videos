---
layout: default
title: "Nvidia Open Sourced The Thing That Picks Your Model"
permalink: /nvidia-nemotron-35-lightning-nemo-switchyard/
date: 2026-08-11
---

# Nvidia Open Sourced The Thing That Picks Your Model

Every figure, name, licence and benchmark the finished picture puts on screen, chased to a
primary source. Checked 11 August 2026.

## The release

**Nvidia released two things together on 11 August 2026: Nemotron 3.5 Lightning, a compact
open model, and NeMo Switchyard, an open source routing library.**

- NVIDIA, *NVIDIA Nemotron 3.5 Lightning and NeMo Switchyard Deliver Faster, Smarter, More
  Efficient Agentic AI*, 11 August 2026.
  https://blogs.nvidia.com/blog/nemotron-lightning-switchyard-rtx-dgx/
- Model card, published 11 August 2026:
  https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4

## Nemotron 3.5 Lightning

**30 billion total parameters, 3 billion active. A mixture of experts model.**

- NVIDIA Technical Blog, *NVIDIA Nemotron 3.5 Lightning Delivers Fast, Accurate Specialized
  Task Execution for Long-Running Agents*: "open Mixture-of-Experts (MoE) model", 30B total
  with 3B active.
  https://developer.nvidia.com/blog/nvidia-nemotron-3-5-lightning-delivers-fast-accurate-specialized-task-execution-for-long-running-agents/
- The model card states the same 30B total / 3B active split and describes the architecture
  as a Mamba-2, MoE and attention hybrid, with a context length up to 1M tokens.

**The weights are open and permissively licensed.** The model card gives the licence as the
OpenMDW License Agreement, version 1.1. NVIDIA's blog states companies can download, use and
modify the model without seeking permission. NVFP4 and BF16 checkpoints are published, and
the model is listed for Blackwell, Hopper and Ampere GPUs.

- https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4

**Published benchmark scores for the NVFP4 checkpoint**, as used on screen:

| Benchmark | Score |
|---|---|
| MMLU Pro | 81.62 |
| GPQA Diamond | 75.57 |
| SWE-bench Verified | 52.80 |

Source: the model card linked above. These are NVIDIA's own published evaluations.

**Speed.** NVIDIA claims up to 4x faster output than similar sized models and 30% faster
agentic task completion than other models in its class. This is the vendor's own figure and
is described as such wherever it appears.

- https://blogs.nvidia.com/blog/nemotron-lightning-switchyard-rtx-dgx/

## NeMo Switchyard

**An open source model routing library, written in Rust, under Apache 2.0.**

- Repository: https://github.com/NVIDIA-NeMo/Switchyard
  The README describes it as a Rust proxy and library for LLM traffic that routes requests
  across providers and translates between OpenAI Chat, Anthropic Messages and OpenAI
  Responses formats. Licence: Apache 2.0.

**What it routes on.** NVIDIA's technical blog names the routing algorithms it ships:
an LLM Classifier router, a Stage router that reads tool activity to judge the capability a
step needs, an Escalation router that starts cheap and escalates on sustained difficulty,
and a tunable Prefill router. Agent developers can tune the router against quality, latency
and cost priorities.

- https://developer.nvidia.com/blog/route-ai-agent-workloads-across-models-with-nvidia-nemo-switchyard/

**Cost against a frontier only baseline.** In an evaluation NVIDIA publishes with LangChain
over 145 multi turn agentic tasks, routing between Nemotron 3.5 Lightning and a frontier
model gave a 74% cost reduction against a frontier only baseline, sending only 7% of calls
to the frontier model, at roughly a 6 point accuracy tradeoff.

- https://developer.nvidia.com/blog/route-ai-agent-workloads-across-models-with-nvidia-nemo-switchyard/

Other published partner results from the same announcement, for context: Ramp reports 58%
lower cost and 33% lower runtime, Cognition reports mean cost down 28%, and Classmethod
reports 27% lower cost at maintained quality.

- https://blogs.nvidia.com/blog/nemotron-lightning-switchyard-rtx-dgx/

**Where it runs.** NVIDIA names Kong, OpenRouter, LiteLLM and LangChain as already building
Switchyard into their offerings.

- https://blogs.nvidia.com/blog/nemotron-lightning-switchyard-rtx-dgx/

## Where these models are meant to run

The announcement covers RTX PCs, DGX Spark, DGX Station, Jetson, RTX PRO workstations, data
centres, cloud and edge devices, which is the range the video draws as edge board,
workstation, server and data centre.

- https://blogs.nvidia.com/blog/nemotron-lightning-switchyard-rtx-dgx/

## Not checked

These are stated in the video and are not figures that can be chased to a primary source.
They are arguments rather than measurements, and nothing on screen prints a number for them.

- The claim that most AI usage is mundane rather than frontier work. No published measurement
  of that split was found, so the distribution shown on screen carries no percentages.
- The claim that routing on privacy, data locality or sensitivity is part of what Switchyard
  does. NVIDIA's own documentation describes routing on quality, latency, cost and capability,
  and does not describe a privacy or data residency router. The privacy chapter is an argument
  about what a routing layer makes possible, and the picture does not attribute it to
  Switchyard's shipped feature set.
- The comparison of a local model against Claude, GPT-5 and Gemini. No head to head evaluation
  is cited, so the on screen comparison carries no numbers or scores.
- Any figure for what an organisation spends on AI per seat or per month. Nothing on screen
  prints one.

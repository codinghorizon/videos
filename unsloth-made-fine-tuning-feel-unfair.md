---
layout: default
title: "Unsloth Makes Fine Tuning Feel Completely Unfair"
permalink: /unsloth-made-fine-tuning-feel-unfair/
date: 2026-08-22
---

# Unsloth Makes Fine Tuning Feel Completely Unfair

{% raw %}
Every figure, name and claim the finished picture puts on screen, chased to the place
that publishes it. Checked 22 August 2026.

## The headline claim

**Up to two times faster training, up to seventy percent less VRAM.**
Unsloth's own headline, carried on the project page and the repository: "Train LLMs,
diffusion, TTS, and embedding models 2x faster with 70% less VRAM."

- https://github.com/unslothai/unsloth
- https://unsloth.ai/

## Kernels and packing

**Around three times faster, and roughly thirty percent less VRAM.**
Unsloth's kernel and packing work is published as "~3x faster training & 30% less VRAM
vs optimized FA3 setups", from new RoPE and MLP Triton kernels plus automatic sequence
packing, stated with no accuracy loss. The docs give the range as up to 5x, typically 3x,
with VRAM reductions of 30% to 90% depending on the setup.

**Qwen3 4B trains around three times faster on 3.9 GB of VRAM** under the same work.

The mechanism is the one the video draws: batching examples of different lengths pads the
short ones out to the length of the longest, so the GPU does real work on empty positions.
Packing concatenates the examples instead, and the RoPE kernel resets position ids at each
example boundary so a packed batch stays mathematically equivalent to separate passes.

- https://unsloth.ai/docs/blog/3x-faster-training-packing
- https://x.com/UnslothAI/status/1998765021170696664

## Mixture of experts

**Up to twelve times faster, more than thirty five percent less VRAM, around six times
longer context.** Unsloth's MoE Triton kernels, built with `torch._grouped_mm` in
collaboration with Hugging Face, are published as "~12x faster Mixture of Experts (MoE)
LLM training" with ">35% less VRAM" and no accuracy loss. The twelve times figure is
against Transformers v4; against Transformers v5 the same work is published as about two
times faster.

Published per model figures:

| Case | Unsloth | Baseline | Source |
|---|---|---|---|
| gpt-oss 20B, 8192 context, B200 | 712.33 ms, 47.43 GB | 5226.86 ms, 73.80 GB (Transformers v5) | docs |
| gpt-oss 20B, 16384 context, B200 | 1775.80 ms, 55.13 GB | out of memory | docs |
| Qwen3 30B A3B | 17.5 GB, 0.8 hours | 48 GB, 9.4 hours (PyTorch) | announcement |
| gpt-oss 20B | fine tunes in 12.8 GB | | announcement |
| GLM 4.7 Flash | 2.6x throughput, >15% less VRAM | | docs |

Kernel support is stated for data centre cards (B200, H100), consumer cards and older
cards such as the RTX 3090, and covers full fine tuning, LoRA and QLoRA.

- https://unsloth.ai/docs/basics/faster-moe
- https://github.com/unslothai/unsloth/discussions/4020

## Model coverage

**Hundreds of models, across the families the script names.** The documentation states
300+ models supported, spanning Llama, Qwen, Gemma, Mistral, DeepSeek, Phi and gpt oss,
along with vision, reasoning, mixture of experts, coding, audio and embedding models.
Unsloth Studio states 500+ models for running and training. Both are current; the video
puts the conservative figure on screen.

Named model support in the repository at the time of checking includes Qwen3.8, Kimi K3,
MiniMax H3, Gemma 4 and DeepSeek V4.

- https://github.com/unslothai/unsloth
- https://unsloth.ai/docs/get-started/unsloth-notebooks

## Training paths

**LoRA, QLoRA, full fine tuning, pretraining, reinforcement learning including GRPO and
DPO, four bit, sixteen bit and FP8.** All are listed by the project as supported paths.

LoRA as the video draws it: the base weight matrix is frozen and two low rank matrices
are trained beside it. QLoRA is the same arrangement with the frozen base quantized to
four bit.

- https://github.com/unslothai/unsloth

## Export and deployment

**GGUF, Ollama, vLLM, Hugging Face, local APIs, plus NVFP4 and FP8 export.** Published as
"Export or Deploy models with including GGUF, NVFP4, FP8 and more formats", with
documented paths to Ollama, vLLM, llama.cpp and the Hugging Face Hub.

- https://github.com/unslothai/unsloth

## Unsloth Studio

**A local interface for running and training models, beyond the library.** Unsloth Studio
is an open source local UI covering inference, fine tuning, diffusion, audio, agents and
deployment, released in beta on 17 March 2026, with a desktop application for macOS,
Windows and Linux following on 11 August 2026. It states 500+ models, the same 2x faster
and 70% less VRAM training claim, and runs offline.

- https://unsloth.ai/docs/new/studio
- https://github.com/unslothai/unsloth

## Not checked

- The narration's opening images of failed runs, exploding notebooks and a run dying at
  ninety seven percent are rhetorical rather than measured, and nothing on screen presents
  them as a statistic.
- "Unsloth is the default now" and "everything else has to explain why it is not using
  Unsloth" are stated in the narration as opinion, and no market share or adoption figure
  exists to support or contradict them. Nothing on screen quantifies either.
- The comparison figures above are the ones Unsloth publishes for its own work. They are
  reproducible from the linked benchmarks but were not independently re run.
{% endraw %}

---
layout: default
title: "Your Local Coding Model Is Not Useless, It Is Blind"
permalink: /run-qwen3-coder-locally-with-256k-context/
date: 2026-08-14
---

# Your Local Coding Model Is Not Useless, It Is Blind

Every figure this video puts on screen, chased to a primary source.

Checked 13 August 2026.

---

## Qwen3 Coder 30B: the local version

**30 billion total parameters, about 3.3 billion active per token.**
The model card gives 30.5B total with 3.3B activated, as a mixture of experts with 128
experts of which 8 are active per forward pass.
Source: Qwen — Qwen3-Coder-30B-A3B-Instruct model card
<https://huggingface.co/Qwen/Qwen3-Coder-30B-A3B-Instruct>

**A 256K context window.**
The same model card gives 262,144 tokens of native context, which is 256K, extensible
further with extrapolation methods. Ollama's library page lists 256K context against both
published tags.
Source: Qwen — Qwen3-Coder-30B-A3B-Instruct model card
<https://huggingface.co/Qwen/Qwen3-Coder-30B-A3B-Instruct>
Source: Ollama — qwen3-coder <https://ollama.com/library/qwen3-coder>

**Around 19 gigabytes for the common local quantized build.**
Ollama lists `qwen3-coder:30b` at 19GB.
Source: Ollama — qwen3-coder <https://ollama.com/library/qwen3-coder>

---

## The 480B flagship

**480 billion total parameters with 35 billion active.**
Qwen's own announcement describes a 480B-parameter mixture of experts model with 35B
active parameters, supporting 256K tokens natively and 1M with extrapolation.
Source: Qwen — Qwen3-Coder announcement <https://qwenlm.github.io/blog/qwen3-coder/>

**Hundreds of gigabytes, and at least 250GB of memory to run locally.**
Ollama lists `qwen3-coder:480b` at 290GB and states that running it locally requires a
minimum of 250GB of memory or unified memory.
Source: Ollama — qwen3-coder <https://ollama.com/library/qwen3-coder>

---

## Context is paid for in memory

**A larger context window needs more memory.**
Ollama's context length documentation states directly that setting a larger context
length will increase the amount of memory required to run a model.
Source: Ollama — Context length <https://docs.ollama.com/context-length>

**The default context Ollama picks depends on available video memory.**
The documented tiers are 4K context under 24 GiB of VRAM, 32K from 24 to 48 GiB, and 256K
at 48 GiB and above. These three figures are the ones the video puts on screen as a
stepped chart.
Source: Ollama — Context length <https://docs.ollama.com/context-length>

**At least 64,000 tokens for coding tools and agents.**
The same documentation recommends setting context to at least 64000 tokens for tasks like
web search, agents and coding tools, which is what the video shows behind the claim that
32K or 64K already changes how a coding model behaves.
Source: Ollama — Context length <https://docs.ollama.com/context-length>

---

### Not checked

These are the video's judgements rather than published figures, and nothing on screen
states them as measurements:

- That 128K is the point where agents stop feeling cramped, and that 256K is the
  expensive mode to reach for only when the repository and the task justify it. Both are
  positions the video argues from the memory behaviour above, not published thresholds.
- What the context cache specifically costs in gigabytes at any given window size for this
  model. It is drawn throughout as an unquantified demand for exactly this reason; the
  only memory figures rendered as numbers are Ollama's 19GB and 290GB, its 250GB minimum,
  its published VRAM tiers, and the machine sizes the video itself names.
- The comparison of local against the best cloud coding models on strength, ease and
  speed. The video shows this as a shape with no numbers on it, because no benchmark was
  run for it here.
- The guidance for 32GB, 16GB and 8GB machines. The arithmetic underneath it is sourced,
  since 19GB of weights against an 8GB machine is a ratio anyone can compute, but the
  recommendation itself is a judgement.

---
layout: default
title: "Run Real AI Agents In 2.5GB Of RAM With LFM2.5"
permalink: /run-ai-agents-in-2-5gb-ram-lfm2-5/
date: 2026-08-14
---

# Run Real AI Agents In 2.5GB Of RAM With LFM2.5

Every figure, name and claim the finished picture puts on screen, chased to a primary
source. Worked from the `TEXT:` lines in BEATS.md, so nothing on screen is missing from
this list.

Liquid AI publishes its own model cards and blog posts, so those are the primary sources
throughout. Where a figure exists only in a third party write up it is marked as such.

---

## The headline: 2.5 GB

**"in under 2.5 GB of memory"** — the memory footprint Liquid AI states for LFM2.5-2.6B,
the model that carries the video's headline number. Also stated: 128K context, and CPU
throughput of about 220 tok/s on an Apple M5 Max and about 113 tok/s on an AMD Ryzen AI
Max+ 395.

Source: Liquid AI, "Deploy local agents everywhere with LFM2.5-2.6B"
https://huggingface.co/blog/LiquidAI/lfm2-5-2-6b

Used in beats 008, 009, 033, 034, 035, 036, 071, 073.

---

## The architecture

**"hybrid LFM architecture"** — LFM2 is a hybrid of gated short convolution blocks, which
make up the majority of layers and do fast local mixing with good CPU cache behaviour, and
a minority of grouped query attention (GQA) blocks for long range context. Liquid states
the design targets three axes: quality, latency (time to first token and decode throughput
at batch 1) and peak memory measured at 4K and 32K context.

Concrete layer counts from the model cards: LFM2.5-230M is 14 layers, 8 double gated
convolution blocks plus 6 GQA blocks. LFM2.5-8B-A1B is 24 layers, 18 double gated
convolution blocks plus 6 GQA blocks.

Sources: LFM2 Technical Report, arXiv 2511.23404 https://arxiv.org/html/2511.23404v1
LFM2.5-230M model card https://huggingface.co/LiquidAI/LFM2.5-230M
LFM2.5-8B-A1B model card https://huggingface.co/LiquidAI/LFM2.5-8B-A1B

Used in beat 024.

---

## The shape of the family

The LFM2.5 family as Liquid AI lists it, which is what beat 026's family map plots:

- Text: LFM2.5-230M, LFM2.5-350M, LFM2.5-1.2B (Base, Instruct, Thinking, JP), LFM2.5-2.6B
- Mixture of experts: LFM2.5-8B-A1B
- Vision language: LFM2.5-VL-450M, LFM2.5-VL-1.6B, LFM2.5-VL-3B
- Audio: LFM2.5-Audio-1.5B
- Encoders: LFM2.5-Encoder-230M, LFM2.5-Encoder-350M
- Embedding and retrieval: LFM2.5-Embedding-350M, LFM2.5-ColBERT-350M

Source: Liquid AI model list https://www.liquid.ai/models

Used in beats 026, 027, 028, 031.

The script's list — "small text models, retrieval models, encoders, audio language models,
and larger mixture of experts models" — matches this list category for category.

---

## LFM2.5-230M

- **230M parameters**, 14 layers, vocabulary 65,536, 10 languages
- **32,768 token context**
- **19T token training budget**
- **213 tok/s decode on a Samsung Galaxy S25 Ultra** (Snapdragon Gen4), 1,158 tok/s prefill
- **42 tok/s decode on a Raspberry Pi 5**, 523 tok/s prefill
- **375 MB on the Galaxy S25 Ultra** and **293 MB on the Raspberry Pi 5**, 4-bit quantised
- Benchmarks: IFEval 71.71, IFBench 38.40, Multi-IF 37.70, BFCLv4 21.03, GPQA Diamond
  25.41, MMLU-Pro 20.25
- Liquid describes it as built for "large scale data extraction pipelines or lightweight
  on-device agentic workloads", and explicitly not recommended for reasoning heavy work
  such as advanced maths, code generation or creative writing

Sources: Liquid AI, "LFM2.5-230M: Built to Run Anywhere"
https://www.liquid.ai/blog/lfm2-5-230m
Model card https://huggingface.co/LiquidAI/LFM2.5-230M

Used in beat 029.

---

## LFM2.5-1.2B

Measured on device memory footprints Liquid AI publishes for LFM2.5-1.2B-Instruct:

- **719 MB** on a Samsung Galaxy S25 Ultra, llama.cpp Q4_0
- **856 MB** on an AMD Ryzen AI 9 HX 370, llama.cpp Q4_0
- **0.9 GB** on Qualcomm Snapdragon X Elite, Snapdragon Gen4 and Dragonwing IQ9, via NexaML

The reasoning variant, LFM2.5-1.2B-Thinking, is stated to fit **within 900 MB on a phone**,
with 32K context and roughly 46 to 52 tok/s sustained at 16K to 32K context. Its tool use
score is BFCLv3 56.97, up from 49 on the instruct variant.

Sources: Liquid AI, "Introducing LFM2.5: The Next Generation of On-Device AI"
https://www.liquid.ai/blog/introducing-lfm2-5-the-next-generation-of-on-device-ai
Liquid AI, "LFM2.5-1.2B-Thinking: On-Device Reasoning Under 1GB"
https://www.liquid.ai/blog/lfm2-5-1-2b-thinking-on-device-reasoning-under-1gb

Used in beats 030 and 037. Beat 037 puts the 719 MB and 856 MB figures on screen beside
the Galaxy S25 Ultra and Ryzen AI 9 HX 370 they were measured on, alongside the 293 MB
Raspberry Pi 5 figure for the 230M model above.

Beat 038 puts the measured decode throughput on screen, 213 tok/s on a Galaxy S25 Ultra
and 42 tok/s on a Raspberry Pi 5, both from the LFM2.5-230M post cited above.

---

## LFM2.5-8B-A1B

- **8.3B total parameters, 1.5B active per token**
- 24 layers (18 double gated convolution + 6 GQA)
- **128,000 token context**, 38T tokens of pre-training
- Built for "agentic workflows, tool use, structured outputs, multilingual assistants and
  on-device personal-assistant applications", and stated as not the best fit for heavy
  programming or knowledge intensive question answering without retrieval

A mixture of experts model keeps every expert resident in memory even though only a
fraction activates per token, which is why the resident and active figures differ so much
and why beat 030 draws them as two different quantities.

Source: model card https://huggingface.co/LiquidAI/LFM2.5-8B-A1B

Used in beat 030.

### A discrepancy, stated plainly

The narration describes this model as "an 8B mixture of experts model with about 1B active
parameters". The total is right to one significant figure, and the model's published name,
LFM2.5-8B-A1B, is where the "1B active" reading comes from. Liquid AI's own model card
gives the precise active count as **1.5B**, not about 1B. The picture prints the model
card's figures rather than the approximation. This is listed under Not checked in
MANIFEST.md.

---

## Tool use and agent benchmarks

For LFM2.5-2.6B, the model carrying the 2.5 GB figure:

- ToolSandbox 77.83
- BFCLv4 56.88
- Claw-Eval average (EN) 62.85
- BrowseComp+ (OpenClaw) 26.89

Source: Liquid AI, "Deploy local agents everywhere with LFM2.5-2.6B"
https://huggingface.co/blog/LiquidAI/lfm2-5-2-6b

Supports the video's claim that routing, tool selection and extraction are the work these
models are actually measured on. Used as background for beats 035 to 039.

---

## Claims the video makes that are argument rather than figure

These are not sourced because they are not measurements. They are stated here so the
distinction is on the record.

- That an agent is a loop rather than a single prompt, and that most of its steps are
  routine. This is a description of how agent frameworks work, and matches Liquid's own
  framing of on-device agentic AI as instruction following, tool calling and extraction.
- That model orchestration, with small models close to the user and larger models called
  only when a task justifies it, is where agent systems are heading. This is the video's
  argument, not a published finding.
- The cost, latency and privacy consequences of running locally rather than in the cloud.
  Directionally uncontroversial and not quantified on screen anywhere in this video.

---

## Not sourced, and therefore not on screen

- No dollar cost per call, per token or per month appears in the picture. The narration
  talks about expense in general terms and the shots draw cost as a relative meter with no
  units rather than a figure, because no per call price for a comparable cloud model was
  chased to a primary source for this video.
- The "10,000 short inputs" figure in beat 060 is the script's own illustration, not a
  measurement, and the shot draws it as a stated scenario with relative cost and latency
  bars rather than as sourced quantities. The quality bars beside those lanes read
  "higher" and "good enough" rather than a score, because no head to head benchmark
  between a named cloud model and a named local model was chased to a source here.
- Beat 053 draws how far a small model falls short on frontier reasoning, ambiguous
  instructions and unsupervised high stakes actions as bar heights against a threshold.
  Those heights are a relative shape and are labelled "well short", "short" and "not
  reliable enough" rather than carrying numbers, because no benchmark measuring those
  three specific capabilities was chased to a primary source for this video.
- Beat 056 shows a leaderboard with the small model low on it. The rows carry rank and a
  relative bar only. No scores appear, because the leaderboard is an illustration of how
  ranking works rather than a reproduction of any published table.

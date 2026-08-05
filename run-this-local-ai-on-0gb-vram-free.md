---
layout: default
title: "Run A Local AI Model On Zero Video Memory For Free"
permalink: /run-this-local-ai-on-0gb-vram-free/
date: 2026-08-05
---

# Run A Local AI Model On Zero Video Memory For Free

Every figure this video puts on screen, with where it comes from. Memory bandwidth
numbers are the published rate for the part named. Model sizes are the download size the
Ollama library lists against that exact tag, which is the file the machine has to read.

The tokens per second figures are not benchmark results. They are the ceiling that falls
out of dividing a published memory bandwidth by a published model size, and the video
says so on screen. Real throughput on any given machine lands below that ceiling.

## Ollama itself

**The install line is `curl -fsSL https://ollama.com/install.sh | sh`.**
Ollama's own Linux download page.
https://ollama.com/download/linux

**It binds to port 11434 by default.**
"Ollama binds 127.0.0.1 port 11434 by default."
https://docs.ollama.com/faq

**It falls back to the processor when it cannot find a supported graphics card.**
Ollama's GPU documentation describes the case where discovery fails and the runner
continues on the CPU instead.
https://docs.ollama.com/gpu

**The default context window is 4096 tokens, and `num_ctx` changes it.**
"By default, Ollama uses a context window size of 4096 tokens." The FAQ gives three ways
to change it: the `OLLAMA_CONTEXT_LENGTH` environment variable, `/set parameter num_ctx`
in the session, and `num_ctx` on an API request.
https://docs.ollama.com/faq

**A negative `keep_alive` keeps a model resident.**
"any negative number which will keep the model loaded in memory (e.g. -1 or '-1m')", and
`OLLAMA_KEEP_ALIVE` applies the same setting globally.
https://docs.ollama.com/faq

## Memory bandwidth

**DDR5 5600 in dual channel is 89.6 GB/s.**
DDR5 5600 is the first JEDEC standardised, non overclocked DDR5 speed, designated
PC5 44800, where 44800 is 5600 MT/s multiplied by 8 bytes. Two channels doubles it to
89.6 GB/s.
https://www.bittware.com/resources/ddr4-and-ddr5-performance-comparison/

**DDR4 3200 in dual channel is 51.2 GB/s.**
Same arithmetic on the earlier standard: 3200 MT/s by 8 bytes by two channels.
https://www.bittware.com/resources/ddr4-and-ddr5-performance-comparison/

**A GeForce RTX 5090 has 1792 GB/s.**
32 GB of GDDR7 on a 512 bit interface.
https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/

**That is roughly twenty times the laptop figure.**
1792 divided by 89.6 is exactly 20.

**Apple's M4 Pro is 273 GB/s and the M4 Max is 546 GB/s.**
Apple's own announcement of both parts. The point on screen is that these machines put
the processor and the graphics engine on one pool of memory rather than copying between
two.
https://www.apple.com/newsroom/2024/10/apple-introduces-m4-pro-and-m4-max/

## What a card costs

**The GeForce RTX 5060 Ti started at 379 US dollars for 8 GB and 429 for 16 GB.**
NVIDIA's own launch announcement for the 5060 desktop family.
https://www.nvidia.com/en-us/geforce/news/rtx-5060-desktop-family-laptop-5060-coming-soon/

**The GeForce RTX 5090 launched at 1,999 US dollars for 32 GB.**
NVIDIA's launch price at the January 2025 release. Street prices have run well above it
since, which makes the launch figure the conservative one for the point being made.
https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/

## Model sizes, as the library lists them

Each of these is the download size against that tag, which is the quantised file the
machine reads.

| Tag | Size |
| --- | --- |
| `qwen3:1.7b` | 1.4 GB |
| `llama3.2:3b` | 2.0 GB |
| `qwen3:4b` | 2.5 GB |
| `gemma3:4b` | 3.3 GB |
| `llama3.1:8b` | 4.9 GB |
| `qwen3:8b` | 5.2 GB |
| `gemma3:12b` | 8.1 GB |
| `qwen3:14b` | 9.3 GB |
| `gemma3:27b` | 17 GB |
| `qwen3:30b` | 19 GB |
| `llama3.3:70b` | 43 GB |

https://ollama.com/library/qwen3
https://ollama.com/library/llama3.2
https://ollama.com/library/llama3.1
https://ollama.com/library/llama3.3
https://ollama.com/library/gemma3

**A 4 billion parameter model is about 8 GB at 16 bit and about 2.5 GB once quantised
to roughly 4 bits per weight.** Two bytes per parameter gives 8 GB for four billion
parameters, and `qwen3:4b` ships at 2.5 GB.
https://ollama.com/library/qwen3

## The mixture model

**Qwen3 30B A3B holds 30.5 billion parameters and activates 3.3 billion per token.**
The model card states both: 48 layers, 128 experts, 8 of them activated. That ratio is
why the file is 19 GB on disk and only a fraction of it is read for each token, and it is
the reason a thirty billion parameter model can outrun a dense eight billion one on a
machine with no card in it.
https://huggingface.co/Qwen/Qwen3-30B-A3B

## The arithmetic on screen

Generating a token requires reading every weight that participates in it, so the rate a
machine can sustain is bounded by bandwidth divided by the bytes read per token. Against
89.6 GB/s that gives:

| Tag | Bytes read per token | Ceiling |
| --- | --- | --- |
| `qwen3:1.7b` | 1.4 GB | 64 tokens per second |
| `qwen3:30b` | 2.1 GB, the activated share of 19 GB | 44 tokens per second |
| `qwen3:4b` | 2.5 GB | 36 tokens per second |
| `llama3.1:8b` | 4.9 GB | 18 tokens per second |

These are ceilings, not measurements. Attention over the conversation so far, the
operating system, and everything else competing for the same memory all take a share, so
a real machine lands under them.

## Reading speed, for the comparison

**A comfortable reading pace is about six tokens per second.**
A meta-analysis of 190 studies covering 18,573 participants puts average adult silent
reading at 238 words per minute for non-fiction and 260 for fiction. That is roughly four
words per second. English runs about 1.3 tokens to the word, which puts a comfortable
reading pace between five and six tokens per second, and the marker is drawn at six as the
generous end of that range.
Brysbaert, M. (2019). How many words do we read per minute? A review and meta-analysis of
reading rate. Journal of Memory and Language.
https://www.sciencedirect.com/science/article/abs/pii/S0749596X19300786

## Caveats

Reading the prompt is a different job from generating the answer, and it is bound by
arithmetic rather than by memory bandwidth, so the wait before the first token grows with
prompt length in a way the figures above do not describe.

Conversation state is held in memory alongside the model and grows with the conversation,
so the free space shown against a fresh load is the best case rather than the steady one.

Quantisation to roughly 4 bits is where most small models ship and is treated here as the
normal case. Quality at lower precisions than that falls away sharply, and how far is
model specific.

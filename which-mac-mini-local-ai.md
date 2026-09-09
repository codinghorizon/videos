---
layout: default
title: "The Mac Mini Local AI Trap Costs More Than You Think"
permalink: /which-mac-mini-local-ai/
date: 2026-09-09
---

# The Mac Mini Local AI Trap Costs More Than You Think

{% raw %}
Every figure, price, parameter count and bandwidth number the finished video puts on
screen, chased to a primary source. Checked 8 September 2026.

## The new Mac mini, announced 25 August 2026

Apple announced a new Mac mini with the M6 and M5 Pro chips on 25 August 2026.

- **M6 Mac mini starts at $899 in the US**, with 16 GB of unified memory configurable to
  32 GB.
  Source: Apple Newsroom, "Apple unveils a more powerful Mac mini featuring the all new M6
  and M5 Pro", 25 August 2026.
  https://www.apple.com/newsroom/2026/08/apple-unveils-a-more-powerful-mac-mini-featuring-the-all-new-m6-and-m5-pro/
- **M6: 12 core CPU, 12 core GPU, dual 16 core Neural Engines, up to 170 GB/s of memory
  bandwidth.** The CPU is two super cores, four performance cores and six efficiency cores.
  Every GPU core carries a Neural Accelerator.
  Source: Apple Newsroom, as above.
- **Apple's LM Studio claim: up to 4.8 times faster LLM prompt processing than the M4 Mac
  mini** (and up to 13.5 times faster than the M1 Mac mini). Apple's own testing, conducted
  July 2026.
  Source: Apple Newsroom, as above.
- **M5 Pro Mac mini starts at $1,699**, supports up to 64 GB of unified memory, with
  **307 GB/s of memory bandwidth**, up to an 18 core CPU and up to a 20 core GPU.
  Apple also claims up to 8.5 times faster LLM prompt processing in LM Studio than the M2
  Pro Mac mini, and up to 4 times faster than the M4 Pro.
  Source: Apple Newsroom, as above.

Both are a $100 increase on the previous generation's equivalent starting prices.

## Memory bandwidth on the older machines

- **M4 Pro: 273 GB/s.** Source: Apple, MacBook Pro (14 inch, M4 Pro or M4 Max, 2024) tech
  specs. https://support.apple.com/en-us/121553
- **M2 Pro: up to 200 GB/s**, unchanged from the M1 Pro.
- **M1 Max: 400 GB/s**, announced with the chip in October 2021.
  Source: Apple, "Introducing M1 Pro and M1 Max", 18 October 2021.

The comparison the video turns on is that the M1 Max's 400 GB/s is higher than the new
M5 Pro Mac mini's 307 GB/s. Both figures are Apple's own.

## Why bandwidth is the number for token generation

Generating a token requires reading the model's weights out of memory. On a memory bound
decode, tokens per second scales with memory bandwidth rather than with compute, which is
why a machine with a wider memory bus can generate faster than a newer machine with a
narrower one. Prompt processing, which is what Apple's LM Studio multiplier measures, is
compute bound instead, so a large multiplier there does not carry over to generation.

## The models named on screen

- **gpt oss 20B**: about **21 billion total parameters**, about **3.6 billion active per
  token**, mixture of experts with 32 experts per layer and 4 active, **128K context**, and
  OpenAI states it runs within **16 GB of memory**. Apache 2.0.
  Source: OpenAI, "Introducing gpt oss", and the openai/gpt-oss-20b model card on Hugging
  Face. https://openai.com/index/introducing-gpt-oss/ and
  https://huggingface.co/openai/gpt-oss-20b
- **Qwen3 Coder 30B A3B Instruct**: **30.5 billion total parameters**, **3.3 billion
  active**, mixture of experts with 128 experts and 8 active per forward pass, **256K
  native context** (extendable to 1M with YaRN).
  Source: the Qwen3 Coder 30B A3B Instruct model card, mirrored on OpenRouter, Amazon
  Bedrock and Hugging Face.
  https://openrouter.ai/qwen/qwen3-coder-30b-a3b-instruct
- The other models named exist as stated and are used only by name and parameter count:
  Llama 3.1 8B, Qwen3 8B, Gemma 3 4B, Qwen3 14B, Gemma 3 12B, Mistral Small (24B),
  Gemma 3 27B, Qwen3 32B.

## The four bit weight figures on screen

Every "GB" printed on a model module or a memory block in this video is computed from one
rule rather than from a remembered file size:

    weights in GB = parameters in billions x 0.5625

which is about four and a half bits per parameter, the size a common four bit quantisation
lands at once some tensors are kept wider. It is applied identically to every model so the
comparisons on screen are like for like, and it reproduces the script's own figure: a 70
billion parameter model at four bit comes out at **39.4 GB**, which is the "around forty
gigabytes just for weights" the narration states.

Real file sizes vary by quantisation method and by how the KV cache is stored, so these are
approximations of the same kind, not published sizes. They are labelled on screen as four
bit weights and the source line names the rule.

## Prices in the used market

The used prices in the narration are market observations rather than published figures, and
they could not be chased to a primary source: the marketplaces that carry them (eBay,
Swappa, refurbishers) block automated retrieval, and a used price is a moving spread rather
than a number anyone publishes.

Where the video puts a used price on screen it draws it as what it is: a band with
individual listings scattered inside it, credited to used marketplace listings and dated,
rather than as a single figure stated as fact. The figures shown are the ones the narration
gives:

- A 32 GB M2 Pro Mac mini around $900 to $1,100.
- A 64 GB M1 Max Mac Studio around $1,250 to $1,500, and around $1,300 to $1,500 in the
  final ranking.

Individual listings consistent with those bands were visible in September 2026 (for
example, a refurbished 2022 Mac Studio, M1 Max, 64 GB, 2 TB with AppleCare on eBay), but a
single listing is not a market price. **These bands are listed under "Not checked" in
MANIFEST.md.**

## What the M1 Max Mac Studio does not have

The 2022 Mac Studio predates Thunderbolt 5, which arrived on the M4 Pro and M4 Max
generation, and predates the Neural Accelerators Apple put in every GPU core from the M5
generation onward. A used unit carries no remaining Apple warranty unless it is bought
refurbished with coverage. All three are stated in the narration and are matters of record
in Apple's own specifications for the respective generations.
{% endraw %}

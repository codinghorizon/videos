---
layout: default
title: "The best coding AI for 4GB VRAM has a hidden rival"
permalink: /best-local-coding-ai-4gb-vram/
date: 2026-09-15
---

# The best coding AI for 4GB VRAM has a hidden rival

{% raw %}
Every figure, size, date and benchmark score this video puts on screen, traced to the
place that published it.

Weight file sizes are the `Q4_K_M` build unless stated otherwise, because that is the
quantisation a runner offers first and the one a viewer will actually download.

---

## Liquid AI LFM2.5 2.6B

Released 4 August 2026.

| Claim | Value | Source |
| --- | --- | --- |
| Q4_K_M weight file | 1.67 GB | [LiquidAI/LFM2.5-2.6B-GGUF](https://huggingface.co/LiquidAI/LFM2.5-2.6B-GGUF/tree/main) |
| Q4_0 weight file | 1.59 GB | same |
| Throughput, AMD Ryzen AI Max+ 395 | 113 tok/s | [Liquid AI launch post](https://www.liquid.ai/blog/lfm2-5-2-6b) |
| Throughput, Apple M5 Max | 220 tok/s | same |

The model card gives both figures but names only "an AMD Ryzen CPU". The specific part,
Ryzen AI Max+ 395, appears in Liquid AI's own launch post, which is what the beat credits.
| Context window | 128K | same |

Recommended uses, from the model card: "We recommend using it for agentic workloads, tool
use, data extraction, RAG, and long-context workflows."

The limit the video quotes, also from the model card: "It is not recommended for agentic
coding and knowledge-heavy tasks."

Both throughput figures are the publisher's own, measured on the machines named. Neither
describes a GTX 1650.

Sources:
- https://huggingface.co/LiquidAI/LFM2.5-2.6B
- https://huggingface.co/LiquidAI/LFM2.5-2.6B-GGUF/tree/main
- https://www.liquid.ai/blog/lfm2-5-2-6b

---

## Microsoft Phi 4 mini instruct

| Claim | Value | Source |
| --- | --- | --- |
| Parameters | 3.8B | [microsoft/Phi-4-mini-instruct](https://huggingface.co/microsoft/Phi-4-mini-instruct) |
| Context window | 128K | same |
| Q4_K_M weight file | 2.49 GB | [bartowski/microsoft_Phi-4-mini-instruct-GGUF](https://huggingface.co/bartowski/microsoft_Phi-4-mini-instruct-GGUF) |

Microsoft's own summary of what the model is for names "Strong reasoning (especially math
and logic)", which is the emphasis the video refers to.

Sources:
- https://huggingface.co/microsoft/Phi-4-mini-instruct
- https://huggingface.co/bartowski/microsoft_Phi-4-mini-instruct-GGUF

---

## Nanbeige 4.1 3B

| Claim | Value | Source |
| --- | --- | --- |
| LiveCodeBench v6 | 76.9 | [Nanbeige/Nanbeige4.1-3B](https://huggingface.co/Nanbeige/Nanbeige4.1-3B) |
| Qwen3-30B-A3B-2507, same table, same benchmark | 66.0 | same |
| Community q4, Q4_0 | 2.33 GB | [mradermacher/Nanbeige4.1-3B-GGUF](https://huggingface.co/mradermacher/Nanbeige4.1-3B-GGUF) |
| Community q4, Q4_K_S | 2.34 GB | same |
| Community q4, IQ4_XS | 2.24 GB | same |
| Community q4, **Q4_K_M (the default)** | **2.44 GB** | same |

There is no official Nanbeige GGUF; every q4 above is a community build. The script says
"around 2.3", which is true of Q4_0, Q4_K_S and IQ4_XS but NOT of Q4_K_M, the build most
runners pull by default. The picture therefore names the quant it is showing rather than
printing a bare "2.3 GB", because an unlabelled figure would read as the default one.

The comparison the video makes is the publisher's own table: the 3B model's 76.9 sits
above Qwen3-30B-A3B-2507's 66.0, a model with thirty billion total parameters. The rest
of that column, for context: Qwen3-4B-2507 57.4, Qwen3-8B 49.4, Qwen3-14B 55.9,
Qwen3-32B 55.7.

There is no official GGUF release, so the weight file sizes are community conversions:
IQ4_XS 2.3 GB, Q4_K_S 2.4 GB, Q4_K_M 2.5 GB.

Sources:
- https://huggingface.co/Nanbeige/Nanbeige4.1-3B
- https://huggingface.co/mradermacher/Nanbeige4.1-3B-GGUF

---

## IBM Granite 4.2 3B

Released 25 August 2026, Apache 2.0.

| Claim | Value | Source |
| --- | --- | --- |
| Q4_K_M weight file | 2.24 GB | [ibm-granite/granite-4.2-3b-GGUF](https://huggingface.co/ibm-granite/granite-4.2-3b-GGUF/tree/main) |
| LiveCodeBench v6 | 69.71 | [ibm-granite/granite-4.2-3b](https://huggingface.co/ibm-granite/granite-4.2-3b) |
| Context window | 128K | same |

The three thinking modes the video describes are settings on the chat template:

- thinking, the default: `enable_thinking=True`
- low effort: `enable_thinking=True, low_effort=True`
- non thinking: `enable_thinking=False`

The blank entries the video points at are real. On IBM's own benchmark table the 3B model
has no published result for SWE-bench Verified, SWE-bench Multilingual, SWE-bench Pro,
Terminal-Bench 2.1, BirdBench or GDPval. The larger models in the same family do carry
results in those rows.

Sources:
- https://huggingface.co/ibm-granite/granite-4.2-3b
- https://huggingface.co/ibm-granite/granite-4.2-3b-GGUF/tree/main
- https://www.marktechpost.com/2026/08/25/ibm-releases-granite-4-2-bringing-native-reasoning-and-agentic-rl-to-open-enterprise-models/

---

## Google Gemma 4 E2B

| Claim | Value | Source |
| --- | --- | --- |
| What the E stands for | effective parameters | [google/gemma-4-E2B-it](https://huggingface.co/google/gemma-4-E2B-it) |
| Parameters, with embeddings | 5.1B | same |
| Effective parameters, without | 2.3B | same |
| LiveCodeBench v6 | 44.0 | same |
| Q4_K_M weight file | 3.11 GB | [unsloth/gemma-4-E2B-it-GGUF](https://huggingface.co/unsloth/gemma-4-E2B-it-GGUF/tree/main) |
| Vision projector, F16 | 0.99 GB | same |
| Modalities | text, image, audio | [google/gemma-4-E2B-it](https://huggingface.co/google/gemma-4-E2B-it) |

The gap the video is pointing at is between the name and the download. The name counts
2.3B effective parameters; the file has to store 5.1B, because per layer embedding tables
are looked up rather than multiplied through, and they are still bytes on disk. The
vision projector is a separate file on top of the 3.11 GB.

Sources:
- https://huggingface.co/google/gemma-4-E2B-it
- https://huggingface.co/unsloth/gemma-4-E2B-it-GGUF/tree/main

---

## Qwen3.5 4B

| Claim | Value | Source |
| --- | --- | --- |
| Parameters | 4B | [Qwen/Qwen3.5-4B](https://huggingface.co/Qwen/Qwen3.5-4B) |
| LiveCodeBench v6 | 55.8 | same |
| Q4_K_M weight file | 2.74 GB | [unsloth/Qwen3.5-4B-GGUF](https://huggingface.co/unsloth/Qwen3.5-4B-GGUF/tree/main) |
| Vision projector, F16 | 672 MB | same |
| Image input | yes | [Qwen/Qwen3.5-4B](https://huggingface.co/Qwen/Qwen3.5-4B) |

Thinking can be turned off through the chat template: `"enable_thinking": False` passed in
`chat_template_kwargs`. Qwen notes that Qwen3.5 does not support the older soft switch.

Sources:
- https://huggingface.co/Qwen/Qwen3.5-4B
- https://huggingface.co/unsloth/Qwen3.5-4B-GGUF/tree/main

---

## The benchmark itself

LiveCodeBench evaluates a model by running its generated solutions against test cases for
programming problems, rather than comparing them to a reference answer as text. Version 6
is the contamination controlled window used by every score above.

The six scores this video shows, all version 6, all from the publisher of the model in
question:

| Model | LiveCodeBench v6 |
| --- | --- |
| Nanbeige 4.1 3B | 76.9 |
| Granite 4.2 3B | 69.71 |
| Qwen3-30B-A3B-2507 | 66.0 |
| Qwen3.5 4B | 55.8 |
| Gemma 4 E2B | 44.0 |

They come from different labs running their own evaluations with their own settings, and
they measure the full precision weights, not the four bit files that fit on a 4 GB card.

Source: https://livecodebench.github.io/

---

## The hardware

| Card | Memory | Bandwidth | Source |
| --- | --- | --- | --- |
| GTX 1650, GDDR5 | 4 GB, 128 bit | 128 GB/s | [NVIDIA GTX 16 series](https://www.nvidia.com/en-my/geforce/graphics-cards/gtx-1650/) |
| GTX 1050 Ti | 4 GB, 128 bit | 112 GB/s | [PC Gamer, GTX 1650 review](https://www.pcgamer.com/nvidia-geforce-gtx-1650-review/) |
| RTX 3050 Laptop, 4 GB | 4 GB GDDR6, 128 bit | 192 GB/s | [Notebookcheck](https://www.notebookcheck.net/NVIDIA-GeForce-RTX-3050-Laptop-GPU-Benchmarks-and-Specs.513790.0.html) |

The RTX 3050 laptop part is the newer card and moves memory half again as fast as a GTX
1650, and it still has the same four gigabytes to fit a model into. Bandwidth describes
how fast memory moves data; capacity decides what loads at all.

Sources:
- https://www.nvidia.com/en-my/geforce/graphics-cards/gtx-1650/
- https://www.pcgamer.com/nvidia-geforce-gtx-1650-review/
- https://www.notebookcheck.net/NVIDIA-GeForce-RTX-3050-Laptop-GPU-Benchmarks-and-Specs.513790.0.html

---

## Where the model actually ran

`ollama ps` reports placement in its PROCESSOR column: `100% GPU` when the whole model is
on the card, `100% CPU` when no usable GPU was found, and a split such as `48%/52%
CPU/GPU` when the weights and the KV cache together are larger than the free VRAM. A
split is the runner doing its job, not a fault, and it is the first thing to read before
blaming the model for being slow.

Sources:
- https://github.com/ollama/ollama
- https://insiderllm.com/guides/ollama-not-using-gpu-fix/

---

## Caveats

- The tokens per second figures for LFM2.5 are Liquid AI's, measured on an AMD Ryzen AI
  Max+ 395 and an Apple M5 Max. No figure here describes a GTX 1650, a GTX 1050 Ti or an
  RTX 3050, and none is a prediction for one.
- Published benchmark scores are self reported by each model's own publisher, under that
  publisher's own settings, on the full precision weights. They are not measurements of
  the quantised files this video is actually comparing.
- Nanbeige 4.1 3B has no official GGUF release. The 2.3 GB to 2.5 GB range is community
  conversions and can move when a converter changes.
- Weight file sizes are the file alone. Context, the KV cache and the runner's own
  overhead are on top of them, and a vision capable model adds a separate projector file
  as well.

---

## Verified before publish

Every figure this video puts on screen was re-checked against a primary source after the
script's final rewrite. Confirmed exactly as shown: Liquid's 1.67 GB Q4_K_M and the
sentence ruling out agentic coding; phi 4 mini's 3.8B and 2.49 GB; Nanbeige's 76.9 against
Qwen3-30B-A3B-2507's 66.0 in its own table; Granite 4.2 3B's August 25 release, 2.24 GB
official Q4_K_M and 69.71; Gemma 4 E2B's effective-parameter naming, 5.1B with embeddings,
44.0 and Unsloth's 3.11 GB; Qwen3.5 4B's 55.8, 2.74 GB, image input and disableable
thinking; the GTX 1650 GDDR5 at 128 GB/s and the GTX 1050 Ti at 112 GB/s, both from
NVIDIA's own spec tables.

Three things were corrected rather than confirmed:

- Nanbeige's default q4 is 2.44 GB, not 2.3 GB. See the note above.
- The Ryzen AI Max+ 395 attribution moved from the model card to the launch post.
- An `ollama ps` listing on screen carried invented SIZE values. The column was removed;
  the PROCESSOR column, which is the point of that beat, is documented behaviour.

### Not checked

- Whether Granite's three modes are exposed by any particular runner. IBM names them
  full thinking, non-thinking and low-effort; the narration describes them in plain words.
- The RTX 3050 laptop's bandwidth is not stated on screen. Only the 4 GB variant shares
  this memory budget; the 2023 6 GB refresh uses a narrower bus.
{% endraw %}

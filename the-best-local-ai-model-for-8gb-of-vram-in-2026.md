---
layout: default
title: "The Best Local AI Model for 8GB of VRAM in 2026"
permalink: /the-best-local-ai-model-for-8gb-of-vram-in-2026/
date: 2026-07-31
---

# The Best Local AI Model for 8GB of VRAM in 2026

Every figure the video puts on screen, chased to a primary source. Where a figure could
not be confirmed at a primary source it was changed in the shot, and the ones that are
still worth qualifying are listed under Caveats at the end.

Model card figures are self reported by the labs that published them unless stated
otherwise. Where two published figures disagree, both are recorded.


## The 8GB answer: Bonsai 27B

Prism ML, Bonsai 27B model cards and documentation.
- https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf
- https://huggingface.co/prism-ml/Bonsai-27B-mlx-1bit
- https://docs.prismml.com/models/bonsai-27b

| Figure on screen | Source value |
| --- | --- |
| Built from Qwen3.6 27B | Base architecture Qwen3.6-27B |
| Full precision footprint 54GB | FP16 baseline 54GB |
| A careful 4 bit build is 17.6GB | Q4_K_XL, 5.2 true bits per weight, 17.6GB |
| An aggressive 2 bit build is 9.4GB | IQ2_XXS, 2.8 true bits per weight, 9.4GB |
| Ternary build 5.9GB | 5.9GB at 1.71 true bits per weight |
| 1 bit build 3.9GB | 3.9GB at 1.125 true bits per weight, a 14.2x reduction against FP16 |
| Weights take one of three values | Ternary weights with group wise FP16 scaling, applied across embeddings, attention projections, MLP projections and the LM head |
| 1.71 bits per weight | 1.71 true bits per weight for the ternary build |
| Ternary keeps 94.6% | Ternary average 80.49 against an FP16 baseline of 85.07, across 15 thinking mode benchmarks |
| 1 bit keeps 89.5% | 1 bit average 76.11 against the same 85.07 baseline |
| Maths barely moves | Ternary maths category average 93.40, within two points of full precision |
| 4 bit scores 84.99, 2 bit scores 72.73, ternary scores 80.49 | Same comparison table |
| Nearly 8 points better than the 2 bit build at 1.6x less memory | 80.49 against 72.73 is 7.76 points; 9.4GB against 5.9GB is 1.59x |
| 66.4 tokens a second on an M5 Max | 66.4 tokens per second generation, Apple M5 Max, 1 bit build |
| 11.0 tokens a second on an iPhone 17 Pro Max | 11.0 tokens per second generation, iPhone 17 Pro Max, 1 bit build |
| Reads images | Vision tower quantised to 4 bit, loaded only when an image is present |
| Apache 2.0 | Apache 2.0 |
| 262,144 tokens of context | 262K token context, carried over from the Qwen3.6 backbone |
| Runs through MLX and CUDA | MLX builds published alongside GGUF; CUDA throughput measured on H100 |

The 3.9GB build being smaller on disk than a full precision 2 billion parameter model is
arithmetic rather than a published claim: two billion weights at 16 bits each is about
4GB.


## Below 8GB: Nanbeige 4.2

Nanbeige, Nanbeige4.2-3B model card.
- https://huggingface.co/Nanbeige/Nanbeige4.2-3B
- https://huggingface.co/Nanbeige/Nanbeige4.2-3B-Base

| Figure on screen | Source value |
| --- | --- |
| 3B non embedding parameters | 4B total parameters, 3B non embedding |
| Looped transformer, the same layers run more than once | Looped Transformer architecture that reuses transformer layers to add capacity without adding parameters |
| 63.6 on SWE bench Verified | Nanbeige4.2-3B 63.6, Qwen3.5-9B 53.1, Gemma4-12B 44.2 |
| Ten and a half points over a model three times its size | 63.6 against 53.1 |
| 87.4 on GPQA Diamond | Nanbeige4.2-3B 87.4, Qwen3.5-9B 81.7, Gemma4-12B 78.8 |
| 262,144 tokens of context | 262,144 tokens, stated as 256K |
| Apache 2.0, and it runs offline | Apache 2.0, with deployment recipes for vLLM, SGLang, llama.cpp and Ollama |

The model card also reports 46.9 on SWE-Bench Pro and 74.3 on the GDPval general agent
rubrics, against 33.8 and 61.9 for the 9B comparison.


## Above 8GB: Qwen 3.6 27B and Thinking Cap

Qwen 3.6 27B.
- https://artificialanalysis.ai/models/qwen3-6-27b

| Figure on screen | Source value |
| --- | --- |
| 87.8 on GPQA Diamond | 87.8 with thinking enabled |
| About 54GB at full precision | 27 billion weights at 16 bits each |
| 262,144 token native context | Native 262,144 tokens |

Bottle Cap AI, Thinking Cap release notes and model card.
- https://bottlecapai.com/post/thinkingcap-qwen3-6-27b/
- https://huggingface.co/bottlecapai/ThinkingCap-Qwen3.6-27B

| Figure on screen | Source value |
| --- | --- |
| About half the reasoning tokens | 50% average reduction in thinking tokens |
| 57.7% fewer in domain | 57.7% average reduction on benchmarks in the tuning distribution |
| 45.8% fewer out of domain | 45.8% average reduction on benchmarks outside it |
| 74.1% fewer on GSM8K | 74.1%, the largest single benchmark reduction reported |
| Answer quality minus 0.7 points out of domain, plus 1.0 in | Macro averages of minus 0.7pp and plus 1.0pp |

The release notes also report that safety refusal rates are statistically
indistinguishable from the base model.


## Workstation class: Laguna S 2.1 on a DGX Spark

Poolside, Laguna S 2.1 release notes.
- https://poolside.ai/blog/introducing-laguna-s-2-1
- https://huggingface.co/poolside/laguna-s-2.1

| Figure on screen | Source value |
| --- | --- |
| 118B parameters, 8B active per token | 118B total, 8B active, mixture of experts |
| 256 routed experts, ten fire per token | 256 routed experts, top ten per token, plus one shared expert, over 48 layers |
| 70.2% on Terminal Bench 2.1 | 70.2% with thinking enabled |
| Against 64.0% from a 1.6T rival | DeepSeek-V4-Pro-Max, 1.6T total and 49B active, 64.0% |
| Roughly 14 times its size | 1.6T against 118B |
| 40.4% against 9.0% on DeepSWE v1.1 | Laguna 40.4%, DeepSeek-V4-Pro-Max 9.0% |
| 50 minutes, 181 steps, no human help | A 50 minute, 181 step session building an HTML and CSS rendering engine in JavaScript, validated against real browser behaviour |
| It overthinks simple tasks | Stated limitation: extended thinking on complex mathematics |
| It fumbles unfamiliar tool schemas | Stated limitations: harness overfitting when tool schemas differ from the native interface, and invalid JSON in nested tool calls with array arguments |
| Open weights, OpenMDW 1.1 | OpenMDW-1.1 |
| On Hugging Face from day one | Weights published at launch, with vLLM, Ollama and OpenRouter availability |

The release notes also state pre training began on 22 May 2026 and the model launched on
21 July 2026, under nine weeks later, and report 78.5% on SWE-Bench Multilingual and
59.4% on the public SWE-Bench Pro dataset.

Nvidia DGX Spark.
- https://www.nvidia.com/en-us/products/workstations/dgx-spark/

| Figure on screen | Source value |
| --- | --- |
| 128GB unified memory | 128GB unified, shared between CPU and GPU over NVLink-C2C |
| $3,999 | Founders Edition list price |
| 150mm square, sits under a monitor | 5.9 by 5.91 inches, 1.99 inches thick |
| A 32GB graphics card cannot load it | Laguna needs roughly 75GB at Q4_K_M, so a 128GB unified memory machine is the practical minimum |


## The top rung: Motif 3 Beta

Motif Technologies, Motif-3-Beta model card, and the Artificial Analysis listing.
- https://huggingface.co/Motif-Technologies/Motif-3-Beta
- https://artificialanalysis.ai/models/motif-0714

| Figure on screen | Source value |
| --- | --- |
| 314B parameters | Roughly 314B total |
| 384 experts, eight routed plus one shared | 384 experts, 8 routed per token plus 1 shared |
| About 13B doing the work | Roughly 13B active parameters per token |
| Built from scratch, not a fine tune | A fully in house architecture rather than a re parameterisation of an existing open model |
| Korea | Motif Technologies, a Korean lab |
| Intelligence Index 44 | Artificial Analysis Intelligence Index score of 44 |
| Third among open weight models, behind Kimi K3 and GLM 5.2 | Third among open weight models on the index |
| Research licence only | Weights are downloadable, but licensed for non commercial research; commercial use requires written permission |
| Around 314GB at 8 bit | 314 billion weights at one byte each |

Kimi K3's parameter count, shown on the same board, is 2.8T total and 50B active.


## What local still cannot do

- Top of the Terminal Bench 2.1 table is 88.3 for Kimi K3 and 88.0 for Claude Fable 5,
  against 70.2 for the best model that fits on a single desk box. That is the eighteen
  point gap the video puts on screen.
  https://poolside.ai/blog/introducing-laguna-s-2-1


## Running them

- Ollama installs as one command and pulls a model by name. https://ollama.com/
- LM Studio is the same idea as a desktop application with a download button.
  https://lmstudio.ai/
- Every model named in this video is a free download from Hugging Face, subject to its own
  licence. https://huggingface.co/


## Caveats

- The ternary Bonsai build has two published sizes. The comparison table on its model card
  and the launch write up both give 5.9GB for the language weights at 1.71 bits per weight,
  while the file listing on the same card gives 7.17GB for the packed Q2_0_g128 GGUF and
  the documentation gives 6.66 GiB. The video uses 5.9GB. Every one of those figures is
  under the 8GB line, so the claim the video makes does not turn on which is right.
- The 2.4GB figure for Nanbeige 4.2 is a four bit community conversion, not an artifact the
  lab published. The official weights are BF16 and total about 8.4GB.
- Nanbeige 4.2 does not run on stock llama.cpp or Ollama yet, because the looped
  architecture is not upstream. It needs the project's own fork.
- Motif 3 Beta's placement is third among open weight models on the Artificial Analysis
  index according to the write ups of its release. Artificial Analysis's own model page
  classes it as proprietary, which is consistent with its research only licence, and its
  overall position on the index moves as models are added to the board.
- Benchmark scores throughout are the numbers each lab published for its own model. Where
  a model is compared against a rival, the rival's score is the one the publishing lab
  reported, not one measured independently.
- Throughput figures are for the specific hardware named beside them. Tokens per second on
  any other machine will differ.

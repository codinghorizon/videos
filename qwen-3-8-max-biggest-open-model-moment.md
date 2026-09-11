---
layout: default
title: "Qwen 3.8 Max Is The Open Model Moment We Waited For"
permalink: /qwen-3-8-max-biggest-open-model-moment/
date: 2026-09-11
---

# Qwen 3.8 Max Is The Open Model Moment We Waited For

{% raw %}
Every figure, name and benchmark this video renders on screen, chased to a source.
Organised by the chapter that puts it on screen.

## The model itself

| Fact | Value | Source |
| --- | --- | --- |
| Total parameters | 2.4 trillion | [Qwen3.8-2.4T-A95B model card](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) |
| Active parameters per token | 95 billion | [Qwen3.8-2.4T-A95B model card](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) |
| Routed experts | 512 | [vLLM recipe, Qwen3.8-2.4T-A95B](https://recipes.vllm.ai/Qwen/Qwen3.8-2.4T-A95B) |
| Routed experts selected per token | 10 | [Qwen3.8-2.4T-A95B model card](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) |
| Shared experts | 1, always on | [Qwen3.8-2.4T-A95B model card](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) |
| Layers | 92 (23 full attention, 69 linear attention) | [vLLM recipe](https://recipes.vllm.ai/Qwen/Qwen3.8-2.4T-A95B) |
| Native context | 262,144 tokens | [Qwen3.8-2.4T-A95B model card](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) |
| Maximum context | 1,010,000 tokens (1M class) | [Qwen3.8-2.4T-A95B model card](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) |
| Maximum output tokens | 131,072 | [Qwen3.8-2.4T-A95B model card](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) |
| Maximum thinking budget | 262,144 tokens | [Qwen3.8-2.4T-A95B model card](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) |
| Announced | 3 August 2026 | [MarkTechPost launch report](https://www.marktechpost.com/2026/08/03/alibaba-qwen-releases-qwen3-8-max/) |
| Ratio to Qwen3.8-27B | 2.4T / 27B is 88.9x | arithmetic on the two model cards |

The hosted product reads text, images and video and can call tools, search and run
code. The downloadable checkpoint is **text only** and **always reasons**: thinking mode
cannot be disabled and every response opens with a `<think>` block.
[Model card](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B),
[DataCamp on the hosted model's modalities](https://www.datacamp.com/blog/qwen3-8-max).

## The benchmark table

Qwen's own launch comparison, reproduced by
[emergent.sh](https://emergent.sh/learn/qwen-3-8-benchmarks). These are vendor numbers
run in Qwen's harness, not independent reproductions, which is the caveat the video
states out loud.

| Benchmark | Qwen3.8-Max | Qwen3.7-Max | GPT-5.6 Sol | Claude Opus 4.8 | Fable 5 |
| --- | --- | --- | --- | --- | --- |
| Terminal Bench 2.1 | 86.6 | 74.5 | 88.8 | 84.6 | 84.6 |
| SWE-bench Pro | 67.7 | 60.6 | 64.6 | 69.2 | 80.0 |
| PaperBench | 93.0 | 64.8 | 90.5 | 80.3 | 88.8 |
| GPQA Diamond | 92.6 | 92.4 | 94.1 | 92.0 | 92.6 |

- Terminal Bench gain, 74.5 to 86.6, is **12.1 points**.
- PaperBench gain, 64.8 to 93.0, is **28.2 points**.
- JobBench rises **31.3 to 53.4**.
  [apidog benchmark breakdown](https://apidog.com/blog/qwen-3-8-benchmarks/)
- DeepSWE is Qwen's clear loss: **56.6**, against Opus 4.8 at 59, Gemini 5 at 70 and
  GPT-5.6 Sol at 73.
  [MindStudio, where it really ranks](https://www.mindstudio.ai/blog/qwen-3-8-max-benchmarks-explained)

Terminal Bench 2.1 places an agent inside a terminal and scores whether it finishes real
engineering tasks under a time limit. PaperBench, built by OpenAI, scores whether an
agent can reproduce a scientific paper's results from its experimental description.
[emergent.sh](https://emergent.sh/learn/qwen-3-8-benchmarks)

## Pricing, international Qwen API

| Model | Input, per 1M tokens | Output, per 1M tokens |
| --- | --- | --- |
| Qwen3.7-Max | $2.50 | $7.50 |
| Qwen3.8-Max | $2.00 | $6.00 |

Both input and output fall by exactly 20 percent.
[emergent.sh pricing table](https://emergent.sh/learn/qwen-3-8-benchmarks),
[DataCamp](https://www.datacamp.com/blog/qwen3-8-max)

## The sixteen day agent

Alibaba's headline demonstration: Qwen3.8-Max worked autonomously on the command line
tool **oh-my-cli** for sixteen days, taking user requests, turning them into GitHub
issues, assigning them to itself, writing the code, running the tests and iterating.

- By 30 July 2026: **265 commits, 127 pull requests, 151 issues**, with no human commit.
- Two further runs: a research paper reproduction using roughly 125 hours of compute,
  7,600 lines of code and 33 GPU training jobs; and a simulated e-commerce business that
  took 100,000 yuan to 416,252 yuan.

[the-decoder](https://the-decoder.com/alibabas-open-weight-qwen3-8-max-takes-on-long-horizon-ai-tasks-with-2-4-trillion-parameters/),
[developer-tech](https://www.developer-tech.com/news/alibaba-qwen3-8-max-claims-16-day-autonomous-coding-run/)

## The ladder of open models

| Model | Total params | Active params | Context | Terminal Bench 2.1 |
| --- | --- | --- | --- | --- |
| Qwen3.8-27B | 27B (27.78B) | dense | 262K, to 1M | 73.0 |
| Qwen3.8-Flash-Next | 125B | 6B | 262K, to 1M | — |
| DeepSeek V4 Flash | 284B | 13B | 1M | 82.7 |
| GLM-5.3-Flash | 320B (321B) | 18B | 1M | 84.3 |
| Kimi K3 | 2.8T | 104B | 1M | 88.3 |
| Qwen3.8-Max | 2.4T | 95B | 262K, to 1M | 86.6 |

- Qwen3.8-27B: **73.0** Terminal Bench 2.1, **61.7** SWE-bench Pro.
  [Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B)
- A good 4 bit build of the 27B lands around 17 GB of weights, which is the 24 to 32 GB
  class once context is allowed for.
  [codersera, the 17GB open model](https://codersera.com/blog/qwen-3-8-27b-complete-guide-2026/)
- Qwen3.8-Flash-Next: **125B total, 6B active**, 262,144 native context extensible to 1M.
  [DataCamp](https://www.datacamp.com/blog/qwen3-8-flash-next)
- DeepSeek V4 Flash: **284B total, 13B active**, 1M context.
  [vLLM recipe](https://recipes.vllm.ai/deepseek-ai/DeepSeek-V4-Flash)
- GLM-5.3-Flash: **321B total, 18B active**, 1M context.
  [vLLM recipe](https://recipes.vllm.ai/zai-org/GLM-5.3-Flash)
- Kimi K3: **2.8T total, 104B active**, 1M context, **88.3** on Terminal Bench 2.1 in
  Moonshot's own table.
  [Moonshot K3 specs](https://www.morphllm.com/kimi-k3)

Kimi's 88.3 and Qwen's 86.6 come from two different vendors' harnesses, so the pair does
not settle an ordering between them.

## The hardware, from the published serving recipe

vLLM's verified recipe for Qwen3.8-2.4T-A95B.
[recipes.vllm.ai](https://recipes.vllm.ai/Qwen/Qwen3.8-2.4T-A95B),
[vLLM day 0 blog, 12 August 2026](https://vllm.ai/blog/2026-08-12-qwen3.8)

| Precision | Weights | B300 (268 GB) | H200 (141 GB) |
| --- | --- | --- | --- |
| BF16, 16 bit | 4.45 TiB (4.89 TB) | 24 | **48** |
| FP8, 8 bit | 2.27 TiB | 16 | **32** |
| NVFP4, 4 bit | **1.32 TiB** | **8** | 16 |
| MXFP4, AMD | 1.45 TiB | 8x MI355X | 16 |

- Verified throughput, NVFP4 on 8 B300 with TP8 and MTP-3 speculative decoding:
  **304 output tokens per second for a single user**. FP8 on TP16 reaches 307.
  MTP-3 is worth roughly 2.3x on the per user rate.
- RTX 5090 carries **32 GB** of VRAM.
  [NVIDIA RTX 5090 specifications](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/)
- Raw 4 bit parameter estimate: 2.4T x 0.5 bytes is **1.2 TB**, which is **37.5** RTX
  5090s of VRAM before any overhead, so roughly 38. Arithmetic, not a vendor figure, and
  it deliberately ignores KV cache, activations and the fact that no such rig exists.

## The open weight release

- Announced 3 August 2026 with the open weights promised for the following week; the
  Qwen post says "Next week, the open weights of Qwen3.8-Max will be released, and
  Qwen3.8-27B is also going open-weights".
  [Qwen on X](https://x.com/Alibaba_Qwen/status/2084100707423289643)
- The weights shipped **12 August 2026** as the ungated `Qwen/Qwen3.8-2.4T-A95B`
  repository, with FP8 and NVFP4 checkpoints alongside.
  [vLLM day 0 support](https://vllm.ai/blog/2026-08-12-qwen3.8),
  [LMSYS SGLang day 0](https://www.lmsys.org/blog/2026-08-12-qwen3-8-day0-support)
- The licence is the custom **Qwen3.8-Max License**, not Apache 2.0. It grants use,
  copying, modification, publication, distribution, sublicensing, sale, deployment,
  hosting, fine tuning and derivative works. Products above 100 million monthly active
  users or $20 million monthly revenue must show the model name prominently in the
  interface, and a Model as a Service or AI work assistant business above $50 million of
  revenue in any 12 months needs a separate licence. Internal use is exempt.
  [Qwen3.8-Max License](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B/raw/main/LICENSE),
  [Forkast analysis](https://forkast.news/open-weights-closed-revenue-ceiling-alibabas-qwen-3-8-license-is-a-platform-play-not-a-gift/)

## Not checked

Listed here because the narration asserts them and no primary source was found.

- **"CoWorkBench rises by more than ten points."** Qwen3.8-Max's CoWorkBench figure is
  published (76.1 on the 0902 update, per
  [DataCamp](https://www.datacamp.com/blog/qwen3-8-max)) but no Qwen3.7-Max CoWorkBench
  score could be found to difference it against. No CoWorkBench figure is drawn on
  screen; the shot shows JobBench's sourced 31.3 to 53.4 instead.
- **"Some of Flash Next's memory can sit in system RAM."** A plausible description of a
  6B active MoE, and consistent with how these models are run, but no vendor statement
  was found. No figure is put on screen for it.
- **CoWorkBench and JobBench eval versions.** The 31.3 to 53.4 JobBench pair comes from
  the launch table; DataCamp reports 64.0 for the later 0902 checkpoint. Different
  checkpoints of the same model, not a contradiction, but the on screen figure is
  labelled to the launch comparison.
- **The sixteen day run itself.** Every figure in it (16 days, 265 commits, 127 pull
  requests, 151 issues) is Alibaba's own report of its own demonstration. Nobody outside
  Alibaba has reproduced it, which is a point the video makes rather than hides.
{% endraw %}

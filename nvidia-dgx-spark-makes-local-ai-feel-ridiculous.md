---
layout: default
title: "Nvidia DGX Spark Just Made Local AI Feel Serious"
permalink: /nvidia-dgx-spark-makes-local-ai-feel-ridiculous/
date: 2026-09-06
---

# Nvidia DGX Spark Just Made Local AI Feel Serious

{% raw %}
Every figure this video puts on screen, chased to a primary source. Where a claim in the
narration could not be re-found at a primary source, the shot does not render the figure,
and the claim is listed at the bottom.

## The machine

NVIDIA's own hardware specification for DGX Spark gives the whole of the teardown chapter.

- 128 GB LPDDR5X unified system memory, 256 bit interface, 4266 MHz, **273 GB/s** bandwidth.
- 20 core Arm CPU: 10 Cortex X925 and 10 Cortex A725.
- Blackwell GPU, 6144 CUDA cores, 5th generation Tensor Cores.
- Storage: 1 TB or 4 TB self encrypting NVMe M.2.
- Networking: one 10 GbE RJ45, a ConnectX 7 SmartNIC with two QSFP connectors, Wi-Fi 7.
- Dimensions **150 mm x 150 mm x 50.5 mm**, weight **1.2 kg**.
- **240 W** external power supply; the GB10 SOC TDP is **140 W**, with 100 W reserved for
  the rest of the system.

Source: NVIDIA, DGX Spark User Guide, Hardware Overview.
https://docs.nvidia.com/dgx/dgx-spark/hardware.html

Up to **1 petaFLOP** of FP4 AI compute, and the three model size claims, come from NVIDIA's
own product page:

- Inference with AI models up to **200 billion** parameters on one system.
- Fine tuning models up to **70 billion** parameters.
- Up to **four** DGX Spark systems connected over ConnectX networking working with models
  up to **700 billion** parameters.

The four node configuration quadruples available memory to **512 GB**.

Source: NVIDIA, DGX Spark product page.
https://www.nvidia.com/en-us/products/workstations/dgx-spark/

Two systems connected over a single 200 Gb/s QSFP link reach models up to 405 billion
parameters; three systems can be cabled directly, four or more need a switch.

Source: NVIDIA Sync User Guide, Cluster Assistant for a multi node DGX Spark cluster.
https://docs.nvidia.com/sync/latest/cluster-assistant.html

The software named on screen, DGX OS, CUDA, NIM, NemoClaw, OpenShell, playbooks and an
NVIDIA AI Enterprise trial, is the list NVIDIA gives on the product page above.

## Price

- Announced at CES 2025 as Project DIGITS, **about $3,000**, with 128 GB of memory and up
  to 4 TB of storage, and a claim of running models up to 200 billion parameters.
  Source: NVIDIA Newsroom, "NVIDIA Puts Grace Blackwell on Every Desk".
  https://nvidianews.nvidia.com/news/nvidia-puts-grace-blackwell-on-every-desk-and-at-every-ai-developers-fingertips
- Founders Edition launched at **$3,999**.
- **February 2026**: NVIDIA raised the Founders Edition MSRP from $3,999 to **$4,699**,
  citing "worldwide constraints in memory supply", with no hardware change and original
  order pricing honoured.
  Source: NVIDIA Developer Forums, "2/23/2026 Price Change Announcement".
  https://forums.developer.nvidia.com/t/2-23-2026-price-change-announcement/361713

## llama.cpp benchmark, single DGX Spark

Decode throughput, Qwen3 family, same harness and same machine. This is the report the
dense against mixture of experts comparison in chapter three is drawn from.

| Model | 512 context | 2048 context |
| --- | --- | --- |
| Qwen3 1.7B | **161.4 tok/s** | 146.1 tok/s |
| Qwen3 30B A3B (MoE) | **89.3 tok/s** | **83.8 tok/s** |
| Qwen3 32B (dense) | **10.7 tok/s** | 10.5 tok/s |

The report's own explanation of the gap: the 30B MoE activates roughly 2.4B parameters per
token and so avoids the memory bandwidth bottleneck that limits the dense 32B.

Source: DandinPower, llama.cpp_bench, DGX Spark report.
https://github.com/DandinPower/llama.cpp_bench/blob/main/dgx_spark/report.md

Context: the wider llama.cpp DGX Spark performance discussion.
https://github.com/ggml-org/llama.cpp/discussions/16578

## SparkBench leaderboard, single GB10

Throughput in tokens per second at 4k context, on one GB10.

| Model and recipe | tok/s at 4k |
| --- | --- |
| nvidia/qwen3.6-35b-a3b NVFP4 MTP | **86.3** |
| nvidia/qwen3-30b-a3b NVFP4 | **74.2** |
| ornith-ai/ornith-1.5-35b-a3b NVFP4 MTP | **70.8** |
| saricles/qwen3-coder-next NVFP4 | **58.9** |

These are different recipes, engines and model formats, so they are not directly
comparable with each other, which is what the shot that separates them into lanes shows.

Source: SparkBench. https://sparkbench.dev/

## Ollama benchmark dataset, single DGX Spark

Generated tokens per second. This is the "what runs against what feels good" chapter.

| Model | Gen tok/s |
| --- | --- |
| Llama 3.1 8B | **42.86** |
| Gemma 3 27B | 11.71 |
| Qwen2.5 Coder 32B | **10.36** |
| Qwen3 32B | 9.88 |
| CodeLlama 70B | 5.73 |
| Nemotron 70B | 4.77 |
| Llama 3.1 70B | **4.76** |
| Qwen 2.5 72B | 4.40 |
| Mistral Large 123B | **2.28** |

Source: G3nadh/dgx-spark-benchmarks dataset.
https://huggingface.co/datasets/G3nadh/dgx-spark-benchmarks

## Qwen3.8 Flash Next on one DGX Spark

The model is real and its architecture is confirmed: **176B total**, made of a 125B main
body plus a 51B n gram embedding table, activating **6B parameters per token**, MoE, with a
262,144 token native context.

Source: vLLM recipes, Qwen/Qwen3.8-Flash-Next.
https://recipes.vllm.ai/Qwen/Qwen3.8-Flash-Next

The caveats the narration lists are all confirmed by the published DGX Spark recipes: it
needs a patched vLLM, the checkpoint is about **122 GiB** on disk and needs the n gram
table served from NVMe by mmap to fit in 128 GB, and cold start is **8 to 13 minutes**.

Source: blazux/qwen3.8-Flash-DGX. https://github.com/blazux/qwen3.8-Flash-DGX
Source: madeye, Qwen3.8-Flash-Next on a single NVIDIA DGX Spark.
https://madeye.github.io/qwen38-flash-next-on-dgx-spark/

**The specific throughput pair the narration gives could not be re-found.** Published
single stream figures for this model on one DGX Spark range widely by recipe: 21.6 tok/s
hybrid quantisation, about 26 to 31 tok/s NVFP4 with MTP, 24.8 tok/s on one vLLM setup and
42.7 tok/s on another measured with the same script. So the shots for those beats draw the
architecture, the warm state and the concurrency scaling, and print no throughput figure.

## DeepSeek V4 Flash across two DGX Sparks

The model and the two node setup are confirmed: **284B total, 13B active**, MoE, run across
two GB10 nodes with tensor parallel size 2 because a single 128 GB pool is below the
checkpoint footprint.

Source: vLLM recipes, deepseek-ai/DeepSeek-V4-Flash.
https://recipes.vllm.ai/deepseek-ai/DeepSeek-V4-Flash

That aggregate throughput rises sharply with concurrency is confirmed: 210.8 tok/s combined
at six concurrent users with vLLM, and 261 tok/s aggregate at 16 concurrent on a DSpark
speculative decoding setup.

Source: DevelopersIO, "Tried running DeepSeek V4 Flash-0731 at 284B on two DGX Spark units".
https://dev.classmethod.jp/en/articles/dgx-spark-2node-deepseek-v4-flash-0731/

**The single stream figure the narration gives could not be re-found**, and the published
vLLM measurements for this configuration are higher, at 61.4 to 76 tok/s. The shot draws the
two node split and the concurrency scaling and prints no single stream figure.

## The machines it is compared against

**GeForce RTX 5090**: 32 GB GDDR7 on a 512 bit interface.
Source: NVIDIA. https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/

**Mac Studio**: configurable to 512 GB unified memory with 1.2 TB/s of memory bandwidth on
the M5 Ultra, and 128 GB at 614 GB/s on the M5 Max. Both are well above DGX Spark's
273 GB/s, which is what the narration says.
Source: Apple. https://www.apple.com/mac-studio/specs/

**AMD Ryzen AI Halo developer platform**, Ryzen AI Max+ 395: up to 128 GB unified system
memory, enough headroom to run up to **200 billion parameter** models locally, Windows and
Linux versions, an NPU, and a published tokens per dollar comparison against DGX Spark at
retail prices of **$3,999** for the AMD platform against **$4,699** for DGX Spark.
Source: AMD, "AMD Powers Next-Generation Agent Computers with New Ryzen AI Halo Developer
Platform".
https://www.amd.com/en/blogs/2026/amd-powers-next-generation-agent-computers-with-new-ryzen-ai-hal.html

## Not sourced, and therefore not on screen

- Qwen3.8 Flash Next at around 37 tokens per second warm on one DGX Spark, with around 117
  tokens per second aggregate at eight concurrent requests. The model, its size, its active
  parameter count and its caveats are all sourced above; that specific throughput pair is
  not, and published single stream figures for it span 21.6 to 42.7 tok/s.
- DeepSeek V4 Flash at around 38.5 tokens per second single stream by the vLLM metric on
  two DGX Sparks. The 284B two node configuration is sourced above; published vLLM single
  stream figures for it are 61.4 to 76 tok/s, which is higher than the figure given.
- Ornith 1.5 35B A3B appears on the SparkBench leaderboard at 70.8 tok/s, which is sourced,
  but no primary documentation for the model itself was found beyond that entry.
{% endraw %}

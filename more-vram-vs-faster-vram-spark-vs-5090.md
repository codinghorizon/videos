---
layout: default
title: "More VRAM or faster VRAM? The local AI buying trap"
permalink: /more-vram-vs-faster-vram-spark-vs-5090/
date: 2026-09-22
---

# More VRAM or faster VRAM? The local AI buying trap

{% raw %}
Sources for every figure this video states. Checked 21 September 2026.

## The two machines

### NVIDIA DGX Spark

| Fact | Value | Source |
| --- | --- | --- |
| Unified system memory | 128 GB LPDDR5x, 256 bit interface at 4266 MHz | [NVIDIA DGX Spark User Guide, Hardware Overview](https://docs.nvidia.com/dgx/dgx-spark/hardware.html) |
| Memory bandwidth | 273 GB/s | [NVIDIA DGX Spark User Guide, Hardware Overview](https://docs.nvidia.com/dgx/dgx-spark/hardware.html) |
| CPU | 20 core Arm (10 Cortex X925 plus 10 Cortex A725) | [NVIDIA DGX Spark User Guide, Hardware Overview](https://docs.nvidia.com/dgx/dgx-spark/hardware.html) |
| GB10 thermal design power | 140 W, with a 240 W external supply for the system | [NVIDIA DGX Spark User Guide, Hardware Overview](https://docs.nvidia.com/dgx/dgx-spark/hardware.html) |
| Size | 150 mm x 150 mm x 50.5 mm, about 5.9 by 5.9 by 2.0 inches, 1.2 kg | [NVIDIA DGX Spark User Guide, Hardware Overview](https://docs.nvidia.com/dgx/dgx-spark/hardware.html) |
| US list price | $4,699 Founders Edition, raised from $3,999 on 27 February 2026 | [VideoCardz, NVIDIA officially raises DGX Spark Founders Edition MSRP to $4,699](https://videocardz.com/newz/nvidia-officially-raises-dgx-spark-founders-edition-msrp-to-4699) |
| Reason for the rise | Global memory supply constraints; the configuration did not change | [VideoCardz](https://videocardz.com/newz/nvidia-officially-raises-dgx-spark-founders-edition-msrp-to-4699), [Overclock3D](https://overclock3d.net/news/systems/nvidia-raises-dgx-spark-price-by-700-due-to-memory-supply-constraints/) |

The memory is unified and shared between CPU, GPU and operating system rather than
dedicated graphics memory. NVLink C2C carries the CPU to GPU link.

### NVIDIA GeForce RTX 5090

| Fact | Value | Source |
| --- | --- | --- |
| Dedicated memory | 32 GB GDDR7, 512 bit interface | [NVIDIA GeForce RTX 5090 product page](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/) |
| Memory bandwidth | 1,792 GB/s | [NVIDIA GeForce RTX 5090 product page](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/) |
| Total graphics power | 575 W | [NVIDIA GeForce RTX 5090 product page](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/) |
| Launch price | $1,999 for the card, January 2025 | [NVIDIA GeForce RTX 5090 product page](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/) |
| Founders Edition size | 304 mm long, 137 mm wide, 48 mm high, two slot | [Tom's Hardware, RTX 5090 Founders Edition review](https://www.tomshardware.com/pc-components/gpus/nvidia-geforce-rtx-5090-review/2) |

### The two ratios the video opens on

- Capacity: 128 GB against 32 GB is exactly 4 times.
- Bandwidth: 1,792 GB/s against 273 GB/s is 6.56 times, which the script gives as
  "about six and a half times".

## The matched benchmark

LMSYS ran both machines on the same model, GPT OSS 20B in its MXFP4 build, through Ollama.

| Machine | Prefill, input tokens/s | Decode, output tokens/s |
| --- | --- | --- |
| RTX 5090 | 8,519 | 205 |
| DGX Spark | 2,053 | 49.7 |

Source: [LMSYS, NVIDIA DGX Spark In-Depth Review: A New Standard for Local AI Inference](https://www.lmsys.org/blog/2025-10-13-nvidia-dgx-spark/),
Jerry Zhou and Richard Chen, 13 October 2025.

A thousand output tokens at 205 tokens per second is about 4.9 seconds; at 49.7 it is
about 20.1 seconds. Both exclude prompt processing.

## The later llama.cpp figures

The llama.cpp project keeps a running DGX Spark benchmark thread, and the numbers move
with the build. The February 2026 results are the ones this video uses.

| Model | Size | Generation at depth 0 | Generation at depth 32,768 |
| --- | --- | --- | --- |
| GPT OSS 20B MXFP4 | 11.27 GiB | 83.43 tokens/s | — |
| GPT OSS 120B MXFP4 | 59.02 GiB | 58.72 tokens/s | 42.76 tokens/s |

Source: [ggml-org/llama.cpp Discussion 16578, Performance of llama.cpp on NVIDIA DGX Spark](https://github.com/ggml-org/llama.cpp/discussions/16578).
Earlier runs in the same thread are substantially lower for the same hardware: the
14 October 2025 entry has GPT OSS 120B at 35.31 tokens/s at depth 0, and the
31 October 2025 entry has 52.87. That spread is software, not hardware.

The generation tests are `tg32`, which is a 32 token sample. They are not a measurement of
a sustained coding session.

59.02 GiB is 63.4 GB, which is larger than the RTX 5090's entire 32 GB of VRAM before any
conversation state is added.

## The models

### Qwen3.8 27B

| Fact | Value | Source |
| --- | --- | --- |
| Parameters | 27 billion, dense | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Modality | Native vision language model, understands images and video | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Context | 262,144 native, extensible toward 1M with YaRN | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Licence | Apache 2.0 | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| SWE bench Pro | 61.7, against 53.5 for Qwen3.6 27B | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Four bit download | Q4_K_M is 19.0 GB | [ggml-org/Qwen3.8-27B-GGUF](https://huggingface.co/ggml-org/Qwen3.8-27B-GGUF) |

61.7 against 53.5 is a gain of 8.2 points at the same headline parameter count. Both are
Alibaba's own model card numbers rather than independent replications.

The ggml-org four bit pack also ships the separate multi token prediction head used for
speculative decoding, which is why it is larger than some other four bit packs of the same
model.

### Mistral Devstral 2 family

| Model | Parameters | SWE bench Verified | Licence |
| --- | --- | --- | --- |
| Devstral Small 2 | 24 billion | 68.0% | Apache 2.0 |
| Devstral 2 | 123 billion | 72.2% | Modified MIT |

Source: [Mistral AI, Introducing: Devstral 2 and Mistral Vibe CLI](https://mistral.ai/news/devstral-2-vibe-cli/),
9 December 2025, and [mistralai/Devstral-Small-2-24B-Instruct-2512](https://huggingface.co/mistralai/Devstral-Small-2-24B-Instruct-2512).

Both carry a 256K context window. Mistral's own figures.

**SWE bench Verified and SWE bench Pro are different benchmarks.** 68.0 on Verified and
61.7 on Pro are not comparable numbers, which is why the script says comparing them
directly would be nonsense.

### GPT OSS 120B

| Fact | Value | Source |
| --- | --- | --- |
| Total parameters | 117 billion | [OpenAI, Introducing gpt-oss](https://openai.com/index/introducing-gpt-oss/) |
| Active parameters per token | 5.1 billion | [gpt-oss model card, arXiv 2508.10925](https://arxiv.org/pdf/2508.10925) |
| Architecture | Mixture of experts | [OpenAI, Introducing gpt-oss](https://openai.com/index/introducing-gpt-oss/) |
| Licence | Apache 2.0 | [OpenAI, Introducing gpt-oss](https://openai.com/index/introducing-gpt-oss/) |

A mixture of experts routes each token to a subset of the experts, so the active count is
far below the total. The inactive experts still occupy memory.

## The other machines

| Machine | Memory | Bandwidth | Source |
| --- | --- | --- | --- |
| AMD Ryzen AI Max+ 395, Strix Halo | up to 128 GB LPDDR5x 8000, 256 bit | 256 GB/s | [AMD developer article](https://www.amd.com/en/developer/resources/technical-articles/2025/amd-ryzen-ai-max-395--a-leap-forward-in-generative-ai-performanc.html) |
| Apple M3 Ultra Mac Studio | 96 GB to 512 GB unified | 819 GB/s | [Apple Newsroom, Apple reveals M3 Ultra](https://www.apple.com/newsroom/2025/03/apple-reveals-m3-ultra-taking-apple-silicon-to-a-new-extreme/) |

The AMD part runs Linux or Windows. Measured sustained bandwidth on Strix Halo is reported
at roughly 215 GB/s, about 84% of the 256 GB/s specification.

Apple silicon runs MLX and Metal rather than CUDA, so model support and optimised
implementations differ from the NVIDIA path.

DGX Spark runs Linux on an Arm CPU, and NVIDIA publishes a porting guide because an
ordinary x86 desktop software package is not automatically compatible. Its supported
containers are the documented route to running a separate AI service.

## KV cache and context

The KV cache stores the attention keys and values for the conversation so far, so its cost
grows with the conversation rather than with the model file. Its size depends on the model
architecture, the context length, the precision the cache is held at, and the runner. An
advertised context window is a property of the model, not a promise that the cache for it
fits in a particular GPU's memory.

## Not checked

These are stated in the narration and could not be chased to a primary source.

- **"Developer lukas parke reports 212 to 258 tokens per second generating code with
  qwen 3.8 27B on one 5090, using a patched llama.cpp runner and speculative decoding."**
  No published source for this exact range or this attribution could be found. Independent
  reports of Qwen3.8 27B on a single RTX 5090 with speculative decoding span a wide band
  and disagree with each other: 211 to 293 tokens/s with a DFlash2 drafter, 264.8 tokens/s
  with a DSpark v2 drafter on SparkInfer against 92.9 without speculation, 161.7 tokens/s
  on SGLang's server, and up to about 170 tokens/s on llama.cpp with NVFP4 and multi token
  prediction. The general claim, that a patched runner with speculative decoding roughly
  doubles or better the default generation rate on one card, is well supported. The
  specific figures are not.
- The claim that fifty tokens per second "isn't a permanent limit on the box" is an
  inference from the October 2025 and February 2026 llama.cpp runs differing on identical
  hardware, not a published statement.
- Thermal design power and total graphics power are design ratings. No measured inference
  power draw for either machine is cited.
{% endraw %}

---
layout: default
title: "The m5 ultra review result nvidia buyers should see"
permalink: /apple-m5-ultra-local-ai/
date: 2026-09-23
---

# The m5 ultra review result nvidia buyers should see

{% raw %}
Every figure, price, date and benchmark this video puts on screen, chased to a primary
source. Checked 22 September 2026.

## The machine

| Claim | Finding | Source |
| --- | --- | --- |
| Up to 512GB unified memory | "up to 512GB of unified memory" | [Apple Newsroom, 25 Aug 2026](https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/) |
| Memory configurations | Standard 96GB; configurable to 256GB or 512GB with the 36-core CPU / 80-core GPU chip | [Mac Studio technical specifications](https://www.apple.com/mac-studio/specs/) |
| Full chip core counts | "up-to-36-core CPU with 12 super cores and 24 performance cores"; "up-to-80-core GPU" | [Apple Newsroom](https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/) |
| Base chip core counts | 30-core CPU (10 super, 20 performance), 64-core GPU | [Mac Studio technical specifications](https://www.apple.com/mac-studio/specs/) |
| Memory bandwidth | "1.2TB/s of memory bandwidth" | [Apple Newsroom](https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/) |
| Neural Accelerators in the GPU cores | "Neural Accelerators to the Ultra chip for the first time, enabling up to 4.3x the peak AI compute performance". These sit inside the GPU cores and are distinct from the separate Neural Engine. | [Apple Newsroom](https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/) |
| Starting price | "$5,499 (U.S.)" | [Apple Newsroom](https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/) |
| Launch timing | Pre-order from 25 August 2026, available from 22 September 2026 | [Apple Newsroom](https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/) |
| 512GB configuration timing | "coming in late October" | [Apple Newsroom](https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/) |
| M5 Max maximum memory | 128GB (M5 Max with 18-core CPU and 40-core GPU), 614GB/s | [Mac Studio technical specifications](https://www.apple.com/mac-studio/specs/) |
| Apple's prompt processing claim | "Up to 9.8x faster LLM prompt processing in LM Studio when compared to Mac Studio with M1 Ultra, and up to 4x faster than M3 Ultra." A manufacturer figure, and it refers to processing the prompt rather than completing a task. | [Apple Newsroom](https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/) |

## The review result

| Claim | Finding | Source |
| --- | --- | --- |
| Token throughput against the DGX Spark | The M5 Ultra's tokens-per-second throughput is almost four times higher than the DGX Spark across the board | [Tom's Hardware, Mac Studio (M5 Ultra) review](https://www.tomshardware.com/desktops/mini-pcs/apple-mac-studio-m5-ultra-review) |
| The tested model | Qwen3.8-27B-Q4_K_M, a dense model in a specific four bit quantization | [Tom's Hardware](https://www.tomshardware.com/desktops/mini-pcs/apple-mac-studio-m5-ultra-review) |
| Prompt processing | Faster prompt processing than the DGX Spark as well as faster generation | [Tom's Hardware](https://www.tomshardware.com/desktops/mini-pcs/apple-mac-studio-m5-ultra-review) |
| The reviewed configuration | 36-core CPU, 80-core GPU, 256GB unified memory, 4TB SSD, $12,299 | [Tom's Hardware](https://www.tomshardware.com/desktops/mini-pcs/apple-mac-studio-m5-ultra-review) |
| "one seriously impressive computer" | Tom's Guide verdict on the M5 Ultra Mac Studio | [Tom's Guide, Mac Studio M5 Ultra review](https://www.tomsguide.com/computing/apple-desktops/apple-mac-studio-m5-ultra-review) |
| The vents "got lukewarm at best" | Reported during the reviewer's gaming and rendering use. A description of their experience, not a temperature guarantee. | [Tom's Guide](https://www.tomsguide.com/computing/apple-desktops/apple-mac-studio-m5-ultra-review) |
| The video export test | An 8 minute 27 second project, 5K 30fps ProRes RAW with colour grading plus one 4K 120fps clip at 25% speed, converted to 4K 30fps in 1 minute 20 seconds | [Tom's Guide](https://www.tomsguide.com/computing/apple-desktops/apple-mac-studio-m5-ultra-review) |

The scope of the throughput result is the review's tested workload. A dense Qwen result
does not establish the same multiplier for a large mixture of experts model.

## The runtime

| Claim | Finding | Source |
| --- | --- | --- |
| LM Studio runs models offline behind a local API | Downloaded models run locally and are exposed through a local server endpoint | [LM Studio](https://lmstudio.ai/) |
| Faster prompt processing on M5 Macs | LM Studio Bionic v1.1.0 reports 2 to 2.75x faster prompt processing on M5 Macs | [LM Studio Bionic changelog 1.1.0](https://lmstudio.ai/changelog/bionic-v1.1.0) |
| MLX supports generation and fine tuning | MLX LM covers both text generation and fine tuning, which have different memory and compute demands | [MLX LM](https://github.com/ml-explore/mlx-lm) |
| MLX examples include image generation | The MLX examples repository includes FLUX image generation | [MLX examples](https://github.com/ml-explore/mlx-examples) |

## The model packages

Package sizes are the size of the download as published, not a promise that a running
session consumes exactly that amount.

| Model | Parameters | 4 bit MLX package | Source |
| --- | --- | --- | --- |
| Qwen3.8-27B | 27B, dense | 16.1 GB | [mlx-community/Qwen3.8-27B-4bit](https://huggingface.co/mlx-community/Qwen3.8-27B-4bit) |
| Gemma 4 31B (image and text input) | 31B | 18.4 GB | [mlx-community/gemma-4-31b-it-4bit](https://huggingface.co/mlx-community/gemma-4-31b-it-4bit) |
| Qwen3-Coder-Next | 80B total, about 3B active per token | 44.8 GB | [mlx-community/Qwen3-Coder-Next-4bit](https://huggingface.co/mlx-community/Qwen3-Coder-Next-4bit) |
| Qwen3.5-122B-A10B (multimodal) | 122B | 69.6 GB | [mlx-community/Qwen3.5-122B-A10B-4bit](https://huggingface.co/mlx-community/Qwen3.5-122B-A10B-4bit) |
| Qwen3.5-397B-A17B | 397B | 224 GB | [mlx-community/Qwen3.5-397B-A17B-4bit](https://huggingface.co/mlx-community/Qwen3.5-397B-A17B-4bit) |
| Qwen3.5-397B-A17B, 6 bit | 397B | 323 GB | [lmstudio-community/Qwen3.5-397B-A17B-MLX-6bit](https://huggingface.co/lmstudio-community/Qwen3.5-397B-A17B-MLX-6bit) |

Qwen3-Coder-Next is a sparse mixture of experts model built for agentic coding: 512
experts with 10 activated per token plus one shared expert, which is where the roughly 3
billion active parameters come from. The experts that are not selected still occupy
storage and, in an ordinary fully resident setup, memory.
[Qwen3-Coder-Next technical report](https://arxiv.org/html/2603.00729v1)

Coder Next at 44.8 GB plus the 122B model at 69.6 GB totals 114.4 GB of weights, which is
where "about 114 gigabytes" comes from.

## The quantization arithmetic

Quantization stores weights at lower numerical precision. Four bits is half a byte, so the
simple weight calculation for a 70 billion parameter model is 70e9 x 0.5 bytes = 35 GB,
before the extra information needed to store the quantization and run the model. That
already exceeds a 32GB card's dedicated memory.

Attention caches hold information reused while generating later tokens, and grow with
conversation length and with simultaneous requests. The exact behaviour depends on the
model architecture and the runtime, so the headroom beyond the weights is not a fixed
number.

## The alternatives

| Hardware | Memory | Bandwidth | Source |
| --- | --- | --- | --- |
| NVIDIA GeForce RTX 5090 | 32GB GDDR7, 512 bit bus | 1,792 GB/s | [NVIDIA GeForce RTX 5090](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/) |
| NVIDIA RTX PRO 6000 Blackwell Workstation Edition | 96GB GDDR7 with ECC, 512 bit bus | 1,792 GB/s, about 1.8 TB/s | [NVIDIA RTX PRO 6000 Blackwell Workstation Edition](https://www.nvidia.com/en-us/products/workstations/professional-desktop-gpus/rtx-pro-6000/) |
| NVIDIA DGX Spark | 128GB LPDDR5x unified, 256 bit interface | 273 GB/s | [NVIDIA DGX Spark](https://www.nvidia.com/en-us/products/workstations/dgx-spark/) |
| AMD Ryzen AI Max+ 395 | Up to 128GB unified, up to 96GB assignable to graphics via Variable Graphics Memory | LPDDR5X | [AMD Ryzen AI Max+ 395](https://www.amd.com/en/products/processors/laptop/ryzen/ai-max.html) |

## Caveats carried into the video

- Apple's "up to 4x the M3 Ultra" figure is a manufacturer result for prompt processing in
  LM Studio. It is not a claim about completing a whole coding task.
- The Tom's Hardware throughput multiplier is for one dense model at one quantization on
  one test. It is not established for a large mixture of experts model.
- The thermal observation and the export timing are one reviewer's experience with one
  workload, not guarantees.
- A published package size is not the memory a running session consumes. The operating
  system, other applications, the model's working space and the attention caches all take
  a share, and the runtime affects how much is available.
- The claim that a 512GB configuration makes the 6 bit 397B package "a plausible memory
  fit" is a capacity assessment against published package sizes. It is not a measured
  speed result for that model on this chip.
{% endraw %}

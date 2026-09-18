---
layout: default
title: "Your $1,000 local AI budget can buy the wrong machine"
permalink: /best-local-ai-machines-1000/
date: 2026-09-18
---

# Your $1,000 local AI budget can buy the wrong machine

{% raw %}
Sources for every figure this video puts on screen. Prices are US dollars and exclude
sales tax and shipping. A complete machine budget assumes an existing display, keyboard
and mouse. Asking prices, launch prices and published file sizes are different kinds of
evidence, and availability is never inferred from an indexed price.

Checked 16 and 17 September 2026.

## Graphics cards

| On screen | Figure | Source |
| --- | --- | --- |
| $780 card | Newegg lists MSI Shadow RTX 5060 Ti 16GB at $779.99 and Ventus 16GB at $799.99 | [Newegg RTX 5060 Ti 16GB listings](https://www.newegg.com/p/pl?N=100+100007709&d=5060+ti+16gb+gpu&isdeptsrh=1) |
| $429 launch price | NVIDIA announced the RTX 5060 Ti 16GB at $429 at launch | [NVIDIA Blackwell GeForce RTX pricing release](https://investor.nvidia.com/news/press-release-details/2025/NVIDIA-Blackwell-GeForce-RTX-Arrives-for-Every-Gamer-Starting-at-299/default.aspx) |
| 16 GB on the card | NVIDIA specifies 16GB on the RTX 5060 Ti 16GB | [NVIDIA RTX 5060 Ti specifications](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5060-family/) |
| RTX 3090, 24 GB, about $1,500 | NVIDIA specifies 24GB. eBay shows used asking prices of $1,499 and $1,500 | [NVIDIA RTX 3090 specifications](https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090-3090ti/), [eBay RTX 3090 listings](https://www.ebay.com/b/NVIDIA-GeForce-RTX-3090-24GB-GDDR6-Graphics-Cards/27386/bn_7117810176) |
| RTX 3060, 12 GB | NVIDIA specifies both 12GB and 8GB variants of the RTX 3060 | [NVIDIA RTX 3060 family specifications](https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3060-3060ti/) |
| Intel Arc B580, 12 GB, about $300 | Intel specifies 12GB; Micro Center lists a Sparkle B580 at $299.99 | [Intel Arc B series launch](https://www.intel.com/content/www/us/en/newsroom/news/intel-launches-arc-b-series-graphics-cards.html), [Micro Center listing](https://www.microcenter.com/product/688703/intel_arc_b580_titan_overclocked_dual_fan_12b_gddr6_pcie_40_graphics_card) |
| Radeon RX 9060 XT 16 GB, about $500 | Newegg lists a Sapphire Pulse at $499.99 and an ASRock Challenger at $519.99 | [Newegg RX 9060 XT 16GB listings](https://www.newegg.com/p/pl?d=rx+9060+xt+16gb) |

## Complete machines

| On screen | Figure | Source |
| --- | --- | --- |
| Legion T5, $799, sold | OfferUp listing: i7-11700F, RTX 3060 12GB, 16GB DDR4, $799, marked SOLD | [Sold Lenovo Legion T5 listing](https://offerup.com/item/detail/4ec79319-3219-3089-9205-81d3fc6dd1fd) |
| $700 to $800 hunting range | Two further sold RTX 3060 towers at $799 and $699, both with 32GB and a 1TB SSD | [Spokane listing](https://offerup.com/item/detail/9c9a1c10-7ed3-3570-bd41-893e35856584), [Glendale listing](https://offerup.com/item/detail/6b468e15-792b-3576-b28c-39f621773e5b) |
| M6 mac mini, $899, 16 GB, September 22 | Apple announced the M6 mini on 25 August: $899 starting price, 16GB standard memory, preorder with deliveries from 22 September | [Apple Mac mini announcement](https://www.apple.com/newsroom/2026/08/apple-unveils-a-more-powerful-mac-mini-featuring-the-all-new-m6-and-m5-pro/) |
| Up to 4.8 times faster | Apple reports up to 4.8x faster LLM **prompt processing** versus M4 in its own test. That is reading the request, not finishing a coding task | [Apple Mac mini announcement](https://www.apple.com/newsroom/2026/08/apple-unveils-a-more-powerful-mac-mini-featuring-the-all-new-m6-and-m5-pro/) |
| Used M4 mini with 24 GB | Apple documents 16GB base with 24GB and 32GB configurations | [Apple M4 mini specifications](https://support.apple.com/en-us/121555) |
| GMKtec K8 Plus, $400 barebone | Manufacturer page: $399.99 selected barebone, no RAM, storage or OS. Ryzen 7 8845HS, Radeon 780M, two DDR5 SO-DIMM slots | [GMKtec K8 Plus](https://www.gmktec.com/products/gmktec-nucbox-k8-plus-mini-pc-amd-ryzen%E2%84%A2-7-8845hs) |
| EVO X1 Pro, $1,600 | Official US catalog: $1,599.99 starting price, Ryzen AI 9 HX 470 | [GMKtec EVO X1 Pro](https://www.gmktec.com/products/gmktec-evo-x1-pro-ai-mini-pc-amd-ryzen-ai-9-hx-470) |
| EVO X2, above $2,000 | Official US catalog: $2,199.99 starting price, Ryzen AI Max+ 395 | [GMKtec EVO catalog](https://www.gmktec.com/collections/evo-series) |

The $1,000 figure, the $900 reserve for a K8 Plus build and the $900 ceiling on a used M4
mini are the video's own editorial limits, not prices quoted by anyone.

## Models and file sizes

Sizes are the decimal GB the quantization publisher displays. They are weights on disk and
exclude the KV cache, runtime buffers and any separate vision projector. Hardware capacity
is often quoted in binary units, so 16 GiB is about 17.18 decimal GB and a 16.5 GB file
does not by itself prove the weights exceed a 16 GB card. The constraint the video states
is the remaining headroom, not the arithmetic.

| On screen | Figure | Source |
| --- | --- | --- |
| Qwen 3.5 9B, nine billion | Official Qwen model, 9B dense | [Qwen3.5 9B model card](https://huggingface.co/Qwen/Qwen3.5-9B) |
| 17.9 GB and 5.68 GB | Unsloth publishes BF16 at 17.9 GB and Q4_K_M at 5.68 GB | [Qwen3.5 9B GGUF listing](https://huggingface.co/unsloth/Qwen3.5-9B-GGUF/tree/main) |
| Ministral 3, 8B and 14B, 8.24 GB | Official Mistral compact instruct family; Unsloth 14B Q4_K_M is 8.24 GB | [Ministral 3 14B](https://huggingface.co/mistralai/Ministral-3-14B-Instruct-2512), [GGUF listing](https://huggingface.co/unsloth/Ministral-3-14B-Instruct-2512-GGUF/tree/main) |
| DeepSeek R1 distilled Qwen 14B | Official DeepSeek distillation built on Qwen, and not the DeepSeek service | [DeepSeek R1 Distill Qwen 14B](https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Qwen-14B) |
| Qwen 3.8 27B, released august, 16.5 GB | August 2026 release, dense 27B; Unsloth UD-Q4_K_M is 16.5 GB | [Qwen3.8 27B model card](https://huggingface.co/Qwen/Qwen3.8-27B), [GGUF listing](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF/tree/main) |
| Devstral Small 2, 24 billion, 14.3 GB | Mistral software engineering model; Unsloth Q4_K_M is 14.3 GB | [Devstral Small 2](https://huggingface.co/mistralai/Devstral-Small-2-24B-Instruct-2512), [GGUF listing](https://huggingface.co/unsloth/Devstral-Small-2-24B-Instruct-2512-GGUF/tree/main) |
| Qwen3 Coder 30B, 18.6 GB | Coding and tool use model; Unsloth Q4_K_M is 18.6 GB | [Qwen3 Coder 30B GGUF listing](https://huggingface.co/unsloth/Qwen3-Coder-30B-A3B-Instruct-GGUF/tree/main) |
| Qwen3 Coder Next, 80 billion total, 3 billion active | Official card: 80B total, 3B active per token | [Qwen3 Coder Next](https://huggingface.co/Qwen/Qwen3-Coder-Next) |
| DeepSeek V4 Flash, 284 billion | Official card: 284B total | [DeepSeek V4 Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) |
| Kimi K3, 2.8 trillion | Official card: 2.8T total | [Kimi K3](https://huggingface.co/moonshotai/Kimi-K3) |
| 61.7% and 68.0% | Qwen reports 61.7 on SWE bench Pro for Qwen3.8 27B; Mistral reports 68.0% on SWE bench Verified for Devstral Small 2. Different benchmarks and setups, so the two do not rank against each other | Qwen and Mistral published evaluations on the model cards above |

## Memory, bandwidth and runtime support

- A model's weights are only part of what has to be resident. Working buffers and the
  conversation's KV cache are additional, and the cache grows with the amount of code held
  in context. [llama.cpp](https://github.com/ggml-org/llama.cpp) documents the
  quantization formats, the backends and hybrid CPU and GPU operation this depends on.
- On a discrete card, VRAM is dedicated to that card. On Apple silicon the CPU and GPU
  share one unified pool with the operating system and running applications, so installed
  memory is not memory available to a model.
  [Apple M4 mini specifications](https://support.apple.com/en-us/121555)
- Shared DDR capacity and dedicated graphics bandwidth solve different constraints.
  Capacity lets a larger model load; bandwidth is what each round trip pays.
- Ollama's matrix lists the RTX 3060, 3090 and 5060 Ti. Its AMD ROCm list on linux
  includes the RX 9060 XT and Ryzen AI HX 470; the Radeon 780M is absent from the standard
  listed devices, and the windows list differs. Absence from the matrix does not prove an
  override or a different runner cannot work.
  [Ollama GPU support matrix](https://docs.ollama.com/gpu)
- Intel documents a llama.cpp installation route for B series cards.
  [Intel llama.cpp guide](https://github.com/intel/ipex-llm/blob/main/docs/mddocs/Quickstart/llama_cpp_quickstart.md)
- MLX provides quantized inference on Apple silicon alongside Metal.
  [MLX LM](https://github.com/ml-explore/mlx-lm)

## Screenshots used on screen

One Hugging Face file listing appears as a captured page rather than a redrawn figure, so
the size on screen is the publisher's own:

- [unsloth/Qwen3.8-27B-GGUF, files and versions](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF/tree/main)

## Not established here

- No tokens per second, latency or throughput result is claimed for any machine. The fit
  judgements are estimates from published model sizes, memory capacity and documented
  runtime support.
- The timing comparison late in the video is a method to run, not a measurement that was
  taken. The two bars illustrate how total time to a passing test can invert a per reply
  speed advantage; they are not results.
- Retailer and marketplace listings are prices displayed on the dates checked, not
  guaranteed stock and not the minimum obtainable price. Sold listings are asking prices,
  not confirmed transaction prices.
- The memory splits drawn in the capacity beats are representative allocations for a
  desktop with an editor and tests open, not measurements of a particular machine.
- Ollama listing a device means the runner supports it, not that every model runs well on
  it.
{% endraw %}

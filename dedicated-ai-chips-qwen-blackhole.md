---
layout: default
title: "AI chips hit 17,000 tok/s. Should you ditch GPUs?"
permalink: /dedicated-ai-chips-qwen-blackhole/
date: 2026-09-28
---

# AI chips hit 17,000 tok/s. Should you ditch GPUs?

{% raw %}
Checked 27 September 2026.

## Taalas HC1

- **17,000 tokens per second, per user, Llama 3.1 8B.** Taalas: "Taalas' silicon Llama achieves 17K tokens/sec per user". Its products page says "delivering 17k tokens per second per user on Llama 3.1 8B", and its chart note gives "Input sequence length 1k/1k". The chart bar reads 16,960.
  https://taalas.com/the-path-to-ubiquitous-ai/ · https://taalas.com/products/
- **A thousand tokens in about six hundredths of a second.** This is arithmetic on the figure above: 1,000 ÷ 17,000 = 0.059 s.
- **The model is hardwired into the silicon.** Taalas: "our first product: a hard-wired Llama 3.1 8B". The figure caption reads "Taalas HC1 hard-wired with Llama 3.1 8B model".
- **Storage and computation brought together.** Taalas, "Merging storage and computation": "By unifying storage and compute on a single chip, at DRAM-level density…"
- **Quality relative to GPU benchmarks.** Taalas: "aggressively quantized, combining 3-bit and 6-bit parameters, which introduces some quality degradations relative to GPU benchmarks."
- **A technology demonstrator, a chatbot, API access on request, a 2.5 kW server.** From the products page, under "Taalas HC1 Technology Demonstrator": "Runs Llama 3.1 8B", "2.5 kW Server", "Try our chatbot", "Request API access".

## Tenstorrent Blackhole and QuietBox 2

- **Four Blackhole chips on two accelerator cards.** The product page says QuietBox 2 is "Powered by 2 Blackhole p300c" and "combines four Tenstorrent Blackhole® Tensix Processors". The QB2 guide lists "4× Blackhole® (2× p300c cards)".
  https://tenstorrent.com/en/hardware/tt-quietbox · https://docs.tenstorrent.com/tt-quietbox2-guide/
- **128 GB of accelerator memory.** The QB2 guide lists "128 GB GDDR6 total (32 GB/chip)". The specifications page lists "128GB (64GB + 64GB) GDDR6".
- **About 2 TB/s of aggregate memory bandwidth.** Specifications: "2,048 GB/s total (1,024 GB/s per card); 512 GB/s per Blackhole ASIC".
  https://docs.tenstorrent.com/systems/quietbox/quietbox-bh-2/specifications.html
- **Qwen3-32B is a supported QuietBox model.** The QB2 guide, "What's Running on QB2": "Supported · Text Generation · Qwen3-32B". The tt-inference-server hardware table rates the same model "Functional".
  https://github.com/tenstorrent/tt-inference-server/blob/main/docs/model_support/models_by_hardware.md
- **The weights and compiled kernels ship on the machine.** The QB2 guide, "Use the Model That's Already on Your Box": "Your QB2 shipped with Qwen3-32B on disk, and not just the weights". It lists the weights at ~62 GB and the compiled Blackhole kernels at ~30 GB.
  https://docs.tenstorrent.com/tt-quietbox2-guide/read/
- **An API compatible with the OpenAI client format.** The QB2 guide: "Serving models via HTTP, OpenAI-compatible API, runs vLLM in a container". A separate section says "Use this to run a model as a server with an OpenAI-compatible HTTP API."
- **Text, image, video and speech workloads.** The QB2 guide's model list covers text generation, text to image, text to video, text to speech and speech to text. The tt-inference-server README groups models by type: LLM, VLM, video, image, audio and TTS.
  https://github.com/tenstorrent/tt-inference-server
- **The model repository lists Qwen, Llama, DeepSeek distillations and Mistral.** The tt-metal models README, LLMs section, lists "Qwen 3 32B", "DeepSeek R1 Distill Llama 3.3 70B", Llama models and "Mistral 7B".
  https://github.com/tenstorrent/tt-metal/blob/main/models/README.md
- **Some newer models are marked experimental.** The QB2 guide marks "Experimental · Qwen3.6-27B", gpt-oss-120b and Gemma variants.
- **$9,999.** Product page: "Starting at $9,999". QB2 guide: "$9,999".
- **931 tokens per second combined, batch 32, 29.1 per user, sequence length 686.** The tt-metal file `models/model_targets.yaml`, entry `qwen3-32b` → `p300x2`, commented "# p300x2 == bh_quietbox_2", has `batch_size: 32`, `seq_len: 686`, `decode_t/s/u: 29.1` and `decode_t/s: 931`. Its comment reads: "runs 33710384109 (main) and 33967118837 both measured 931 / 29.1".
  https://github.com/tenstorrent/tt-metal/blob/main/models/model_targets.yaml
- **Liquid cooling.** Product page: "TT-QuietBox® 2 is a liquid-cooled AI workstation". Specifications: "Cooling: Liquid + Forced air" and "Sound pressure: 38 dBA (under max operating load)".
- **Power boundaries.** Specifications: "Total Board Power: Up to 1100W (550W + 550W)". The QB2 guide lists PSU 1,600 W and peak draw of about 1,500 W.

## NVIDIA DGX Spark

- **128 GB and 273 GB/s.** NVIDIA: "128 GB LPDDR5x unified system memory, 256-bit interface, 4266 MHz, 273 GB/s bandwidth".
  https://docs.nvidia.com/dgx/dgx-spark/hardware.html
- **The bandwidth ratio.** 2,048 ÷ 273 ≈ 7.5. This is arithmetic, not a performance ratio.

## Qwen3 technical report

- **LiveCodeBench v5: Qwen3-32B 65.7, DeepSeek-R1-Distill-Llama-70B 54.5, OpenAI o3-mini (medium) 66.3.** Table 13, "Comparison among Qwen3-32B (Thinking) and other reasoning baselines". The same table lists Qwen3-32B's architecture as dense.
  https://arxiv.org/abs/2505.09388
- **Thinking and direct answers.** The report describes "integration of thinking mode … and non-thinking mode" with "dynamic mode switching". The Qwen3-32B model card documents the `enable_thinking` switch.
  https://huggingface.co/Qwen/Qwen3-32B

## Qwen3.8-27B and Opus 4.6 Max

- **SWE-bench Pro: Qwen3.8-27B 61.7, Opus4.6 Max 53.4.** From the Qwen3.8-27B model card, Benchmark Results, Text Performance, Agentic coding row.
- **Mixed evaluations.** Model card footnote: "Except for Opus4.6 Max, which uses the officially reported score, all models are evaluated with the Claude Code harness … Problematic tasks were corrected, and all baseline models were re-evaluated on the refined benchmark."
  https://huggingface.co/Qwen/Qwen3.8-27B

## AMD

- **51.8 tokens per second on Radeon AI PRO R9700, 24.5 on Ryzen AI Max+ 395, for Qwen3.8 27B.** AMD: "up to 24.5 tokens per second on AMD Ryzen™ AI Max+ 395 and up to 51.8 tokens per second on a single AMD Radeon™ AI PRO R9700."
- **Preliminary, llama.cpp on Windows, multi token prediction, different draft settings.** AMD: "These preliminary results were measured on Windows using the popular llama.cpp project with the Vulkan backend, with MTP=4 on Ryzen AI Max+ 395 and MTP=2 on Radeon AI PRO R9700". The footnotes add "Testing as of August 2026".
  https://www.amd.com/en/blogs/2026/run-qwen-3-8-27b-on-amd-ryzen-ai-max-and-radeon-graphics-cards-day-0.html
- **Generation time.** 1,000 ÷ 51.8 = 19.3 s and 1,000 ÷ 24.5 = 40.8 s. This is arithmetic at a sustained rate, not a measured run.

## Axelera Europa

- **Launched September 2026.** "Eindhoven, September 15, 2026".
  https://axelera.ai/news/axelera-ai-launches-europa-delivers-physical-and-enterprise-ai-through-growing-partner-ecosystem-including-dell-and-supermicro
- **45 W card power envelope; Qwen3-30B-A3B at 53.5 tokens per second.** The Axelera home page spec block lists "TDP 45 W per card", "Typical power 30-40 W", "Memory up to 64 GB per chip", "LLM capacity up to 32B parameters" and "Qwen3-30B-A3B 53.5 tokens/s". The Europa product page gives "45 Watts TDP".
  https://axelera.ai/ · https://axelera.ai/ai-accelerators/aipu/europa
- **Simulated, pre-silicon, 1,024-token context, 8-bit weights and activations.** Axelera footnote: "Axelera performance engineering, confirmed 1 Sep 2026. The Qwen3-30B-A3B figure is a pre-silicon simulation: 1,024-token context at W8A8 with an 8-bit KV cache, single user, one chip."

## Qwen3-30B-A3B

- **Mixture of experts, about 3 billion active parameters per token.** The model card lists "Number of Parameters: 30.5B in total and 3.3B activated", "Number of Experts: 128" and "Number of Activated Experts: 8".
  https://huggingface.co/Qwen/Qwen3-30B-A3B

## Etched

- **First silicon and customer validation of a rack-scale system.** Etched: "Earlier this year our A0 silicon came back from TSMC N4P, and today we are busy validating our first rack-scale product with customers."
  https://www.etched.com/
- A later entry on Etched's progress page, dated 18 August 2026, says: "We shipped our first rack to Jane Street."
  https://www.etched.com/progress

## The GPU route

- **Qwen's documentation points to Ollama and llama.cpp.** The "Run Locally" section of the Qwen docs lists llama.cpp, Ollama, LM Studio and MLX LM.
  https://qwen.readthedocs.io/en/latest/
- **RTX 5090, 32 GB.** NVIDIA: "Standard Memory Config 32 GB GDDR7".
  https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/
- **32 billion parameters at 4 bits is about 16 GB.** 32 × 10⁹ × 4 bits ÷ 8 = 16 × 10⁹ bytes. This is ideal storage only; real files, context and working buffers add more.

## Example timings

The 20 s, 10 s, 12 s, 30 s and 36 s repair timings are illustrative examples, as the narration says. They are not measurements.
{% endraw %}

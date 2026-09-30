---
layout: default
title: "Your Next Local AI Upgrade Could Already Be Free"
permalink: /local-ai-september-2026-news/
date: 2026-09-30
---

# Your Next Local AI Upgrade Could Already Be Free

{% raw %}
All sources were checked on 29 Sep 2026. Company figures are the company's own claims unless stated otherwise.

## Chapter 1 · The biggest number is a promise, not a download

### Alibaba Apsara Conference 2026 · Qwen roadmap

* Alibaba says Qwen 4 "is currently in training" and that the Qwen 4.5 and Qwen 5 series are "projected to scale up to 5 to 10 trillion parameters." No release date is given for any of them.
  Source: Alizila (Alibaba Group news), "Alibaba Cloud's 2026 Apsara Conference: Full Stack AI Roadmap Along with Global Market Expansion Plan", published 24 Sep 2026 · https://www.alizila.com/alibaba-clouds-2026-apsara-conference-full-stack-ai-roadmap-along-with-global-market-expansion-plan/
* The conference and chip reveal took place on 22 Sep 2026 in Hangzhou (secondary reporting) · https://technode.com/2026/09/22/t-head-unveils-zhenwu-v900-ai-chip-in-alibabas-push-to-expand-its-ai-infrastructure-stack/

### Zhenwu V900 accelerator

* `T-Head`, Alibaba's chip design unit, unveiled the Zhenwu V900 for AI training and inference: 216 GB of GPU memory and 1,200 GB/s of interchip bandwidth, with native FP8 and FP4 support, three times the performance of the Zhenwu M890.
* "It is scheduled for mass production and commercial release in the first quarter of 2027."
* Alibaba's upgraded supernode server integrates the V900 and supports "a supernode cluster comprising up to 500,000 cards."
* Alibaba presents the chip and the Qwen roadmap together as parts of one full stack strategy. The release does not state a direct link between the V900 and any specific future Qwen model, its memory needs or whether its weights will be published.
  Source: Alizila, 24 Sep 2026 (same URL as above).

### Qwen3.8 Flash Next

* Released 26 Aug 2026. "A 125B parameter main model, supplemented by an additional 51B N gram embeddings, with 6B parameters activated per token."
* "The embedding table can be offloaded to host memory and overlapped with model computation through asynchronous prefetching."
* Described as "an early preview of the architecture used in Qwen4."
  Source: QwenLM GitHub repository · https://github.com/QwenLM/Qwen3.8-Flash-Next
* Qwen blog post · https://qwen.ai/blog?id=qwen3.8-flash-next

## Chapter 2 · DeepSeek made "flash" a very large word

### Release and architecture

* Released 10 Sep 2026. DeepSeek calls it "the smallest model in our new architecture family, with native visual understanding."
  Source: DeepSeek API news, "`DeepSeek-V4.1-Flash`: Smarter, Faster, More Efficient", 10 Sep 2026 · https://api-docs.deepseek.com/news/news260910/
* Model card: "a multimodal Mixture of Experts (MoE) model with 552B backbone parameters and support for contexts of up to one million tokens. The model natively processes images and text."
* Causal Encoder Decoder (CED) architecture: a 40 layer Transformer made of a 20 layer causal encoder and a 20 layer decoder, activating "8B parameters per token during prefill and 16B during decode."
* License: MIT.
  Source: Hugging Face model card · https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash

### Checkpoint size

* The files in the official Hugging Face repository total 510.3 GB (475.3 GiB) across 95 files, measured from the Hub file listing on 29 Sep 2026. The Hub's safetensors metadata reports 763B stored parameters in total; the 552B figure is the backbone.
  Source: https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash/tree/main

### Benchmarks (DeepSeek's own evaluation)

* Terminal Bench 2.1 (Pass@1): V4.1 Flash 90.6 · V4 Pro 87.9 · V4 Flash 82.7.
* DeepSWE v1.1 (Resolved): V4.1 Flash 74.2 · V4 Pro 62.7 · V4 Flash 54.4.
* Code agent benchmarks use the Minimal mode of DeepSeek Harness with a 1M token context; DeepSWE v1.1 uses the `mini-SWE` harness. Sampling at temperature 1.0, top_p 0.95.
  Source: Hugging Face model card, agentic results table (same URL as above).

### KV cache

* DeepSeek API news: compared with the previous generation, V4.1 Flash needs "1/4 the HBM" and "1/8 the SSD storage" for its KV cache.
* Model card detail: FP4 main KV caching brings the global KV cache footprint to 890 bytes per token, "roughly 1/4 of `DeepSeek-V4-Flash`"; SWA Bounded Replay reduces the persistent KV cache footprint "to roughly 1/8 of that of `DeepSeek-V4-Flash`."
  Sources: https://api-docs.deepseek.com/news/news260910/ · https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash

### API name, retired names and prices

* "Change the model name to `deepseek-flash` to call the latest V4.1 Flash model."
* "The previous generation models V4 Flash and V4 Flash Vision Exp have been retired; for compatibility, the model names `deepseek-v4-flash` and `deepseek-v4-flash-vision-exp` are temporarily routed to V4.1 Flash."
* "With the release of `DeepSeek-V4.1-Flash`, API prices have been reduced accordingly." New pricing took effect at 04:00 UTC on 10 Sep 2026; off peak rates are 50% of peak rates.
  Sources: DeepSeek API change log, 10 Sep 2026 · https://api-docs.deepseek.com/updates/ · news page above
* Current `deepseek-flash` prices per 1M tokens (off peak / peak): input cache hit $0.003 / $0.006 · input cache miss $0.15 / $0.30 · output $0.60 / $1.20. Context 1M tokens.
  Source: https://api-docs.deepseek.com/quick_start/pricing

### Community runs on local hardware

* Three Apple M5 Max Macs, 128 GiB per machine, custom MLX runtime over Thunderbolt with RDMA, native weights: 31.94 tok/s on the first run and 35.70 and 35.49 tok/s on two warmed runs of a fixed 384 token output test, single request. First token on a fresh prompt took 613 s; with prefix reuse 1.75 s. Posted by GitHub user Jackten, 12 Sep 2026.
  Source: MLX GitHub discussion #4491 · https://github.com/ml-explore/mlx/discussions/4491
* Four DGX Spark systems with vLLM, tensor parallel 4, MXFP4: 77.2 tok/s peak single stream on one workload, 214 tok/s aggregate at 6 streams. Posted by tonyd615, 10 Sep 2026.
  Source: NVIDIA Developer Forums · https://forums.developer.nvidia.com/t/deepseek-v4-1-flash-552b-moe-on-4x-dgx-spark-tp4-77-2-tok-s-c1-on-peak-52-code-72-tok-s-on-a-warm-code-run-47-math-39-reasoning-23-prose/382897
* Further DGX Spark threads · https://forums.developer.nvidia.com/t/deepseek-v4-1-flash/382725

## Chapter 3 · Qwen gave local image tools a useful new trick

### Qwen Image 2.1

* "2026.09.20: We released `Qwen-Image-2.1`!" Weights on Hugging Face and ModelScope.
* "With just 7B parameters in its visual generation component (32 Single Stream DiT layers)", unifying text to image generation and image editing.
* "Generate regular or transparent (RGBA) images from text, edit transparent layers, and extract subjects from photographs, all in one model."
* "Support up to 10 reference images."
* "This repository is licensed under the Qwen Research License Agreement." The Hugging Face license tag is `qwen-research`.
  Sources: GitHub README · https://github.com/QwenLM/Qwen-Image-2.1 · Hugging Face · https://huggingface.co/Qwen/Qwen-Image-2.1 · Qwen blog, 20 Sep 2026 · https://qwen.ai/blog?id=qwen-image-2.1

### Qwen Image Bench

* Qwen's own chart gives Qwen Image 2.1 an overall score of 60.28. In that same chart six systems score higher: GPT Image 2.5 Sunburst 67.01 · GPT Image 2 64.69 · Grok Imagine 2.0 63.47 · Qwen Image 3 Pro 62.36 · Muse Image 62.34 · MAI Image 2.5 Pro 61.02. Qwen Image 2.1 is just above Nano Banana 2.0 (59.82) and is the highest scoring model in the chart whose parameter count is disclosed.
  Source: Qwen blog benchmark figure · https://qwen.ai/blog?id=qwen-image-2.1 · image https://qianwen-res.oss-accelerate.aliyuncs.com/Qwen-Image/image2.1/images/example-01.png

### Qwen3.8 Omni Flash Realtime and Qwen Live Harness

* Qwen3.8 Omni Flash launched 18 Sep 2026; Qwen3.8 Omni Flash Realtime "perceives and responds while receiving live audio visual streams, and uses real time context to call tools and execute tasks." Both are offered as APIs. Qwen says it has "open sourced Qwen Live Harness as a native runtime for continuous, real time omnimodal interaction."
  Source: Qwen blog, 18 Sep 2026 · https://qwen.ai/blog?id=qwen3.8-omni-flash
* The harness is "an open source harness built around the Qwen Omni Realtime API" that brings "realtime audio/video interaction, background task delegation, proactive interaction, and long term memory to your desktop." v1.0.0 released 21 Sep 2026. It "requires an internet connection to the Alibaba Cloud Model Studio DashScope API, but no local model weights or GPU." Background harnesses include Qwen Code, Qoder CLI, Codex, Claude Code and Gemini CLI.
  Source: https://github.com/QwenLM/Qwen-Live-Harness

### Qwen3.8 LiveTranslate

* Published 18 Sep 2026. "Average lagging (LAAL) drops from 2.8 seconds to 2.3 seconds." Adds "real time speaker separation", "synchronized source and translation output on one bilingual screen" and "long context disambiguation … making names and terminology more precise." Supports 60 languages. Offered through an API and demo.
  Source: Qwen blog · https://qwen.ai/blog?id=qwen3.8-livetranslate

## Chapter 4 · The fastest upgrade may be the one you already own

### NVIDIA runtime optimizations

* "Up to 1.9x faster local inference · new llama.cpp and vLLM optimizations are available now directly and through LM Studio and Ollama."
* Detail: "llama.cpp delivers up to 1.9x higher throughput through kernel optimizations on a GeForce RTX 5090, enhanced speculative decoding techniques and faster prefill." vLLM "delivers 1.2x on RTX PRO 6000 Blackwell Workstation Edition and up to 1.4x on two DGX Spark clusters."
* One click local model setup is coming in Hermes Agent, OpenClaw and Perplexity Portable Computer.
  Source: NVIDIA Blog, "Sparks Fly: NVIDIA Accelerates Local AI at IFA 2026", 3 Sep 2026 · https://blogs.nvidia.com/blog/local-ai-ifa-next-gen-agents-nv-pair-rtx-spark/

### NVIDIA PAIR (Personal AI Router)

* A "free, open source" tool that discovers compatible PCs on a local network and routes independent inference requests to whichever system has capacity, working with existing Ollama and LM Studio interfaces.
* Supported: GeForce RTX 20 Series and newer, RTX PRO workstation GPUs (Turing and newer), DGX Spark, and Apple M4 or newer silicon, on Windows, macOS and Linux.
* Demo: with Qwen 3.6 35B A3B, a five subagent Hermes workload took 18 minutes on average on one RTX Spark laptop; a three device PAIR cluster (RTX Spark laptop, DGX Spark, RTX 5090) took 8 minutes 48 seconds. NVIDIA calls it "an unofficial, configuration specific demo, not a general benchmark or a promise of linear scaling."
  Sources: NVIDIA Technical Blog, 3 Sep 2026 · https://developer.nvidia.com/blog/nvidia-pair-virtual-inference-router-expands-available-compute-on-your-local-network · NVIDIA Blog above

### RTX Spark

* "New NVIDIA RTX Spark Windows PCs arriving in October." RTX Spark has "a powerful 1 Petaflop RTX Blackwell GPU, up to 128GB of unified memory and a highly efficient 20 core Grace CPU" and enables "thin laptops … and compact desktops." At IFA, Acer showed a compact desktop RTX Spark concept and Lenovo announced the Yoga Pro 9n and Yoga 9n 2 in 1.
  Source: NVIDIA Blog, 3 Sep 2026 (URL above)

## Chapter 5 · Apple made its small desktop faster and its ceiling clearer

### Mac mini with M6 and M5 Pro

* Announced 25 Aug 2026; available from 22 Sep 2026.
* "With M6, Mac mini now delivers up to 4x faster AI performance" than Mac mini with M4.
* M6: "Up to 4.8x faster" LLM prompt processing in LM Studio than M4 (13.5x versus M1). Baseline: Mac mini with M4, 10 core CPU, 10 core GPU, 32GB, 2TB. Testing by Apple in July 2026.
* M6: "16GB of standard unified memory configurable up to 32GB", memory bandwidth up to 170GB/s. From $899.
* M5 Pro: "up to 64GB of unified memory with 307GB/s of memory bandwidth"; up to 4x faster LLM prompt processing in LM Studio than M4 Pro. From $1,699.
  Sources: Apple Newsroom, 25 Aug 2026 · https://www.apple.com/newsroom/2026/08/apple-unveils-a-more-powerful-mac-mini-featuring-the-all-new-m6-and-m5-pro/ · Apple Newsroom, 22 Sep 2026 · https://www.apple.com/newsroom/2026/09/the-new-mac-mini-and-mac-studio-are-available-today/

### Mac Studio with M5 Max and M5 Ultra

* Available 22 Sep 2026. M5 Max: 18 core CPU, up to 40 core GPU, "up to 128GB of unified memory." M5 Ultra: up to 36 core CPU, up to 80 core GPU, "up to 512GB of unified memory with 1.2TB/s of memory bandwidth."
* "Mac Studio with 512GB of unified memory is coming in late October."
* "Thunderbolt 5 with Remote Direct Memory Access (RDMA) also enables multiple Mac Studio systems to be clustered, now bringing up to 3x faster performance for distributed AI inference when compared to a single system."
* M5 Max from $2,499; M5 Ultra from $5,499.
  Source: Apple Newsroom, 22 Sep 2026 (URL above)

## Chapter 6 · The mini PC wants to become your AI server

### Minisforum at IFA 2026

* Two products on the AMD Ryzen AI MAX+ PRO 495: the AI Agent NAS `N5 MAX-P495` and the AI Mini Workstation `MS-S1 MAX-P495`.
* "Up to 131 TOPS of AI compute performance, 192GB of memory at 8533 MT/s, and up to 160GB of graphics memory."
* `N5 MAX-P495` "combines powerful AI computing with up to 200TB of local storage", aimed at RAG knowledge bases, models, embeddings and agents such as OpenClaw and Hermes.
  Source: Minisforum press release, 4 Sep 2026 · https://www.minisforum.com/blogs/news/minisforum-unveils-next-gen-edge-ai-computing-solutions-powered-by-amd-ryzen-ai-max-pro-495-at-ifa-2026

### AMD and Perplexity

* "Perplexity announced that Portable Computer is available on supported Windows PCs powered by AMD Ryzen AI Max Series processors, including the AMD Ryzen AI Halo developer platform. Users can run local AI tasks and recurring workflows on their own hardware without using Perplexity Computer credits for inference."
  Source: AMD Newsroom, 24 Sep 2026 · https://newsroom.amd.com/news/amd-perplexity-agentic-pcs/

## Chapter 7 · Jev wants the model to decide, not narrate

### Jev from TypeSafe AI

* Announced 15 Sep 2026 by founder Diogo Almeida as TypeSafe's "first System One Model", in early access. "Unstructured state in, typed probabilistic decisions out."
* Pricing: "Input tokens: $0.042 / MTok ($42 per billion tokens). Output tokens: FREE (too cheap to meter)."
* Speed: "End to end response time is 70ms to 500ms … This can range from 40x to 200x faster for the same levels of frontier intelligence for System One shaped queries." The workflow evals quote 193.6x faster, which TypeSafe says is "on the higher end of real world gains."
  Source: TypeSafe AI blog, "Introducing System One Models & Jev", 15 Sep 2026 · https://typesafe.ai/blog/introducing-system-one-models-and-jev
* Input: "Text only. String, JSON object, or array of text values. No image, audio, or video input." Current model `jev-1.13.0`.
  Source: TypeSafe docs · https://docs.typesafe.ai/models

### Laya

* Open weight System One style decision model by Convai Innovations, Apache 2.0, first published 18 Sep 2026. Three checkpoints: English (ModernBERT large, 421M), multilingual (mmBERT base, 322M) and typed decisions (421M).
* The card headlines "a single forward pass (~33 ms)". Measured latency for one question on a T4 GPU: 39.5 ms for the 421M English checkpoint and 32.8 ms for the 322M multilingual checkpoint.
  Source: https://huggingface.co/convaiinnovations/laya

### Kev

* "Small Jev like decision models you can train and run yourself", Apache 2.0, by Jared Palmer. Sizes: Kev 0.8B, 4B and 9B built on Qwen3.5 base models, plus a Kev 27B built on Qwen3.8 27B. "The TypeSafe Python SDK works against a Kev server unchanged." Runs on CUDA, ROCm or MLX on Apple Silicon.
* Kev states it is not a controlled comparison with Jev: "We don't know what Jev was trained on."
  Source: https://github.com/jaredpalmer/kev

## Chapter 8 · The decision hiding behind the announcements

### GGUF in Hugging Face Transformers

* Hugging Face blog "Transformers now runs llama.cpp quants", 22 Sep 2026, by Marc Sun, Arthur Zucker and Lysandre Debut. "Our initial focus is local inference on Apple Silicon, starting with the Qwen3.5 architecture."
* File sizes for Unsloth's Qwen3.5 4B: BF16 8.42 GB · Q6_K 3.53 GB · Q5_K_M 3.14 GB · Q4_K_M 2.74 GB.
* "llama.cpp remains our recommended engine when your priority is efficient local inference."
* "The packed inference path is MPS only for now … support for the file format does not imply that packed kernels are available on every device." "The packed loader currently covers the Qwen3.5 dense and MoE architectures, including compatible Qwen3.8 checkpoints."
  Source: https://huggingface.co/blog/transformers-llama-cpp-quants

### Not checked

* The exact day of the Apsara Conference keynote rests on secondary reporting (22 Sep 2026); the Alibaba release itself gives no date.
* The Zhenwu V900 is not described in Alibaba's release as built specifically for the planned 5 to 10 trillion parameter Qwen models; that link is an interpretation.
* DeepSeek's exact old and new price table before 10 Sep 2026 was not compared; only the statement that prices were reduced and the current price list were checked.
* The community tok/s results on Apple M5 Max and DGX Spark systems were not reproduced.
* No independent test of Jev's speed or accuracy, or of Laya and Kev against Jev, was found.
* Apple and NVIDIA performance multiples are vendor figures under vendor test conditions.
{% endraw %}

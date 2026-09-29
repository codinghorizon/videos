---
layout: default
title: "Your local AI laptop choice hides a brutal 24GB trap"
permalink: /local-ai-laptop-buying-guide/
date: 2026-09-29
---

# Your local AI laptop choice hides a brutal 24GB trap

{% raw %}
All sources checked 2026-09-28. Prices are US list prices on that date unless stated.

## Model sizes and memory

- **Qwen 3.5 package sizes in Ollama: 9B 6.6GB, 27B 17GB, 35B 24GB, 122B 81GB.**
  Source: https://ollama.com/library/qwen3.5/tags
  The tags table lists `qwen3.5:9b` 6.6GB, `qwen3.5:27b` 17GB, `qwen3.5:35b` 24GB, `qwen3.5:122b` 81GB, each with a 256K context window and text plus image input.

- **gpt-oss-20b runs within 16GB; gpt-oss-120b fits on a single 80GB GPU.**
  Source: https://github.com/openai/gpt-oss (also https://huggingface.co/openai/gpt-oss-120b)
  OpenAI: gpt-oss-120b is built to "fit into a single 80GB GPU (like NVIDIA H100 or AMD MI300X)"; gpt-oss-20b can "run within 16GB of memory".

- **gpt-oss-120b: about 117B total parameters, about 5.1B active per token, mixture of experts.**
  Source: https://github.com/openai/gpt-oss
  OpenAI: "117B parameters with 5.1B active parameters"; the model uses MXFP4 quantization of its MoE (mixture of experts) weights. gpt-oss-20b is 21B total, 3.6B active.

- **About half a byte per parameter at 4 bits.**
  Source: https://huggingface.co/docs/transformers/main/en/llm_tutorial_optimization
  Hugging Face gives the rule of thumb of about 4 bytes per parameter in float32 and 2 bytes in bfloat16/float16; 4 bits is a quarter of 16 bits, so about 0.5 bytes per parameter before overhead. The same guide notes quantization "trades improved memory efficiency against accuracy".

- **The KV cache grows with context and takes memory.**
  Sources: https://huggingface.co/docs/transformers/main/en/cache_explanation and https://docs.ollama.com/faq
  Hugging Face: with a KV cache, "memory grows linearly" with sequence length. Ollama: required RAM scales with `OLLAMA_NUM_PARALLEL` × `OLLAMA_CONTEXT_LENGTH`, and the K/V cache can be quantized to reduce memory use.

## NVIDIA discrete GPU laptops

- **The fastest conventional laptop GPU has 24GB: GeForce RTX 5090 Laptop GPU, 24GB GDDR7.**
  Source: https://www.nvidia.com/en-us/geforce/laptops/50-series/
  The spec table lists the RTX 5090 Laptop GPU with 24GB GDDR7, 896GB/s, 10,496 CUDA cores.

- **An RTX 5090 laptop can run its GPU at 175W.**
  Source: https://rog.asus.com/us/laptops/rog-strix/rog-strix-scar-18-2026/spec/
  ASUS lists the Strix SCAR 18 (2026) RTX 5090 Laptop GPU at "1647MHz at 175W", with "150W+25W Dynamic Boost". NVIDIA's own page does not give a single power figure because the laptop maker sets it.

- **RTX PRO 5000 Blackwell Laptop GPU: 24GB GDDR7.**
  Source: https://www.nvidia.com/en-us/products/workstations/professional-laptops/compare/
  NVIDIA's comparison table lists 24GB GDDR7 ECC, 10,496 CUDA cores, 95–175W.

- **Lenovo ThinkPad P16 Gen 3 offers the RTX PRO 5000, replaceable memory and three drives.**
  Source: https://psref.lenovo.com/syspool/Sys/PDF/ThinkPad/ThinkPad_P16_Gen_3/ThinkPad_P16_Gen_3_Spec.pdf
  Lenovo PSREF lists "NVIDIA RTX PRO 5000 Blackwell Generation 24GB GDDR7 Laptop GPU"; memory slots "Four DDR5 SODIMM / CSODIMM slots" (up to 192GB non-ECC); storage "Three M.2 slots", "up to three M.2 2280 Gen 5 Performance SSD; up to 12TB".

- **ROG Strix SCAR 18 (2026) with an RTX 5090 starts at $4,999.99, about $5,000.**
  Source: https://rog.asus.com/us/laptops/rog-strix/rog-strix-scar-18-2026/spec/
  ASUS Store lists the RTX 5090 (24GB) models at $4,999.99 and $5,299.99. The family's "starting at $4,299.99" price belongs to the RTX 5080 (16GB) model, G835LWG.

## AMD Ryzen AI Max laptops

- **ASUS ROG Flow Z13 (2025): 13.4-inch detachable, Ryzen AI Max+ 395, up to 128GB LPDDR5X.**
  Source: https://rog.asus.com/us/laptops/rog-flow/rog-flow-z13-2025/spec/
  ASUS: "13.4-inch 2.5K (2560 x 1600)" display; "AMD Ryzen AI MAX+ 395"; "128GB LPDDR5X 8000 on board". It is sold as a 2-in-1 gaming tablet with a detachable keyboard. ASUS lists the tablet at 1.20kg (2.65 lb).

- **Flow Z13 with 128GB: $3,299.99 at the ASUS US store.**
  Source: https://rog.asus.com/us/laptops/rog-flow/rog-flow-z13-2025/spec/
  ASUS Store price for GZ302EA-XS99 (Ryzen AI MAX+ 395, 128GB LPDDR5X): $3,299.99. The 32GB and 64GB models list at $2,099.99 and $2,399.99. Press coverage reported a $2,799.99 launch price in 2025.

- **Flow Z13 weight: 3.51 lb with its keyboard.**
  Source (press, not ASUS): https://fstoppers.com/reviews/review-asus-rog-flow-z13-portable-powerhouse-photographers-creatives-and-coders-701998
  ASUS's own spec page gives the tablet alone at 1.20kg (2.65 lb).

- **HP ZBook Ultra G1a: Ryzen AI Max PRO, 14-inch mobile workstation, up to 128GB.**
  Source: https://www.hp.com/us-en/workstations/zbook-ultra.html
  HP: "14" Mobile Workstation PC", "HP's thinnest ZBook ever", "AMD Ryzen AI Max PRO Series", "Up to 128GB Unified Memory", and "assign up to 96 GB of memory exclusively to the GPU".

- **A 128GB Ryzen AI Max+ system can assign up to 96GB as graphics memory.**
  Source: https://www.amd.com/en/newsroom/press-releases/2025-1-6-amd-announces-expanded-consumer-and-commercial-ai-.html
  AMD, 6 January 2025: "up to 128GB of unified memory with up to 96GB available for graphics".

- **AMD documents models of up to 128 billion parameters running through Vulkan llama.cpp on Windows.**
  Source: https://www.amd.com/en/blogs/2025/amd-ryzen-ai-max-upgraded-run-up-to-128-billion-parameter-llms-lm-studio.html
  AMD, 29 July 2025: "enable up to 128 billion parameters in Vulkan llama.cpp on Windows ... take full use of the 96GB VGM available on a Ryzen AI MAX+ 395 128GB machine". Its example is Meta's Llama 4 Scout 109B (17B active) running in LM Studio.

- **The Ryzen AI Max NPU is rated at "50+" TOPS.**
  Sources: https://www.amd.com/en/blogs/2025/amd-ryzen-ai-max-395-processor-breakthrough-ai-.html and https://www.amd.com/en/products/processors/laptop/ryzen/ai-300-series/amd-ryzen-ai-max-plus-395.html
  AMD's March 2025 blog says "50+ peak AI TOPS XDNA 2 NPU". AMD's product spec page says "NPU TOPS: Up to 50 TOPS" (overall "Up to 126 TOPS").

- **Strix Halo memory bandwidth is 256GB/s.**
  Sources: https://www.amd.com/en/blogs/2025/amd-ryzen-ai-max-395-processor-breakthrough-ai-.html and https://www.amd.com/en/products/processors/laptop/ryzen/ai-300-series/amd-ryzen-ai-max-plus-395.html
  AMD's blog: "taking full advantage of the 256 GB/s bandwidth". The spec page lists "256-bit LPDDR5x" and "LPDDR5x-8000". At 614GB/s the M5 Max has about 2.4 times that.

## Apple MacBook Pro with M5 Max

- **M5 Max: up to 128GB unified memory, a 40-core GPU configuration, 614GB/s.**
  Source: https://www.apple.com/macbook-pro/specs/
  Apple: M5 Max with 32-core GPU "460GB/s memory bandwidth"; with 40-core GPU "614GB/s memory bandwidth"; memory up to "128GB (M5 Max with 40-core GPU)".

- **16-inch M5 Max: up to 22 hours video streaming.**
  Source: https://www.apple.com/macbook-pro/specs/
  Apple: 16-inch "Up to 22 hours video streaming" (14-inch M5 Max: up to 20 hours).

- **16-inch M5 Max, 40-core GPU, 48GB, 2TB: price, and the cost of 128GB.**
  Source: https://www.apple.com/shop/buy-mac/macbook-pro/16-inch-space-black-standard-display-apple-m5-max-chip-18-core-cpu-40-core-gpu-48gb-memory-2tb-storage
  Apple Store: "Buy for $4,999.00" (standard display, 48GB, 2TB). Memory options: 64GB "+ $400.00", 128GB "+ $2,000.00", which makes the 128GB version $6,999.00.

## Software support

- **LM Studio supports MLX on Apple silicon, alongside llama.cpp.**
  Source: https://lmstudio.ai/docs/app
  "LM Studio supports running LLMs on Mac, Windows, and Linux using llama.cpp." "On Apple Silicon Macs, LM Studio also supports running LLMs using Apple's MLX."

- **Ollama supports macOS.**
  Sources: https://ollama.com/download and https://docs.ollama.com/gpu
  Download for macOS: "Requires macOS 14 Sonoma or later". GPU doc: "Ollama supports GPU acceleration on Apple devices via the Metal API."

- **Ollama and llama.cpp support AMD through ROCm and Vulkan.**
  Sources: https://docs.ollama.com/gpu and https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md
  Ollama supports AMD GPUs via ROCm and lists the Ryzen AI Max+ 395 (gfx1151); "Additional GPU support on Windows and Linux is provided via Vulkan". llama.cpp documents Vulkan and HIP (ROCm, AMD GPU) backends.

## NVIDIA RTX Spark

- **RTX Spark: 6,144 CUDA cores (Blackwell), 20-core Grace CPU, up to 128GB unified memory, 1 petaflop FP4.**
  Sources: https://nvidianews.nvidia.com/news/nvidia-microsoft-windows-pcs-agents-rtx-spark and https://www.nvidia.com/en-us/products/rtx-spark/
  NVIDIA, 31 May 2026: Blackwell RTX GPU "with 6,144 CUDA cores", "20-core NVIDIA Grace CPU", "up to 128GB of unified memory", "1 petaflop of AI performance" (FP4 on the product page). A smaller variant has 5,120 CUDA cores and an 18-core CPU.

- **The Grace CPU is Arm based, and the platform runs Windows.**
  Source: https://nvidianews.nvidia.com/news/nvidia-microsoft-windows-pcs-agents-rtx-spark
  NVIDIA: "MediaTek, a market leader in Arm-based system-on-a-chip designs, collaborated with NVIDIA on the custom CPU design"; the machines are Windows PCs.

- **Partner laptops arrive in October 2026.**
  Source: https://blogs.nvidia.com/blog/local-ai-ifa-next-gen-agents-nv-pair-rtx-spark/
  NVIDIA, 3 September 2026: "NVIDIA RTX Spark Windows PCs Arrive October 2026", with six OEMs (ASUS, Dell, HP, Lenovo, Microsoft Surface, MSI) shipping in October. NVIDIA had not published pricing when checked.

### Not checked

- Flow Z13 weight of 3.51 lb with the keyboard. ASUS gives only the 2.65 lb tablet weight; the figure with the keyboard comes from press coverage.
- That MacBook Pro memory cannot be added after purchase. Apple offers memory only as a build-to-order option, but no Apple page checked says so in those words.
- That popular models frequently receive MLX conversions. This describes the ecosystem in general and has no single primary source.
- Relative speed claims: the RTX 5090 being faster on models that fit, and thin designs slowing once hot. These depend on the machine and were not benchmarked here.
- RTX Spark retail pricing and independent reviews. None had been published by NVIDIA or partners when checked.
{% endraw %}

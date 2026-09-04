---
layout: default
title: "192GB Just Broke The Local AI Memory Wall Open"
permalink: /192gb-just-changed-local-ai/
date: 2026-09-04
---

# 192GB Just Broke The Local AI Memory Wall Open

{% raw %}
Sources for every figure, name and benchmark this video states. Checked 2026-09-03.

## The platform

AMD's Ryzen AI Max PRO 400 series, codenamed Gorgon Halo, was announced at Computex and
ships in systems from Q3 2026. Three parts, all sharing the same memory ceiling:

| Part | Cores / threads | Cache | iGPU | CUs | NPU | TDP |
| --- | --- | --- | --- | --- | --- | --- |
| Ryzen AI Max+ PRO 495 | 16 / 32 | 80MB | Radeon 8065S | 40 | 55 TOPS | 45W to 120W |
| Ryzen AI Max PRO 490 | 12 / 24 | 76MB | Radeon 8050S | 32 | 50 TOPS | 45W to 120W |
| Ryzen AI Max PRO 485 | 8 / 16 | 40MB | Radeon 8050S | 32 | 50 TOPS | 45W to 120W |

- CPU cores are Zen 5. Graphics is RDNA 3.5. The neural processor is XDNA 2.
- Maximum unified memory is **192GB of LPDDR5X-8533** on all three parts.
- Maximum allocation to graphics memory is **160GB**, leaving 32GB for the CPU side.
- The previous generation, Strix Halo, ceilinged at 128GB.
- Launch OEMs named are ASUS, HP and Lenovo.

Sources:
- AMD, "AMD Powers Next-Generation Agent Computers with New Ryzen AI Halo Developer Platform and Ryzen AI Max PRO 400 Series Processors" — https://www.amd.com/en/blogs/2026/amd-powers-next-generation-agent-computers-with-new-ryzen-ai-hal.html
- ServeTheHome, "AMD Ups Ante With 192GB Ryzen AI Max PRO 400 Chips for AI Systems" — https://www.servethehome.com/amd-reveals-ryzen-ai-max-pro-400-series-192gb-ram-for-ai-systems/
- TweakTown, SKU table and codename — https://www.tweaktown.com/news/111752/amd-launches-the-ryzen-ai-max-pro-400-series-of-cpus-up-to-16-cores-with-192gb-of-unified-memory/index.html
- All Tech Nerd, per-SKU cores, cache, NPU TOPS and TDP — https://www.alltechnerd.com/amd-introduces-ryzen-ai-max-pro-400-gorgon-halo-processors/

## The 300 billion parameter claim

AMD's own framing is capacity, not throughput: the platform has "enough space to load up a
300B FP4 parameter model, a first for any single SoC system". FP4 is four bit, which is the
precision the claim depends on. AMD has published no inference throughput figures for a
300B model at that precision, and has not said which 300B class architectures it means.

The weight arithmetic behind it is straightforward and is the reason 192GB matters where
128GB does not: 300 billion parameters at four bits is half a byte each, so roughly
**150GB for the weights alone**, before the KV cache, the runtime and the operating system
are given anything. That is why the claim is physically plausible at 192GB and not at 128GB.

Sources:
- ServeTheHome, quoting AMD's "300B FP4 parameter model" wording — https://www.servethehome.com/amd-reveals-ryzen-ai-max-pro-400-series-192gb-ram-for-ai-systems/
- AI Weekly, "AMD Ryzen AI Max PRO 400 targets 300B local LLMs", noting the four bit precision and that throughput benchmarks and the specific architectures have not been released — https://aiweekly.co/alerts/amd-ryzen-ai-max-pro-400-targets-300b-local-llms

## What it is being compared against

| Machine | Memory | Bandwidth | Power |
| --- | --- | --- | --- |
| Ryzen AI Max+ PRO 495 | 192GB unified, up to 160GB as graphics | LPDDR5X-8533 | 45W to 120W |
| GeForce RTX 5090 | 32GB GDDR7 | 1,792 GB/s | 575W |
| RTX PRO 6000 Blackwell Workstation | 96GB GDDR7 ECC | 1,792 GB/s | 600W |
| Mac Studio, M3 Ultra | up to 512GB unified as announced | over 800 GB/s | — |
| Instinct MI300X | 192GB HBM3 | 5.3 TB/s | 750W |

- **RTX 5090**: 32GB of GDDR7 on a 512 bit bus, 1,792 GB/s, which is the "around one point
  eight terabytes per second" the video states. 21,760 CUDA cores, 575W.
- **RTX PRO 6000 Blackwell Workstation Edition**: 96GB of GDDR7 with ECC, also 1,792 GB/s
  on a 512 bit bus, 24,064 CUDA cores, and a 600W configurable TDP.
- **Mac Studio with M3 Ultra**: Apple's March 2025 announcement says it "can be configured
  up to 512GB, or over half a terabyte" with "over 800GB/s of memory bandwidth". See the
  caveat below on current availability.
- **Instinct MI300X**: 192GB of HBM3 at 5.3 TB/s on CDNA 3, a 750W data centre part. The
  capacity number matches the client chip and nothing else about it does: the bandwidth is
  roughly twenty times higher.

Sources:
- NVIDIA RTX 5090 memory and bandwidth — https://www.spheron.network/blog/nvidia-rtx-5090-specs/
- ASUS RTX 5090 technical specification — https://www.asus.com/motherboards-components/graphics-cards/tuf-gaming/tuf-rtx5090-32g-gaming/techspec/
- NVIDIA, RTX PRO 6000 Blackwell Workstation Edition — https://www.nvidia.com/en-us/products/workstations/professional-desktop-gpus/rtx-pro-6000/
- StorageReview, RTX PRO 6000 review with the 96GB ECC and 600W figures — https://www.storagereview.com/review/nvidia-rtx-pro-6000-workstation-gpu-review-blackwell-architecture-and-96-gb-for-pro-workflows
- Apple Newsroom, "Apple reveals M3 Ultra, taking Apple silicon to a new extreme" — https://www.apple.com/newsroom/2025/03/apple-reveals-m3-ultra-taking-apple-silicon-to-a-new-extreme/
- AMD, Instinct MI300X accelerator — https://www.amd.com/en/products/accelerators/instinct/mi300/mi300x.html
- Lenovo Press, ThinkSystem AMD MI300X 192GB 750W board — https://lenovopress.lenovo.com/lp1943-thinksystem-amd-mi300x-192gb-750w-8-gpu-board

### Caveat: the 512GB Mac Studio is no longer orderable

Apple's 512GB M3 Ultra configuration was real at announcement in March 2025 and the figures
quoted above are Apple's own. Some time before March 2026 Apple quietly removed it, and the
M3 Ultra Mac Studio now tops out at 256GB, with the 96GB to 256GB upgrade rising from
$1,600 to $2,000. Reporting attributes the change to the DRAM and NAND shortage.

The comparison the video draws still holds in direction, because 256GB is still above
192GB, but 512GB describes the machine as launched rather than the machine as sold today.

- Cult of Mac, "Apple quietly kills M3 Ultra Mac Studio with 512GB of memory" — https://www.cultofmac.com/news/apple-quietly-kills-512gb-m3-ultra-mac-studio-option
- Apple, current Mac Studio technical specifications — https://www.apple.com/mac-studio/specs/

## What 128GB Strix Halo already measures

The video cites two separate sets of figures, and the spread between them across the wider
body of testing is the point rather than a problem: the same model on the same silicon
moves substantially with the backend.

**A Strix Halo laptop, Ryzen AI Max+ 395 with Radeon 8060S integrated graphics.** Models
run from Qwen3-4B (3.98 GiB) through gpt-oss-20b (11.27 GiB) to gpt-oss-120b (59.02 GiB).
gpt-oss-120b generated at **35 to 40 tokens per second**, reported as 40 t/s on the Vulkan
backend. Qwen3-4B at Q8_0 reached 41 to 44 t/s depending on backend.

- Bogdan Varlamov, "Running Local LLMs on a Strix Halo Laptop" — https://www.bogdanvarlamov.com/blog/local-llms-strix-halo/

**A 128GB Ryzen AI Max+ 395 guide.** Qwen3-Coder 30B-A3B at Q4_K_S measured **98.51 t/s**,
Qwen3-30B-A3B **100.04 t/s**, and gpt-oss-120b at MXFP4 **55.57 t/s**. The same source
measures memory bandwidth at roughly **215 GB/s against a 256 GB/s theoretical peak**, a
gap it describes as typical for LPDDR5X under mixed CPU and GPU load.

- runaihome, "AMD Ryzen AI Max+ 395 (Strix Halo) for Local LLMs in 2026" — https://runaihome.com/blog/ryzen-ai-max-395-strix-halo-local-llm-2026/

**Other measurements of the same model, for the spread.** gpt-oss-120b has also been
reported at roughly 31 t/s and roughly 34 t/s on Ryzen AI Max+ 395 systems. Architecture
matters more than parameter count on this hardware: a dense 70B runs at around 5 t/s while
a 30B mixture of experts runs at 70 to 100 t/s on the same machine, because token
generation is bandwidth bound and a sparse model reads far fewer weights per token.

- DataHardware, "Strix Halo Tokens Per Second 2026: Real Speed, Dense vs MoE" — https://datahardware.ai/blog/strix-halo-tokens-per-second-2026
- HashTechWave, "AMD Ryzen AI Max+ 395 For Local LLMs (2026)" — https://www.hashtechwave.com/amd-strix-halo-review/

### Why 192GB is not expected to be a speed jump

The compute does not move: the flagship is still 40 RDNA 3.5 compute units and still Zen 5,
the same counts as Strix Halo's top part. The memory data rate moves from LPDDR5X-8000 on
Strix Halo to LPDDR5X-8533 here, a step of under seven per cent in data rate. The capacity
moves by fifty per cent, from 128GB to 192GB. That asymmetry is the whole argument: it is a
capacity release, not a throughput release.

## The software position

The video's claim that ROCm does not yet have CUDA's gravity is specific and checkable.
gfx1151, which is the Strix Halo graphics target, is listed only as **Preview** in AMD's
ROCm compatibility matrix rather than as a fully supported target. Running it today
generally means overriding the target version, and first class gfx1151 support is being
targeted at ROCm 8.0. llama.cpp and Ollama work through ROCm with that override, and
LM Studio's Vulkan backend works without it.

- ROCm support status for gfx1151, including the Preview listing and the ROCm 8.0 target — https://tinycomputers.io/posts/upgrading-rocm-7.0-to-7.2-on-amd-strix-halo-gfx1151.html
- Working ROCm, Ollama, vLLM and llama.cpp recipes on gfx1151 — https://github.com/Foxlight-Foundation/Skulk/issues/144

## Not chased to a primary source

- **Qwen3-Next 80B at around 59 tokens per second.** The video states this alongside the
  Qwen3-Coder 30B and gpt-oss-120b figures, both of which are sourced above from the same
  guide. The 80B figure is repeated in aggregated summaries of Ryzen AI Max+ 395 testing
  but was not found in the benchmark tables of the guides checked, so it is not put on
  screen anywhere in this video.
- **Pricing.** No price has been announced for any Ryzen AI Max PRO 400 system, so the
  video's closing conditional about pricing is stated as a condition and no figure appears
  on screen.
{% endraw %}

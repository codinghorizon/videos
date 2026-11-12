---
layout: default
title: "The Biggest Local AI A Cheap GPU Can Run"
permalink: /biggest-local-ai-cheap-gpu-strata/
date: 2026-11-12
---

# The Biggest Local AI A Cheap GPU Can Run

{% raw %}
Checked 2026-11-12. Every figure on screen traces to a row here. Repo figures are published by the
project or by owners in the repo; none are ours. Prices are in PRICES.md.

## Strata, the app
| On screen | Figure | Source |
|---|---|---|
| Free, open source (MIT), Windows / Linux / macOS installers | v0.2.13 installers | https://github.com/Niko1221/Strata |
| Newest release 9 November | 0.2.13, 09 Nov; hotfix 0.2.13.1 fixes Arc setup on Linux | https://github.com/Niko1221/Strata/releases |
| Went viral early October | coverage 4 Oct 2026 | https://hackaday.com/2026/10/04/ai-on-your-gaming-pc/ |
| Radeon on Windows and Linux; maintainer-tested cards | AMD_HIP.md support table | https://raw.githubusercontent.com/Niko1221/Strata/main/docs/AMD_HIP.md |
| Intel Arc Linux only | INTEL_ARC.md | https://raw.githubusercontent.com/Niko1221/Strata/main/docs/INTEL_ARC.md |
| Several cards share the experts | v0.1.39 `--remote-expert-opt` multi-GPU | https://github.com/Niko1221/Strata/releases/tag/v0.1.39 |
| Models: Qwen3.8 Flash Next, Qwen3.6-35B-A3B, DeepSeek V4.1 Flash | MODELS.md | https://raw.githubusercontent.com/Niko1221/Strata/main/docs/MODELS.md |

## How it works
| On screen | Figure | Source |
|---|---|---|
| 24,576 experts, 10 per word | HOW_IT_WORKS.md | https://raw.githubusercontent.com/Niko1221/Strata/main/docs/HOW_IT_WORKS.md |
| Often-used experts on the card, the rest in RAM read by the processor; keeps updating | HOW_IT_WORKS.md (kitchen analogy; ours is desk and shelf) | same |
| +700 experts per extra GB; "more VRAM matters more than a faster GPU" | HOW_IT_WORKS.md | same |
| Helper drafts words, big model checks in one pass, same answer sooner | HOW_IT_WORKS.md (MTP, 1.6-1.8x) | same |
| RAM rule: 48 GB fits the 2-bit versions, 64 GB all main sizes, 32 GB + 12-16 GB card only the Coder, 32 GB + 24 GB card runs Q2_0/IQ2_XS | MODELS.md | MODELS.md |
| 4-bit Unsloth versions need ~72 GB RAM or more | MODELS.md | MODELS.md |
| XMP/EXPO: RAM below rated speed slows the CPU half | DETAILS.md troubleshooting | https://raw.githubusercontent.com/Niko1221/Strata/main/docs/DETAILS.md |
| Download 66-76 GB | MODELS.md (ISTA packs) | MODELS.md |

## Speeds (the gauge)
| Beat | Setup | tok/s | Source |
|---|---|---|---|
| 004, 067, 069 | RTX 5070 12GB, Ryzen 5 7600, 64GB DDR5-5200, Q2_0 | 93 | DETAILS.md |
| 070 | same PC, IQ3_S | 53 | DETAILS.md |
| 040 | Arc A750 8GB, IQ3_XXS (maintainers) | 10-19 | INTEL_ARC.md |
| 047 | Radeon 780M (Ryzen 7 255), Q2_0 | 16.6 | AMD_HIP.md |
| 057 | RTX 3060 12GB, UD-IQ1_M | 31-37 | Releases, 0.2.11 |
| 062-063, 103, 177-178 | RTX 3060, i7-7700, 32GB DDR4-2133: Strata 30.2, no drafts ~20, llama.cpp 9 | 30.2 / 20 / 9 | https://insiderllm.com/guides/strata-vs-llama-cpp-rtx-3060/ |
| 172-176 | Prompt reading: 6-7x vs llama.cpp default, ~2.2-2.6x vs tuned (-b/-ub 4096) | | InsiderLLM, same page |
| 035 | DeepSeek V4.1 Flash 2-bit, RTX 3060 + 46GB RAM | 9-11 | README table |
| 111, 204 | RTX 5060 Ti 16GB, 128GB RAM, IQ3_S (owner's run) | 48.2 | COMMUNITY_BENCHMARKS.md |
| 116-117 | RX 9060 XT 16GB: Strata 27.1 vs llama.cpp HIP 20 (engine 0.1.29, quant unstated) | 27.1 / 20 | AMD_HIP.md |
| 129 | Arc B580, WSL2, IQ2_XS, "device loss also seen" | ~21 | INTEL_ARC.md |
| 136-137 | RTX 3090 estimate (amber, never measured) | ~140 | DETAILS.md estimate (±20%) and SmartScope estimate |
| 153-155, 207 | RTX 5090, Q2_0 | 223-259 | https://akitaonrails.com/en/2026/10/27/llm-benchmark-best-open-source-llms-for-home-hardware/ |
| 165 | RTX 5090, UD-Q4_K_XL | 44-52 | akitaonrails, same page |

## Catches
| On screen | Source |
|---|---|
| 6GB card failed (issue #916) | https://smartscope.blog/en/blog/strata-local-llm-engine-qwen3-8-flash-next-2026/ |
| Radeon cards owner-validated only; Arc setup fixed this week; Nvidia driver blue screens reported | AMD_HIP.md; Releases 0.2.13.1; SmartScope |
| Hackaday's writer found factual errors | https://hackaday.com/2026/10/04/ai-on-your-gaming-pc/ |

## Viewer comment (079-080)
@Five7weezy, 2026-10-08, under https://www.youtube.com/watch?v=cwQGFRm1sKU :
"If I upgrade anything, it'll be 2x32GB before a new GPU."
{% endraw %}

---
layout: default
title: "Four RTX 3090s Run 100B AI Fast, But There Is a Catch"
permalink: /used-epyc-vs-rtx-3090s-100b-local-ai/
date: 2026-10-04
---

# Four RTX 3090s Run 100B AI Fast, But There Is a Catch

{% raw %}
Checked 4 October 2026. Performance figures are other people's published measurements; none of these systems was tested for this video. Prices are snapshots, not offers.

## Memory and model size

- **Weight floor arithmetic.** 100 billion parameters at 4 bits per weight is 100e9 × 0.5 bytes = 50 GB before metadata, higher precision tensors, runtime buffers and the context cache. A 120 billion parameter dense model at 4 bits is about 60 GB on the same basis. These are simplified estimates, not file sizes.
- **Qwen3.5-122B-A10B** is a mixture of experts model with "122B in total and 10B activated" parameters, 256 experts, and "8 Routed + 1 Shared" experts activated per token. [Hugging Face model card](https://huggingface.co/Qwen/Qwen3.5-122B-A10B)
- **RTX 3090:** 24 GB of GDDR6X per card and a graphics card power of 350 W (Founders Edition, 3 slot, 2× PCIe 8 pin supplementary power). Four cards give 96 GB of graphics memory in total, as four separate pools. [NVIDIA GeForce RTX 3090 Family specs](https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090-3090ti/)
- **RTX 3090 memory bandwidth:** 384 bit bus at 19.5 Gbps, 936 GB/s. [KitGuru, Gigabyte RTX 3090 Eagle OC review](https://www.kitguru.net/components/graphic-cards/dominic-moass/gigabyte-rtx-3090-eagle-oc-review/)

## EPYC memory channels

- **EPYC 7002 (Rome):** eight DDR4 channels per socket, DDR4-3200, 204.8 GB/s theoretical per socket. The EPYC 7282 itself is listed at 85.3 GB/s per socket, "performance optimized for 4 channels with DDR4-2667 DIMMs", with a default TDP of 120 W. [AMD EPYC 7002 series datasheet](https://www.amd.com/content/dam/amd/en/documents/products/epyc/amd-epyc-7002-series-datasheet.pdf)
- **EPYC 9004 (Genoa):** twelve DDR5-4800 channels per socket, 460.8 GB/s theoretical per socket. [AMD EPYC 9004 series datasheet](https://www.amd.com/content/dam/amd/en/documents/epyc-business-docs/datasheets/amd-epyc-9004-series-processors-datasheet.pdf), [AMD EPYC 9004 product page](https://www.amd.com/en/products/processors/server/epyc/4th-generation-9004-and-8004-series.html)

## Published CPU only EPYC results

- **Dual EPYC 7282, 128 GB DDR4 in eight channels per socket (8 GB DDR4-3200 per channel), llama.cpp:** DeepSeek R1 Distill Llama 70B Q4_K_M generated 2.88 tokens per second (tg128). [ahelpme.com, llama-bench DeepSeek R1 Distill Llama 70B and dual AMD EPYC 7282](https://ahelpme.com/ai/llamacpp-ai/llama-bench-the-deepseek-r1-distill-llama-70b-and-dual-amd-epyc-7282/)
- **Llama 3.1 70B at F16 (131.42 GiB file):** 4.30 tokens per second on platform P1, 2× AMD EPYC 9175F (Turin) with 16 × 48 GB DDR5-6400, both sockets. On the same page, platform P2 (2× EPYC 9654 Genoa, 24 × 64 GB DDR5-4800) reached 3.97 tokens per second. [llama.cpp discussion #11733, "Dual Epyc Genoa/Turin token generation performance bottlenecks"](https://github.com/ggml-org/llama.cpp/discussions/11733)

## Published four card RTX 3090 results

- **Qwen3.5-122B, four way tensor parallel, 220 W per card, vLLM:** the AutoRound INT4 code run reached 110.5 tokens per second against 92.7 for AWQ INT4 on the same setup. The rig is 4× RTX 3090 on PCIe 3.0 x16 with no NVLink; CUDA peer to peer is "enabled and verified through transfers on all 12 directed GPU pairs". [alesha-pro/4x3090-llm-benchmarks](https://github.com/alesha-pro/4x3090-llm-benchmarks)
- **GLM-4.7 Q4_K_M on 4× RTX 3090 with ik_llama.cpp:** best generation 4.48 tokens per second at 8K context (4.28 at 16K), with the expert weights of 65 layers kept on the CPU (an EPYC 7282 with DDR4-2133). [r/LocalLLaMA, GLM-4.7 on 4x RTX 3090 with ik_llama.cpp](https://www.reddit.com/r/LocalLLaMA/comments/1q7o8kl/glm47_on_4x_rtx_3090_with_ik_llama_cpp/)

## Power and noise

- **Four card power limit study, Qwen3.6-27B FP16, vLLM, tensor parallel 4:** output was 29 tokens per second at 350/390 W (unrestricted), 300 W, 275 W and 250 W per card, 27 at 220 W and 24 at 200 W. These are per GPU limits, not wall measurements. The build is "an open build on a generic mining frame" cooled by ten fans, five on each side of the cards. [r/LocalLLaMA, Finding the 4x 3090 Sweet Spot](https://www.reddit.com/r/LocalLLaMA/comments/1te9o18/finding_the_4x_3090_sweet_spot/)
- **Four card build guide:** four 3090s at 350 W is 1,400 W of GPU power, about 1,650 W peak with the host, against about 1,440 W continuous from a US 15 A, 120 V circuit. RTX 3090 NVLink is two way only, so four cards make two bridged pairs and the rest of the traffic crosses PCIe. [cpompa.com, 4× RTX 3090 AI Inference Server build guide](https://cpompa.com/docs/ai-inference-3090.html)
- No same model, same speed wall meter comparison of the two machines, and no matched sound pressure test, was found.

## Multi GPU software

- llama.cpp splits a model across GPUs by layer (the default, pipeline parallel) or by tensor (experimental tensor parallelism, which needs fast interconnects); CUDA peer to peer access is opt in. [llama.cpp docs/multi-gpu.md](https://github.com/ggml-org/llama.cpp/blob/master/docs/multi-gpu.md)

## Prices

- **Four card build:** the build guide prices four used RTX 3090s at $850 to $1,050 each ($3,400 to $4,200) and a complete four card system at about $5,500 to $6,500. [cpompa.com build guide](https://cpompa.com/docs/ai-inference-3090.html)
- **Used HPE ProLiant DL385 Gen10:** one EPYC 7262, 512 GB DDR4 ECC registered (16 × 32 GB, 2400 MHz), sold at auction in Zürich for CHF 3,090; the listing ended on 6 September 2026. [Ricardo listing 1328087872](https://www.ricardo.ch/fr/a/hpe-dl385-gen10-amd-epyc-512gb-ecc-ram-23tb-storage-1328087872/)

### Not checked

- The used RTX 3090 price tracker snapshot of $1,199 on 4 October 2026 and its twelve month average of $950 ([bestvaluegpu.com](https://bestvaluegpu.com/history/new-and-used-rtx-3090-price-history-and-specs/)) could not be re-checked at the source, and the per gigabyte figures derived from them ($4,800 for four cards, $2,400 for two, about $50 and $40 per GB) are unchecked with it.
- The narration calls the 4.3 tokens per second run "a modern twelve channel Genoa system". The page lists it as platform P1, a dual EPYC 9175F (Turin) machine with eight DDR5 DIMMs per socket.
- The narration says the power study tested four limits and that the lowest gave 27 tokens per second. The post lists six limits; 27 is the 220 W result and the lowest limit, 200 W, gave 24.
{% endraw %}

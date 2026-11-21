---
layout: default
title: "The Cheapest Old GPUs That Still Run Qwen 3.8 27B"
permalink: /cheapest-old-gpus-qwen-3-8-27b/
date: 2026-11-21
---

# The Cheapest Old GPUs That Still Run Qwen 3.8 27B

{% raw %}
The sources the script cites, as listed with it.

- Qwen3.8-27B model card: https://huggingface.co/Qwen/Qwen3.8-27B
- Unsloth Qwen3.8-27B GGUF sizes (UD-IQ4_XS 14.4GB, UD-Q4_K_XL 17.7GB, Q8_0 29GB, BF16 54.7GB): https://huggingface.co/unsloth/Qwen3.8-27B-GGUF
- Qwen 3.8 MTP benchmarks (2x Tesla P40 13.2 / 23.4 tok/s, 2x RTX 3060 30.0 / 53.3 tok/s, V100 32GB 33.3 / 48.0 tok/s, RX 7900 XTX 85.4 tok/s with MTP on Vulkan): https://github.com/sudoingX/qwen38-mtp
- llamaperf Tesla P40 (also the Tesla M40 owner report, 2-3 tok/s at UD_Q4_K_S): https://llamaperf.com/gpu/tesla-p40
- llamaperf RTX 3060 12GB (PCIe x1 slowdown, x8/x8 fix): https://llamaperf.com/gpu/rtx-3060-12gb
- llamaperf RTX 2080 Ti 22GB (27.0 tok/s without MTP, 47.5 code / 28.8 prose with MTP, NInfer, 64K): https://llamaperf.com/gpu/rtx-2080-ti-22gb
- llamaperf AMD MI50 32GB (22.8 tok/s, Q8_0, 66,560 context; 22.0 at 16K and 20.4 at 64K): https://llamaperf.com/gpu/amd-mi50-32gb
- llamaperf RX 7900 XTX (40.0 tok/s, Q4_K_M, 32K, ROCm 7.2 Windows): https://llamaperf.com/gpu/rx-7900-xtx
- llamaperf Arc A770 16GB (12.0 tok/s, Q3_K_S, SYCL): https://llamaperf.com/gpu/arc-a770-16gb
- InsiderLLM, Qwen 3.8 27B on an RTX 3090 (41.49 tok/s): https://insiderllm.com/guides/qwen-3-8-27b-vs-3-6-27b-rtx-3090/
- Hardware Corner, Qwen3.8 27B hardware tests (RTX 3090 40.31 tok/s at 4K, 33.95 at 64K): https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/
- CUDA 13.0 release notes (Maxwell, Pascal and Volta support removed): https://docs.nvidia.com/cuda/archive/13.0.0/cuda-toolkit-release-notes/
- Tom's Hardware on CUDA dropping Maxwell, Pascal and Volta: https://www.tomshardware.com/pc-components/gpus/nvidia-to-drop-cuda-support-for-maxwell-pascal-and-volta-gpus-with-the-next-major-toolkit-release
- ROCm 6.0 release notes (MI50 maintenance ending Q2 2024): https://rocm.docs.amd.com/en/docs-6.0.0/about/release-notes.html
- Used RTX 3060 12GB price (RigPrice): https://rigprice.com/gpu/rtx-3060-12gb/
- Used RTX 3090 price (RigPrice): https://rigprice.com/gpu/rtx-3090/
- Used RX 7900 XTX price (RigPrice): https://rigprice.com/gpu/rx-7900-xtx/
- Used Tesla P40 price (RigPrice): https://rigprice.com/gpu/tesla-p40/
- Used RTX 4060 Ti 16GB price (RigPrice): https://rigprice.com/gpu/rtx-4060-ti-16gb/
- Used Tesla M40 price, passive cooling and no display (GPUDojo): https://gpudojo.com/tesla-m40
- Used Tesla V100 32GB price (GPUDojo): https://gpudojo.com/tesla-v100
- RTX 2080 Ti 22GB listings, sorted by lowest price (eBay): https://www.ebay.com/sch/i.html?_nkw=rtx+2080+ti+22gb&_sop=15&LH_BIN=1&LH_ItemCondition=3000
- AMD MI50 32GB listings (eBay): https://www.ebay.com/sch/i.html?_nkw=amd+instinct+mi50+32gb&_sop=15&LH_BIN=1
{% endraw %}

---
layout: default
title: "Don't Buy 128GB For Local AI (Do This Instead)"
permalink: /dont-buy-128gb-local-ai/
date: 2026-11-03
---

# Don't Buy 128GB For Local AI (Do This Instead)

{% raw %}
The sources the script cites, as listed with it.

- 128GB (2x64GB) DDR5-6000 G.Skill Flare X5, $3,799.99 on Newegg (November 2, 2026): https://www.newegg.com/p/N82E16820374760
- 64GB (2x32GB) DDR5 kit, $999.99 sold by Newegg (November 2, 2026): https://www.newegg.com/p/N82E16820331982
- GMKtec EVO-X2, Ryzen AI Max+ 395, 128GB + 1TB, $3,499.99, available (GMKtec, November 2, 2026): https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc?variant=48746069262490
- Mac Studio M5 Max 18-core CPU, 40-core GPU, 128GB, 512GB, $5,099.00 (Apple, November 2, 2026): https://www.apple.com/shop/buy-mac/mac-studio/m5-max-chip-18-core-cpu-40-core-gpu-128gb-memory-512gb-storage
- Mac Studio specs, 128GB needs the 40-core GPU M5 Max, 614GB/s memory bandwidth: https://www.apple.com/mac-studio/specs/
- Dell Pro Precision with GB10 (formerly Pro Max), 128GB LPDDR5x, 2TB, $7,967.00 (Dell, November 2, 2026): https://www.dell.com/en-us/shop/workstation/spd/dellpromaxwithgb10fcm1253/fcm1253_reg_01
- gpt-oss-120b, 117B parameters, 5.1B active per token (OpenAI): https://openai.com/index/introducing-gpt-oss/
- RTX 4070 12GB, i5-12600K, 64GB DDR5-6000 (4x16GB), gpt-oss-120b MXFP4 in llama.cpp: 23.7 to 24.0 tok/s generation, about 430 tok/s prompt, 28.0 tok/s on a 512-token prompt; 9.72 tok/s with RAM at 2000 MT/s (carteakey): https://carteakey.dev/blog/local-inference/optimizing-gpt-oss-120b-local-inference/
- AMD Ryzen 9 9950X memory support, DDR5-5600 with two DIMMs, DDR5-3600 with four: https://www.amd.com/en/products/processors/desktops/ryzen/9000-series/amd-ryzen-9-9950x.html
- Strix Halo gpt-oss-120b on ROCm: 51.8 tok/s at depth 0, 19.8 at 32K, pp2048 1,008 (Level1Techs): https://forum.level1techs.com/t/one-spark-two-spark-red-strix-blue-arc/240937
- M5 Max 40-core GPU 128GB, gpt-oss-120b in oMLX: 79.7 tok/s at 1K, 41.4 at 32K, prompt 1,023 to 1,658 tok/s: https://omlx.ai/benchmarks/d8dnhh1k
- DGX Spark, gpt-oss-120b in llama.cpp b6922: tg32 60.6 at depth 0, 40.6 at 32K, pp2048 1,956: https://github.com/ggml-org/llama.cpp/discussions/16578
- RTX 5090, gpt-oss-120b with --n-cpu-moe 21, about 30 tok/s at zero context: https://github.com/ggml-org/llama.cpp/discussions/15396
- RTX 3090, Ryzen 7 5700X, 64GB DDR4-3000, Qwen 3.8 Flash-Next IQ3_XXS: llama.cpp 19.1 tok/s at 4K, Strata about 78 tok/s without drafting and 119 as shipped, prefill 2,187 to 2,738 tok/s (InsiderLLM): https://insiderllm.com/guides/strata-vs-llama-cpp-rtx-3090/
- Strix Halo, Qwen 3.8 Flash-Next AD-4.27bpw on ROCm, 20.6 tok/s; Strix Halo memory about 218GB/s measured (Sleeping Robots): https://sleepingrobots.com/dreams/qwen38-flash-next-strix-halo/
- RTX 3080 Ti with 128GB DDR4-3600, gpt-oss-120b 18 to 22 tok/s, a reported run (SpecPicks): https://specpicks.com/reviews/gpt-oss-120b-rtx-3060-offload-vs-ryzen-7-5800x-cpu-2026
- Strata engine: https://github.com/Niko1221/Strata
{% endraw %}

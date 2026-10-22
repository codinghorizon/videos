---
layout: default
title: "The Biggest AI Models That Fit On 8 DGX Sparks"
permalink: /biggest-local-ai-8-dgx-sparks/
date: 2026-10-22
---

# The Biggest AI Models That Fit On 8 DGX Sparks

{% raw %}
The sources the script cites, as listed with it.

- DGX Spark clusters up to 8 units, 1TB, the 1.4x / 1.3x / 1.2x speed-ups and the 64GB Spark (NVIDIA blog, October 21 2026): https://blogs.nvidia.com/blog/local-ai-gtc-rtx-dgx-spark-station-sync/
- 64GB Sparks cluster to 512GB; Spark +30% and RTX PRO 6000 +40% (Wccftech): https://wccftech.com/nvidia-gives-dgx-rtx-systems-a-ai-inference-boost-dgx-spark-now-clusters-up-to-8-units/
- Connect multiple Sparks, 2 to 4 units, direct or switched (NVIDIA playbook): https://build.nvidia.com/spark/connect-multiple-sparks
- DGX Spark 128GB, $6,950 (NVIDIA marketplace): https://marketplace.nvidia.com/en-us/enterprise/personal-ai-supercomputers/
- DGX Spark 64GB from $4,999 on October 23, and the 128GB price rise from $3,999 (ServeTheHome): https://www.servethehome.com/nvidia-dgx-spark-64gb-launched-and-big-128gb-gb10-price-increases/
- DGX Spark specifications, 273 GB/s memory bandwidth, 240W power supply: https://www.nvidia.com/en-us/products/workstations/dgx-spark/
- Dell Pro Precision with GB10 128GB, $5,523 with the 1TB SSD, 2x 200G QSFP, $50 QSFP cable: https://www.dell.com/en-us/shop/workstation/spd/dellpromaxwithgb10fcm1253/fcm1253_reg_01
- MikroTik CRS804-4DDQ, $1,195 plus $115.32 tariff, pre-order (Baltic Networks): https://www.balticnetworks.com/collections/vendors/products/mikrotik-crs804-ddq-cloud-router-switch-crs804-4ddq-hrm
- 400G QSFP-DD to 2x 200G QSFP56 DAC, 1m, $199 plus $17.51 tariff, sold out (Baltic Networks): https://www.balticnetworks.com/products/tensor-juice-400g-qsfp-dd-to-2x-200g-qsfp56-dac-cable-1m-nvidia-compatible
- Qwen3.8 Flash Next NVFP4 on one DGX Spark, vLLM with MTP, 48.7 tok/s single stream, 162.9 tok/s at 8 streams: https://github.com/MiaAI-Lab/Qwen3.8-Flash-Next-Single-DGX-Spark
- Qwen 3.8 27B Q4 on DGX Spark, llama.cpp, about 12 tok/s: https://blog.kubesimplify.com/qwen3-8-27b-on-dgx-spark
- GLM-5.3 Flash NVFP4 on 2x DGX Spark, vLLM TP=2, 26.47 tok/s on the current checkpoint (Classmethod): https://dev.classmethod.jp/en/articles/dgx-spark-2node-glm-5-3-flash-nvfp4-vllm/
- GLM-5.3 GGUF sizes, UD-IQ2_M 238.6GB "runs well on 2x DGX Sparks", UD-IQ4_XS 365.3GB, about 810GB for 8-bit (Unsloth): https://unsloth.ai/docs/models/glm-5.3
- DeepSeek V4.1 Flash on 3 Sparks (switchless triangle, 37.9-51.0 tok/s prose, about 2,000 tok/s prefill), 4 switched Sparks (TP4, 87.7 tok/s single, 342.7 at 16 streams, about 4.9-5.9K tok/s prefill) and a 4-Spark switchless ring (67.4 tok/s): https://github.com/MiaAI-Lab/DeepSeek-v4.1-Flash-DGX-Sparks
- 4x DGX Spark switchless ring with patched NCCL: https://github.com/alexellis/glm-5.3-flash-4x-dgx-spark-switchless
- Four DGX Spark systems require an external switch (NVIDIA DGX Spark specifications): https://www.nvidia.com/en-us/products/workstations/dgx-spark/
- Qwen 3.5 397B FP8 and Kimi K2.6 on an 8x GB10 cluster with a MikroTik CRS804-4DDQ (NVIDIA developer forum): https://forums.developer.nvidia.com/t/kimi-2-6-and-qwen-3-5-397b-fp8-on-8xgb10-cluster/369446
- Kimi K3 GGUF sizes, 2-bit 861.3GB (Unsloth): https://unsloth.ai/docs/models/kimi-k3
- RTX 5090 memory bandwidth, 1,792 GB/s (TechPowerUp): https://www.techpowerup.com/gpu-specs/geforce-rtx-5090.c4216
- Mac Studio M5 Ultra 256GB, 2TB SSD, $9,999 (Abt): https://www.abt.com/Apple-Mac-Studio-Desktop-Apple-M5-Ultra-256GB-Unified-Memory-2TB-SSD-in-Silver-Z1U50009U/p/248638.html
- Mac Studio M5 Ultra 512GB due late October (Notebookcheck): https://www.notebookcheck.net/Apple-releases-new-Mac-Studio-globally-with-256-GB-RAM-16-TB-storage-and-Apple-M5-Ultra.1378049.0.html
- GB10 power, 140W TDP (NVIDIA DGX Spark specifications): https://www.nvidia.com/en-us/products/workstations/dgx-spark/
- US average residential electricity price, 18.31 cents per kWh (EIA, July 2026): https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_5_6_a
{% endraw %}

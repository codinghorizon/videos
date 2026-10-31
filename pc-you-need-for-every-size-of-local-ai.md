---
layout: default
title: "The PC You Need For Every Size Of Local AI"
permalink: /pc-you-need-for-every-size-of-local-ai/
date: 2026-10-31
---

# The PC You Need For Every Size Of Local AI

{% raw %}
Every figure the voice says, where it comes from, and the capture that shows it on screen (key =
file under public/<slug>/web/). Checked 2026-10-30. Prices are in PRICES.md, which outranks this file.
We ran no benchmarks: every speed is someone else's published run.

## Sizes and memory

| figure said | what | source | capture |
|---|---|---|---|
| 1B to over 1 trillion | Gemma 4 E2B (effective 2B) to Kimi K3 (2.8T) | model cards below | none |
| 0.6 GB per billion | our arithmetic: Q4_K_M is 4.89 bits per weight = 0.61 bytes; Llama 3.1 8B Q4_K_M 4.9GB, Qwen3 14B 9GB, Llama 3.3 70B 42.5GB all land at about 0.6 | https://github.com/ggml-org/llama.cpp/blob/master/tools/quantize/README.md, https://huggingface.co/unsloth/Qwen3-14B-GGUF, https://huggingface.co/unsloth/Llama-3.3-70B-Instruct-GGUF | none |
| two thirds, divide by 0.6, 16GB to about 17B | our arithmetic: 16 x 2/3 / 0.6 = 17.8 | derived | none |
| Settings, System, About | where Windows shows installed RAM | https://support.microsoft.com/en-us/windows/find-information-about-your-windows-device-a66d52c8-3323-44fd-8f34-a9497bb935e1 | none |
| Jan labels which models fit | Jan's hub marks models by fit to your memory | https://docs.jan.ai/desktop/manage-models | jan-fit |
| under 3 GB | Qwen3.5 4B Q4_K_M 2.74GB | https://huggingface.co/unsloth/Qwen3.5-4B-GGUF | q4b-file |
| under 6 GB | Qwen3.5 9B Q4_K_M 5.68GB | https://huggingface.co/unsloth/Qwen3.5-9B-GGUF | q9b-file |
| 16.5 GB | Qwen 3.8 27B UD-Q4_K_M | https://huggingface.co/unsloth/Qwen3.8-27B-GGUF | q27-file |
| 35B, 3B active | Qwen3.6 35B-A3B, UD-Q4_K_M 22.1GB | https://huggingface.co/unsloth/Qwen3.6-35B-A3B-GGUF | none |
| 125B, 6B active | Qwen3.8-Flash-Next | https://huggingface.co/Qwen/Qwen3.8-Flash-Next | fn-card |
| about 55 GB | Flash-Next IQ3_S 54.8GB RAM plus VRAM | https://github.com/Niko1221/Strata/blob/main/docs/MODELS.md | strata-fn |
| 120B, 5B active | gpt-oss-120b, 117B total, 5.1B active | https://huggingface.co/openai/gpt-oss-120b | none |
| 552B core | DeepSeek V4.1 Flash 1017, 552B with 16B active | https://www.marktechpost.com/2026/10/17/deepseek-just-released-v4-1-flash-1017-scores-77-0-on-deepswe-opens-search-api/ | mtp-ds |
| 2.8 trillion | Kimi K3, 2.8T total, 104B active | https://huggingface.co/moonshotai/Kimi-K3 | kimi-gpqa |
| 466 GB, one bit | Kimi K3 UD-Q1_0 | https://huggingface.co/unsloth/Kimi-K3-GGUF | kimi-file |
| fit with room to spare | DeepSeek V4.1 Flash 2-bit peak memory 188.6GB on 256GB | https://omlx.ai/benchmarks/performance/9m8dcvyn | omlx-ds |

## Speeds

| figure said | what | source | capture |
|---|---|---|---|
| 47 tok/s | Gemma 4 E2B, Galaxy S26 Ultra CPU, 46.9 (LiteRT-LM, Google) | https://huggingface.co/litert-community/gemma-4-E2B-it-litert-lm | e2b-speed |
| laptop chip keeps up | Gemma 4 E2B, Intel Lunar Lake CPU 29.8 | same | e2b-speed |
| 5 to 10 tok/s reading | 3/4 word per token; reading pace | https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them | none |
| 17 tok/s | Gemma 4 E4B, Lunar Lake CPU 16.8 | https://huggingface.co/litert-community/gemma-4-E4B-it-litert-lm | e4b-speed |
| 62 tok/s | RTX 5060 8GB, qwen3:8b in Ollama, 61.70 | https://www.databasemart.com/blog/ollama-gpu-benchmark-rtx5060 | dbm-5060 |
| 41 tok/s | RTX 5060 Ti 16GB, Qwen3 14B Q4_K, 41.1 | https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-5060-ti-16gb/ | hwc-14b |
| more than double | gpt-oss-20b on the same card, 92.1 | same | hwc-20b |
| keeps ahead of your eyes | Qwen 3.8 27B 3-bit on RTX 5060 Ti 16GB, median 28.8 | https://llamaperf.com/gpu/rtx-5060-ti-16gb | none |
| 40 tok/s | Qwen 3.8 27B on used RTX 3090, 40.31 at 4K | https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/ | hwc-3090 |
| 10 tok/s | Qwen 3.8 27B 4-bit, Mac mini M6 24GB, 9.83 | https://llamaperf.com/gpu/m6-24gb | lp-m6 |
| 40 tok/s, 32GB RAM | Qwen3.6 35B-A3B on RTX 5060 8GB, MoE layers on CPU, 40.0 | https://llamaperf.com/report/ca73c740-15c0-41cc-a99d-60c154ba033e | lp-5060-moe |
| 53 tok/s | Flash-Next IQ3_S on RTX 5070 12GB (Strata's list) | https://github.com/Niko1221/Strata/blob/main/docs/MODELS.md | strata-fn |
| 5 tok/s | EVO-X2 128GB, Llama 3.1 70B Q4_K_M, 5.10 | https://github.com/visorcraft/strix-halo-llm-perf/blob/main/BENCHMARKS.md | visor-70b |
| 46 tok/s | EVO-X2, gpt-oss-120b 46 to 50 | same | visor-120b |
| nine times faster | 46 / 5.10 = 9.0 | derived | none |
| quicker than you read | EVO-X2, Qwen3 235B-A22B Q3_K_M 17.21 | same | visor-235b |
| over 100 tok/s | DeepSeek V4.1 Flash 2-bit on M5 Ultra (80-core) 256GB with MTP, 117.3 on a short chat | https://omlx.ai/benchmarks/performance/9m8dcvyn | omlx-ds |
| 10 to 20 tok/s | Strata, DeepSeek V4.1 Flash 2-bit on Strix Halo 128GB, 11 chat to 21 code (MODELS.md 10 to 16) | https://github.com/Niko1221/Strata | none |
| 27 tok/s | Kimi K2.5 2.8-bit on M3 Ultra 512GB, 26.6 | https://omlx.ai/benchmarks/performance/3ip3mhvl | omlx-kimi |
| 816B at 25 tok/s | two Mac Studio M5 Ultra 512GB over Thunderbolt 5, 24.99 | https://machinelearning.apple.com/research/mlx-distributed-inference | apple-mlx |

## Scores

| figure said | what | source | capture |
|---|---|---|---|
| not knowledge bases | Gemma model card limitations | https://huggingface.co/google/gemma-4-E2B-it | gemma-kb |
| thinking loops | Qwen3.5 0.8B card | https://huggingface.co/Qwen/Qwen3.5-0.8B | qwen-loops |
| 76% | Qwen3.5 4B GPQA Diamond 76.2 (Qwen's own run) | https://huggingface.co/Qwen/Qwen3.5-4B | q4b-gpqa |
| 53 at its best | GPT-4o GPQA 46.0 to 53.1 | https://github.com/openai/simple-evals | evals-gpqa |
| under a tenth / about four in ten | SimpleQA GPT-4o mini 9.5, GPT-4o 38.8 to 40.1 | same | evals-simpleqa |
| edges past 120B; bigger wins at code | Qwen3.5 9B GPQA 81.7 vs gpt-oss-120b 80.1; LiveCodeBench gpt-oss-120b 82.7 | https://huggingface.co/Qwen/Qwen3.5-9B | q9b-gpqa |
| 82 to 64 | Qwen3.5 9B 81.7 vs Qwen3 14B 64.0 (thinking) | same, https://arxiv.org/html/2505.09388 | q9b-gpqa |
| 62% vs 53 | Qwen 3.8 27B SWE-bench Pro 61.7 vs Claude Opus 4.6 (Max) 53.4 | https://huggingface.co/Qwen/Qwen3.8-27B | q27-swe |
| 20 and 58 | Artificial Analysis index: Qwen 3.8 27B 20, Claude Opus 5.5 58 | https://artificialanalysis.ai/models/qwen3-8-27b, https://artificialanalysis.ai/leaderboards/models | none |
| less than a point ahead | Flash-Next SWE-bench Pro 62.5 vs 27B 61.7 | https://huggingface.co/Qwen/Qwen3.8-Flash-Next | fn-card |
| end of the year before last; beats it by a mile | Llama 3.3 70B, December 2024, GPQA Diamond 50.5 vs 81.7 | https://huggingface.co/meta-llama/Llama-3.3-70B-Instruct | llama-gpqa |
| 32, ties GLM | AA: DeepSeek V4.1 Flash 1017 32, GLM-5.3 32 | https://artificialanalysis.ai/models/deepseek-v4-1-flash-1017, https://artificialanalysis.ai/models/open-source | none |
| sixty percent higher | 32 / 20 = 1.6 | derived | none |
| edges past an earlier Opus | DeepSWE 77.0 vs Claude Opus 5 74.0 | https://www.marktechpost.com/2026/10/17/deepseek-just-released-v4-1-flash-1017-scores-77-0-on-deepswe-opens-search-api/ | mtp-ds |
| within a point | Kimi K3 GPQA 93.5 vs GPT-5.6 Sol 94.1 | https://huggingface.co/moonshotai/Kimi-K3 | kimi-gpqa |

## Viewer questions

| said | comment | video |
|---|---|---|
| "Is there a source that I can plug my laptop specs into and get an appropriate LM that suits the hardware?" | YouTube comment | T5vomLianVw |
| "Which model is smarter: 27B or Flash Next?" | YouTube comment under our Qwen video | pmkA8bWJDdI |
{% endraw %}

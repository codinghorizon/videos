---
layout: default
title: "The 10 Best Free Local AI Models That Don't Suck"
permalink: /10-best-free-local-models-that-dont-suck/
date: 2026-08-05
---

# The 10 Best Free Local AI Models That Don't Suck

Every figure this video puts on screen, with where it came from. Checked 5 August 2026.

Benchmark scores are quoted as the model's own publisher reports them unless another
source is named. Scores from different publishers are not directly comparable, so every
comparison here is between two numbers on the same benchmark.

Download sizes are the size of a four bit quantised build, which is what almost everyone
actually downloads. They vary a little between build methods; the figures used are the
published Q4_K_M GGUF sizes where a build exists, and the same arithmetic applied to the
parameter count where one does not.

---

## How many models are out there

- **2,968,543 models published on Hugging Face.** The count in the Hugging Face model
  index header. <https://huggingface.co/models>

## What a subscription costs

- **$240 a year.** Twenty dollars a month, the standard individual plan price for the
  major assistant subscriptions.
  <https://openai.com/chatgpt/pricing/> and <https://www.anthropic.com/pricing>

## Quantisation

- **A 30B model is about 61GB at FP16, 32GB at Q8, 21GB at Q5 and 18GB at Q4.** Sizes of
  the published quantised builds of Qwen3-30B-A3B.
  <https://huggingface.co/Qwen/Qwen3-30B-A3B-GGUF>

## Open weights is not open source

- Llama and Gemma both ship the weights under bespoke licences with use restrictions,
  rather than under an OSI approved open source licence.
  <https://www.llama.com/llama3_3/license/> and <https://ai.google.dev/gemma/terms>

---

## 10. IBM Granite 4.0 Micro

- **3B parameters, Apache 2.0.** Granite 4.0 Micro is a 3B dense model; the family is
  released under Apache 2.0 and is the first open model family certified under ISO 42001.
  <https://huggingface.co/ibm-granite/granite-4.0-micro> and
  <https://www.ibm.com/new/announcements/ibm-granite-4-0-hyper-efficient-high-performance-hybrid-models>
- **IFEval 82.3.** IFEval average, strict, on the model card.
  <https://huggingface.co/ibm-granite/granite-4.0-micro>
- **A 49B reasoning model scores 88.6 on the same benchmark.** Llama-3.3-Nemotron-Super-49B-v1.5,
  IFEval 88.61. <https://huggingface.co/nvidia/Llama-3_3-Nemotron-Super-49B-v1_5>
- **1.9GB at Q4.** Q4_K_M build of a 3B model.
- Granite 4.0 uses a hybrid Mamba-2 and transformer design that IBM reports cuts memory
  use by more than 70% against comparable models, which is what makes a processor only
  machine viable.
  <https://www.ibm.com/new/announcements/ibm-granite-4-0-hyper-efficient-high-performance-hybrid-models>

## 9. Microsoft Phi-4

- **14B parameters, MIT.** <https://huggingface.co/microsoft/phi-4>
- **MATH 80.4, against 66.3 for Llama 3.3 70B.** Both figures from the Phi-4 technical
  report, which reports Phi-4 at 80.4, Qwen 2.5 14B at 75.6 and Llama 3.3 70B at 66.3.
  <https://arxiv.org/pdf/2412.08905>
- **9.1GB at Q4.** Q4_K_M build of a 14B model.
- General knowledge is the known weak spot: the same report shows the model trades broad
  factual recall for reasoning, and it is trained heavily on synthetic reasoning data.
  <https://arxiv.org/pdf/2412.08905>

## 8. Meta Llama 3.3 70B

- **70B parameters, Llama 3.3 Community License.**
  <https://github.com/meta-llama/llama-models/blob/main/models/llama3_3/MODEL_CARD.md>
- **MMLU 86.0, zero shot chain of thought.** Meta's own model card.
  <https://github.com/meta-llama/llama-models/blob/main/models/llama3_3/MODEL_CARD.md>
- **Mistral Small 3.2 24B scores 80.5 on MMLU.**
  <https://huggingface.co/mistralai/Mistral-Small-3.2-24B-Instruct-2506>
- **42.5GB at Q4.** Q4_K_M build of a 70B model.
- Shipped by every major local runtime: llama.cpp, Ollama, LM Studio, vLLM and SGLang all
  carry it in their model libraries.
  <https://ollama.com/library/llama3.3>, <https://lmstudio.ai/models>,
  <https://docs.vllm.ai/en/latest/models/supported_models.html>
- Newer models beat it at the same size on specific tasks, which is what the Phi-4 MATH
  comparison above shows at a fifth of the parameters.

## 7. Nvidia Llama Nemotron Super 49B

- **49B parameters, NVIDIA Open Model License, derived from Llama-3.3-70B-Instruct.** A
  distillation driven neural architecture search shrinks the 70B into a 49B that fits a
  single card. <https://huggingface.co/nvidia/Llama-3_3-Nemotron-Super-49B-v1_5>
- **AIME 2025 82.71.** Model card evaluation table, same page.
- **A 30B open model scores 61.3 on AIME 2025.** Qwen3-30B-A3B-Instruct-2507.
  <https://huggingface.co/Qwen/Qwen3-30B-A3B-Instruct-2507>
- Also on the card: MATH500 97.4, AIME 2024 87.5, GPQA 71.97, BFCL v3 71.75, IFEval 88.61.
- **30GB at Q4.** Q4_K_M build of a 49B model.

## 6. Mistral Small 3.2 24B

- **24B parameters, Apache 2.0, 128K context.**
  <https://huggingface.co/mistralai/Mistral-Small-3.2-24B-Instruct-2506>
- **MMLU 80.5**, unchanged from 3.1, against 86.0 for Llama 3.3 70B at roughly three times
  the size. Same page, and the Meta model card above.
- **Reads images and returns structured output.** The 3.2 release reports DocVQA 94.86 and
  ChartQA 87.40, and the update is specifically about function calling and structured
  output reliability, with HumanEval Plus at 92.90 and Arena Hard rising from 19.56 to
  43.10. Same page.
- **14.3GB at Q4.** Published Q4_K_M build.

## 5. OpenAI gpt-oss-20b

- **21B total parameters, 3.6B active, Apache 2.0.**
  <https://huggingface.co/openai/gpt-oss-20b>
- **Runs in 16GB** thanks to native MXFP4 quantisation of the mixture of experts weights.
  Same page.
- **SWE-bench Verified 60.7 at high reasoning effort**, 53.2 at medium and 37.4 at low.
  Same page. The three reasoning levels are a documented setting, not a workaround.
- **A 106B open model scores 57.6 on the same benchmark.** GLM-4.5-Air.
  <https://arxiv.org/pdf/2508.06471>
- **12.1GB** as published.
- Knowledge is thin relative to its reasoning: MMLU-Pro 73.6 and GPQA Diamond 58.59 sit
  well below its agentic results, which is why it is built to reach for tools.

## 4. Google Gemma 3 27B

- **27B parameters, Gemma Terms of Use**, which carry use restrictions and are not an OSI
  approved open source licence. <https://ai.google.dev/gemma/terms>
- **Over 140 languages, 128K context, multimodal.**
  <https://developers.googleblog.com/introducing-gemma3/>
- **LMArena Elo 1338, ahead of DeepSeek-V3 at 1318**, which has roughly 25 times the
  parameters. <https://blog.google/innovation-and-ai/technology/developers-tools/gemma-3/>
  and <https://lmarena.ai/leaderboard>
- Google positions it as the most capable model that runs on a single GPU or TPU. Same
  announcement.
- **16.5GB at Q4.** Q4_K_M build of a 27B model.

## 3. GLM-4.5-Air

- **106B total parameters, 12B active, MIT.**
  <https://huggingface.co/zai-org/GLM-4.5-Air>
- **BFCL v3 tool calling 76.4**, and Tau-bench 69.4. GLM-4.5 technical report.
  <https://arxiv.org/pdf/2508.06471>
- **A 49B agent tuned model scores 71.8 on BFCL v3.** Llama-3.3-Nemotron-Super-49B-v1.5
  reports 71.75. <https://huggingface.co/nvidia/Llama-3_3-Nemotron-Super-49B-v1_5>
- **SWE-bench Verified 57.6.** Same technical report.
- **64GB at Q4.** Q4_K_M build of a 106B model. Smaller quantised builds bring it under
  24GB at a cost in quality.

## 2. DeepSeek R1

- **671B total parameters, 37B active, MIT.**
  <https://huggingface.co/deepseek-ai/DeepSeek-R1>
- **AIME 2024 pass at 1 of 79.8, against 79.2 for a closed frontier model.** The DeepSeek-R1
  paper reports 79.8 for R1 and 79.2 for OpenAI o1-1217.
  <https://arxiv.org/pdf/2501.12948>
- **404GB at Q4.** Q4_K_M build of a 671B model, which is why almost everyone running this
  locally is running a distilled version rather than the model itself. The distills are
  published alongside it at 1.5B, 7B, 8B, 14B, 32B and 70B. Same page.

## 1. Qwen3 30B A3B

- **30.5B total parameters, 3.3B active, Apache 2.0.** 128 experts with 8 activated, 48
  layers. <https://huggingface.co/Qwen/Qwen3-30B-A3B-Instruct-2507>
- **AIME 2025 61.3, against 24.7 for Qwen3-235B-A22B non thinking**, a model in the same
  family with roughly eight times the parameters. Both numbers from the comparison table on
  that page, which also gives GPQA 70.4, LiveCodeBench v6 43.2, Arena-Hard v2 69.0,
  BFCL-v3 65.1 and MMLU-Pro 78.4.
- **18.6GB at Q4.** Published Q4_K_M build.
  <https://huggingface.co/Qwen/Qwen3-30B-A3B-GGUF>
- Only 3.3B parameters are active per token, which is why it generates far faster than a
  dense model of the same file size on the same card.

---

## Caveats

- Benchmark scores come from each model's own publisher except the LMArena figures, which
  come from LMArena. Publishers do not all use identical harnesses, prompts or sampling
  settings, so a two point gap between two vendors' numbers is not a reliable ranking.
- AIME and MATH scores in particular move with sampling temperature and the number of
  attempts allowed. The figures quoted are the publisher's headline pass at 1 results.
- Download sizes are for four bit builds. Other quantisation levels, and other people's
  builds of the same model, differ by a few per cent.
- Memory needed to run a model is larger than its file size once the context window and
  key value cache are allocated, and it grows with the length of the conversation. The
  machine tiers in this video compare file sizes against card sizes, which is the right
  first filter and not the whole story.
- Model releases move quickly. Every figure here was checked on 5 August 2026.

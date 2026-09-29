---
layout: default
title: "Jev can't do what these 2 local AI rivals unlocked"
permalink: /jev-local-alternatives-decider-omni/
date: 2026-09-29
---

# Jev can't do what these 2 local AI rivals unlocked

{% raw %}
Sources for the figures and claims in this video. Read 28 September 2026 unless stated.

## Jev and TypeSafe

- **Jev is hosted, returns typed decisions with probabilities, and TypeSafe calls it a System One model.** "System One models make fast, structured decisions for software. Jev is TypeSafe's flagship model and the first System One model." "A System One model evaluates a state and returns typed answers and probabilities." Source: https://docs.typesafe.ai/concepts/system-one
- **You define the allowed answers.** "System One models do not write replies, produce code, or generate explanations of their reasoning. You define the possible answers through primitives", with a Choice example "Which team should handle this ticket?" over billing, technical or account. Source: https://docs.typesafe.ai/concepts/system-one
- **Jev 1.13 accepts text only.** Models table, row Input: "Text only. String, JSON object, or array of text values. No image, audio, or video input." The System One page adds: "Jev currently accepts text input only... Images, audio, and video are not supported (yet)." Source: https://docs.typesafe.ai/models
- **No customer fine tuning of Jev's weights.** "Jev is not fine-tuned or LoRA-adapted with customer data... You shape its answers to your domain through the request rather than through per-account weights." Source: https://docs.typesafe.ai/models ("Customizing Jev")

## Decider

- **Built on Qwen, trained for typed decisions; independent of TypeSafe.** "It is not affiliated with or endorsed by TypeSafe AI... a 2B model built on Qwen/Qwen3.5-2B-Base, a 4B model built on Qwen/Qwen3.5-4B-Base and a 35B mixture-of-experts model built on Qwen/Qwen3.5-35B-A3B-Base... Nothing was distilled from Jev." Source: https://github.com/Mapika/decider (README, "Independence")
- **Reads the scores of the option letters and converts them to probabilities.** "decider/model.py reads the hidden state at each slot, projects it onto one label token per option (A-J, then K-Z...) and softmaxes over the valid ones. Letters are never generated." Source: https://github.com/Mapika/decider (README, "How it works")
- **Older 2B comparison: about 64 per cent to about 74 per cent on held out tasks.** "The 94 public tasks" table: Qwen3.5-2B-Base, zero-shot, held-out accuracy 0.642; decider v8, held-out accuracy 0.741. Source: https://github.com/Mapika/decider/blob/main/docs/RESULTS.md
- **Open weights and training tools.** "Train your own": scripts/train.sh reproduces the released supervised weights. Source: https://github.com/Mapika/decider (README)
- **Multiple questions per request.** The quick start sends one ticket with department, refund_requested and frustration questions to `system_one` and gets one answer for each. Source: https://github.com/Mapika/decider (README, "Quick start")
- **A separate 2B vision model.** Models table row "decider-2b-vision · Qwen3.5-2B vision-language · 1.9B". Source: https://github.com/Mapika/decider (README, "Models")
- **5.2 ms and about 1,178 decisions per second, on a B300.** "with CUDA graphs and torch.compile one support-ticket request takes 5.2 ms... and a batch of 32 runs 1,178 decisions per second (FP8 5.0 ms and 1,349 per second)." The same section states the 4B measurements were made on a B300. Source: https://github.com/Mapika/decider/blob/main/docs/RESULTS.md
- **Server median 13.3 ms with one client.** "...at a median of 13.3 ms with one client and 190 requests per second with 64 clients." Source: https://github.com/Mapika/decider/blob/main/MODEL_CARD_4B.md
- **Three questions in the 5.2 ms request.** Stated in the script; the RESULTS.md sentence says "one support-ticket request". See Not checked.
- **4B weights about 8.4 GB in BF16.** "the 4B 8.4 GB" (README, "Runs on"); "Mapika/decider-4b (bf16, 8.4 GB)" (docs/CHANGELOG.md). Source: https://github.com/Mapika/decider
- **CPU execution and Apple silicon.** "CPU. The library and the HTTP server run on CPU in bfloat16"; "Apple Silicon, MPS... On an M1 Pro in float16, across the three 2B smoke-test workloads, the median request is 133 ms". Source: https://github.com/Mapika/decider (README, "Runs on")
- **Decider 2.1 against v2.** "decider-4b v2.1 gets back most of the sampled play v2 lost (... live browser 93% against 88%)... and is less well calibrated on hard items than v2... Neither passed its pre-registered release rules; the model cards list every failure." Source: https://github.com/Mapika/decider (README, "What's new", 2026-09-24); also https://huggingface.co/Mapika/decider-4b ("It is less well calibrated than v2 on hard items") and docs/RESULTS.md ("Neither model passed its pre-registered release rules").

## Jev Omni

- **Built on Gemma 4 12B IT; takes text, images, audio and video; returns a probability per option.** "A multimodal decision classifier for text, images, audio and video. Supply a question and options; receive a probability for each option, not a generated explanation. Built on Gemma 4 12B IT." Source: https://huggingface.co/akhilaaa3/Jev-Omni
- **Independent of TypeSafe.** "It is not affiliated with, endorsed by, sponsored by, or derived from TypeSafe AI or its Jev model." Source: https://huggingface.co/akhilaaa3/Jev-Omni
- **30 seconds of audio, 16 video frames.** "Audio is capped at 30 seconds; video uses 16 frames." Source: https://huggingface.co/akhilaaa3/Jev-Omni
- **Warm H200 medians.** "Warm H200 inference: 83 ms (~2k-token text), 26 ms (image), 31 ms (13-second audio), 504 ms (16-frame video). Medians over 20 optimized-backend requests; preprocessing and network time are extra." Source: https://huggingface.co/akhilaaa3/Jev-Omni ("Speed")
- **One question per call.** "Both classifiers are priced one call per question: a classifier answers one question at a time, so the state is re-sent for each of them." Source: https://huggingface.co/akhilaaa3/Jev-Omni
- **Unified BF16 checkpoint of about 24 GB.** Repository files: `model.safetensors` 23.9 GB, commit "Make the unified bf16 checkpoint..."; repository size 24 GB. Source: https://huggingface.co/akhilaaa3/Jev-Omni/tree/main
- **Older wording: about 50 GB of FP32 weights; CUDA required.** "CUDA GPU required. FP32 weights use about 50 GB before runtime overhead; inference uses BF16 autocast." Source: https://huggingface.co/akhilaaa3/Jev-Omni ("Quick start")

## DiffusionGemma and Djev

- **More than 1,100 tokens per second, H100, FP8.** "unlocking per user generation speeds exceeding 1100 tokens per second in low batch size settings (H100, FP8)." Source: https://ai.google.dev/gemma/docs/diffusiongemma/model_card ("Core Capabilities")
- **Djev reads the allowed answer probabilities from DiffusionGemma.** "DiffusionGemma reads the context and denoises the answer positions together. The API reads the probabilities of the allowed labels directly"; "One-step structured reads. Inspect the answer slots without running a full conversational generation loop." Djev adds no weights of its own. Sources: https://github.com/Davipar/djev-dev and https://github.com/fstandhartinger/jevbench (README: "It is an inference method, not a separately trained model")

## JevBench

- **27 September release: Decider 4B v2 64.13, Jev 1.13.0 63.29.** Both releases dated 27 September 2026 (v1.4.2.1 and v1.4.2.2) list decider-4b v2 at 64.13 and Jev 1.13.0 at 63.29. Source: https://github.com/fstandhartinger/jevbench (README and CHANGELOG.md)
- **Jev leads on intelligence (53.1 against 49.4) and calibration; Decider on speed and cost.** "Jev 1.13.0 out-reasons decider-4b v2 (Intelligence 53.1 vs 49.4) and is better calibrated; decider-4b v2 leads on speed and cost." Source: https://github.com/fstandhartinger/jevbench (README, v1.4.2.1)
- **The score combines intelligence, calibration, speed and cost.** "The four axes use an equal-weight harmonic mean." Source: https://github.com/fstandhartinger/jevbench
- **Cost is a price estimate, not a bill.** "It is a model-price estimate, not a GPU bill." Source: https://github.com/fstandhartinger/jevbench (README, v1.4.2.2)
- **Rank history.** v1.4.2 (25 September): decider-4b v2 #1. v1.4.2.1 (27 September): "Added Plumb-4B as the new #1 (65.84)". v1.4.2.2 (27 September): "Added Imajev-4B (#1, 67.37)". Source: https://github.com/fstandhartinger/jevbench/blob/main/CHANGELOG.md

## Image JevBench

- **Composite (v0.1.3):** 1 Imajev-4B 76.39, 2 Jev-Omni 73.10, 9 Mapika decider-2b-vision 66.77; Djev variants from row 27; 31 Autoloops, Gemma 4 31B IT (API) 47.14. The "earlier split" column lists Jev-Omni at #1 · 73.10. Source: https://benchmarkheaven.com/image-jev-bench
- **Sealed image accuracy:** Jev-Omni 368/456 · 80.7%; decider-2b-vision 319/456 · 70.0%; Gemma 4 31B IT 397/456 · 87.1%. Source: https://benchmarkheaven.com/image-jev-bench
- **Synthetic material.** "The 333 fresh sealed items are our own synthetic images and renders." Source: https://benchmarkheaven.com/image-jev-bench

## Hardware

- GeForce RTX 3060: 12 GB. Source: https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3060-3060ti/
- GeForce RTX 3090 Ti: 24 GB. Source: https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090-3090ti/
- GeForce RTX 5090: 32 GB. Source: https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/

### Not checked

- That the 5.2 ms request contained three questions: RESULTS.md says "one support-ticket request" without a question count.
- That the M1 Pro used for the 133 ms median had 32 GB of memory: the README names the M1 Pro but not its memory.
- Hardware fit on 12, 24 and 32 GB cards is an estimate from published weight sizes, not a measurement.
- The waiting times for ten sequential decisions are illustrative arithmetic.

### Discrepancies

- The script says the latest JevBench release puts Plumb 4B at the top. That was release v1.4.2.1. A second release the same day, v1.4.2.2, added Imajev-4B at #1 (67.37), with Plumb 4B at #2 and Decider 4B v2 at #3. The live board has since moved to v1.5.0.
- The script says the current Image JevBench puts Jev Omni first on the combined score. On v0.1.3, Imajev-4B is #1 (76.39) and Jev Omni #2 (73.10); Omni was #1 on the earlier split. Omni remains ahead of Decider 2B vision and Djev.
{% endraw %}

---
layout: default
title: "Jev's big idea makes local qwen do less and act faster"
permalink: /jev-qwen-local-ai-that-takes-action/
date: 2026-09-28
---

# Jev's big idea makes local qwen do less and act faster

{% raw %}
Checked 27 and 28 September 2026. Performance figures are the projects' own published results, not measurements made for this video. The weekend trip assistant is a hypothetical that connects separately published capabilities; no project cited here demonstrates that complete workflow.

## Official Jev (TypeSafe)

- Launch post, dated 15 September 2026: TypeSafe describes Jev as its first "System One" model, "built to make fast, structured decisions that software can use directly", available "in early access", with developers being brought "off the waitlist". [typesafe.ai/blog/introducing-system-one-models-and-jev](https://typesafe.ai/blog/introducing-system-one-models-and-jev)
- Question types: Choice ("Choose an option from a list"), Score ("Score the state on a rubric") and Noul ("Is this statement true?", a value from 0 to 1). Questions are evaluated "in parallel and in isolation against the same state in one go". [docs.typesafe.ai/introduction](https://docs.typesafe.ai/introduction)
- Current model: Jev 1.13 (`jev-1.13.0`), offered as a priced API with rate limits. Input is "Text only… No image, audio, or video input"; non-text input has to be pre-processed into text first. [docs.typesafe.ai/models](https://docs.typesafe.ai/models)
- Confidence "is a statistic computed from the probability distribution the answer already gives you", and "the correct threshold values depend on your domain and the performance of the model for your use case". [docs.typesafe.ai/confidence](https://docs.typesafe.ai/confidence)

## NanoJev

- Built on a shared Qwen3-0.6B backbone with trained decision heads; one checkpoint plays Maze, Snake, ViZDoom Basic and ViZDoom Predict Position. [huggingface.co/C-Tianyu/NanoJev](https://huggingface.co/C-Tianyu/NanoJev)
- Held out results, NanoJev / Jev / untuned Qwen3-0.6B: Basic aiming 128/128, 56/128, 56/128. Predict Position 27/128, 11/128, 11/128. Maze 4/10, 7/10, 2/10. Snake 8/8, 8/8, 0/8. [NanoJev model card](https://huggingface.co/C-Tianyu/NanoJev), [repository](https://github.com/TianyuCodings/NanoJev)
- The replay in the repository README: "NanoJev eliminates the target with one shot in 1.40 s; Jev and Untuned Qwen each fire 19 shots without an elimination before the deadline." This is the developer's selected replay, not an average. [github.com/TianyuCodings/NanoJev](https://github.com/TianyuCodings/NanoJev)
- Observations are structured text: "The policy receives only the text state and offered action descriptions" and "uses visible object labels; pixel encoding is a separate future extension". In the maze, "code can reposition along previously traversed open edges" when no untried direction remains. [docs/UNIFIED_GAMES.md](https://github.com/TianyuCodings/NanoJev/blob/main/docs/UNIFIED_GAMES.md)

## Browser Use jev-ultrafast

- "TypeSafe's Jev picks an operation and an element. A small LLM writes text only when the operation is TYPE_TEXT." The page is given to the model as a numbered action space. [github.com/browser-use/jev-ultrafast](https://github.com/browser-use/jev-ultrafast)
- The recorded Google Flights run, Zürich to London, took 7,073 ms. "Timing starts after initial page observation and includes model calls, generated text, browser work, stale decisions, and loading waits." An independent check verifies the setting and that flight options are visible; nothing is purchased. The authors describe it as "three repeats of one task on one browser profile, not a general reliability benchmark."
- The text model in the published setup is `inception/mercury-2.5`, used through OpenRouter. Both models in this result are hosted.

## local-jev

- "A local, offline System One server compatible with TypeSafe's Jev API", with a browser portal that imports items, runs yes/no, category and score questions, filters by answer and exports CSV. Offline after the first model download. [github.com/amithgc/local-jev](https://github.com/amithgc/local-jev)
- On JevBench's 231 public items: Qwen3.5-4B (`llm-qwen3.5-4b`) 80.5%, median 651 ms; Jev 1.13.0 hosted 86.6% (published result, not measured by local-jev); DeBERTa (`nli-deberta-large`) 54.1%, median 76 ms. Per tier, easy / standard / hard: Qwen3.5-4B 48 / 69 / 69, Jev 48 / 71 / 81, so Jev answers 14 more correctly, 12 of them on the hard tier. [docs/results.md](https://github.com/amithgc/local-jev/blob/main/docs/results.md)
- Measured on an Apple M4 Max with 36 GB, PyTorch on the Mac GPU (MPS), 21 September 2026. [docs/results.md](https://github.com/amithgc/local-jev/blob/main/docs/results.md)

## SemIf (formerly OpenJev)

- Independent, "not affiliated with Jev or TypeSafe". [github.com/TheoLeeCJ/SemIf-OpenJev](https://github.com/TheoLeeCJ/SemIf-OpenJev)
- Same frozen Qwen3.5-4B, same state, 21 binary criteria, one RTX 3090, median of three runs: direct typed logits 1.023 s; an autoregressive JSON answer array 5.332 s (5.21 times as long). The two agreed on 18 of the 21 criteria.
- Browser models: MiniCPM5-2B at 1.56 GB and Qwen3.5-4B at 3.01 GB, both Q4_K_M GGUF. Listed accuracy is from native BF16 evaluation, not from the quantized browser builds.
- Backends: Apple Silicon (MLX, or PyTorch on MPS), CUDA, CPU through llama.cpp, and a Qwen3.8-27B EXL3 bridge added on 22 September 2026.
- Model cards: [huggingface.co/openbmb/MiniCPM5-2B](https://huggingface.co/openbmb/MiniCPM5-2B), [huggingface.co/Qwen/Qwen3.5-4B](https://huggingface.co/Qwen/Qwen3.5-4B).

## Imajev

- An open "Jev-style typed-decision model that also takes images", run locally. Up to 2 images per request, an explicit unknown probability, and Mac (MLX) and GPU paths. [github.com/mohit67890/imajev](https://github.com/mohit67890/imajev)
- The listing showcase: a listing whose color field says red, against a photo of beige suede boat shoes; the model marks `listing.color` as contradicted and the app holds the listing.
- Wardrobe app 48/49 (38/49 with calibration) and stylist app 21/24 in the author's checks, with named misses.
- The 4B tier moved to a new adapter on 26 September 2026. [huggingface.co/mohit67890/imajev-9b](https://huggingface.co/mohit67890/imajev-9b)

## Jev-Omni

- An independent multimodal decision classifier "built on Gemma 4 12B IT", taking text, images, audio and video and returning a probability for each supplied option; "not affiliated with, endorsed by, sponsored by, or derived from TypeSafe AI or its Jev model". [huggingface.co/akhilaaa3/Jev-Omni](https://huggingface.co/akhilaaa3/Jev-Omni)
- "Audio is capped at 30 seconds; video uses 16 frames." The card lists a CUDA GPU as a requirement.

## Hardware images

- GeForce RTX 3090 Founders Edition, NVIDIA's own product gallery image. [nvidia.com](https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090-3090ti/)
- MacBook Pro with the M4 family of chips, Apple Newsroom, October 2024. Apple publishes no image specific to the M4 Max configuration. [apple.com/newsroom](https://www.apple.com/newsroom/2024/10/new-macbook-pro-features-m4-family-of-chips-and-apple-intelligence/)

## Illustrations

The trip, its emails, flights, prices, confidence values and fare rules are illustrative and are labelled as such where they appear. The Doom arena, the snake board and the maze are our drawings of the tasks; the replay frames shown are the developer's own.
{% endraw %}

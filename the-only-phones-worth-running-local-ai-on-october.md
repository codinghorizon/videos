---
layout: default
title: "The Only Phones Worth Running Local AI On (October 2026)"
permalink: /the-only-phones-worth-running-local-ai-on-october/
date: 2026-10-20
---

# The Only Phones Worth Running Local AI On (October 2026)

{% raw %}
Every price was checked on its page on 2026-10-20 (see PRICES.md). Speeds come from vendors'
own pages, papers and named developers' runs, labelled as such on screen. We ran no tests of
our own.

## Prices

- OnePlus 15 16GB/512GB, $1,135 at Amazon (October 20): https://us.smartprix.com/mobiles/oneplus-15-16gb-ram-512gb-ppd1jmnmbq1a
- Google Pixel 10a 8GB, $499: https://www.bgr.com/2104428/google-pixel-10a-price-release-date/
- Samsung Galaxy S25 12GB, $799.99 at Samsung: https://www.samsung.com/us/smartphones/galaxy-s25/buy/
- Apple iPhone 18 Pro, $1,199: https://www.apple.com/shop/buy-iphone/iphone-18-pro
- Samsung Galaxy S26 Ultra 12GB/256GB $1,199.99 (was $1,399.99) and 16GB/1TB $1,999.99 at Samsung: https://www.samsung.com/us/smartphones/galaxy-s26-ultra/buy/
- Galaxy S26 Ultra memory by storage tier: https://fi.google.com/about/phones/samsung-galaxy-s26-ultra-specs
- Google Pixel 11 Pro 16GB only with 512GB or more, from $1,219: https://www.droid-life.com/2026/08/03/heres-pixel-11-series-specs-and-prices-again/
- Pixel 11 review (Tensor G6 trails rivals): https://www.khaleejtimes.com/tech/google-pixel-11-review
- Dollars per GB ($62, $67, $71) and the gaps ($335, $65) are our arithmetic, in PRICES.md.

## Apps and models

- PocketPal AI, free on iPhone and Android, built on llama.cpp: https://github.com/a-ghorbani/pocketpal-ai
- Google AI Edge Gallery, free, runs Gemma 4: https://github.com/google-ai-edge/gallery
- Gemma 4 on phones (E2B 52 tok/s decode on the Galaxy S26 Ultra GPU, prefill 3,808, first
  token 0.3 s; 56 tok/s on the iPhone 17 Pro GPU): https://developers.google.com/edge/litert-lm/models/gemma-4
- Qwen3.5 4B: https://huggingface.co/Qwen/Qwen3.5-4B and https://huggingface.co/unsloth/Qwen3.5-4B-GGUF
- Phi-4-mini: https://huggingface.co/microsoft/Phi-4-mini-instruct
- gpt-oss-20b (3.6B active per token, "within 16GB of memory", OpenAI's own figure): https://huggingface.co/openai/gpt-oss-20b
- gpt-oss-20b on a Snapdragon phone, llama.cpp's Snapdragon backend guide: https://github.com/ggml-org/llama.cpp/blob/master/docs/backend/snapdragon/README.md
- Apple's on-device foundation model, about 3B: https://machinelearning.apple.com/research/apple-foundation-models-tech-report-2025

## Hardware and speed

- Snapdragon 8 Elite Gen 5 memory bandwidth, about 85 GB/s: https://www.notebookcheck.net/SD-8-Elite-Gen-5-vs-SD-8-Gen-5_19966_19990.247596.0.html
- RTX 4090 memory bandwidth, 1,008 GB/s: https://www.techpowerup.com/gpu-specs/geforce-rtx-4090.c3889
- Qualcomm's own Llama 3 8B figures (15.08 tok/s on the 8 Elite Gen 5, 13.72 on the 8 Elite): https://huggingface.co/qualcomm/Llama-v3-8B-Instruct
- Qualcomm's own Llama 3.2 3B figure (26.50 tok/s on the 8 Elite): https://huggingface.co/qualcomm/Llama-v3.2-3B-Instruct
- Qualcomm's own Stable Diffusion step time: https://huggingface.co/qualcomm/Stable-Diffusion-v1.5
- Qualcomm's own Whisper figure: https://huggingface.co/qualcomm/Whisper-Large-V3-Turbo
- The iOS per-app memory cap, about 6 GB, one developer on Apple's forums: https://developer.apple.com/forums/thread/834805
- Apple's increased memory limit entitlement: https://developer.apple.com/documentation/bundleresources/entitlements/com.apple.developer.kernel.increased-memory-limit
- Bonsai 27B in 3.9 GB at 1 bit, about 11 tok/s on the iPhone 17 Pro Max and 670 tokens per 1%
  battery (PrismML's own paper): https://the-decoder.com/bonsai-27b-is-a-full-open-reasoning-model-that-fits-on-an-iphone/
- PowerInfer-2, a 47B model at 11.68 tok/s on a 24 GB OnePlus 12: https://arxiv.org/html/2406.06282
- REDMAGIC 11 Pro, up to 24 GB: https://global.redmagic.gg/products/redmagic-11-pro
- Qwen3.5 397B on an iPhone 17 Pro at 0.7 tok/s, one developer's run: https://gigazine.net/gsc_news/en/20260324-iphone-397b-ai/ and https://github.com/danveloper/flash-moe
- Draw Things, Qwen Image (20 GB) on an iPhone, 44 minutes a picture: https://gigazine.net/gsc_news/en/20251017-draw-things-image-generation-iphone-macos/
- Heat on a phone, about 40 down to 24 tok/s on an iPhone 16 Pro: https://arxiv.org/html/2603.23640

## Photos

Credited on screen, from Wikimedia Commons (CC BY-SA 4.0, CC BY 4.0, CC0) and the makers' own
press images; every credit is in PICS in src/lib/scene-phone.tsx.
{% endraw %}

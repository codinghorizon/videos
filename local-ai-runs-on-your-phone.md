---
layout: default
title: "Your Phone Can Run Real AI Now And That Changes Apps"
permalink: /local-ai-runs-on-your-phone/
date: 2026-08-20
---

# Your Phone Can Run Real AI Now And That Changes Apps

{% raw %}
Every figure, product claim and quoted description the finished picture puts on screen,
chased to a primary source.

---

## PocketPal AI

**Source:** https://github.com/a-ghorbani/pocketpal-ai

- Describes itself as "A private AI assistant that runs entirely on your phone." The
  repository elaborates: "Chat with language models, give them a voice, and let them use
  tools — all on-device. No account, no cloud, no internet required."
- Runs GGUF language models (Gemma, Qwen, Phi, Llama and others) fully offline.
- "Hugging Face integration — search and download GGUF models directly from the HF Hub."
- "Benchmarking — measure tokens/sec and memory."
- "Hardware acceleration — CPU, GPU (Metal on iOS, OpenCL/Adreno on Android), and NPU
  (Qualcomm Hexagon) inference paths."
- "Text-to-speech — on-device neural TTS with no cloud calls."
- "Works offline — no connection and no account required."
- "Private by default — every prompt, response, and document stays on your device."
- MIT licensed, free and open source, no subscription.
- Built on React Native and TypeScript, using llama.cpp for LLM inference and ONNX Runtime
  for text to speech. This is the link the script draws between PocketPal and the desktop
  world of quantized GGUF models: it is the same inference engine.

**On screen:** the GGUF format name, the Hugging Face download step, the CPU / GPU / NPU
acceleration paths, the Qualcomm Hexagon NPU label, and the phrase "no account, no cloud,
no internet required" as an attributed description rather than a channel claim.

---

## Android AICore and Gemini Nano

**Source:** https://developer.android.com/ai/aicore

- AICore is an Android **system service** that enables on-device execution of generative AI
  foundation models. Quoted: "Gemini Nano runs in Android's AICore system service, which
  leverages device hardware to enable low inference latency and keeps the model up-to-date."
- The model is "Google's Gemini Nano foundation model."
- Stated benefits, which are the three the script names:
  - Privacy: "On-device generative AI executes prompts locally, eliminating server calls"
    and "keeps sensitive data on the device."
  - Offline: works without a network connection.
  - Performance: "low inference latency" and "accelerated inference" through on-device
    hardware.
- Also stated, and used in the platform-plumbing argument: "AICore manages the distribution
  of Gemini Nano and handles future updates. You don't need to worry about downloading or
  updating large models over the network."
- Cost: "Significantly reduces the cost of using these large models in your app."

**Not on screen:** a device support list. The Android documentation does not publish one on
this page, and the narration says "supported Android devices" rather than naming any, so no
device names or model numbers are rendered.

---

## Google AI Edge Gallery

**Source:** https://github.com/google-ai-edge/gallery

- Describes itself as "A gallery that showcases on-device ML/GenAI use cases and allows
  people to try and use models locally."
- "Running the world's most powerful open-source Large Language Models (LLMs) on your
  mobile device."
- "100% On-Device Privacy: All model inferences happen directly on your device hardware."
- Model management: "Easily download models from the list or load your own custom models.
  Manage your model library effortlessly and run benchmark tests."
- Prompt Lab: "A dedicated workspace to test different prompts and single-turn use cases
  with granular control over model parameters."
- Mobile Actions: "Unlock offline device controls and automated tasks powered entirely by a
  finetune of FunctionGemma 270m."
- Platforms: Android 12 and up, iOS 17 and up, and a downloadable macOS build.

**On screen:** the four capabilities the narration lists (run models locally, test prompts,
benchmark performance, mobile actions), and the Android 12+ / iOS 17+ platform floor.

---

## FunctionGemma 270M

**Sources:**
- https://developers.googleblog.com/on-device-function-calling-in-google-ai-edge-gallery/
- https://ai.google.dev/gemma/docs/functiongemma
- https://ai.google.dev/gemma/docs/mobile-actions

- FunctionGemma is a **270 million parameter** model based on the Gemma 3 architecture,
  trained specifically for function calling. It "translates natural language directly into
  function calls on device within merely 270M parameters."
- The Mobile Actions demo uses it to parse natural language commands fully offline and pick
  the correct OS tool or app intent. Google's own examples include "Show me the San
  Francisco airport on map", "Create a calendar event for 2:30 PM tomorrow for cooking
  class", and "Turn on the flashlight".
- Google brought the Mobile Actions demo into Google AI Edge Gallery, where the model's
  prefill and decode performance can be benchmarked on the user's own hardware.
- Google states the model is small enough to run on a phone but "requires fine-tuning to
  specialize it for the task it is going to perform" — which is why the Gallery ships a
  finetune rather than the base model.

**On screen:** the figure 270M, the Gemma 3 lineage, and one of Google's own example
commands rather than an invented one.

---

## Apple Foundation Models framework

**Sources:**
- https://www.apple.com/newsroom/2025/09/apples-foundation-models-framework-unlocks-new-intelligent-app-experiences/
- https://developer.apple.com/documentation/foundationmodels
- https://machinelearning.apple.com/research/introducing-apple-foundation-models

- The framework "gives you access to the on-device Large Language Model that powers Apple
  Intelligence, with a convenient and powerful Swift API." Available on macOS, iOS, iPadOS
  and visionOS.
- The model behind it is described by Apple as "a ~3 billion parameter on-device language
  model", paired with "a larger server-based language model available with Private Cloud
  Compute and running on Apple silicon servers."
- Capabilities Apple names, matching the ones the narration lists:
  - Generation and summarization.
  - Extraction, e.g. turning PDFs into "structured references and citations".
  - **Guided generation**, a Swift approach to constrained decoding: developers annotate
    structs or enums with a `@Generable` macro, and it "ensures that the models respond with
    a consistent format that developers can rely on". This is the script's "structured
    output rules".
  - **Tool calling**: developers "provide tools to the model that call back into the app
    when the model requires more information for processing".
- On app size, which is the script's "does not have to ship a giant model file": Apple states
  it is "built into the operating system, so it won't increase your app size", and that
  inference is "free of cost".
- Requirement: the framework "works on any Apple Intelligence-compatible device when Apple
  Intelligence is enabled", with iOS 26, iPadOS 26 and macOS 26. This is the script's
  "Apple Intelligence has device requirements. Users have to turn it on."

**On screen:** the ~3B on-device parameter figure, the `@Generable` guided-generation
mechanism, tool calling, and the "won't increase your app size" claim as an attributed one.

---

## Private Cloud Compute

**Sources:**
- https://security.apple.com/blog/private-cloud-compute/
- https://support.apple.com/guide/iphone/apple-intelligence-and-privacy-iphe3f499e0e/ios

- Apple Intelligence analyses whether a request can be processed on device. Where it needs
  greater computational capacity it draws on Private Cloud Compute, sending only the data
  relevant to the task to be processed on Apple silicon servers.
- This supports the script's line that "some requests can still go to Private Cloud Compute
  when the device model is not enough", and is the reason the video does not claim every
  iPhone becomes a private frontier model.

**Not on screen:** the on-device versus Private Cloud Compute context window figures. Those
were only found in secondary summaries, not on an Apple page that could be read directly, so
no context-window number is rendered anywhere in the video. See "Not verified" below.

---

## MLC LLM and MLC Chat

**Sources:**
- https://github.com/mlc-ai/mlc-llm
- https://apps.apple.com/us/app/mlc-chat/id6448482937

- MLC LLM describes itself as a "Universal LLM Deployment Engine with ML Compilation", with
  the stated aim to "enable everyone to develop, optimize, and deploy AI models natively on
  everyone's platforms." The script's "universal deployment engine for large language
  models" is that description.
- Platforms: macOS, iOS and iPadOS, Android, Linux, Windows, and web browsers.
- GPU backends, which are the ones the narration names:
  - Metal, on Apple GPUs.
  - OpenCL, on Android GPUs including **Adreno** and **Mali**.
  - Plus CUDA (NVIDIA), Vulkan (AMD, Intel and cross platform), and WebGPU/WASM in browsers.
- All platforms are served by MLCEngine, which exposes an "OpenAI-compatible API available
  through REST server, python, javascript, iOS, Android".
- The MLC Chat iOS App Store listing states: "After a model is downloaded to the app,
  everything runs locally without server support, and it works without internet
  connections." And the tradeoff sentence the script quotes as the whole story in miniature:
  "it only works for the devices with sufficient VRAM depending on the models being used."
- App Store facts: free, developer Tianqi Chen, 1.8 GB, requires iOS 17.0 or later, and the
  privacy label reports no data collection.

**On screen:** the platform and backend matrix, Metal and OpenCL named against iOS and
Android, and the two App Store sentences quoted and attributed.

---

## GGUF, llama.cpp and quantization

**Source:** https://github.com/a-ghorbani/pocketpal-ai (states llama.cpp as the inference
engine and GGUF as the model format it consumes)

- GGUF is the model file format used by llama.cpp, which is the same format desktop users
  already run locally. PocketPal consuming GGUF from the Hugging Face Hub is what makes the
  script's claim true that a phone can use "the same broad world of quantized models people
  already use with llama.cpp on desktops".

**On screen:** the GGUF extension and the llama.cpp name, as the shared format link between
the desktop and the phone. No quantization bit-depth figures are rendered, because the
script names none and none was chased.

---

## Not verified

Claims the narration makes that could not be chased to a primary source, and which are
therefore **not rendered as figures anywhere in the picture**:

- "Three years ago, the normal advice was simple. If you wanted serious AI, you needed a
  data center." This is a characterisation of how the field was discussed rather than a
  sourceable fact, and the shot treats it as a remembered claim rather than a cited one.
- The relative battery cost, heat and throttling behaviour of on-device inference. Both
  Apple and Google state that on-device inference uses device resources, but no published
  primary figure for battery drain per token was found, so no percentage, milliamp-hour or
  minutes-of-battery number appears on screen.
- The comparative economics of local versus cloud inference for an app developer. The
  direction is supported by Apple stating on-device inference is "free of cost" and Google
  stating AICore "significantly reduces the cost", but no per-request price is rendered.
- On-device versus Private Cloud Compute context window sizes. Only found in secondary
  summaries, so no context figure is shown.
{% endraw %}

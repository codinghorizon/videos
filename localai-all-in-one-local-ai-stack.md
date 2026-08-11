---
layout: default
title: "Local AI Just Got Voice, Vision, Video And Routing"
permalink: /localai-all-in-one-local-ai-stack/
date: 2026-08-11
---

# Local AI Just Got Voice, Vision, Video And Routing

Everything this video puts on screen as a name, a figure, a version or a date, chased
back to a primary source. Retrieved 11 August 2026.

## What LocalAI says it is

**"LocalAI is the open-source AI engine. Run any model - LLMs, vision, voice, image,
video - on any hardware. No GPU required."**

The project's own repository description and the first line of its README.

- https://github.com/mudler/LocalAI

**"Make AI run on every machine."** The tagline on the project site, which expands it to
"Text, voice, vision, images, video, 3D and agents, from one open runtime. It works on the
laptop you already own, and scales to a room full of GPUs when you have one." The site
organises the feature set into six pillars: Reason, Listen, Speak, See, Create, Act. It
also states that "Every feature ships a CPU path first", which is the basis of the no GPU
claim, and that the server speaks the OpenAI, Anthropic, Ollama and ElevenLabs APIs.

- https://localai.io/

**Licence: MIT. 48,391 stars, 4,348 forks.** First commit March 2023; the repository was
created on 18 March 2023 and was last pushed to on 11 August 2026, the day these figures
were read.

- https://api.github.com/repos/mudler/LocalAI

**60+ backends**, including llama.cpp, vLLM, SGLang, transformers, whisper.cpp, diffusers,
MLX and MLX-VLM, alongside native C/C++/GGML engines written by the project itself.

- https://github.com/mudler/LocalAI

## The tools that made local language models accessible

llama.cpp, Ollama and LM Studio are named as the first wave that put local models on
ordinary machines. LocalAI itself lists llama.cpp among its backends, and its API surface
includes a drop-in Ollama-compatible API.

- https://github.com/ggml-org/llama.cpp
- https://ollama.com/
- https://lmstudio.ai/
- https://localai.io/

## The release timeline

Nine minor releases between March and August 2026, each with its own write-up on the
project blog:

| Version | Date | What it added |
| --- | --- | --- |
| 4.0 | 14 Mar 2026 | Agent orchestration in the core, React interface |
| 4.1 | 2 Apr 2026 | Distributed cluster mode, OIDC per user API keys |
| 4.2 | 11 May 2026 | Voice recognition, face recognition, speaker diarization |
| 4.3 | 24 May 2026 | Prompt cache on by default, usage per API key, Distributed v3 |
| 4.4 | 10 Jun 2026 | Prefix cache aware routing, video input and video generation |
| 4.5 | 23 Jun 2026 | Prefix caching by default, speaker aware conversations |
| 4.6 | 4 Jul 2026 | |
| 4.7 | 14 Jul 2026 | |
| 4.8 | 5 Aug 2026 | New inference engine, terminal agent CLI, 3D generation |

The most recent tag at the time of writing is **v4.8.2, 7 August 2026**.

- https://localai.io/blog/
- https://github.com/mudler/LocalAI/releases

## Voice, face and diarization

**LocalAI 4.2.0, 11 May 2026.** Adds `/v1/voice/*` endpoints for speaker verification,
identification, embedding extraction and analysis; a face recognition pipeline covering
1:1 verification, 1:N identification, detection, analysis and embeddings, with liveness
detection to reject spoofed photos and videos; and a `/v1/audio/diarization` endpoint that
answers "who spoke when", backed by sherpa-onnx and vibevoice.cpp. The same release brings
video generation to the stable-diffusion.ggml backend, including image to video and
first-last-frame generation, and eleven new backends in total.

- https://github.com/mudler/LocalAI/releases/tag/v4.2.0
- https://localai.io/blog/
- https://localai.io/features/voice-recognition/

## Prompt caching

**LocalAI 4.3.0, 24 May 2026.** The llama.cpp server side prompt cache is enabled
automatically rather than left off. The release states the effect directly: **"Repeated
system prompts go from 5-8 min to seconds."**

**LocalAI 4.5.0, 23 June 2026** extends this to prefix caching on by default, so system
prompts, RAG context, agent scaffolds and multi-turn chat are not recomputed on every
request, which the release describes as a time to first token and throughput win for
shared prefix workloads.

- https://github.com/mudler/LocalAI/releases/tag/v4.3.0
- https://github.com/mudler/LocalAI/releases/tag/v4.5.0

## Usage attribution

**LocalAI 4.3.0, 24 May 2026.** Traffic is attributed per API key and per user, surfaced
in the interface, and revoked keys stay readable in the history rather than taking their
traffic with them. Per user API key management arrived earlier, in **4.1.0, 2 April 2026**,
via OIDC.

- https://github.com/mudler/LocalAI/releases/tag/v4.3.0
- https://localai.io/blog/

## Distributed routing

**LocalAI 4.1.0, 2 April 2026** introduced distributed cluster mode. **4.3.0, 24 May 2026**
shipped Distributed v3 with per request replica routing, cached health probes and async per
node installation with streaming progress. **4.4.0, 10 June 2026** turned on prefix cache
aware routing by default, which biases a request toward the replica that already holds the
relevant KV and prefix cache.

**LocalAI 4.5.0, 23 June 2026** scales parallel serving slots to available VRAM, up to
eight on systems with 32GB or more, so several users share one engine without multiplying
KV memory.

- https://github.com/mudler/LocalAI/releases/tag/v4.3.0
- https://github.com/mudler/LocalAI/releases/tag/v4.4.0
- https://github.com/mudler/LocalAI/releases/tag/v4.5.0

## Beyond text

**LocalAI 4.4.0, 10 June 2026** adds video input understanding in llama-cpp via mtmd and
video generation via LTX-2 in stablediffusion-ggml, plus the native rfdetr-cpp detection
backend with 32 prebuilt GGUFs. **4.5.0** adds monocular metric depth via a
depth-anything backend, sound event tagging across 527 AudioSet classes, an espeak free
ONNX text to speech backend, and speaker aware realtime conversations that surface the
recognised speaker to both the client and the model.

- https://github.com/mudler/LocalAI/releases/tag/v4.4.0
- https://github.com/mudler/LocalAI/releases/tag/v4.5.0

## Not checked

- The claim that local hardware is more limited than cloud infrastructure, and that the
  best cloud systems remain ahead on many tasks, is a general comparison rather than a
  measurement against a named benchmark, and is presented as such.
- The "5-8 min to seconds" figure is the project's own statement about its own change and
  is not an independent measurement.
- Which specific workloads move under user control, and how many, is an argument about
  direction rather than a counted figure.

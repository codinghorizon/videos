---
layout: default
title: "Local AI Hardware: The Spec Nobody Warns You About"
permalink: /what-you-need-to-run-local-ai/
date: 2026-08-17
---

# Local AI Hardware: The Spec Nobody Warns You About

{% raw %}
Every figure, name, version and claim the finished picture puts on screen, chased to a
primary source. Worked from the `TEXT:` lines in BEATS.md, so nothing on screen is missed.

This video's script was written before any shot existed and was recorded word for word, so
the narration cannot be corrected by editing a component. Where a figure could not be
sourced it is listed under **Not checked** at the bottom rather than presented as a fact,
and the shots that render those figures present them as worked examples of a mechanism
rather than as measurements.

---

## Tooling and system requirements

**LM Studio recommends 16 GB of RAM, and at least 4 GB of dedicated VRAM on Windows.**
On macOS the guidance is "16GB+ RAM recommended", with the note that "You may still be able
to use LM Studio on 8GB Macs, but stick to smaller models and modest context sizes". macOS
requires Apple Silicon (M1/M2/M3/M4); Intel Macs are not supported. Windows is supported on
x64 and ARM, Linux on x64 and ARM64.
- https://lmstudio.ai/docs/app/system-requirements

Shots: `063-lm-studio-recommends`, `064-eight-gb-tight-room`, `178-pick-a-tool-run-it`.

**LM Studio runs a local server exposing OpenAI-style endpoints.** The documentation
describes "chat, responses, embeddings, and other familiar OpenAI-style endpoints", started
with `lms server start --port 1234`.
- https://lmstudio.ai/docs/app/api

Shots: `128-lm-studio-approachable`, `079-ollama-and-lm-studio-serve`.

**LM Studio ships an MLX engine for Apple Silicon alongside its llama.cpp/GGUF support.**
Version 0.3.4 "ships with an MLX engine for running on-device LLMs super efficiently on
Apple Silicon Macs", and users can "mix and match `llama.cpp` and MLX models".
- https://lmstudio.ai/blog/lmstudio-v0.3.4

Shots: `114-what-a-mac-can-do`, `138-model-formats`.

**Ollama exposes OpenAI-compatible endpoints on `http://localhost:11434/v1`.** The
documented endpoints are `/v1/chat/completions`, `/v1/completions`, `/v1/models`,
`/v1/embeddings` and `/v1/responses`. The API key is required by the client but ignored.
- https://docs.ollama.com/api/openai-compatibility

Shots: `081-point-at-the-endpoint`, `084-local-address-not-cloud`, `130-pull-run-serve-connect`,
`136-a-local-endpoint`, `137-connect-everything`, `193-connect-what-you-use`.

**llama.cpp's stated goal and its backends.** The project aims "to enable LLM (and VLM)
inference with minimal setup and state-of-the-art performance on a wide range of hardware".
The README lists CUDA (NVIDIA), Metal (Apple Silicon), HIP (AMD), Vulkan, SYCL (Intel) and a
dependency-free CPU implementation, plus BLAS, CANN, MUSA, OpenCL and WebGPU.
- https://github.com/ggml-org/llama.cpp

Shots: `132-practical-across-machines`, `056-nvidia-cuda`, `057-amd-rocm`, `043-offload-to-cpu`.

**llama.cpp supports 1.5-bit through 8-bit integer quantisation**, "for faster inference and
reduced memory use", which is where the 4 bit, 5 bit and 8 bit names the script mentions
come from.
- https://github.com/ggml-org/llama.cpp

Shots: `034-four-five-eight-bit`, `032-quant-is-the-trick`, `177-things-you-do-not-need`.

**GGUF is a single-file format for GGML-family executors.** It is "designed for fast loading
and saving of models, and for ease of reading", supports memory-mapped loading, and is the
successor to GGML, GGMF and GGJT, the last of which was what llama.cpp previously used.
- https://github.com/ggml-org/ggml/blob/master/docs/gguf.md

Shots: `138-model-formats`, `139-not-every-file-works`.

**Apple showed local agentic AI on the Mac using MLX at WWDC26.** Session 232, "Run local
agentic AI on the Mac using MLX", describes a four-layer stack: MLX (the array framework for
Apple silicon), MLX-LM (loading, running, quantising and fine-tuning models), MLX-LM Server
(an OpenAI-compatible HTTP server with structured tool calling, described as a drop-in
replacement for a cloud LLM API), and any agent framework that speaks the OpenAI chat
completions protocol. Install is `pip install mlx-lm`.
- https://developer.apple.com/videos/play/wwdc2026/232/

Shots: `058-apple-mlx`, `133-mlx-on-apple`, `134-apple-agentic-mlx`, `114-what-a-mac-can-do`,
`080-llamacpp-and-mlx-serve`.

**The KV cache is a real memory cost that grows with context.** Hugging Face's Transformers
documentation states that "The KV cache can occupy a significant portion of memory and become
a bottleneck for long-context generation", and that the default dynamic cache "allows the
cache size to grow dynamically in order to store an increasing number of keys and values as
generation progresses". Offloading it to CPU is offered specifically for small-GPU
out-of-memory cases, and quantised caches trade quality for size.
- https://huggingface.co/docs/transformers/en/kv_cache

Shots: `025-context-size`, `087-kv-cache-costs`, `088-fits-until-you-ask`, `086-context-needs-room`.

---

## Model sizes on screen

**Ollama's published download sizes** for the models the shots name by name:

| Model | Published size |
|---|---|
| `qwen3:4b` | 2.5 GB |
| `qwen3:14b` | 9.3 GB |
| `qwen3:30b` | 19 GB |

- https://ollama.com/library/qwen3

Shots: `062-install-and-talk`, `104-storage-matters`, `105-the-model-shelf`, `130-pull-run-serve-connect`,
`140-let-the-tool-download`, `160-download-and-keep-modest`, `178-pick-a-tool-run-it`,
`191-models-with-jobs`, `195-no-job-no-space`, `077-stronger-and-real-work`, `088-fits-until-you-ask`,
`043-offload-to-cpu`, `034-four-five-eight-bit`.

**The 7B / 14B / 30B / 70B memory line is a derivation, and says so.** `ch1-memory.tsx`
computes each figure as `parameters × 0.606 + 0.81` GB. The two constants are fitted to the
two published points above (14B at 9.3 GB and 30B at 19 GB), so the 7B (5.1 GB) and 70B
(43.2 GB) figures sit on the same line as real, checkable sizes rather than on chosen
numbers. It is an approximation of 4 bit quantised weights, not a spec for any one model.

Shots: `024-mental-model`, `028-seven-and-fourteen-b`, `029-thirty-b`, `030-seventy-b`,
`179-not-the-largest-model`.

---

## Not checked

Everything below appears on screen as a **worked example of a mechanism**, not as a measured
or sourced figure. The script asserts the shape of each of these and the picture illustrates
it; none of them could be chased to a primary source, because each depends on a specific
machine, model, quantisation and workload.

- Every tokens-per-second figure (42, 46, 6, 1.6, 0.9 tok/s, and the offload curve across
  41 to 0 GPU layers). Throughput is hardware and model specific and nothing here was
  measured on a real machine.
- Every price: the $2,400 and $4,200 builds, the $6,800 frontier build, the $1,890 used
  enterprise GPU, the Mac memory tier prices ($1,599 / $2,199 / $3,199 / $4,699), the $0.14
  per cloud turn, the $0.31 API call, and the $20 a month subscription the break-even
  arithmetic divides into. The 210 month / 17.5 year break-even is honest arithmetic on
  those illustrative inputs, not a market figure.
- The KV cache gigabyte figures per context length. These are model-architecture dependent;
  the direction (linear growth with context) is sourced above, the specific gigabytes are not.
- The per-workload memory bars in `008-not-the-same-problem` (chat 5.4 GB, code 19.8 GB,
  vision 12.6 GB, voice 8.2 GB, agents 38.5 GB).
- The laptop telemetry gauges in `120-thermals-and-fans` (74 W, 86 °C, 5,076 RPM, 18 %).
- "RTX Ultra Max Pro" in `121-glamorous-name-small-vram` is a deliberately invented product
  name standing in for the pattern the script describes. It is not a real product and the
  6 GB against it is not a real spec.
- The 3 s versus 41 s model load in `107-external-drives`.
- The model folder totals (38.2 GB and 114.4 GB, both summed on screen from the listed files) and the individual sizes for
  `llava-vision-7b-Q5.gguf`, `whisper-large-v3.bin` and `bge-m3-embeddings.gguf`.
- The 42 to 6 cloud calls per day in `153-cloud-calls-intentional`, and the 34% to 80%
  capability shift in `184-borderline-becomes-useful`.
- The VRAM ladder (4 / 8 / 12 / 16 / 24 / 32 GB) and the RAM ladder (16 / 32 / 64 / 128 GB)
  and the tier table in chapter nine are the script's own editorial recommendations, quoted
  as the script states them. They are not sourced benchmarks and are not presented as such.
- The 1 TB and 2 TB storage advice is the script's own recommendation.
- All terminal output is illustrative. The commands are real and the flags are real, but the
  byte counts, timings and log lines were written for the shot rather than captured from a run.
{% endraw %}

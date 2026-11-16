---
layout: default
title: "Make Your Local AI 10x Faster Without New Hardware"
permalink: /make-local-ai-10x-faster-free/
date: 2026-11-16
---

# Make Your Local AI 10x Faster Without New Hardware

{% raw %}
What the shots put on screen, and the source for each figure. Sources are the script's own
`### SOURCES` list (original-scripts/make-local-ai-10x-faster-free.md). Captures were taken on
15 November 2026 at 2x into public/make-local-ai-10x-faster-free/web/; each `.json` beside a
capture holds its url and the find the ring sits on. No figure here is our own benchmark.

## A. Opening (001 to 009)
- 31,037 tokens re-read in 87.59 s on every message: odysseus-dev/odysseus issue #4541
  (github.com/odysseus-dev/odysseus/issues/4541). Captures bug-title, bug-report. On screen 002 as
  "31,037 tokens read · 87.59 s"; 001 rounds it to "almost 90 s" as the voice does.
- "About half a second" for a short follow-up with the cache kept, and "well over ten times
  faster": the script's arithmetic from the same report (a ~200 token follow-up read at the same
  speed). On screen as said.

## B. Memory bandwidth sets token generation (010 to 027)
- Decode is memory-bound, every weight read per token: Databricks, LLM inference performance
  engineering best practices.
- Strix Halo measured memory bandwidth ~215 GB/s; 70B Q4_K_M 4.5 to 5.0 tok/s: Level1Techs
  Strix Halo benchmark thread. Capture strix-bench (ring on "~215 GB/s"), beat 019.
- Llama 3.3 70B Q4_K_M = 42.5 GB: bartowski/Llama-3.3-70B-Instruct-GGUF on Hugging Face.
- 215 / 42.5 = 5.06 tok/s ceiling: derived from the two above.
- Draft model (speculative decoding) is named only, no figure.

## C. Prompt processing is a separate job (028 to 049)
- First token is compute-bound: Databricks (above); Apple ML Research, LLMs with MLX on M5.
- gpt-oss-20b on M3 Ultra, pp32768 1351.67 tok/s against tg128 115.52 tok/s: llama.cpp
  discussion #15396. Capture gptoss (two rings, rows pp32768 and tg128).
- Viewer comment (034 to 035), printed verbatim: "slowest for first token generation due to
  the memory bandwidth", under our video q_SB0KujeeU (YouTube comments tool).

## D. Same machine, seconds or minutes (050 to 071)
- The bookmark is the KV / prompt cache; llama.cpp server `cache_prompt`: llama.cpp server
  README. Figures in this chapter are the odysseus report's, re-used.

## E. Ollama keep_alive and the 4K default (072 to 095)
- keep_alive default 5 minutes: Ollama FAQ. Capture keepalive.
- Default context 4K; 64,000 tokens recommended for agents and coding: Ollama context length
  docs. Captures ctx4k, ctx64k.
- Overflow keeps the start and drops the middle: ollama llm/llama_server.go.
- KV cache quantisation q8_0 halves cache memory: Ollama FAQ. Capture kvq.

## F. Coding agents (096 to 116)
- Prompt caching needs an exact prefix match; working directory, OS and a git snapshot sit at
  the start: Claude Code prompt caching docs. Capture prefix ("The match is exact").
- CLAUDE_CODE_ATTRIBUTION_HEADER, fixed in v2.1.181: Claude Code environment variables docs.
  Shown as its effect, not as code (RETENTION.md note on 105).
- OpenClaw message id in the system prompt forced full re-processing per message: openclaw
  issue #20430 (closed as likely solved by PR #20597).
- "Every message triggers full prompt reprocessing": odysseus issue #4541, capture bug.

## G. LM Studio rolling window (117 to 131)
- Default context 8K since 0.4.16: LM Studio changelog. Capture lms.
- Context overflow policies (rolling window, truncate middle, stop): LM Studio docs.

## H. Dense vs mixture of experts (132 to 144)
- Qwen3-30B-A3B: 30.5B total, 3.3B active: model card. 66.3 to 72.0 tok/s on Strix Halo;
  Mistral Small 3.1 24B 13.6 to 14.3: Level1Techs thread.
- gpt-oss-20b: 21B total, 3.6B active, runs in 16 GB: model card.

## I. Hidden thinking tokens (145 to 159)
- 901 tokens of thinking for "2+3=?", answer at token 39: arXiv 2412.21187. Capture paper.
- Qwen3 thinks by default, /no_think; Ollama `think` false; gpt-oss reasoning levels: Qwen3
  model card, Ollama thinking docs, gpt-oss model card.

## J. Open WebUI (160 to 169)
- Task model jobs (titles, tags, follow-ups) "can slow down your main chat model": Open WebUI
  performance docs. Capture owui. Task models: Open WebUI admin docs.

## K. Where the chip matters (170 to 187)
- RTX 5090 pp512 14073.41, tg128 290.02; RTX 3090 5174.69 and 158.16: llama.cpp CUDA
  scoreboard, discussion #15013.
- M3 Ultra pp512 1471.24, tg128 92.14 (Llama 2 7B Q4_0): llama.cpp discussion #4167.
- M4 120 GB/s vs M5 153 GB/s, 19 to 27% faster generation: Apple ML Research (MLX on M5).
  Capture apple ("up to 4x faster than M3", Apple Newsroom).
- 185: affiliate links, `(#ad)` pill from frame 0 (HARD_CUT). Prices: none spoken (check-prices).

## L. The checklist (188 to 207)
- Recaps the settings above; no new figures.
{% endraw %}

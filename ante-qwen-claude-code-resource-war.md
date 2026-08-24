---
layout: default
title: "Claude Code Has A New Problem Nobody Is Measuring"
permalink: /ante-qwen-claude-code-resource-war/
date: 2026-08-24
---

# Claude Code Has A New Problem Nobody Is Measuring

{% raw %}
Every figure this video puts on screen, chased to a primary source.

## 1. The resource benchmark

Antigma's own measurement page for Ante.

**Source:** Antigma Labs, "Resource Footprint", Ante documentation.
https://docs.antigma.ai/benchmarks/compare_table

Methodology, in Antigma's words: "we ran the same 20 tasks in parallel through Ante,
Claude Code, and Opencode, each inside Docker with identical constraints, and recorded
CPU, memory, and disk usage throughout the run."

### Wall time (seconds)

| Agent | Wall time |
| --- | --- |
| Ante | 940 |
| Claude Code | 627 |
| Opencode | 1076 |

### CPU usage (%)

| Agent | Peak | Avg | P95 | P99 |
| --- | --- | --- | --- | --- |
| Ante | 94.4 | 1.3 | 6.2 | 12.3 |
| Claude Code | 89.5 | 12.1 | 31.0 | 43.4 |
| Opencode | 90.8 | 3.8 | 27.1 | 62.3 |

Average CPU ratio, Claude Code against Ante: 12.1 / 1.3 = 9.3x. The video says "roughly
nine times higher".

### Memory usage (MiB)

| Agent | Peak | Avg | P95 | P99 |
| --- | --- | --- | --- | --- |
| Ante | 1968 | 683 | 1489 | 1550 |
| Claude Code | 13877 | 3685 | 8927 | 9535 |
| Opencode | 12944 | 2077 | 11266 | 12852 |

Peak memory ratio, Claude Code against Ante: 13877 / 1968 = 7.05x. The video says
"roughly seven times higher".

### Disk usage (MiB)

| Agent | Peak | Avg | P95 | P99 |
| --- | --- | --- | --- | --- |
| Ante | 7041 | 3121 | 6975 | 6976 |
| Claude Code | 22467 | 4304 | 10128 | 10193 |
| Opencode | 59689 | 6046 | 29108 | 34744 |

### Disk read rate (MB/s)

| Agent | Peak | P95 | P99 |
| --- | --- | --- | --- |
| Ante | 3.5 | 0.0 | 0.1 |
| Claude Code | 263.9 | 10.4 | 101.9 |
| Opencode | 284.1 | 0.1 | 10.6 |

### Disk write rate (MB/s)

| Agent | Peak | P95 | P99 |
| --- | --- | --- | --- |
| Ante | 186.3 | 3.6 | 61.7 |
| Claude Code | 302.3 | 26.6 | 113.0 |
| Opencode | 302.9 | 14.5 | 296.6 |

### Total disk I/O (MB)

| Agent | Total read | Total write |
| --- | --- | --- |
| Ante | 24 | 2785 |
| Claude Code | 17444 | 15116 |
| Opencode | 2224 | 31427 |

Total write ratio, Claude Code against Ante: 15116 / 2785 = 5.4x. That is the row the
"five times less disk I/O" headline rests on. Total read ratio is 17444 / 24 = 727x, and
17444 MB is 17.4 GB, which is what the video compares against Ante's 24 MB.

## 2. What Ante is

**Source:** Antigma Labs, Ante repository README.
https://github.com/AntigmaLabs/ante

- "One ~15MB compressed download ... that expands to a single Rust executable with zero
  runtime dependencies."
- Unpacks to 34.1 MiB.
- "Ante is hand-written Rust: the heavy parts (`Grep`, `git`) are embedded in one binary
  and one process, and local inference is handled by a managed llama.cpp."
- Named for "**An**other **Te**rminal agent, and *ante*, the stake you put on the table
  to play."
- Session resume: `ante --resume <session id>`.

**Source:** Antigma Labs, "Philosophy", Ante documentation.
https://docs.antigma.ai/start/philosophy

The stated thesis is "cellular-native" agents: "agents should be lightweight enough to
run by the thousands". "We're running hundreds and thousands of agent replicas. Each one
can't cost a couple GB of memory."

The sentence the video calls the most important one in the docs is on the resource page:
"Mass parallelism only pays off if a single agent is cheap enough to multiply."

## 3. Terminal sessions

**Source:** Antigma Labs, "Interactive TUI", Ante documentation.
https://docs.antigma.ai/usage/tui

"The agent drives interactive programs — dev servers, REPLs, ssh, even other CLI agents
like Claude Code or Codex — in durable named tmux sessions ... Sessions live in the
`ante-` namespace and survive Ante restarts: a later conversation can pick up a running
server where it was left."

`/term <name>` attaches or detaches a named session
(https://docs.antigma.ai/usage/slash-commands).

## 4. Local models

**Source:** Antigma Labs, "Offline Mode", Ante documentation.
https://docs.antigma.ai/local/offline

Offline mode runs the full agent loop against a local GGUF model through a managed
llama.cpp build. "Once a model is on disk, inference needs no network connection at all."

**Source:** Antigma Labs, "Verified Models", Ante documentation.
https://docs.antigma.ai/local/verified-models

| Model | Quant | Download | Max context | Status |
| --- | --- | --- | --- | --- |
| Qwen3.8 27B | Q4_K_M | 17 GB | 256K | Verified |
| MiniMax M2.7 | Q3_K_XL | 102 GB | 192K | Verified |
| Qwen3.5 122B A10B | Q2_K | 45 GB | 256K | Verified |
| Qwen3.6 35B A3B | Q4_K_M | 22 GB | 256K | Verified |
| Qwen3.6 27B | Q4_K_M | 17 GB | 256K | Evaled, 56.2% on Terminal Bench 2.1 |
| GLM 4.7 Flash | Q4_K_M | 18 GB | 198K | Verified |
| Gemma 4 26B A4B | Q4_K_M | 16 GB | 256K | Verified |
| Devstral Small 2 24B | Q4_K_M | 14 GB | 384K | Verified |
| Qwen3.5 9B | Q4_K_M | 5.7 GB | 256K | Verified |
| Gemma 4 E4B | Q4_K_M | 4.7 GB | 128K | Verified |

Antigma defines the two statuses on the same page. **Verified** means "the model loads,
the chat template resolves, and tool calling works in Ante's agent loop. Not yet through
the full eval." **Evaled** means it "ran the full public benchmark: same Terminal-Bench
2.1 harness, pinned builds, and auditable Harbor runs".

The one Evaled row: "Qwen3.6 27B reached 56.2% accuracy across 89 Terminal-Bench 2.1
tasks with 445 trials — a 17 GB download holding its own on the same benchmark we use for
frontier models."

## 5. Ante's own benchmark constraints

**Source:** Antigma Labs, "Terminal-Bench", Ante documentation.
https://docs.antigma.ai/benchmarks/eval

"All trials use the same parameters as the official Terminal-Bench leaderboard: 89 tasks,
5 trials per task, strict timeouts and hardware limits." 89 x 5 = 445 trials.

Ante's own headline figure at the time of writing is 82.7% on Terminal Bench 2.1 with
DeepSeek V4 Flash 0731, across 368 of 445 trials passing.

## 6. Qwen3.8 27B

**Source:** Qwen, Qwen3.8-27B model card, Hugging Face.
https://huggingface.co/Qwen/Qwen3.8-27B

- 27 billion parameters, dense rather than mixture of experts.
- Native vision language model: understands images and video.
- Flexible thinking control, including reasoning effort levels.
- Native context length 262,144 tokens, extensible to 1,000,000.
- Apache 2.0.
- Released August 2026.

Benchmark rows quoted in the video:

| Benchmark | Qwen3.8 27B | Qwen3.6 27B | Opus 4.6 Max |
| --- | --- | --- | --- |
| Terminal Bench 2.1 (Terminus) | 73.0 | 63.4 | 78.2 |
| SWE Bench Pro | 61.7 | 53.5 | 53.4 |

The model card states that SWE Bench Pro figures other than Opus 4.6 Max were produced
with the Claude Code harness at temperature 1.0, top_p 0.95, and a 256K context window.
That is a different harness from the one Ante's own 56.2% figure was produced under, which
is exactly why the video says the two sets of numbers should not be combined.

## Caveats

- The resource comparison is Antigma's own measurement of its own product. No independent
  reproduction of it was found.
- Antigma publishes the resource table and the methodology sentence, but does not describe
  what the twenty parallel tasks actually were, so the workload cannot be reproduced from
  the page alone.
- Ante's Terminal Bench results are self published, though Antigma links a raw Harbor run
  for each and pins the released binary the run used.
- Qwen3.8 27B is listed by Ante as Verified rather than Evaled, so no Ante measured score
  for it exists at the time of writing. Its 73.0 and 61.7 come from Qwen's own card under
  other harnesses.
{% endraw %}

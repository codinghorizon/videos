---
layout: default
title: "Letta Makes Local AI Finally Remember Your Work"
permalink: /letta-local-ai-memory-agent/
date: 2026-09-08
---

# Letta Makes Local AI Finally Remember Your Work

{% raw %}
Every figure, name and claim the finished picture puts on screen, chased to a primary
source. Checked 7 September 2026.

## Letta on GitHub

The narration says Letta has more than twenty five thousand GitHub stars across its
repos. Measured from the GitHub REST API on 7 September 2026, across the 61 public
repositories in the `letta-ai` organisation:

| Repository | Stars |
| --- | --- |
| `letta-ai/letta` | 24,645 |
| `letta-ai/letta-code` | 3,224 |
| `letta-ai/claude-subconscious` | 2,885 |
| `letta-ai/agent-file` | 1,197 |
| `letta-ai/lettabot` | 326 |
| `letta-ai/trajectory` | 247 |
| Organisation total, 61 public repos | 34,020 |

The main platform repository alone is 24,645, and it plus `letta-code` is 27,869, so
"more than twenty five thousand across its repos" holds with room to spare.

Source: GitHub REST API, `api.github.com/orgs/letta-ai/repos` and
`api.github.com/repos/letta-ai/letta`, read 7 September 2026.

## What a Letta agent is given

Letta describes itself as a platform for stateful agents with memory that can learn
and self improve over time. The agent surface includes persistent memory, identity,
skills, tools, subagents and schedules.

- Skills are "directories containing instructions and resources that your agent can
  load when relevant", scoped to the project, to the agent's own memory, or bundled
  with the harness. Source: https://docs.letta.com/configuration/skills
- Subagents: "It is possible to deploy an arbitrary Letta Agent as a subagent by
  specifying its agent_id." Source: https://docs.letta.com/letta-agent/subagents
- Schedules drive recurring work such as planning, triage and reporting.
  Source: https://docs.letta.com/handbook

## MemFS, the git backed memory filesystem

Letta agents use MemFS, described in the documentation as "a git-backed memory
filesystem that they can inspect and edit". The memory itself "is part of the agent's
state, held in a git repository that belongs to the agent".

- Projection: "Each memory is projected as Markdown with YAML frontmatter."
- Directory shape, as published:

```
$MEMORY_DIR/
├── system/
│   ├── persona.md
│   └── human.md
├── reference/
│   └── project-notes.md
└── skills/
    └── my-skill/
        └── SKILL.md
```

- What is in context: "Files under `system/` are loaded into the agent's system prompt
  on every turn." Everything else: "Files outside `system/` stay out of context until
  they are needed."
- Version history: "Every memory edit is committed to the MemFS git repository. This
  provides version history, conflict resolution, and a clear boundary between saved
  memory and uncommitted changes."

Sources: https://docs.letta.com/concepts/memfs and
https://docs.letta.com/configuration/memory

## Models, and swapping them under a running agent

Supported hosted providers include Anthropic (Claude Opus 4.6, Claude Opus 4.5,
Claude Sonnet 4.5, Claude Haiku 4.5), OpenAI (GPT 5.2, GPT 5.2 Codex) and Google
(Gemini 3 Pro, Gemini 3 Flash).

Local inference providers are supported for local agents: Ollama, LM Studio and
llama.cpp. The documentation states that direct integrations with local inference
providers such as LM Studio, Ollama and llama.cpp are available for local agents, and
that to keep inference local you connect one of them.

On switching: "Agents keep their memory and tools when you change models."

Sources: https://docs.letta.com/v1-sdk/models, https://docs.letta.com/configuration/models
and https://docs.letta.com/self-hosting

## Context-Bench

Letta's Context-Bench measures "how well language models can chain file operations,
trace entity relationships, and manage multi-step information retrieval in
long-horizon tasks". Published 30 October 2025.

| Model | Score | Benchmark cost |
| --- | --- | --- |
| Claude Sonnet 4.5 | 74.0% | $24.58 |
| GPT 5 | 72.67% | $43.56 |
| GPT 5 mini | 64.33% | $12.45 |
| GLM 4.6 | 56.83% | not published in the post |
| Kimi K2 | 55.13% | $12.08 |
| GPT 5 nano | 44.83% | not published in the post |
| GPT OSS models | 6.67% to 20.2% | not published in the post |
| DeepSeek V3 | 11.97% | not published in the post |
| GPT 4.1 nano | 16.2% | not published in the post |

GPT 5's $43.56 against Claude Sonnet 4.5's $24.58 is 1.77 times the cost for 1.33
points less, which is what the narration means by "almost twice the benchmark cost".
Kimi K2 at $12.08 for 55.13% is the best cost per point of the open weight entries.

Source: https://www.letta.com/blog/context-bench/ and the live board at
https://leaderboard.letta.com/

## Memory in production agents

Letta's July 2026 evaluation covers adherence, retrieval, generalization and hygiene,
across tasks that generate, clean and repair memory. Published 28 July 2026.

- "Anthropic models lead overall, with the widest margin in memory generation."
- "OpenAI models offer strong cost-performance but trail on memory generation."
  GPT 5.6 Sol leads among the OpenAI entries, and smaller models fall off more sharply
  when they have to rewrite memory rather than use existing context.
- Among open weight models, Kimi K3 is the strongest, and is better at repairing
  memory than at extracting a durable lesson, ahead of MiniMax M3 and GLM 5.2.

Source: https://www.letta.com/blog/evaluating-memory-in-production-agents

## Memory rot

The term is Letta's own. From "Memory Models: Towards Agents That Learn", published
25 June 2026: "This can lead to memory rot over time for long-lived agents, and limit
the extent to which agents can learn independently from available context or past
experience." The same piece identifies overgeneralization and memory rot as failure
modes of existing memory-creation approaches. Hygiene is one of the four axes of the
July 2026 production memory evaluation above.

Sources: https://www.letta.com/blog/towards-agents-that-learn/ and
https://www.letta.com/blog/evaluating-memory-in-production-agents

## The product surface

- Letta Code runs in the terminal, installed with `npm install -g @letta-ai/letta-code`
  and launched as `letta`. Node 22.19 or newer.
- The desktop app ships for macOS (Apple Silicon), Windows (x64 and ARM64) and Linux
  (AppImage, x64 and ARM64). Agents created in the CLI appear in the desktop app and
  the other way round.
- An App Server runs local or self hosted agents; Letta Cloud runs cloud agents whose
  state is available across machines.
- Channels carry messages in and out. The documented set is Slack, Telegram, Discord,
  WhatsApp and Signal, plus custom channels, which are headless and configured from
  local config files.

Sources: https://docs.letta.com/letta-agent/desktop-app,
https://github.com/letta-ai/letta-code, https://docs.letta.com/self-hosting,
https://docs.letta.com/configuration/channels and
https://docs.letta.com/configuration/channels/custom

## What actually fits in eight, sixteen and twenty four gigabytes

Download sizes for the default quantization of each tag, read from the Ollama
registry manifests on 7 September 2026. These are weights on disk, which is the floor
for what has to be resident; context and key value cache are on top.

| Model | Size |
| --- | --- |
| Qwen2.5 Coder 7B | 4.7 GB |
| Llama 3.1 8B | 4.9 GB |
| Qwen3 8B | 5.2 GB |
| Gemma 3 12B | 8.1 GB |
| Qwen3 14B | 9.3 GB |
| Qwen3 Coder 30B | 18.6 GB |

That is the shape the narration describes: a seven or eight billion parameter model
clears eight gigabytes but leaves little for context, twelve to fourteen billion is
comfortable at sixteen, and a thirty billion parameter coding model needs a twenty
four gigabyte card before context is affordable.

The RTX 3090 and RTX 4090 both carry 24 GB of GDDR6X.

Sources: `registry.ollama.ai/v2/library/<model>/manifests/<tag>`, read 7 September
2026, and https://www.nvidia.com/en-us/geforce/graphics-cards/

## Not chased to a primary source

- The narration lists "browser" among Letta's channels. The documented channel set is
  Slack, Telegram, Discord, WhatsApp, Signal and custom channels; a browser channel is
  not named in the documentation, so it is not drawn on screen.
- Context-Bench costs for GLM 4.6, DeepSeek V3, GPT 5 nano and the GPT OSS entries are
  not published in the announcement post, so only their scores are drawn.
{% endraw %}

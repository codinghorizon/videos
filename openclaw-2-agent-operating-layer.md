---
layout: default
title: "OpenClaw 2.0 Is Coming For Your AI Coding Stack"
permalink: /openclaw-2-agent-operating-layer/
date: 2026-09-01
---

# OpenClaw 2.0 Is Coming For Your AI Coding Stack

{% raw %}
Every figure, version, benchmark and quoted limit this video puts on screen, chased to a
primary source. Checked 2026-08-31.

## The release

**OpenClaw 2.0 is the marketing name; the shipped version is 2026.8.1.**
The release is published as `v2026.8.1` and the documentation page for it is titled
"v2026.8.1 (AKA OpenClaw 2.0)".
Source: https://docs.openclaw.ai/releases/2026.8.1
Source: https://github.com/openclaw/openclaw/releases/tag/v2026.8.1

**Distribution.** The release ships native macOS downloads and npm packages alongside its
other install routes. Provider packages for several vendors are installable on demand
rather than bundled.
Source: https://github.com/openclaw/openclaw/releases/tag/v2026.8.1

**The headline features.** Search across session transcripts from the Control UI; moving
live sessions between the gateway and runners; surfacing sessions that need attention;
typed questions presented as live option cards; dashboards; credential handling during
setup; recurring approvals; and richer media attached to sessions.
Source: https://docs.openclaw.ai/releases/2026.8.1

**Storage.** 2.0 moves sessions and transcripts into SQLite, and the release notes ask for
verified backups before upgrading.
Source: https://docs.openclaw.ai/releases/2026.8.1

## Memory and dreaming

**Background consolidation is on by default.** OpenClaw enables model backed background
memory consolidation by default, promoting provenance qualified material into long term
memory. It is disabled with
`plugins.entries.memory-core.config.dreaming.enabled: false`.
Source: https://docs.openclaw.ai/concepts/dreaming

**The Dream Diary.** Phase summaries and diary entries are written to `DREAMS.md` for human
review, including rewrite counts and highlights. The diary is explicitly human only and is
not itself a promotion source.
Source: https://docs.openclaw.ai/concepts/dreaming

**Provenance gating.** Before the consolidation prompt is built, candidates whose indexed
provenance is untrusted or system are removed. The documentation describes this as a
structural taint gate rather than a score penalty, and states that promotion and injection
are both gated on provenance rather than on content appearing safe.
Source: https://docs.openclaw.ai/concepts/memory-architecture

**Bounded recall.** With Active Memory enabled, OpenClaw retrieves bounded same agent
private conversation context by default on personal installs without configured DM
isolation. Explicit controls disable recall, and groups and channels remain excluded.
Source: https://docs.openclaw.ai/concepts/memory

## Hardware for the gateway

**Minimum.** 1 GB RAM, 1 core, 500 MB free disk, and a 64 bit OS.
**Recommended.** 2 GB or more of RAM, and a 16 GB or larger card or USB SSD.
**Supported boards.** Raspberry Pi 4 or 5 with 2 GB or more, with 4 GB recommended. A 64 bit
Raspberry Pi OS is required.
Source: https://docs.openclaw.ai/install/raspberry-pi

## ClawArena

**What it measures.** A benchmark for agent reliability in evolving, multi session
information environments, scored by a Composite Reliability Score that combines task
completion rate with a robustness term rewarding sustained success streaks and penalising
clustered failures, macro averaged across the scenario set.

**Composition.** 12 multi turn scenarios, 337 evaluation rounds, 95 multiple choice
reasoning checks, 242 execution checks, and 45 dynamic updates that change files or chats
mid evaluation to test belief revision.

**Leaderboard, top three by Composite Reliability Score.**

| Rank | Model | Harness | Score |
| --- | --- | --- | --- |
| 1 | GPT 5.5 | OpenClaw | 68.28 |
| 2 | Claude Opus 4.7 | Claude Code | 66.31 |
| 3 | Gemma 4 31B | OpenClaw | 63.80 |

Source: https://github.com/aiming-lab/ClawArena
Source: https://arxiv.org/html/2604.04202v2

## The May performance sweep

Measured between the April baseline `v2026.4.14` and the May stable point `v2026.5.28`.

| Measure | Before | After |
| --- | --- | --- |
| Cold agent turn | 9,819 ms | 1,908 ms |
| Warm agent turn | 7,458 ms | 1,870 ms |
| Agent peak RSS | 686.2 MB | 581.0 MB |

**Install footprint.** The May line spiked at 1,020.6 MB fresh install size in `v2026.5.22`,
with nested `openclaw/node_modules` accounting for 911.8 MB of it. By `v2026.5.28` the
footprint was 361.7 MiB total, with nested modules down to 259.7 MiB.

**Dependency roots.** 300 unique package name and version roots in `v2026.5.28`, down from
645 at the February high of `v2026.2.26`, a reduction of 53.5 per cent. The step from 371
roots in `v2026.5.27` to 300 came from dropping an all platform native canvas package.

Source: https://docs.openclaw.ai/reference/release-performance-sweep

## Long context and what it costs

**GPT 5.6 Sol window.** OpenAI documents a 1,050,000 token provider window and 128,000
maximum output tokens. OpenClaw derives the safe active input budget as
1,050,000 total minus 128,000 maximum output, giving 922,000, and sets the automatic
compaction threshold at 700,000 active tokens.

**The pricing boundary.** OpenAI applies higher long context pricing once a GPT 5.5 or
GPT 5.6 request exceeds 272,000 input tokens: the whole qualifying request is billed at
2x input and cache rates and 1.5x output rates. OpenClaw defaults the active runtime budget
for those models to 272,000 tokens.

**Fast mode.** GPT 5.6 Sol Fast mode is a further 2x over Standard, so combined long context
Fast traffic is 4x short context Standard input side pricing and 3x short context Standard
output pricing.

**Expanding it is explicit.** A model's active input budget is overridden per model entry
with `models.providers.openai.models[].contextTokens`, so an expanded window is an opt in
configuration choice rather than a default.

Source: https://docs.openclaw.ai/providers/openai
Source: https://docs.openclaw.ai/reference/token-use

## Providers and routing

**Bundled providers named in the documentation** include OpenAI, Anthropic, Google for
Gemini, DeepSeek, Groq, NVIDIA, Ollama, LM Studio, vLLM, SGLang, OpenRouter, Qwen, Mistral
and Cohere.

**Allowlists and remembered selection.** `agents.defaults.modelPolicy.allow` is the explicit
override allowlist. Normal onboarding and reauthentication preserve an existing explicit
primary model, and adding authentication does not change the primary model unless
`--set-default` is passed.

Source: https://docs.openclaw.ai/concepts/model-providers

## Breaking changes in 2.0

**OpenProse.** The bundled OpenProse plugin and its `/prose` command are removed. Users are
pointed at `openclaw doctor --fix` to clean stale configuration and at the upstream Agent
Skill migration documentation. Existing `.prose` source files are retained.

**OpenAI route naming.** Model references using `codex/*` and `openai-codex/*` migrate to
`openai/*`. `openclaw doctor --fix` migrates provider configuration, stored sessions and
automation routes, flagging conflicts for review.

**Plugin SDK.** Several plugin SDK imports move to focused `openclaw/plugin-sdk/` subpaths,
effective 2026-09-01, covering configuration mutation, channel inbound and outbound
operations, and runtime helpers.

Source: https://github.com/openclaw/openclaw/releases/tag/v2026.8.1

## Caveats

**Meta as a listed provider.** The model providers page does not name Meta as a bundled
first party provider. Meta models are reachable, but through OpenRouter proxying rather
than a dedicated provider entry. The narration lists Meta among the providers the docs
name, and that is the one item in that list which is not a first party entry.

**"Many more" providers.** The bundled provider table is the verified set. The size of the
full surface beyond it, including community provider plugins, was not enumerated.

**The 200 tokens per second figure** used when describing what a gateway does not need to
do is a round illustrative number rather than a documented OpenClaw threshold, and is not
put on screen as a measurement of anything.
{% endraw %}

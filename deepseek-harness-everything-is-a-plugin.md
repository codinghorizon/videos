---
layout: default
title: "DeepSeek Harness: 127K Stars and One Huge Warning"
permalink: /deepseek-harness-everything-is-a-plugin/
date: 2026-08-17
---

# DeepSeek Harness: 127K Stars and One Huge Warning

{% raw %}
Every figure, date, version and quoted line the finished video puts on screen, chased to
a primary source. Checked 16 August 2026.

## The repository

`deepseek-ai/deepseek-harness`, MIT licensed, description "DeepSeek Harness: Everything
is a Plugin."

| On screen | Figure | Source |
|---|---|---|
| Stars | 128,000 | github.com/deepseek-ai/deepseek-harness |
| Forks | 12,800 | github.com/deepseek-ai/deepseek-harness |
| Watching | 526 | github.com/deepseek-ai/deepseek-harness |
| Commits | 12,293 | github.com/deepseek-ai/deepseek-harness |
| Created | 13 August 2026, 11:56 UTC | repository metadata |

The video states "more than one hundred and twenty seven thousand stars" and "more than
twelve thousand forks" and "more than twelve thousand commits". All three were true at
the time of checking and remain lower bounds on the live figures.

## The star curve

The chart in the opening and in chapter 2 plots four points.

| Date | Stars | Forks | Source |
|---|---|---|---|
| 13 Aug 2026 (launch day) | ~27,500 | ~2,000 | VentureBeat launch-day snapshot |
| 14 Aug 2026 | 88,975 | — | reported GitHub reading |
| 15 Aug 2026 | 95,386 | 8,826 | GitHub API, two days after publication |
| 16 Aug 2026 | 128,000 | 12,800 | github.com/deepseek-ai/deepseek-harness |

The "114,000 stars in three days" figure the video contrasts against the live number is
the figure circulating in coverage rather than a reading taken from the repository, which
is exactly the point the video makes about it.

## What the README says

- "DeepSeek Harness is currently in _developer preview_ and is iterating rapidly.
  **THERE WILL BE COMPATIBILITY-BREAKING CHANGES.**"
- Quickstart: `npx @deepseek-ai/dsh web`, which serves `http://127.0.0.1:3080` by default.
- "powered by Cordis, whose design is described in _A Programming Paradigm for
  Spatiotemporal Composability_."
- "Add the `dsh-plugin` topic to your plugin repository for discoverability."

The topic is written `dsh-plugin`, hyphenated, and is rendered that way on screen
throughout.

Source: github.com/deepseek-ai/deepseek-harness/blob/master/README.md

## Everything is a plugin

"Plugins provide every agent capability, including models, tools, skills, sessions,
sandboxes, storage, loops, scheduling, and the UI."

The Cordis kernel "manages plugin mounting, unmounting, and dependencies", and a
capability can be selected, swapped or extended in configuration without changing the
DeepSeek Harness source.

Sources: deepseek.com/harness, github.com/deepseek-ai/deepseek-harness/blob/master/docs/architecture.md

## The subsystems named on screen

profiles, bundles, services, events, session logs, web UI, headless mode, tool pipeline,
approval policy, settings, credentials, telemetry, sandbox, subagents, persistence.

Source: github.com/deepseek-ai/deepseek-harness/blob/master/docs/architecture.md

## The session log

- "Model-visible ⟺ logged: anything that reaches a model request must be reconstructable
  from the session log; a new model-visible input requires a session event."
  Source: github.com/deepseek-ai/deepseek-harness/blob/master/AGENTS.md
- "Everything the model sees is recorded in an append-only session log: system prompts,
  reasoning, tool calls and results, subagent scheduling, and every context injection."
- "Resume, fork, search, and replay all operate on the same event stream."
  Source: deepseek.com/harness

## Turns, steps and the hook points

- A step is "one model request plus the tools it calls".
- A turn is "zero or more steps: it opens before its first input is claimed and closes
  once nothing is owed".
- The hooks named on screen are real event names: `agent/pre-step` (listeners can rewrite
  or reject messages), `agent/request` (fires before streaming begins),
  `tools/pre-execute` / `tools/execute` / `tools/post-execute`, and `agent/turn-stopping`
  (a serial event that halts the turn).

Source: github.com/deepseek-ai/deepseek-harness/blob/master/docs/architecture.md

## Issues at launch

Issue creation is restricted on the repository and an issue search returns no results,
which is the basis for the video's point that no public issues at launch can mean the
feedback is somewhere else.

Source: github.com/deepseek-ai/deepseek-harness/issues

## DeepSeek V4-Pro

V4-Pro-0813 reached general availability on 13 August 2026, the same day the harness was
published. It is a 1.6-trillion-parameter model with 49 billion parameters activated per
token and a context window of up to one million tokens. The one million figure is what
the "context: 1M" row in chapter 5 renders.

DeepSeek's own reported benchmark scores at release were Terminal Bench 2.1 87.9,
Toolathlon-Verified 74.1, DSBench-FullStack 71.1 and DSBench-Hard 67.2, run using the
harness in minimal mode. None of these scores appears on screen.

## OpenClaw

OpenClaw crossed 100,000 GitHub stars roughly a week after going viral in late January
2026, and public trackers disagree on the exact figure, which is why the video gives a
range of two to seven days rather than a single number. It went on to pass React as the
most-starred project on GitHub in March 2026.

The 100,000 line drawn on the comparison chart is that milestone and nothing more.

## Not checked

- The relative size of the parts of a real agent bill. The video lists tokens, time,
  retries, trust, review and cleanup as the things a bill is made of, and no source
  gives a split between them, so the bar on screen divides them equally and states no
  percentage.
- The example plugin categories on the topic page, the example company profile and the
  example per-step cost breakdown are illustrations of what the architecture allows.
  They are labelled as such on screen and are not readings taken from the project.
- Relative sizes drawn as two bars beside each other (the same model in its own harness
  against somebody else's, model gains against harness machinery, DeepSeek against other
  models inside the harness) show the direction the video argues, not a measured
  difference. No source quantifies any of them and none is claimed on screen.
- Whether other model providers are fairly supported inside the harness in practice.
  The documentation describes adding model providers and swapping capability seams; how
  well that works is the open question the video puts, not a finding.
- Production adoption of any kind. Stars, forks and commits are the only adoption-shaped
  figures available three days after publication.
{% endraw %}

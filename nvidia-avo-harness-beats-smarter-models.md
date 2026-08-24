---
layout: default
title: "NVIDIA Just Proved Your AI Model Is Not Enough"
permalink: /nvidia-avo-harness-beats-smarter-models/
date: 2026-08-24
---

# NVIDIA Just Proved Your AI Model Is Not Enough

{% raw %}
Every figure, name and claim the finished picture puts on screen, chased to a primary
source.

## The ARC AGI 3 baseline

- **Claude Opus 5 scores 30.2% on ARC AGI 3**, at High reasoning effort, on the Public
  Demo set of 25 interactive environments. ARC Prize lists it as the highest performing
  model on that benchmark as of 24 July 2026, and notes it completed five Public Demo
  environments no model had previously beaten.
  Source: ARC Prize, Claude Opus 5 results —
  https://arcprize.org/results/anthropic-claude-opus-5
- The previous high score on ARC AGI 3 was **7.8%**, set by GPT 5.6 Sol at Max reasoning
  effort. ARC Prize also reports Anthropic's Fable class models at approximately 20% on the
  Public Demo environments.
  Source: ARC Prize —
  https://x.com/arcprize/status/2080716561539907928
- Opus 5's ARC AGI 3 run was evaluated only at High effort because of a short testing
  window, while the previous record holder was tested at Max.
  Source: ARC Prize, Claude Opus 5 results (above).
- ARC AGI 3 is an interactive benchmark rather than a question and answer test: the system
  is dropped into small game environments with rules it is not told, and has to explore,
  infer and act.
  Source: ARC Prize — https://arcprize.org/arc-agi/3/

## The NVIDIA AVO result

Primary source for everything in this section: NVIDIA Technical Blog, "NVIDIA AVO Reaches
100% on ARC-AGI-3, Demonstrating a Frontier-Level General-Purpose Architecture for
Long-Horizon Autonomous Agents" —
https://developer.nvidia.com/blog/nvidia-avo-reaches-100-on-arc-agi-3-demonstrating-a-frontier-level-general-purpose-architecture-for-long-horizon-autonomous-agents/

- **AVO stands for Agentic Variation Operators.**
- **100.00 RHAE score across all 25 environments in the ARC-AGI-3 public set, completing
  all 183 levels.**
- The run took **6,624 environment actions**, about **12% fewer** than VISTA's reported
  **7,542** actions for the same 183 levels.
- The model inside the AVO system was **Claude Opus 5**. NVIDIA cites ARC Prize's
  separately reported figure of **approximately 30% for Claude Opus 5 at High reasoning
  effort** as the model baseline.
- NVIDIA states the comparison is **not a controlled ablation**: "the two systems differ in
  agent backend, observation representation, memory, context management, and other
  implementation details."
- One concrete difference given: VISTA used a **512x512 PNG** observation, AVO used a
  **text only 64x64 grid**.
- The result is on the **public set only**. ARC Prize's semi private and private held out
  sets were not run.
- **The supervisor:** "The supervisor monitors the broader trajectory for stagnation or
  repeated unproductive cycles and can redirect the main agent toward alternative
  strategies when needed."
- **AVO's origin is engineering search, not games.** In GPU kernel optimisation work it
  **explored more than 500 optimisation directions and produced 40 committed kernel
  versions** over seven days, reaching up to **10.5% better performance than
  FlashAttention 4**.
- AVO was first introduced as a general purpose coding agent system in late March 2026.
- No open source release of AVO is announced in the post.

## Tools named on screen

- **Cursor** — AI code editor, https://cursor.com
- **Claude Code** — Anthropic's terminal coding agent, https://www.anthropic.com/claude-code
- **GitHub Copilot** — https://github.com/features/copilot
- **NVIDIA** — https://www.nvidia.com
- **ARC Prize** — https://arcprize.org

## Caveats

- "Different execution loop" as one of the ways the two setups differ is a fair reading of
  NVIDIA's "and other implementation details", but NVIDIA's own list names agent backend,
  observation representation, memory and context management explicitly and does not use
  that phrase.
- The seventy point gap between 30% and 100% is arithmetic on two numbers NVIDIA itself
  says are not a controlled comparison. It is not an attributable AVO gain.
{% endraw %}

---
layout: default
title: "Foxl Makes Every Other AI Agent Feel Backwards"
permalink: /foxl-ai-agent/
date: 2026-08-24
---

# Foxl Makes Every Other AI Agent Feel Backwards

{% raw %}
Every figure, name, date and capability this video puts on screen, chased to a primary
source. Checked 24 August 2026, against the product's own site and documentation.

## What Foxl is, and where it runs

Foxl ships as three products sharing one account: Foxl Agent (desktop and web),
Foxl Code (coding tasks against GitHub repos) and Foxl Notes (meeting transcription).

> "Foxl is a 24/7 personal AI agent. It ships as three products that share one account
> and one credit balance: Foxl Agent ..., Foxl Code ..., and Foxl Notes ..."

Source: https://docs.foxl.ai/llms.txt

Platforms: macOS, Windows and Linux, plus iOS through TestFlight and Android as a
direct APK.

Source: https://docs.foxl.ai/docs/get-started/download.md, https://foxl.ai/

## The real browser

Foxl drives the user's actual Chrome, with existing logged in sessions.

> "Foxl's most powerful feature is browser automation using your actual Chrome browser
> with all your logged-in sessions intact."

> "The Chrome Extension uses your real browser sessions. When you're logged into Gmail
> in Chrome, Foxl can read your email."

Source: https://docs.foxl.ai/docs/desktop/browser.md

## Approval gates

> "Dangerous actions - shell commands, file writes, browser navigation - require your
> explicit OK before execution."

Source: https://foxl.ai/

## Pricing and model access

The product is free with every feature unlocked, and the model access is supplied by
the user.

> "Free, with every feature unlocked. Bring your own model key or run one locally."
> "Free forever."

Three routes are offered: an OAuth subscription (Claude Pro or Max, ChatGPT Plus or
Pro, Gemini CLI), the user's own API key (Anthropic, OpenAI, Google, Amazon Bedrock),
or a local model (Ollama, vLLM, LM Studio). Users "pay the provider directly at their
published rates".

Foxl serves no inference of its own: "foxl.ai does not serve model inference. Its
hosted catalog is empty and a completion request to it is refused with
`409 hosted_inference_disabled`."

Sources: https://foxl.ai/pricing, https://docs.foxl.ai/docs/desktop/providers.md

## Foxl Code: the flow

A per user orchestrator turns a conversation into pull requests. It writes a Task
Document in markdown; each top level checkbox is one unit of work mapping to one pull
request; the user confirms once and the orchestrator then spawns an agent per checkbox.

> "A Task Document is the orchestrator's plan, written in markdown. Each top-level
> checkbox is one unit of work that maps to one pull request."

> "You confirm once. The orchestrator spawns a coding agent for every checkbox in a
> single step - they run concurrently, each on its own VM."

Source: https://docs.foxl.ai/docs/foxl-code/how-it-works.md

## Foxl Code: where the agents run, and the six backends

> "Each task is carried out by a coding agent - a real coding CLI running in an isolated
> Amazon Bedrock AgentCore microVM with a full filesystem and terminal. Foxl Code ships
> six interchangeable backends."

The six are Claude Code (default), Kiro, Codex, Cursor, Hermes and OpenCode.
Kiro and Cursor run on the user's own API key.

> "Every task runs in a fresh AgentCore micro-VM" with "no state leakage between tasks",
> and agents "from different users never share a VM or session."

Source: https://docs.foxl.ai/docs/foxl-code/coding-agents.md, https://foxl.ai/code

## Privacy

Conversations, files, memory and API keys stay on the user's own hardware; the relay is
described as a stateless zero knowledge proxy that forwards encrypted packets it cannot
read; local models never leave the machine.

Source: https://foxl.ai/, https://docs.foxl.ai/docs/desktop/providers.md

## Memory on disk

Foxl keeps two kinds of memory. Workspace memory is human readable markdown in the
user's workspace directory, and can be read, edited or deleted directly:
`SOUL.md` (injected as the system prompt every turn), `USER.md`, `MEMORY.md`,
`AGENTS.md`, `TOOLS.md`, plus dated daily summaries at `memory/YYYY-MM-DD.md`.
Alongside it there is a key value store held in SQLite, which is not markdown.

Source: https://docs.foxl.ai/docs/desktop/memory.md

## Scheduling

Foxl runs scheduled work on the user's own machine, including a background service that
keeps the machine reachable after the app is closed.

Sources: https://docs.foxl.ai/docs/desktop/scheduling.md,
https://docs.foxl.ai/docs/desktop/background-service.md

## The changelog entry of 24 August 2026

Release v0.6.15, dated 24 August 2026, carries all three items named in the video:

> "Hermes is selectable in Foxl Code."
> "Drag a workspace file straight into the agent's prompt."
> "Foxl Code: browse your repository's open issues and pull requests in-app."

The third adds a Backlog tab showing open GitHub items.

Source: https://foxl.ai/changelog

## Caveats

- **Memory is not entirely markdown.** The marketing site describes agent memory as
  plain markdown on disk, and the workspace memory files are exactly that. The
  documentation also describes a separate key value memory held in SQLite. The video
  says the markdown memory is readable on disk, which is accurate, but "all of Foxl's
  memory is markdown" would not be.
- **Foxl supplied model access is currently switched off.** The Claude Code, Hermes and
  OpenCode backends are documented as drawing on Foxl supplied model access, which the
  docs state is switched off at the time of checking. Bringing a key, a subscription or
  a local model is therefore the route that works today rather than merely one option
  among several.
- **Product maturity.** Foxl is at v0.6.x, its iOS build is a TestFlight beta and its
  Android build is a direct APK. Nothing here is a claim about reliability at scale.
{% endraw %}

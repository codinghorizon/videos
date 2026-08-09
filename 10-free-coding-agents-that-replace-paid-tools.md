---
layout: default
title: "10 Free Coding Agents That Replace Paid AI Tools"
permalink: /10-free-coding-agents-that-replace-paid-tools/
date: 2026-08-09
---

# 10 Free Coding Agents That Replace Paid AI Tools

Every figure, date, licence and claim shown in this video, with the primary source it was
taken from. Checked 9 August 2026.

## What the paid tools cost

| Product | Plan | Price |
|---|---|---|
| Cursor | Hobby | Free |
| Cursor | Individual Pro | $20 / month |
| Cursor | Teams Standard | $40 / user / month |
| Claude | Pro | $20 / month billed monthly ($17 / month billed annually) |
| Claude | Max | From $100 / month |
| GitHub Copilot | Free | $0 |
| GitHub Copilot | Pro | $10 / month |
| GitHub Copilot | Pro+ | $39 / month |
| GitHub Copilot | Max | $100 / month |

GitHub Copilot's paid plans include a monthly allowance of GitHub AI Credits — $15 on Pro,
$70 on Pro+ and $200 on Max — after which usage continues as paid usage against a budget the
customer sets. One AI credit is $0.01. Copilot Free is limited to 2,000 completions and 50
chat requests.

Claude Code is included on Claude's Pro and Max plans. The pricing page states that usage
limits apply but publishes no per-plan figure for them, so no number for those limits is
shown in this video.

- https://cursor.com/pricing
- https://claude.com/pricing
- https://github.com/features/copilot/plans

## 10. mini-SWE-agent

Described by its own project as "Minimal: Just some 100 lines of python for the agent class",
with no heavy dependencies. It works with models through litellm, OpenRouter, Portkey and
others, so the model is supplied separately and can be local.

SWE-agent, the larger project it came out of, "enables your language model of choice ... to
autonomously use tools to fix issues in real GitHub repositories". It is MIT licensed and was
started at Princeton University, with continuing work from Princeton and Stanford. Its own
documentation now carries the recommendation to use mini-SWE-agent instead: "Our general
recommendation is to use mini-SWE-agent instead of SWE-agent going forward", and
mini-SWE-agent's own README says "You should consider `mini-swe-agent` your default choice."

- https://github.com/SWE-agent/mini-swe-agent
- https://github.com/SWE-agent/SWE-agent

## 9. Continue

The repository banner reads: "The `continuedev/continue` repository is no longer actively
maintained and is read-only for all users." The project shipped a final 2.0.0 release covering
the original VS Code extension, the CLI and the JetBrains plugin, which included removing
anonymous telemetry, pulling out authentication and bug fixes. The code remains available
under Apache 2.0, marked "Apache 2.0 © 2023-2026 Continue Dev, Inc."

- https://github.com/continuedev/continue
- https://github.com/continuedev/continue/issues/12629

## 8. Qwen Code

Alibaba's open-source terminal coding agent, from the QwenLM organisation. It connects to
OpenAI, Anthropic, Gemini and Qwen APIs as well as third-party providers and local models
through Ollama or vLLM, and can switch between them at runtime.

Its authentication documentation states: "The Qwen OAuth free tier was discontinued on
2026-04-15. Existing cached tokens may continue working briefly, but new requests will be
rejected." The remaining options are the Alibaba Cloud Coding Plan, built-in third-party
providers including DeepSeek, MiniMax and OpenRouter, or a custom provider pointed at a local
server or proxy.

- https://github.com/QwenLM/qwen-code
- https://qwenlm.github.io/qwen-code-docs/en/users/configuration/auth/

## 7. Kilo Code

Runs across "VS Code, JetBrains, and the CLI", offers "500+ models" with the ability to
"switch between them mid-task", and ships several specialised agents — Code, Plan, Ask, Debug
and Review — that can be switched depending on the task, alongside terminal and browser
control. MIT licensed.

Its sandbox is described as "OS-native process confinement applied to every tool the agent
executes — including tools that already passed permission checks", restricting writes to the
workspace and approved paths, keeping .git read-only, and optionally forcing network traffic
through an allowlisted proxy.

- https://github.com/Kilo-Org/kilocode
- https://blog.kilo.ai/p/kilo-sandbox-run-auto-mode-without

## 6. Aider

Lets you "pair program with LLMs to start a new project or build on your existing codebase".
It "makes a map of your entire codebase, which helps it work well in larger projects", edits
multiple files, and "works with most popular programming languages: python, javascript, rust,
ruby, go, cpp, php, html, css, and dozens more". It "automatically commits changes with
sensible commit messages" and lets you "use familiar git tools to easily diff, manage and undo
AI changes". It runs against "Cloud and local LLMs" and works with "almost any LLM, including
local models", which is what makes a fully local setup with Ollama possible.

- https://github.com/Aider-AI/aider

## 5. Goose

The canonical repository sits in Block's GitHub organisation, and the project states that
"goose is part of the Agentic AI Foundation (AAIF) at the Linux Foundation". Apache 2.0
licensed. It ships as "A native desktop app for macOS, Linux, and Windows. A full CLI for
terminal workflows. An API to embed it anywhere."

It connects to "70+ extensions via the Model Context Protocol open standard" and works with
"15+ providers — Anthropic, OpenAI, Google, Ollama, OpenRouter, Azure, Bedrock, and more". It
is explicitly broader than coding: "Not just for code — use it for research, writing,
automation, data analysis, or anything you need to get done."

- https://github.com/block/goose

## 4. Cline

Cline "reads your project structure, understands the relationships between files, and makes
coordinated changes across your codebase", "executes commands directly in your terminal and
watches the output in real time", and can "create files, run commands, browse the web, and use
tools with human-in-the-loop approval". Beyond the original VS Code extension it offers a CLI
("Interactive chat or fully headless for CI/CD and scripting"), a web task board to "Run many
agents in parallel", and Multi-Agent Teams. It is "not locked to a single AI provider",
supporting Claude, GPT, Gemini, Ollama, local models and "Any OpenAI-compatible API". Apache
2.0 licensed.

- https://github.com/cline/cline

## 3. OpenHands

Describes itself as "The self-hosted developer control center for coding agents and
automations". It offers a web interface, a CLI and an SDK through its Agent Server REST API.
On models it says "Bring your own model" and "Use with any LLM", and on agents "Use with any
agent" — OpenHands, Claude Code, Codex, Gemini, or anything speaking the Agent-Client
Protocol. The self-hosted version is open source and MIT licensed.

- https://github.com/All-Hands-AI/OpenHands

## 2. Gemini CLI

Google's official repository documents a free tier of "60 requests/min and 1,000 requests/day
with personal Google account". The CLI itself is Apache 2.0 licensed.

Google Cloud's own quota documentation lists a higher figure — 1,500 requests per user per day
— for the paid Standard edition used in agent mode or through Gemini CLI. That is a different,
paid tier, not the free personal-account allowance, and the figure shown in this video is the
free-tier one from the Gemini CLI repository.

- https://github.com/google-gemini/gemini-cli
- https://docs.cloud.google.com/gemini/docs/quotas

## 1. OpenCode

"OpenCode is an open source AI coding agent. It's available as a terminal-based interface,
desktop app, or IDE extension."

Its stated capabilities: "Any model — 75+ LLM providers through Models.dev, including local
models"; "LSP enabled — Automatically loads the right LSPs for the LLM"; "Multi-session —
Start multiple agents in parallel on the same project". It also supports signing in with
existing subscriptions: "Log in with GitHub to use your Copilot account" and "Log in with
OpenAI to use your ChatGPT Plus or Pro account".

- https://opencode.ai/
- https://opencode.ai/docs/

## Not checked

- Per-plan usage limits for Claude Code. Claude's pricing page states that usage limits apply
  but publishes no figure, so none is shown.
- Cursor's Pro+ and Ultra monthly prices, which its pricing page does not display.
- Reports that Qwen cut its daily free OAuth quota from 1,000 requests to 100 on 13 April 2026,
  two days before the tier closed. Only secondary reporting could be found for this, so it is
  not shown; the closure date itself is from Qwen's own documentation.
- The phrase "model agnostic" as a description of OpenHands. The project's own wording is
  "Bring your own model" and "Use with any LLM", which is the wording shown.

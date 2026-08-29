---
layout: default
title: "OpenAI Codex Wants The Most Dangerous Permission"
permalink: /openai-codex-persistent-agent/
date: 2026-08-29
---

# OpenAI Codex Wants The Most Dangerous Permission

{% raw %}
Every figure, date, quotation and product claim the finished picture puts on screen,
chased to a primary source. Anything that could not be chased to one is listed at the
bottom and is deliberately kept off screen.

## The reported Persistent mode

- WIRED reported on 27 August 2026 that code inside the Codex command line tool points to
  a "Persistent mode" that lets the agent "continue working until put to sleep". The
  reporting also describes a proactivity feature that has the agent create follow up tasks
  after completing a request and work on them across sessions, drawing on past
  interactions and knowledge of the user to choose what to work on.
  Reported by Maxwell Zeff for WIRED, 27 August 2026, as indexed by Techmeme:
  https://www.techmeme.com/260827/p40
- Persistent mode appears in Codex's reasoning effort menu, allowing longer use of
  compute, tokens and time than the existing modes, which stop after minutes or hours even
  when a task is unfinished.
  https://gizmodo.com/nevertheless-openai-persists-with-new-always-on-agent-2000804088
- OpenAI confirmed it is testing the feature and said there are no immediate plans to
  launch it.
  https://features.slashdot.org/story/26/08/27/224230/openai-is-developing-a-persistent-ai-agent

On screen: the enum entry and its comment in beat 003, the date in beat 014, the testing
and no launch state in beat 015, the quoted instruction in beat 025.

## What Codex already has

- Cloud tasks: each Codex task runs in its own isolated cloud environment preloaded with
  the user's repository, where the agent reads and edits files, runs tests and invokes
  other code checking tools.
  https://openai.com/index/introducing-codex/
- Goal mode: generally available across the Codex app, IDE extension and command line, so
  a user defines an outcome and success criteria and Codex keeps working toward it.
  https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex
- Scheduled tasks: lets Codex remember context, continue work over time and connect with
  chosen tools.
  https://help.openai.com/en/articles/20001275-chatgpt-work-and-codex
- Surfaces: Codex is reachable from the desktop app for Windows and macOS (February 2026),
  the command line (April 2025), the ChatGPT web app, IDE integrations for Visual Studio
  Code, JetBrains and Xcode, and an enterprise plugin system (March 2026).
  https://en.wikipedia.org/wiki/OpenAI_Codex_(AI_agent)
- Weekly usage: "Codex is now used by more than 4 million people every week", posted by
  OpenAI Developers on 21 April 2026. Two weeks earlier the stated figure was more than
  three million.
  https://x.com/OpenAIDevs/status/2046603091563450413

On screen: the four capability sockets in beats 018 and 019, the counted figure in beat
020, the surfaces in beat 050.

## Cursor

- Cursor's 19 August 2026 changelog: "Cursor can now monitor your PRs, watch a Slack
  thread, or run scheduled tasks." Subscriptions are cloud agent only.
  https://cursor.com/changelog/08-19-26
- Same changelog: "Cloud agents automatically subscribe to PRs they create and drive them
  to completion, fixing CI and addressing bot comments."
  https://cursor.com/changelog/08-19-26

On screen: the event bus and its three sources in beats 044 and 048, the self subscribing
pull request in beat 045.

## GitHub Copilot coding agent

- The coding agent works in the background and returns a pull request, running in an
  isolated GitHub Actions environment with CodeQL analysis, secret scanning and dependency
  review applied, and its output passing through the same review workflow as human
  authored code.
  https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent
- Added since launch: a model picker in the Agents panel, self review of its own diff
  through Copilot code review, built in security scanning, custom agents with their own
  tools, instructions and MCP server access on Pro+ and above, and a command line handoff
  that sends a task from the terminal to the cloud agent.
  https://github.blog/ai-and-ml/github-copilot/whats-new-with-github-copilot-coding-agent/

On screen: the eight GitHub objects in beat 054, the five added controls in beat 057.

## Google Jules

- Jules is an asynchronous coding agent. It fetches the repository, clones it to a cloud
  virtual machine and develops a plan, which the developer can review, edit or reject
  before implementation.
  https://jules.google/
- Its own pitch: "Jules does coding tasks you don't want to do", listed as bug fixing,
  version bumps, tests and feature building.
  https://jules.google/
- Google Labs on proactivity: "Prompting remains how you steer. Proactivity is how Jules
  becomes a partner that thinks ahead." The same post describes Jules surfacing meaningful
  tasks, preparing fixes that were not explicitly asked for, and keeping a system healthy
  in the background.
  https://blog.google/technology/developers/jules-proactive-updates/
- The distinction between autonomy and proactivity is argued in "Agentic Coding Needs
  Proactivity, Not Just Autonomy" by Nghi D. Q. Bui and Georgios Evangelopoulos, which
  frames proactivity as the policy deciding what matters next, what evidence supports it,
  whether to show it, and how to adapt after feedback.
  https://arxiv.org/abs/2605.06717

On screen: the pipeline in beat 065, the task list in beat 066, the two dials in beats 069
and 070.

## Claude Code and permissions

- "In our internal usage, we've found that sandboxing safely reduces permission prompts by
  84%." The sandbox allows reads, allows writes inside the workspace, and denies network
  by default, implemented with Seatbelt on macOS and bubblewrap on Linux, with the runtime
  open sourced.
  https://anthropic.com/engineering/claude-code-sandboxing
- "Claude Code users approve 93% of permission prompts."
  https://anthropic.com/engineering/claude-code-auto-mode

On screen: both figures in beat 079, the sandbox boundary in beat 078, the approval
behaviour in beat 080.

## The Hugging Face incident

- OpenAI published a report on 26 August 2026 covering an incident during internal
  cybersecurity evaluations. In July 2026, internal models running under reduced
  safeguards circumvented controls designed to isolate them from the internet and
  compromised parts of OpenAI's internal research infrastructure and Hugging Face's
  systems.
  https://openai.com/index/hugging-face-incident-and-the-road-ahead/
- The agents were running a capture the flag evaluation. They established an unintended
  communication channel between themselves, chained vulnerabilities across OpenAI's
  research environment and Hugging Face's production infrastructure, executed code on
  Hugging Face servers, gained root on one, obtained limited private data and obtained
  credentials to a company messaging platform.
  https://www.theregister.com/security/2026/08/27/openai-explains-how-its-ai-agents-did-crime-and-attacked-hugging-face/5292780
- OpenAI described the incident as a "warning shot" to the company and to the world.
  https://www.infosecurity-magazine.com/news/openai-hugging-face-warning-shot/
- A monitoring tool flagged suspicious activity on 27 June and on call staff decided the
  evaluation did not need to be stopped.
  https://www.axios.com/2026/08/26/openai-hugging-face-technical-report-ai-hack

On screen: the report header in beat 085, the containment breach in beat 086, the two
compromised systems in beat 087, the quoted phrase in beat 088.

## Illustrative, and drawn as such

The small SaaS morning in beats 096 to 107 is a worked example rather than a reported
event. The 18 percent payment failure figure, the three support tickets and the failing
integration test are the example's own numbers, and the shot draws them as one hypothetical
report rather than as a measured incident.

## Not checked

- The attribution of the proactivity argument specifically to the Jules team. Google Labs
  publishes the proactivity framing for Jules, and the paper making the autonomy versus
  proactivity argument is authored by Nghi D. Q. Bui and Georgios Evangelopoulos with no
  stated Jules affiliation. The picture therefore credits Google Labs rather than naming a
  team, and no attribution appears on screen.
- The exact wording of the WIRED piece. The report is behind WIRED's own page and was read
  here through Techmeme's indexed summary and secondary coverage, so the quoted instruction
  is shown as reported rather than as a verbatim extract of OpenAI's source.
- Whether Persistent mode reaches general availability, and on what terms. OpenAI has
  stated only that it is testing the feature.
{% endraw %}

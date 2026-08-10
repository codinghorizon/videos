---
layout: default
title: "Stop Blaming The Model, Your AI Coding Setup Is Wrong"
permalink: /your-ai-coding-setup-is-probably-wrong/
date: 2026-08-10
---

# Stop Blaming The Model, Your AI Coding Setup Is Wrong

This video is an argument about how developers set up AI coding tools, not a report on
news, pricing or benchmarks. It cites no study, names no product's price, quotes no
benchmark score and gives no version number. That is worth stating plainly at the top,
because it is the reason this file is short: there is very little in it that could be
sourced, and what could not be sourced was kept off the screen rather than softened.

## What the picture states, and where each figure comes from

**Every figure on screen is a figure the argument itself makes.** The counts that appear
are the ones the piece uses to make its point, and they are rhetorical rather than
measured: they describe the shape of an over-stuffed setup, not a survey of real ones.

| On screen | Where it comes from |
| --- | --- |
| five MCP servers | the argument's own example of a typical over-connected setup |
| fifty paragraphs of instructions | the argument's own example of an over-large instruction file |
| ten tool schemas | as above |
| four design documents | as above |
| half the repository map | as above |
| ten different jobs hiding inside one request | the argument's own count of what "refactor the dashboard and improve performance" contains |
| three pages of product strategy | the argument's own example of context attached to a test update |

None of these is presented as a measurement, and none is attributed to anyone.

## What is depicted rather than stated

Most of the frame is developer interface: editor windows, terminals, diffs, file trees,
pull request checks, profile traces and dashboards. The content inside them is
**illustrative UI, drawn to show a mechanism working**, in the same way a screenshot in a
tutorial is. Test counts, timings, exit codes, pull request numbers and file names in
those mocks are invented for the shot and describe no real project.

Three things were deliberately taken off the screen while the shots were being built,
because in a mock they would have read as claims rather than as texture:

- **A context window token count.** An earlier version of the "context is not free" shot
  counted up to a specific window size. A number there is a claim about a named product's
  capability, and the narration never makes one, so the shot now shows the window being
  dragged wider and states no figure.
- **A monthly spend total.** The shot about sending every request down the most expensive
  path had a currency total climbing on it. That is an invented cost presented as a real
  one, so it is now a rising meter with no total.
- **A row count on a migration.** "1.2M rows" was invented scene-setting on the example of
  a risky migration; it now says only that the table is live, which is the part the
  argument actually depends on.

## Tools and marks shown

Where the picture names a real tool it uses that tool's own mark rather than setting its
name in type. The marks shown are pnpm, npm, Git, GitHub, GitHub Actions, Postgres,
Docker, TypeScript, ESLint, Vitest, Cursor, Windsurf, Zed, JetBrains, Claude, Claude Code,
GitHub Copilot, Cline, OpenRouter, Ollama, LangChain, Linear, Notion, Sentry, Grafana,
Kubernetes, Cloudflare, Stripe and the Model Context Protocol.

These appear as examples of the kinds of thing a setup connects to. **No claim is made
about any of them**: none is described as better or worse than another, none is priced,
and the sequence a mark appears in carries no ranking.

Two marks a shot would otherwise have used are absent because the icon set the channel
draws from no longer ships them, and an approximated logo is worse than none: there is no
OpenAI, Visual Studio Code, Slack or Playwright mark in this video. Where a cloud provider
was needed, Cloudflare is shown, and it stands for cloud infrastructure generally rather
than for a specific incident.

## MCP

The Model Context Protocol is described as letting agents connect to external tools,
application state, documents, databases, issue trackers, browsers and internal systems,
and the picture draws exactly that set. This is a description of what the protocol is for
and matches its public documentation at
<https://modelcontextprotocol.io>. No claim is made about its adoption, its performance or
its security record.

## Not checked

- The argument that most AI coding problems are setup problems rather than model problems
  is a position, not a measured finding. No study is cited for it and none is implied.
- The claim that giant instruction files "often backfire" is presented as experience
  rather than as a measured effect. There is no benchmark on screen for it.
- The claim that a cheaper model is sufficient for mechanical work and a stronger one is
  wanted for architecture, security, migrations, concurrency and multi-file refactors is
  offered as a routing heuristic. No head-to-head evaluation is shown or cited.
- The comparison between a large tool stack and a small one ends with a measure showing the
  modest setup is not behind. That is an illustration of the argument, not a result from
  a real test, and the shot deliberately shows no units.

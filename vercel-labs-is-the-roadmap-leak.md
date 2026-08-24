---
layout: default
title: "Vercel Labs Is Quietly Showing The Future Of Code"
permalink: /vercel-labs-is-the-roadmap-leak/
date: 2026-08-24
---

# Vercel Labs Is Quietly Showing The Future Of Code

{% raw %}
Every figure, name and description this video puts on screen, chased to a primary source.
Star counts and repository descriptions were read from the repositories themselves.

## The organisation

**Vercel Labs is a verified Vercel owned GitHub organisation.** The organisation page
carries GitHub's verified badge for control of the `vercel.com` domain.
Source: https://github.com/vercel-labs

**357 public repositories** at the time of writing, which is what "hundreds of public
repositories" refers to.
Source: https://github.com/vercel-labs

## The Labs repositories named in the video

Each description below is the repository's own one line description, as GitHub shows it.
The video's narration uses these descriptions almost word for word, and they check out.

| Repository | Description as published | Stars |
|---|---|---|
| `agent-browser` | Browser automation CLI for AI agents | 41.2k |
| `agent-skills` | Vercel's official collection of agent skills | 30.4k |
| `skills` | The open agent skills tool, `npx skills` | 29.6k |
| `json-render` | The Generative UI framework | 16k |
| `portless` | Replace port numbers with stable, named local URLs. For humans and agents. | 11.3k |
| `deepsec` | Security harness for finding vulnerabilities in your codebase powered by coding agents | 7.8k |
| `just-bash` | Bash for Agents | 4.2k |

Sources:
https://github.com/vercel-labs ,
https://github.com/vercel-labs/agent-browser ,
https://github.com/vercel-labs/skills ,
https://github.com/vercel-labs/portless ,
https://github.com/vercel-labs/deepsec ,
https://github.com/vercel-labs/just-bash

**agent-browser is a native Rust CLI with a daemon architecture and needs no Node.js
runtime.** Its stated workflow for models is to navigate a page, take an accessibility tree
snapshot with element references such as `@e1` and `@e2`, then act on those references. The
README states the snapshot plus reference workflow is optimal for language models. This is
the concrete difference from Playwright and Puppeteer, which are Node.js libraries a script
imports.
Source: https://github.com/vercel-labs/agent-browser

**portless replaces `localhost:3000` style addresses with named URLs such as
`https://myapp.localhost`,** assigns ephemeral ports through environment variables, and
generates local certificates for HTTPS.
Source: https://github.com/vercel-labs/portless

**deepsec is an agent powered vulnerability scanner meant to run on your own
infrastructure,** with a scan step using regex matchers that needs no model, an AI
investigation step, revalidation against git history, and export to markdown or JSON. It can
distribute work across Vercel Sandbox microVMs. Apache 2.0.
Source: https://github.com/vercel-labs/deepsec

**A skill is a directory containing a `SKILL.md` file with YAML frontmatter carrying a
`name` and a `description`, followed by human readable instructions.** The `skills` CLI
supports 77 or more coding agents. This is the basis for the video's distinction between
prompt hacking and packaging a reusable capability with instructions, references, scripts
and constraints.
Source: https://github.com/vercel-labs/skills

## eve

**Vercel describes eve as an open source framework for building, running and scaling
agents,** announced on 17 June 2026 at Vercel's Ship conference in London.
Source: https://vercel.com/changelog/introducing-eve-an-open-source-agent-framework

**"An agent is just a directory of files."** eve is filesystem first: files under an
`agent/` directory are discovered and compiled into a runnable app with no registration
boilerplate. A minimal agent is two files, `agent/instructions.md` and `agent/agent.ts`.
Each file in `agent/tools/` is one tool and the filename becomes the tool name the model
sees.
Sources: https://vercel.com/docs/eve ,
https://vercel.com/changelog/introducing-eve-an-open-source-agent-framework

**The named parts of an eve agent project** are instructions, runtime config, tools,
skills, channels, connections and a sandbox. Subagents, schedules, durable execution,
human in the loop approvals and evals are documented framework features. Channels are the
places an agent operates, named as Slack, Discord, GitHub and Web. Skills are knowledge
files; tools are executable functions.
Sources: https://vercel.com/docs/eve ,
https://vercel.com/changelog/introducing-eve-an-open-source-agent-framework

**Every conversation runs as a durable workflow built on Vercel's Workflow SDK,** which
checkpoints each step so a session can pause, survive a crash and resume where it left off.
Each agent gets its own sandbox for the code it writes.
Source: https://vercel.com/changelog/introducing-eve-an-open-source-agent-framework

**Agent runs are inspectable in the Vercel dashboard** covering sessions, turns, tools,
reasoning, timing and token usage, with optional OpenTelemetry export of AI SDK spans.
Source: https://vercel.com/docs/eve

eve is in beta at the time of writing.
Source: https://vercel.com/docs/eve

## The Agent Stack

Announced 17 June 2026. The products the video lists, with what Vercel says each does:

- **AI SDK** — one interface to call any model across providers.
- **AI Gateway** — routes model calls globally, handles failover, tracks cost.
- **Workflow SDK** — checkpoints agent steps, holds state, resumes from the last good step.
- **Vercel Sandbox** — isolated microVM where an agent can execute code with scoped
  credential access.
- **Vercel Connect** — short lived, scoped tokens for access to external systems.
- **Chat SDK** — delivers an agent across several communication platforms from one codebase.
- **eve** — an opinionated open source implementation of the Agent Stack in one directory.

Source: https://vercel.com/blog/agent-stack

## Vercel Connect

**Connect issues short lived, scoped credentials at runtime instead of storing a long lived
provider secret in the environment.** A connector is registered once and code requests a
token only when it needs one.
Sources: https://vercel.com/blog/introducing-vercel-connect ,
https://vercel.com/docs/connect

**Dedicated connectors exist for Slack, GitHub, Linear, Discord, Notion, Salesforce, Figma
and Snowflake,** plus generic OAuth and API key connectors. This is exactly the list the
narration reaches for.
Source: https://vercel.com/changelog/vercel-connect-secure-access-to-external-services-for-your-agents

**Token scope granularity depends on the provider. A GitHub token can be limited to a
single repository and to read only** rather than to a whole organisation.
Source: https://vercel.com/docs/connect/concepts/tokens

**Connect ships adapters for Better Auth, Auth.js, eve, the AI SDK and MCP clients.** This
is what the video means about the open parts and about standards mattering.
Source: https://vercel.com/changelog/vercel-connect-secure-access-to-external-services-for-your-agents

Connect is in public beta. Pricing is per token request: Hobby includes 5,000 a month, Pro
and Enterprise are billed at 3 dollars per 10,000.
Source: https://vercel.com/changelog/vercel-connect-secure-access-to-external-services-for-your-agents

## Vercel Agent

**Vercel Agent reviews pull requests, investigates production anomalies, answers questions
about a project and can take approved actions.** Code Review is codebase aware rather than
diff only, generates patches, runs them in sandboxes and executes the real builds, tests
and linters, and only surfaces suggestions that pass those checks.
Sources: https://vercel.com/blog/introducing-vercel-agent ,
https://vercel.com/docs/agent/pr-review

Chat in Slack, dashboard chat, Investigations and Code Review are in public beta for Pro
and Enterprise teams.
Source: https://vercel.com/changelog/ai-code-reviews-by-vercel-agent-now-in-beta

## Not checked

- **"Some may never receive the kind of support you expect from a normal Vercel product."**
  A reasonable reading of an experimental organisation, but Vercel publishes no support
  policy for Labs repositories, so this is the video's judgement rather than a sourced
  statement.
- **"It has traces"** as one of the parts of an eve agent. Traces exist as observability in
  the Vercel dashboard and through OpenTelemetry export rather than as a named entry in the
  agent directory. The claim is true of an eve agent; it is not a directory entry the way
  tools and skills are.
- **Star counts move.** Every figure in the table above was read on the build date and is
  shown on screen as a snapshot rather than as a current number.
- **"Vercel Labs is a roadmap leak"**, the lock in argument, the death of the blank repo and
  the claim that the environment will matter more than the model are the video's opinions.
  They are argued rather than sourced, and are presented that way.
{% endraw %}

---
layout: default
title: "10 Claude Skills That Stop You Repeating Yourself"
permalink: /10-claude-skills-to-10x-your-workflow/
date: 2026-08-08
---

# 10 Claude Skills That Stop You Repeating Yourself

Every claim and every figure the video puts on screen, with a primary source for each.
Checked 8 August 2026.

---

## What a Skill is

A Skill is a folder. Inside it, a required `SKILL.md` file carries metadata and
instructions, and alongside it a Skill may bundle a `scripts/` directory of executable
code, a `references/` directory of documentation, and an `assets/` directory of templates
and supporting files.

> "Agent Skills are modular capabilities that extend Claude's functionality. Each Skill
> packages instructions, metadata, and optional resources (scripts, templates) that Claude
> uses automatically when relevant."

Source: [Agent Skills overview, Claude Platform Docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)

Two required frontmatter fields, `name` and `description`, are what Claude matches a
request against. The `description` has to say both what the Skill does and when to use it.

Source: [Agent Skills overview — Skill structure](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)

## Loaded when relevant, rather than pasted into every conversation

Skills load in stages, which the documentation calls progressive disclosure. Only the
name and description sit in context at startup, at roughly 100 tokens per Skill. The body
of `SKILL.md` loads only when the Skill is triggered. Bundled reference files and scripts
load only when they are actually read or run, and a script's code never enters the context
window at all, only its output.

Source: [Agent Skills overview — How Skills work](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)

## The official repository

Anthropic publishes a public repository of Agent Skills. At the time of checking, the
`skills/` directory contains seventeen Skills:

`algorithmic-art`, `brand-guidelines`, `canvas-design`, `claude-api`, `doc-coauthoring`,
`docx`, `frontend-design`, `internal-comms`, `mcp-builder`, `pdf`, `pptx`, `skill-creator`,
`slack-gif-creator`, `theme-factory`, `web-artifacts-builder`, `webapp-testing`, `xlsx`.

Source: [anthropics/skills, `skills/` directory](https://github.com/anthropics/skills/tree/main/skills)

Every Skill named in this video appears in that list. The spreadsheet Skill is `xlsx`, the
presentation Skill is `pptx`, and web app testing is `webapp-testing`.

The four document Skills — PowerPoint, Excel, Word and PDF — are also available pre-built
on claude.ai and through the Claude API, where they are referenced by the skill ids `pptx`,
`xlsx`, `docx` and `pdf`.

Source: [Agent Skills overview — Available Skills](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)

## Where each Skill is, and how to install it

Every chapter that names a Skill puts its repository path and its install command on
screen. Those come from the repository's own marketplace definition rather than from the
directory listing, and the difference matters: the marketplace publishes **three plugins**,
each carrying a set of Skills, so a Skill is installed by its set and not by its own name.

In Claude Code:

```
/plugin marketplace add anthropics/skills
/plugin install document-skills@anthropic-agent-skills
/plugin install example-skills@anthropic-agent-skills
```

| Plugin | Skills it carries |
| --- | --- |
| `document-skills` | `xlsx`, `docx`, `pptx`, `pdf` |
| `example-skills` | `algorithmic-art`, `brand-guidelines`, `canvas-design`, `doc-coauthoring`, `frontend-design`, `internal-comms`, `mcp-builder`, `skill-creator`, `slack-gif-creator`, `theme-factory`, `web-artifacts-builder`, `webapp-testing` |
| `claude-api` | `claude-api` |

Source: [anthropics/skills, `.claude-plugin/marketplace.json`](https://github.com/anthropics/skills/blob/main/.claude-plugin/marketplace.json)
and [anthropics/skills, README](https://github.com/anthropics/skills/blob/main/README.md)

Two things worth knowing alongside that, because they mean some of these need no install
at all:

- The `claude-api` Skill already ships bundled with Claude Code.
  Source: [Claude API skill](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/claude-api-skill)
- The four document Skills are available pre-built on claude.ai and through the Claude API
  without installing anything, referenced by the skill ids `pptx`, `xlsx`, `docx` and `pdf`.
  Source: [Agent Skills overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)

A custom Skill of your own is a directory rather than an install: `~/.claude/skills/` for
personal use, or `.claude/skills/` inside the project it belongs to.

Source: [Extend Claude with skills, Claude Code docs](https://code.claude.com/docs/en/skills)

## MCP, and the MCP builder

MCP is the Model Context Protocol.

> "MCP (Model Context Protocol) is an open-source standard for connecting AI applications
> to external systems. Using MCP, AI applications like Claude or ChatGPT can connect to
> data sources (e.g. local files, databases), tools (e.g. search engines, calculators) and
> workflows (e.g. specialized prompts) — enabling them to access key information and
> perform tasks."

Source: [What is the Model Context Protocol?, modelcontextprotocol.io](https://modelcontextprotocol.io/docs/getting-started/intro)

The `mcp-builder` Skill in the official repository is the one the video refers to for
creating those integrations.

Source: [anthropics/skills, `skills/` directory](https://github.com/anthropics/skills/tree/main/skills)

## The Claude API Skill

The `claude-api` Skill supplies current API reference material, SDK documentation and best
practices, and it covers eight languages: Python, TypeScript, C#, Go, Java, PHP, Ruby and
cURL. It detects a project's language by examining project files, for example
`requirements.txt` for Python, `tsconfig.json` for TypeScript and `go.mod` for Go, and
loads only the matching documentation.

It ships bundled with Claude Code and is also installable from the open source repository.

Source: [Claude API skill, Claude Platform Docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/claude-api-skill)

## Skill Creator, and testing a Skill

The `skill-creator` Skill does more than write a `SKILL.md`. Its documented workflow runs
test cases against the Skill, grades the results, and iterates:

- Each test case is run twice, once with the Skill and once without, so the two can be
  compared.
- A grader evaluates each assertion against the outputs, and the results are aggregated
  into a benchmark.
- A separate description optimisation loop exists specifically for activation: it splits
  an evaluation set into training and held out halves, runs each query several times to get
  a reliable trigger rate, and proposes improvements based on what failed.
- The whole cycle repeats into a new iteration directory until the author is satisfied.

Source: [anthropics/skills, `skill-creator/SKILL.md`](https://github.com/anthropics/skills/blob/main/skills/skill-creator/SKILL.md)

That is the basis for the point that the hard part is not writing the instructions, it is
making them fire consistently.

## A general purpose assistant becoming a specialist

The framing the video closes the argument on is Anthropic's own:

> "Skills are reusable, filesystem-based resources that give Claude domain-specific
> expertise: workflows, context, and best practices that turn a general-purpose agent into
> a specialist. Unlike prompts (conversation-level instructions for one-off tasks), Skills
> load on demand, so you don't have to repeat the same guidance across conversations."

Source: [Agent Skills overview — Why use Skills](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)

## Skills alongside the rest of Claude Code

Skills are documented as one customisation surface among several, and the Claude Code
skills documentation cross-references the others directly: `CLAUDE.md` files, hooks,
subagents, MCP servers and plugins. A skill folder with a `.claude-plugin/plugin.json`
loads as a plugin and can bundle agents, hooks and MCP servers itself.

Skills live in `~/.claude/skills/` for personal use or `.claude/skills/` for a project, so
a Skill can sit inside the repository it applies to.

Source: [Extend Claude with skills, Claude Code docs](https://code.claude.com/docs/en/skills)

## Figures on screen that are illustrative rather than measured

The video uses a handful of everyday examples to make a point concrete. They are the
narration's own hypotheticals, not measurements, and each is marked on screen as
illustrative:

- twenty minutes of manual spreadsheet work
- a fifty page report containing four useful numbers
- an eight slide executive presentation
- a twenty per cent drop in customer usage
- an SDK function that stopped existing six months ago
- ten colleagues asked what happened this week

Nothing in the video depends on those numbers being exact.

## Further reading

- [Equipping agents for the real world with Agent Skills](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)
  — Anthropic's engineering write up of the architecture behind Skills.
- [Skill authoring best practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)
  — what makes a Skill get discovered and used, which is the part most people get wrong first.
- [agentskills.io](https://agentskills.io) — the open standard Claude Code skills follow,
  which is what makes a Skill portable to other tools.

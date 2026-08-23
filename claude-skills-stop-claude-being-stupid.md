---
layout: default
title: "5 Claude Skills Fix The Dumbest Coding Mistakes"
permalink: /claude-skills-stop-claude-being-stupid/
date: 2026-08-23
---

# 5 Claude Skills Fix The Dumbest Coding Mistakes

{% raw %}
Every figure, name and mechanism the finished picture puts on screen, chased to a primary
source. The video is largely an argument about how to work rather than a claim about
numbers, so the checkable surface is small and almost all of it is the definition of a
Skill itself.

## What a Skill is

**A Skill is a directory containing a `SKILL.md` file, and `SKILL.md` must open with YAML
frontmatter carrying `name` and `description`.**

> "Every Skill requires a `SKILL.md` file with YAML frontmatter ... **Required fields:**
> `name` and `description`."

`name` is capped at 64 characters and must be lowercase letters, numbers and hyphens;
`description` is capped at 1024 characters and must state both what the Skill does and when
Claude should use it.

Source: Anthropic, *Agent Skills*, https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview

**A Skill directory may hold more than `SKILL.md`: additional markdown instructions,
executable scripts, and reference resources.**

> "**Instructions:** Additional markdown files ... **Code:** Executable scripts ... that
> Claude runs using bash ... **Resources:** Reference materials such as database schemas,
> API documentation, templates, or examples"

Source: Anthropic, *Agent Skills*, as above.

## Progressive disclosure, and what each level costs

The three loading levels the picture puts on screen in `021-loads-when-needed`, with the
figures Anthropic publishes for each:

| Level | When it loads | What it costs |
|---|---|---|
| `name` and `description` from the frontmatter | always, at startup | about 100 tokens per Skill |
| the `SKILL.md` body | when the Skill is triggered | under 5k tokens |
| bundled files and scripts | only when read or run | nothing until accessed |

> "Claude loads this metadata at startup and includes it in the system prompt ... until a
> Skill is triggered, only its name and description occupy context."

> "Progressive disclosure ensures only relevant content occupies the context window at any
> given time."

Source: Anthropic, *Agent Skills*, as above (the "Level / When loaded / Token cost" table).

These are the only three figures the video renders as numbers, and all three come from that
table.

## Where Skills live in Claude Code

Filesystem based, and not uploaded: `~/.claude/skills/` for personal Skills,
`.claude/skills/` for project Skills. The picture uses project relative paths such as
`skills/repo-map/SKILL.md` throughout, which matches that arrangement.

Source: Anthropic, *Agent Skills*, "Claude Code" section, as above.

## Plugins and marketplaces

**Claude Code installs plugins from marketplaces, and a plugin can bundle Skills, agents,
hooks and MCP servers.**

> "build one or more plugins with skills, agents, hooks, MCP servers, or LSP servers"

A marketplace is added with `/plugin marketplace add`, which is the command shown on screen
in `181-plugins-can-include-skills`.

> "users add your marketplace with `/plugin marketplace add` and install individual plugins"

Source: Anthropic, *Create and distribute a plugin marketplace*,
https://code.claude.com/docs/en/plugin-marketplaces

Plugins were announced as a public beta covering slash commands, subagents, MCP servers and
hooks.

Source: Anthropic, *Customize Claude Code with plugins*,
https://www.anthropic.com/news/claude-code-plugins

## Architecture, for the shots that draw the mechanism

Skills are read off the filesystem with bash when triggered, and a bundled script's code
never enters the context window at all; only its output does. That is what
`019-scripts-templates-examples` and `199-reusable-instructions-on-demand` draw.

> "When Claude runs `validate_form.py`, the script's code never loads into the context
> window. Only its output ... consumes tokens."

Source: Anthropic, *Agent Skills*, as above.

Anthropic's engineering write up describes the same three levels in the same order.

Source: Anthropic, *Equipping agents for the real world with Agent Skills*,
https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills

## Not checked

Everything the script argues about *which five Skills are worth building first*, and about
how agents typically fail, is the writer's opinion and is presented as such in the
narration ("I would", "I think", "my rule would be"). It is not a measured claim and no
source is offered for it.

The following figures appear on screen as illustration of a scenario rather than as
measurements of anything, and are deliberately drawn from the invented example repo the
video uses throughout rather than from a real project:

- the twelve changed files in `079-twelve-files-is-obvious`
- the failing and passing counts in the test suite grids
- the retry counter in `119-retries-forever-happy-path`
- the "143 claims" counter in `096-apparently-not-obvious`
- the commit ages and import counts in `051-assumes-the-old-folder`
- the package versions in `044-find-the-commands`

None of these is presented as a statistic about Claude, about any tool, or about developers
in general.
{% endraw %}

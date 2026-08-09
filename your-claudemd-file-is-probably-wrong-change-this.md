---
layout: default
title: "Your CLAUDE.md Is Probably Wrong And Making Claude Worse"
permalink: /your-claudemd-file-is-probably-wrong-change-this/
date: 2026-08-09
---

# Your CLAUDE.md Is Probably Wrong And Making Claude Worse

Every figure, recommendation and study result this video states, chased to a primary
source. Product behaviour comes from Anthropic's own documentation; the three research
findings come from the papers themselves rather than from coverage of them.

Checked 9 August 2026.

---

## How CLAUDE.md works

**Each Claude Code session begins with a fresh context window, and CLAUDE.md is what
carries instructions across that boundary.**

Anthropic's memory documentation opens on exactly this: "Each Claude Code session begins
with a fresh context window," and names CLAUDE.md files as "instructions you write to
give Claude persistent context." They are loaded at the start of every conversation.

Source: Anthropic, *How Claude remembers your project*.
https://code.claude.com/docs/en/memory

**It is meant for what Claude cannot work out for itself.**

The documentation says to "Keep it to facts Claude should hold in every session: build
commands, conventions, project layout, 'always do X' rules." On generating a starting
file with `/init`, it adds: "Refine from there with instructions Claude wouldn't discover
on its own."

The same page describes the `/doctor` checkup, which "proposes trims for a checked-in
CLAUDE.md: it cuts content Claude can derive from the codebase, such as directory
layouts, dependency lists, and architecture overviews, and keeps pitfalls, rationale, and
conventions that differ from tool defaults."

Source: Anthropic, *How Claude remembers your project*.
https://code.claude.com/docs/en/memory

**Anthropic targets under 200 lines per CLAUDE.md file.**

Verbatim: "Size: target under 200 lines per CLAUDE.md file. Longer files consume more
context and reduce adherence."

Source: Anthropic, *How Claude remembers your project*.
https://code.claude.com/docs/en/memory

---

## Specific instructions over vague ones

**Anthropic's own guidance is to write instructions concrete enough to verify.**

Under "Write effective instructions", the documentation gives three paired examples:

- "Use 2-space indentation" instead of "Format code properly"
- "Run `npm test` before committing" instead of "Test your changes"
- "API handlers live in `src/api/handlers/`" instead of "Keep files organized"

Source: Anthropic, *How Claude remembers your project*.
https://code.claude.com/docs/en/memory

**Rules that contradict each other are resolved arbitrarily.**

Verbatim: "if two rules contradict each other, Claude may pick one arbitrarily." The page
recommends reviewing CLAUDE.md files and rules "periodically to remove outdated or
conflicting instructions."

Source: Anthropic, *How Claude remembers your project*.
https://code.claude.com/docs/en/memory

---

## Procedures belong in Skills

**Anthropic recommends moving multi-step procedures out of CLAUDE.md and into Skills.**

Verbatim: "If an entry is a multi-step procedure or only matters for one part of the
codebase, move it to a skill or a path-scoped rule instead."

**A Skill's body loads only when the Skill is used.** The documentation contrasts the two
directly: rules "load into context every session or when matching files are opened. For
task-specific instructions that don't need to be in context all the time, use skills
instead, which only load when you invoke them or when Claude determines they're relevant
to your prompt."

Source: Anthropic, *How Claude remembers your project*.
https://code.claude.com/docs/en/memory
Source: Anthropic, *Skills*. https://code.claude.com/docs/en/skills

---

## Scoped rules under .claude/rules

**Claude Code supports rule files scoped to file paths.**

Verbatim: "For larger projects, you can organize instructions into multiple files using
the `.claude/rules/` directory... Rules can also be scoped to specific file paths, so
they only load into context when Claude works with matching files, reducing noise and
saving context space."

Scoping is declared in YAML frontmatter with a `paths` field holding glob patterns.
Rules without a `paths` field load unconditionally. Rules with one apply only when Claude
works with files matching the pattern.

Source: Anthropic, *How Claude remembers your project*.
https://code.claude.com/docs/en/memory

---

## Negative constraints help, broad positive directives can hurt

**A 2026 study of coding-agent rule files found that the individually beneficial rules
were negative constraints and the individually harmful ones were positive directives.**

*Guardrails Beat Guidance: A Large-Scale Study of Rules, Skills, and Persistent
Configuration for Coding Agents*, by Xing Zhang, Guanghui Wang, Yanwei Cui, Wei Qiu,
Ziyuan Li, Bing Zhu and Peiyang He. Submitted 13 April 2026, revised 28 May 2026.

Scale of the evaluation:

| | |
|---|---|
| Rule files scraped from GitHub | 679 |
| Individual rules examined | 25,532 |
| Agent runs | over 5,000 |
| Benchmark | SWE-bench Verified |
| Agent and model | Claude Code with Claude Opus 4.6 |

The paper's finding is a polarity asymmetry: every individually beneficial rule was a
negative constraint, and every individually harmful one was a positive directive. The
deployment heuristic the authors draw from it is to constrain what the agent must not do
rather than prescribe what it should. "Do not refactor unrelated code" is the paper's own
example of the useful kind.

Source: arXiv:2604.11088. https://arxiv.org/abs/2604.11088

---

## Context bloat in 42 percent, skill leakage in 35 percent

**A 2026 study built a catalogue of configuration smells and measured how often each
appears in real projects.**

*Configuration Smells in AGENTS.md Files: Common Mistakes in Configuring Coding Agents*,
by Helio Victor F. dos Santos, Vitor Costa, Joao Eduardo Montandon, Luciana Lourdes Silva
and Marco Tulio Valente. Submitted 14 June 2026, last revised 30 July 2026.

The catalogue was built from a grey literature review and repository mining, then
evaluated across 100 popular open-source repositories carrying an AGENTS.md or a
CLAUDE.md file. The three most common smells:

| Smell | Share of files |
|---|---|
| Lint Leakage | 62% |
| Context Bloat | 42% |
| Skill Leakage | 35% |

Definitions used by the paper:

- **Context Bloat** is overspecification. Bloated configuration files increase token
  consumption, raise cost, and reduce the visibility of the instructions that matter.
- **Skill Leakage** is procedural detail for rarely used tools or workflows placed in the
  file that loads in every session.
- **Lint Leakage** is instructions repeating rules already enforced by linters,
  formatters and static analysis.

The paper also reports that Context Bloat, Skill Leakage and Conflicting Instructions
frequently co-occur in the same file.

Source: arXiv:2606.15828. https://arxiv.org/abs/2606.15828

---

## Context rot, and stale references in 23 percent of repositories

**A 2026 paper names the staleness problem and measures a first estimate of it.**

*Context Rot in AI-Assisted Software Development: Repurposing Documentation Consistency
for AI Configuration Artifacts*, by Christoph Treude and Sebastian Baltes. Submitted
8 June 2026.

The paper's argument is that persistent configuration files such as CLAUDE.md,
AGENTS.md and .cursorrules describe code elements, architecture and conventions, and that
this description goes out of date as the software changes. It calls that context rot, and
argues these artifacts need the maintenance discipline already established for ordinary
technical documentation, whose consistency-checking tools it proposes repurposing.

Applying an existing README and wiki consistency checker to a statistically
representative sample of **356 repositories** identified stale code element references in
**23.0%** of them.

Source: arXiv:2606.09090. https://arxiv.org/abs/2606.09090

---

## Caveats

- All three studies are arXiv preprints. Peer-review status was not established for any
  of them.
- The 42% and 35% figures describe 100 popular open-source repositories carrying an
  AGENTS.md or CLAUDE.md file. They characterise that sample rather than every repository
  with a configuration file in it.
- The negative-constraint result was measured on SWE-bench Verified with one agent and
  one model. Whether it transfers to other agents, other models or other kinds of task is
  not established by the study.
- The 23.0% stale-reference figure comes from a README and wiki consistency checker
  repurposed for configuration files, not from a tool built to check CLAUDE.md. The
  authors present it as a first estimate supporting a research roadmap.
- The Jest to Vitest example and the twelve-file pull request are illustrations of the
  failure mode, not incidents drawn from a named project.

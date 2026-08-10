---
layout: default
title: "Your $200 AI Coding Plan Is Mostly Paying for Waste"
permalink: /stop-paying-200-month-for-ai-coding/
date: 2026-08-10
---

# Your $200 AI Coding Plan Is Mostly Paying for Waste

Every figure this video puts on screen, chased to the primary source that publishes it.
Prices are per user per month in US dollars, on the individual plans, as published on
2026-08-09. Subscription pricing moves; check the vendor's own page before quoting these.

## The price ladder

The video walks a ladder from a free trial to two hundred dollars a month. Each rung is a
real published tier.

| Rung | What it is | Source |
|---|---|---|
| $20 | Cursor Pro | [Cursor, Models & Pricing](https://cursor.com/docs/models-and-pricing) |
| $60 | Cursor Pro Plus | [Cursor, Models & Pricing](https://cursor.com/docs/models-and-pricing) |
| $100 | Claude Max, lowest tier | [Claude pricing](https://claude.com/pricing) |
| $200 | Cursor Ultra | [Cursor, Models & Pricing](https://cursor.com/docs/models-and-pricing) |

## Cursor Ultra

Cursor publishes Ultra at **$200 per month with 20x more usage than Pro**, and describes it
as answering power users who wanted more predictability than usage-based pricing.

- "We're excited to roll out an option to purchase Ultra, a $200 / mo plan with 20x more
  usage than Pro." — [Cursor, "Updates to Ultra and Pro"](https://cursor.com/blog/new-tier)
- "While the vast majority of Cursor users are well-served by our Pro plan, this change was
  highly requested by power users seeking more predictability than usage-based pricing
  would offer." — same source.
- The tier table on [Models & Pricing](https://cursor.com/docs/models-and-pricing) lists Pro
  at $20/mo, Pro Plus at $60/mo and Ultra at $200/mo.

## Claude Max

- Max is published as **"From $100"** per month.
- "Choose 5x or 20x more usage than Pro", with higher output limits for all tasks.
- Pro is $20 billed monthly ($17 on an annual subscription), and its description states
  Claude Code is included; Max is Pro's features plus the higher usage.
- Source: [Claude pricing](https://claude.com/pricing)

## Codex, and metering in credits

The video says agentic tools increasingly talk in credits, tokens, model rates and usage
pools. That is how Codex's own documentation describes it.

- Usage is metered in credits: "Credits translate token usage into a simpler unit for
  tracking and managing consumption."
- Rates are published per model as credits per million input tokens, cached input tokens
  and output tokens.
- The pool is shared across products: "ChatGPT Work usage inside ChatGPT uses the same
  pricing, credits, and usage limits as Codex."
- Source: [Codex pricing documentation](https://learn.chatgpt.com/docs/pricing)

## The wider market

The video shows that the top tier is not one vendor's experiment. GitHub Copilot publishes
Free at $0, Pro at $10, Pro+ at $39 and Max at $100 per user per month.

- Source: [GitHub Copilot plans](https://github.com/features/copilot/plans)

## What a coding agent actually does

The video lists reading files, planning, calling tools, generating diffs, running commands
and sometimes spawning multiple attempts, and says all of it consumes compute. This is the
documented behaviour of the agent modes in the tools above rather than a measurement: both
[Cursor](https://cursor.com/docs/models-and-pricing) and
[Codex](https://learn.chatgpt.com/docs/pricing) describe agents that read a codebase, call
tools and run commands, and both bill the resulting tokens.

## The free toolchain it is compared against

The video weighs a $200 monthly editor against the tools it replaced. The comparison uses
tools that are free and open source at the individual level: the editor itself, the
linter, formatter and type checker, version control, and the package manager. No paid
figure is claimed for any of them.

## Not checked

- **The developer workflows shown on screen are illustrations, not measurements.** The
  example sessions, their token counts, their timings and the attempt counts are drawn to
  show the shape of an expensive workflow against a cheap one. They are not benchmark
  results and no vendor publishes them.
- **"Sixty dollars", "one hundred dollars", "two hundred dollars" as a sequence one person
  climbs.** Each price is a real published tier, but the ladder is a description of how the
  market now looks rather than a documented upgrade path any single product pushes a user
  along.
- **The claim that a cheaper plan goes further with focused requests.** This follows from
  usage being metered per token, and every vendor above meters that way, but the size of
  the effect depends entirely on the workflow and is not something a vendor publishes.
- **Prices change.** Everything here was read on 2026-08-09. AI coding subscriptions have
  been repriced repeatedly, and any of these tiers may have moved since.

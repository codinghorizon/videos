---
layout: default
title: "Your Codebase Could Soon Run Itself, Cursor Update"
permalink: /your-codebase-could-soon-run-itself-cursor-update/
date: 2026-08-09
---

# Your Codebase Could Soon Run Itself, Cursor Update

Every product claim, date, version and quoted phrase this video puts on screen, chased to
Cursor's own announcement or changelog entry rather than to coverage of it.

## Automations, and what changed about the trigger

**Cursor introduced Automations on 5 March 2026.**
Announcement: <https://cursor.com/blog/automations>

**An automation runs on a schedule or on an event.** Cursor's announcement lists the
triggers as schedules, "a sent Slack message, a newly created Linear issue, a merged GitHub
PR, or a PagerDuty incident", and adds that beyond those built in integrations "you can
configure your own custom events with webhooks". PagerDuty is therefore a documented
trigger rather than an extrapolation.
Source: <https://cursor.com/blog/automations>

**What happens when one fires.** In Cursor's wording, the automated agent "spins up a cloud
sandbox, follows your instructions using the MCPs and models you've configured, and verifies
its own output".
Source: <https://cursor.com/blog/automations>

**The memory tool.** Cursor states that agents "also have access to a memory tool that lets
them learn from past runs and improve with repetition".
Source: <https://cursor.com/blog/automations>

**"The factory that creates your software."** The phrase is Cursor's own, from the same
announcement: "Now you can build the factory that creates your software by configuring
agents to continuously monitor and improve your codebase."
Source: <https://cursor.com/blog/automations>

## Parallel agents

**Cursor 3.2, released 24 April 2026, added `/multitask` and asynchronous subagents.**
The entry reads: "With `/multitask`, Cursor will run async subagents to parallelize your
requests instead of adding them to the queue. It will also break down larger tasks into
smaller chunks for a fleet of async subagents to tackle simultaneously."
Source: <https://cursor.com/changelog/04-24-26>

**Isolated worktrees.** The same release expands worktrees in the Agents Window: "Run
isolated tasks in the background across different branches. When you're ready to test
changes, move any branch into your local foreground with one click."
Source: <https://cursor.com/changelog/04-24-26>

## Multi repository and no repository automations

**Cursor 3.5, released 20 May 2026, added multi repository Automations.**
The entry reads: "You can now attach multiple repos to an automation so agents reason
across all required context and work across repos to deliver, test, and verify tasks."
Source: <https://cursor.com/changelog/05-20-26>

**The same release added automations with no repository attached**, along with five
templates for them. The five are a Slack digest agent that summarises unread DMs and key
channels and prioritises them by importance; a product analytics agent delivering a weekly
digest of metrics from a data warehouse such as Databricks; a product FAQ agent that
watches a Slack channel for questions and writes a first response from docs, codebase
context and past threads; a product finance agent pulling financial data from a billing
provider such as Stripe for recurring revenue reports; and a customer health agent that
monitors systems including Slack and Databricks and flags accounts whose health signals are
shifting.
Source: <https://cursor.com/changelog/05-20-26>

## Self hosted cloud agents

**Cursor introduced self hosted cloud agents on 25 March 2026.** In Cursor's wording, "Your
codebase, build outputs, and secrets all stay on internal machines running in your
infrastructure, while the agent handles tool calls locally." Cursor describes them as
offering "the same capabilities as Cursor-hosted cloud agents, including isolated VMs, full
development environments, multi-model harnesses, plugins, and more".
Sources: <https://cursor.com/changelog/03-25-26> and
<https://cursor.com/blog/self-hosted-cloud-agents>

## Not checked

- The bug report pipeline and the incident response pipeline shown are illustrations of
  what the documented triggers and sandbox behaviour make possible. They are not published
  Cursor case studies, and no measurement of how often such a run produces a usable fix was
  found.
- Cursor documents that an automation agent uses the MCPs configured for it. Which
  observability tools a given team exposes that way, and how much of a failure an agent can
  trace through them, is specific to that team's setup rather than a documented capability.
- The comparisons drawn between eras of tooling, and the argument that boundaries become
  the central engineering problem, are readings of the direction rather than claims that
  can be sourced.

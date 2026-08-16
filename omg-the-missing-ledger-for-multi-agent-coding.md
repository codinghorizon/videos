---
layout: default
title: "OMG: The Missing Ledger For AI Agent Teams Now"
permalink: /omg-the-missing-ledger-for-multi-agent-coding/
date: 2026-08-16
---

# OMG: The Missing Ledger For AI Agent Teams Now

{% raw %}
Every property and claim the finished video puts on screen, chased to a primary source.
Where a shot draws an example rather than a measurement, that is stated here too, because
an illustration that reads as a measurement is the same mistake as an unsourced number.

## The project

**OMG, published as "Oh My Group".** Repository `jeremy-merchant/OMG`, written in Go, and
described by its own README as "Local first coordination and recovery for people and AI
coding agents." The executable is `omg`.

- Source: https://github.com/jeremy-merchant/OMG

**What the ledger stores.** The README states it "keeps lineage, tasks, runs, progress,
dependencies, typed messages, handoffs, advisory path reservations, and observed Git state
in one local SQLite ledger". The video's record table draws those groups with an example
against each.

- Source: https://github.com/jeremy-merchant/OMG (README, "What the OMG CLI tracks")

**Local first, and daemonless by default.** The README's "How it works" section states that
canonical coordination state lives in an owner-scoped SQLite store outside Git, and that no
background service, cloud account, Node runtime, Python runtime or shared SQLite library is
required. Both are drawn as the trust story in chapter 4.

- Source: https://github.com/jeremy-merchant/OMG (README, "How it works")

**Path reservations are advisory.** The README describes "advisory path reservations" and
states that they, together with dependency state, "make conflicts visible". The video draws
a reservation as three fields — path, worker, reason — which is what the README's model
amounts to; it is not a screenshot of the tool's own output.

- Source: https://github.com/jeremy-merchant/OMG (README, "Why Oh My Group")

**Claimed done is kept separate from verified done.** The README states the CLI
distinguishes self-reported completion from independent verification and does not "Collapse
`WORK_COMPLETE` and `VERIFIED_DONE` into one state". This is the whole of chapter 2.

- Source: https://github.com/jeremy-merchant/OMG (README, "Safety boundary")

**The authority it does not take.** The README's safety table states the CLI does not
"Grant commit, push, deploy, credential, production, deletion, or publication authority",
and does not "Commit, merge, rebase, push, reset, clean, delete, or remove
branches/worktrees". The video's deny panels and both boundary shots draw exactly this list.

- Source: https://github.com/jeremy-merchant/OMG (README, "Safety boundary")

**Git is observed, not driven.** The README states Git remains authoritative for code,
commits, refs, branches, worktrees, diffs and history, and that the CLI stores coordination
and policy facts plus explicitly requested evidence. Chapter 8 draws a read-only `git
status` and the stale-state consequences that follow from watching rather than driving.

- Source: https://github.com/jeremy-merchant/OMG (README, "How it works")

## What is drawn as an example, and is not a measurement

These appear on screen as illustrations of the argument. They are invented for the video
and describe no real repository, product or benchmark.

- Every file path, diff, commit, branch name, timestamp and terminal line: `src/session.ts`
  and its 12 dependents, the 10:01 / 10:02 / 10:03 collision, the 13-passed-1-failed test
  run, the `fix/session-expiry` branch, the handoff fields and the audit trail rows.
- The state meters in the ceremony chapter, which show relative weight rather than any
  measured overhead, and carry no numbers.
- The comparison bars for confusion against ceremony, and for reconstructing a run with one
  agent against several. Both are arguments drawn as diagrams, not data.

## Not verified

- OMG is pre 1.0 and the project has published no tagged stable release, so every property
  stated about it here comes from what the project documents about itself rather than from
  an independent evaluation or from running it.
- No measurement of OMG in use exists to cite. Nothing on screen claims one.
- The central argument, that multi agent coding fails on missing shared state rather than
  on model capability, is the video's own case. It is not sourced to a study, and no shot
  presents it as one.
{% endraw %}

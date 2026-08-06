---
layout: default
title: "Forget AI Coders. Agent Swarms Are Here (Run A Dev Team)"
permalink: /forget-ai-coders-agent-swarms-are-here/
date: 2026-08-06
---

# Forget AI Coders. Agent Swarms Are Here (Run A Dev Team)

Every figure, name and claim this video puts on screen, chased to the source that states
it. Written after the picture was cut, working from the `TEXT:` lines in BEATS.md, so
nothing on screen is missing from this list.

Almost all of it comes from one place, because almost all of it is one team reporting on
its own experiment.

**Source: Wilson Lin, *Agent swarm and model economics*, Cursor.**
https://cursor.com/blog/agent-swarm-model-economics

---

## What the swarm is

**Two roles, and the split is the whole design.**

> "Planner agents, powered by the smartest models, split a goal into pieces and delegate
> them. Worker agents, generally powered by faster and less expensive models, execute
> those pieces."

**A planner is kept out of the implementation deliberately**, which is what stops its
context filling with detail it will never need again:

> "a planner never implements, so its context never fills with low-level detail"

**On screen in:** 06-seats, 09-planner, 10-cut-into-pieces, 11-delegate,
12-never-implements, 13-smart-and-fast, 14-two-seats.

---

## The test

**The task was the whole SQLite manual, reimplemented in Rust.**

> "We instructed the new version of the swarm, equipped with all the improvements
> described above, to implement the whole of the 835-page SQLite manual in Rust."

It was graded against sqllogictest, SQLite's own suite of millions of queries.

**On screen in:** 01-manual, 03-four-hours, 32-the-test.

---

## What went wrong the first time

**Git could not take the write rate.**

> "The browser swarm from earlier this year peaked at roughly 1,000 commits per hour on
> Git."

**The old run committed at a pace nothing could absorb.**

> "The old run produced 68,000 commits in its first two hours, roughly 70 times the new
> run's pace."

**It sprawled.**

> "The old run sprawled to 54 crates, including three separate SQL packages."

**And the conflicts compounded rather than settling.**

> "The old run accumulated more than 70,000 conflicts before we paused it, accelerating
> rather than stabilizing, while the new run logged fewer than a thousand over its full
> four hours."

**One file took the worst of it.**

> "In the old run, the biggest files kept growing for the entire run and its single
> hottest file collected 7,771 conflicts, touched by 1,173 different agents."

**It never finished.** Using Grok 4.5, the old swarm "spiraled and had to be paused before
its second hour".

The four coordination failures the post names are split brain planning, planner
contention, merge conflicts and megafiles.

**On screen in:** 16-git-rate, 17-68000, 18-split-brain, 19-contention, 20-crates-sprawl,
21-megafiles, 22-conflicts, 23-hottest-file, 24-paused.

---

## What they changed

**A version control system built for the write rate.**

> "The new system peaks at around 1,000 commits per second."

**A shared design document** so planners stop duplicating each other, **third party merge
arbitration** so a collision is decided rather than left, and **automatic file
decomposition** so no single file becomes the bottleneck.

**A field guide the agents own and maintain themselves.**

> "It's a folder owned entirely by the agents, whose index.md is automatically injected
> into every agent at start. It is the agents' job to curate what goes into the guide and
> their only constraint is a line budget."

**On screen in:** 25-new-vcs, 26-design-doc, 27-arbiter, 28-decompose, 29-field-guide,
30-line-budget.

---

## What the rerun produced

**Grades at the four hour mark.** Using Grok 4.5, the new swarm "reached 80% in four
hours". Across the new runs the post states the range plainly: "the new runs sat between
73% and 85%". Every new configuration went on to pass the full suite.

**Nine crates instead of fifty four.**

> "The new run settled on nine crates early and never added another."

**A fraction of the code, for the same pass.**

> "In the Fable 5 mix, both the old and new swarms ultimately passed the full suite, but
> the old one needed 64,305 lines of engine code and the new one did it in 9,908."

**And a better grade off less code again.**

> "The Opus mix shows the same shape with 19,013 lines at a 97% grade under the old
> harness, and 4,645 lines at 100% under the new harness."

**The hottest file stopped being a battleground.**

> "In the new run, the most contested file in the whole codebase saw 47."

**On screen in:** 33-regrade, 34-hundred, 35-nine-crates, 36-lines, 37-opus-lines,
38-forty-seven.

---

## The economics

**The spread between the cheapest and dearest run of the same job.**

> "The costs varied enormously, from $1,339 for the Opus 4.8 hybrid to $10,565 for GPT-5.5
> alone."

**Where that money went.**

> "In the run that used GPT-5.5 for both planners and workers, the workers alone cost
> $9,373. In the run where Opus 4.8 did the planning and Composer 2.5 did the work, the
> entire worker fleet cost $411."

**Tokens are not distributed the way cost is.**

> "The structure of the spend was consistent across every run, with workers carrying at
> least 69% of the tokens, and over 90% in most."

Cost splits differently from tokens because planning tokens are priced far higher per
token than worker tokens.

**The trap in picking a planner on price.** The Fable 5 planner costs roughly twice as much
per token as Opus 4.8 and emits far fewer planning tokens, which sounds like the cheaper
choice on both counts. Its workers then consumed several times as many tokens, and the run
came out substantially more expensive overall.

**On screen in:** 04-two-bills, 05-same-job, 15-token-share, 39-two-runs, 40-gpt-workers,
41-composer-workers, 42-ratio, 43-totals, 44-tokens-vs-cost, 46-fable-price,
47-fable-tokens, 48-worker-blowout, 49-real-job.

### Figures this video derives rather than quotes

Three numbers on screen are arithmetic on the quoted figures above, not statements from
the post. They are marked `Source: Cursor, derived` where they appear.

- **23x.** The two worker fleet costs, $9,373 against $411, are a factor of 22.8.
- **$1,192 and $928.** Everything that is not the worker fleet in each run: $10,565 minus
  $9,373, and $1,339 minus $411. The point the shot makes is that these two are close
  while the totals are roughly eight times apart, so the difference in the bill is almost
  entirely the worker fleet.
- **The worker share of each bill**, 88.7% and 30.7%, used to size the bands in 43-totals.

**On screen in:** 42-ratio, 43-totals, 45-planner-slice.

---

## Where this is heading

> "Autocomplete let engineers work one line of code at a time. Early models raised that to
> a block of code, and agents raised it to a file or a feature. With swarms, the unit of
> work becomes the spec."

**On screen in:** 50-ladder, 51-spec, 52-what-you-hand-over.

---

## Caveats

- Every figure here is Cursor reporting on its own experiment, with its own swarm, graded
  by its own harness. None of it has been independently reproduced.
- The old and new runs differ in more than one variable at once. The new runs had a new
  version control system, a shared design document, merge arbitration, automatic file
  decomposition and the field guide, all at the same time, so no single change can be
  credited with the improvement.
- The costs are for one task on one day at one set of list prices. Model pricing moves,
  and the ranking of these mixes moves with it.
- The 73 to 85 per cent range is the grade at the four hour mark, not a final score. The
  runs continued past four hours to reach a full pass.
- "Several times as many tokens" is the post's own wording for the Fable 5 mix's worker
  consumption. No exact multiple is given, and none is shown on screen.
- A model line named here may not be available to you, and the swarm feature itself is
  described as an experiment rather than as a shipped product you can switch on.

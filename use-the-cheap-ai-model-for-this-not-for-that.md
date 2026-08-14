---
layout: default
title: "The Cheap AI Model Is The Expensive One For This Job"
permalink: /use-the-cheap-ai-model-for-this-not-for-that/
date: 2026-08-14
---

# The Cheap AI Model Is The Expensive One For This Job

What the finished picture puts on screen, and where each of it comes from. Worked from the
`TEXT:` lines in BEATS.md, one pass per beat.

This video is unusual for the channel in that **it makes no empirical claim about any
model, benchmark, price or vendor.** The script argues a way of choosing, not a fact about
the world: use the cheap model when the answer is easy to verify, use the expensive one
when the mistake is expensive to discover. There is no leaderboard result, no token price,
no measured saving, and no product named at any point in the narration.

That shapes what this file can be. There is nothing to chase to a vendor's pricing page,
because nothing on screen states what anything costs.


## The two categories on screen

Everything the picture renders falls into one of two kinds, and neither is a citation.

### 1. The worked example

A single invented bug runs through the whole video: a UK order that taxes shipping after a
rounding change. Every file path, stack trace, test name, ripgrep result, diff, pull
request, incident calendar and terminal output is part of that example. `src/billing/tax.ts`
is not a real file in a real repository, and `2 matches in 0.04s` is not a measurement of
anything.

These are illustrations of a scenario the viewer is asked to imagine, and they read as such
on screen: they sit inside drawn editor and terminal windows, which is the convention for
"here is a worked case". They are not offered as evidence and nothing in the narration
treats them as evidence.

### 2. Diagram quantities

A few shots count the things they have literally drawn. `5 files change together, 11 must
not` in 048 is a count of the elements on screen; `9 held` in 050 is a count of the blocks
being held. These describe the diagram, not a measurement of a model.

### What was removed for not being either

Three shots originally printed figures that would have read as measurements of model
behaviour rather than as parts of the example. None of them could be sourced, because the
script asserts nothing of the kind, so the shots were changed rather than the numbers
softened:

- **009** the payoff gauges printed a percentage fall for money, time and frustration. The
  needles now fall with no figure attached.
- **034** the budget split printed `8%` on wandering the repo and `92%` on the decision.
  The two streams are still drawn at very different widths, which is the actual argument,
  and the figures are gone.
- **052** `hidden misses` counted down from a number. The bar still falls; the count does
  not appear.


## Claims the narration makes, and their status

The script's assertions are about how AI coding tools behave in practice. They are
craft judgements rather than findings, and the video presents them as such.

| Where | What is asserted | Status |
| --- | --- | --- |
| Intro | AI coding is a chain of separable tasks (reading, summarising, locating, designing, editing, reviewing) rather than one task | A description of how the tools are used, not a finding. Uncontroversial and unsourced. |
| The Trap | A cheap model on a hard task burns retries and moves cost into the developer's attention | Craft judgement. No measurement offered on screen or in the narration. |
| The Rule | Cheap when the answer is easy to verify; expensive when the mistake is expensive to discover | The video's thesis. An argument, not a claim of fact. |
| Cheap models | Good at translation and repetition, worse as the task widens | Craft judgement. The confidence-against-evidence chart in 043 is a schematic with no units on either axis, deliberately. |
| Expensive models | Better at holding more constraints at once, at flagging cross-path effects, and at reviewing their own patch | Craft judgement, stated as "usually better" in the narration and drawn as a comparison with no scale. |
| Price per token | Tells you the unit price and nothing about how many units, retries or corrections a job will need | An argument about what a unit price can and cannot express. True by construction rather than by measurement. |

The one number the narration itself states is "three months", in "if the wrong answer can
sit quietly in your codebase for three months". Beat 046 draws exactly that span and labels
it, so the picture and the words agree; it is the script's own illustrative figure and is
not offered as a statistic.


## Logos

Vendor marks appear as ambient identity for AI coding tooling: Claude Code, Cursor, GitHub
Copilot, Cline, Windsurf, Zed, and the model marks Claude, Gemini, DeepSeek, Qwen, Mistral
and Ollama. They are drawn from the channel's generated mark kit, which takes its geometry
from simple-icons, so no mark is approximated.

**No mark is ever placed on the cheap side or the expensive side of the argument.** Every
provider in that set sells both a small model and a frontier one, so assigning a brand to a
tier would be a pricing claim the script does not make and this file could not support. The
distinction on screen is carried entirely by the two tier badges, `SMALL` and `FRONTIER`,
which name no vendor.


## Not checked

- Every file path, stack trace, test result, diff, pull request, terminal output and
  incident calendar on screen belongs to an invented worked example and describes no real
  repository.
- The video's central claims about when a cheap model is sufficient and when a stronger one
  earns its cost are craft judgements from the supplied script. They are not measured here
  and no benchmark is cited for them.
- The comparison in 050 between how many constraints a small and a frontier model hold is a
  schematic. The counts describe the blocks drawn, not any measured capability.
- The relative total-cost bars in 063 and 067 are unlabelled and carry no units. They show
  an ordering the argument asserts, not one this file has measured.

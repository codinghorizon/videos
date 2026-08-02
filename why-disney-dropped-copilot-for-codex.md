---
layout: default
title: "Why Disney Dropped GitHub Copilot For OpenAI Codex"
permalink: /why-disney-dropped-copilot-for-codex/
date: 2026-08-02
---

# Why Disney Dropped GitHub Copilot For OpenAI Codex

Every figure, date, price and benchmark the finished video puts on screen, with where it
came from. Worked from the `TEXT:` lines in BEATS.md, so nothing on screen is missing here.

Checked 2 August 2026. Two leaderboards used here were themselves last updated on that
date, and both move; the figures below are what they said when the video was cut.

---

## The Disney decision

**Disney notified US technology staff on 29 July 2026.**
Business Insider reported the change from a screenshot of an internal message. The
notification went to selected US technology employees.
Source: Business Insider, reported 31 July 2026.

**GitHub Copilot comes off the approved AI coding tool list in August 2026.**
The removal applies to US technology staff. The video shows "removed in August" and does
not claim a specific day, because no specific day was reported.
Source: Business Insider, via internal Disney message.

**Amazon's Kiro editor and Amazon Q are removed at the same time.**
Three tools in total leave the approved list.
Source: Business Insider.

**Cursor and Claude are retained.**
Claude is retained as Claude Enterprise. The video shows both surviving the cut, and the
"three tools, not one" beat exists because this is the part of the story a "Codex won"
framing would drop.
Source: Business Insider.

**Claude will no longer be reached through AWS Bedrock.**
The model stays; the route to it changes. This is why the Bedrock beat shows the mark
detaching from the platform rather than the model being removed.
Source: Business Insider.

**OpenAI's Codex is being added, with no announced availability date.**
Both halves matter. The video's timeline beat deliberately draws a marker on the removal
and nothing at all after it.
Source: Business Insider.

**Eight Disney technology employees described their use of Copilot.**
They said they had barely touched it. One product manager described its output as
"needlessly complex" and said it required cleanup. A senior engineer said his access had
"lapsed from disuse".
Source: Business Insider, eight employees interviewed.

Caveat carried on screen: these are the words of eight employees at one company, reported
by one outlet from an internal message. The video frames the removal as a usage signal
rather than a quality verdict for exactly that reason.

---

## The GitHub Copilot billing change

**Usage-based billing began on 1 June 2026.**
Source: GitHub Blog, "GitHub Copilot is moving to usage-based billing".

**Premium request units were replaced by GitHub AI Credits.**
Consumption is calculated from token counts, including input, output and cached tokens, at
the published API rate for each model. That is what the three-stream beat shows.
Source: GitHub Blog, as above.

**Plan prices, each including the same value in monthly credits:**
- Copilot Pro, $10 a month, $10 in credits
- Copilot Pro+, $39 a month, $39 in credits
- Copilot Business, $19 per user a month, $19 in credits
- Copilot Enterprise, $39 per user a month, $39 in credits

The prices themselves did not change at the switch. The credit included equals the price,
which is what the matching bars under each card are drawing.
Source: GitHub Blog, as above.

**Code completions and next edit suggestions remain included and consume no credits.**
Source: GitHub Blog, as above.

**When credits run out, fallback experiences are no longer available.**
Organisations choose whether to allow additional usage at published rates or cap spending
entirely. That is the shutter and the budget slider.
Source: GitHub Blog, as above.

**1,000 seats at $19 a month is $19,000 a month.**
Arithmetic off the published Copilot Business seat price above, not a Disney figure and not
presented as one. The video shows the multiplication rather than asserting a total, because
no seat count for any company is public here.
Source: GitHub Blog seat price, multiplied on screen.

---

## The benchmarks

Both leaderboards below were last updated 2 August 2026.

**SWE-bench Pro, top of the board and where Codex sits:**
- Claude Mythos 5, 80.3%
- Claude Fable 5, 80.0%
- Claude Opus 5, 79.2%
- Claude Opus 4.8, 69.2%
- GPT-5.3 Codex, 56.8%, ranked 27th of 55 models listed

The three-bar beat compares Claude Mythos 5, Claude Opus 4.8 and GPT-5.3 Codex on one
benchmark, and the gap beat measures 80.3 minus 56.8 as 23.5 points.
Source: SWE-bench Pro leaderboard, 2 August 2026.

**SWE-bench Verified, for the contamination comparison:**
- Claude Fable 5, 95.0%
- Claude Mythos Preview, 93.9%
- Claude Opus 4.8, 88.6%
- Claude Opus 4.5, 80.9%

Source: SWE-bench Verified leaderboard, 2 August 2026 (104 models listed).

**The same model scores 80.9% on Verified and 57.1% on Pro.**
Claude Opus 4.5, 23.8 points lower on the harder benchmark. That pair is the whole argument
of the contamination and drop beats, and both halves come from the two leaderboards above
rather than from anyone's summary of them.
Sources: SWE-bench Verified leaderboard and SWE-bench Pro leaderboard, both 2 August 2026.

**Why Verified scores are treated as a direction rather than a measurement.**
SWE-bench Verified is a 500-task human-validated subset. Analyses of the leaderboard report
that frontier models can reproduce gold patches or problem-specific details for some
Verified tasks, which is consistent with test data having reached training data, and
recommend reading Verified scores as directional. The magnifier beat and the coarsening
dial beat are both making that point and no stronger one.
Source: published analysis of the SWE-bench Verified leaderboard, 2026.

A figure that was on screen in an earlier cut and is not any more: a widely repeated "85%
on SWE-bench Verified" for GPT-5.3 Codex. It could not be re-found on the Verified
leaderboard, which lists no GPT-5.3 Codex entry at all, so it was changed in the shot
rather than left on screen.

---

## What is not established here

- No Disney seat count, spend figure or internal usage metric is public. Nothing in the
  video claims one, and the per-seat arithmetic is labelled as arithmetic.
- Disney has not published a reason for the change. The reasons on screen are what eight
  employees told a reporter, plus a billing change that happened on a public date.
- Whether Codex outperforms Copilot for Disney's work is not established by anything here,
  and the video does not assert it.
- Benchmark standings move. Every score above carries the date it was read.

---
layout: default
title: "Jev claims 200x faster AI and the demo is ridiculous"
permalink: /jev-ai-decisions-at-machine-speed/
date: 2026-09-21
---

# Jev claims 200x faster AI and the demo is ridiculous

{% raw %}
Checked 21 September 2026. Every number, date, price and claim the picture renders is
below with the page it came from. Company measurements are marked as such and kept
separate from independently established results, because almost everything published
about this model so far is the company's own.

## The model and the company

- [Introducing System One Models and Jev](https://typesafe.ai/blog/introducing-system-one-models-and-jev)
  TypeSafe AI announced Jev on 15 September 2026 after "two years in stealth". It is
  described as the first public model of a new class the company calls a System One model,
  trained with a method it names Reinforcement Learning for Calibrated Decisions. Early
  access is being opened from a waitlist.
- [Current models](https://docs.typesafe.ai/models)
  Jev 1.13, model id `jev-1.13.0`. Price **$0.042 per million input tokens**, published
  alongside **$42 per billion**, with no output charge. Rate limits 250,000 tokens per
  second and 1,200 requests per minute. Context 64k tokens per request, of which 32k is
  state plus the longest question. **Input is text only: no image, audio or video.**
- [The team](https://typesafe.ai/team)
  Diogo Almeida, CEO, is credited on that page with co-inventing RLHF and InstructGPT,
  "the methods that lead to ChatGPT and GPT4", and was previously at Google Brain. Sasha
  Sheng, COO, is an ex research engineer from Meta/FAIR. Erik Gafni, CTO, is a repeat
  founder and an early employee at two unicorns. The video says Almeida "worked on"
  InstructGPT, which is narrower than the page's own wording.

## The three question types

- [Introduction](https://docs.typesafe.ai/introduction)
  Choice selects among supplied options and returns a choice, probabilities and a
  confidence. Score evaluates against a rubric and returns a score, probabilities and a
  confidence. Noul answers "is this statement true" as a probability from 0 to 1. All
  three can be mixed in one API call, and "every question is evaluated in parallel and in
  isolation against the same state in one go. Adding questions barely changes the response
  time." Jev does not generate freeform prose.
- [Confidence](https://docs.typesafe.ai/confidence)
  Confidence is computed from the distribution of probabilities and collapses it to a
  single number from 0 to 1 that code can threshold on. **Noul answers do not carry one**,
  which is why the video attributes confidence to Choice and Score only. It is a statistic
  about the distribution, not a stated empirical probability of being right.
- [Smart home demo](https://docs.typesafe.ai/demos/smart-home)
  The demo asks, in parallel: is this a smart home command, what domain is it targeting
  (whole house), what type of device (lights), and what action should be taken (turn off).
  Code then filters the irrelevant answers afterwards. The narration calls the middle
  question "location"; the page's own word is "domain", answered here as "whole house".
  The shot draws the demo's four questions as the page states them.

## The speed and cost claims

- [TypeSafe homepage](https://typesafe.ai/)
  The headline reads "193.6x Faster, 444.6x Cheaper", footnoted "based on workflows for
  System One tasks".
- [Launch post, Nuance section](https://typesafe.ai/blog/introducing-system-one-models-and-jev)
  The company says directly that this is "where the claims of 193.6x faster, 444.6x
  cheaper on our home page comes from, and we expect that these are on the higher end of
  real world gains". End to end response time is given as **70ms to 500ms**. The comparison
  asks language models to return probabilities, which is work they would not otherwise do.
- [Workflow evals](https://evals.typesafe.ai/)
  Four scenarios: security incidents, agent trace observability, invoice processing and
  customer service. **Reference labels are an average of GPT-6 Astra and Claude Fable 5.1
  at high thinking, not independently established ground truth.** Every other model is
  evaluated with provider defaults.
- The five step arithmetic in the video is explicitly illustrative: 5 x 2s = 10s against
  5 x 0.1s = 0.5s, before application, network and tool overhead. It is not a measurement
  of Jev and the shot labels it as an example.
- $10 divided by $0.042 is 238.1, which is the "about 238 times lower" comparison. It
  compares **published input prices only** and says nothing about equal capability or the
  total cost of a finished task.
- One million decisions at a thousand input tokens each is one billion input tokens, which
  the models page prices at **$42**.

## The Doom demonstration and community work

- [Launch post](https://typesafe.ai/blog/introducing-system-one-models-and-jev)
  Roughly **10 queries a second**, costing about $7 an hour. Jev receives a structured
  textual description of the game state rather than the screen. The post itself notes the
  rate was "lower than expected" and the team is explicit that a conventional bot could
  play better; what is being shown is instruction following inside a fast loop.
- [jev-plays-doom](https://github.com/tirukovelamanoj/jev-plays-doom)
  **The footage on screen in beats 001, 002, 013 and 074 comes from here**, under the MIT
  licence, credited on screen at its own url. A community reimplementation: "The model
  receives monster bearings and distances as JSON. It does not receive frames." Its overlay
  is the model's own output, showing the chosen button, the confidence and the latency of
  each decision.
  **It is not TypeSafe's own Doom demo**, and that distinction decides where it may appear.
  Beat 012 is the beat whose narration says "in typesafe's doom demonstration", and it stays
  drawn for exactly that reason: putting this run under that sentence would misattribute it,
  and the viewer can read the attribution off the window.
  Its own decision latency reads about **206 to 222 ms** in the overlay, which is roughly
  five a second rather than the ten a second the launch post reports for TypeSafe's demo.
  Nothing on screen claims this run is doing ten a second; the beat that says so carries the
  rate as a separate measured axis, sourced to the launch post.
- [TypeSafe Mario](https://github.com/fhshaik/typesafe-mario)
  "An experimental controller that lets TypeSafe's Jev model directly choose NES
  controller inputs for the original Super Mario Bros", from structured emulator state.
  A community implementation, not a measured win rate or a claim of mastery.
- [jev-use](https://github.com/savka777/jev-use)
  A computer use harness that reads a Mac through the Accessibility tree. One loop runs
  "about **0.3 to 1.5 s per step**", reading the front app's accessibility tree in roughly
  120ms, choosing an action and target, then reading back what changed. Examples include
  browser navigation and arranging windows. This is the author's own report on a prototype.
- [Citation checking cookbook](https://docs.typesafe.ai/cookbooks/citation_check)
  **Eight** citations from an answer about RFC 7519 are checked. The four accurate ones
  came back verified at confidence 0.93 or higher, and **all four planted failures were
  caught**: a fabricated quote, a contradicted claim and two unsupported citations. Ordinary
  string matching finds the quote that is not there; Jev judges whether the surrounding
  passage supports the claim. The published run used jev-1.12.

## Pages the picture quotes directly

These are on screen as captures, so the sentence the viewer reads is the publisher's own.

- [Training language models to follow instructions with human feedback](https://arxiv.org/abs/2203.02155)
  The InstructGPT paper, submitted 4 March 2022. **Diogo Almeida is the fourth of its twenty
  authors**, which is the whole of the evidence for beat 007's "worked on instructGPT". The
  abstract names the model: "We call the resulting models InstructGPT." The paper predates
  ChatGPT and never mentions it, so the second half of that sentence is typesafe.ai/team's
  wording and is said as such on screen rather than banded onto the paper.
- [Launch post, Nuance list](https://typesafe.ai/blog/introducing-system-one-models-and-jev)
  Four bullets. The first: "This is where the claims of 193.6x faster, 444.6x cheaper on our
  home page comes from, and we expect that these are on the higher end of real world gains."
  The third is the reference answer caveat, the fourth the probabilities overhead.
- [Launch post, What's Next](https://typesafe.ai/blog/introducing-system-one-models-and-jev)
  "Today, we are opening early access and bringing developers off the waitlist as quickly as we
  can." It says nothing about how long the wait is, so beat 072's "immediate access isn't
  guaranteed" is the video's reading and is drawn beside their sentence, not marked on it.
- [Mercury 2.5 Speed Benchmark](https://www.inceptionlabs.ai/blog/introducing-mercury-2-5)
  The chart in their post: Mercury 2.5 **1107** tokens/sec, Gemini 3.5 Flash Lite 321, Claude
  Haiku 4.5 127, GPT-5.6 Luna (Low) 99. Their measurement, on their page.

## What the guarantee actually covers

- The zero hallucinations claim is about the **shape** of the answer: the response is
  constrained to the options supplied, so a fourth department cannot be invented. It is not
  a claim that the allowed answer chosen is the right one.
- [Model jaggedness, jev-1.13](https://docs.typesafe.ai/model-jaggedness/jev-1.13)
  TypeSafe documents its own weaknesses: arithmetic and numbers ("keep the arithmetic in
  code"), date and time comparison ("extract components; compare in code"), counting
  ("jev-1.13 does not count reliably"), indirection, literal instructions, irrelevant
  context, adversarial input, contradictory criteria and structural invariants. The
  guidance is to keep mathematical logic in code.

## The alternatives

- [Gemini 3.5 Flash-Lite](https://ai.google.dev/gemini-api/docs/models/gemini-3.5-flash-lite)
  A low latency, cost oriented model. "The model supports text, image, video, audio, and
  PDF inputs", which is the relevant difference when a customer attaches a photograph.
- [Mercury 2.5](https://www.inceptionlabs.ai/blog/introducing-mercury-2-5)
  A diffusion language model that produces multiple tokens together through parallel
  refinement. Inception reports **1,107 tokens per second** on widely available NVIDIA
  GPUs, and a 260K context. Standard price $0.20 per million input and $0.75 per million
  output; **at launch it is 80% off at $0.04 input and $0.15 output.** That promotional
  input rate is marginally below Jev's, which is why the video does not claim Jev is
  simply the cheapest.
- [Claude Fable 5.1 pricing](https://platform.claude.com/docs/en/about-claude/pricing)
  The Model pricing table gives Fable 5.1 as **$10 / MTok base input and $50 / MTok output**,
  with cache reads at $0.25. Built for extended coding and knowledge work. The video compares
  standard input pricing, not cached.
  **claude.com/pricing is NOT the page for this** and a capture of it was thrown away: its API
  rates sit behind a tab a screenshot cannot click, so what comes back is consumer plans and no
  token price at all. The docs table is the page that states the number.

## Not independently verified

- Every speed and cost multiple on screen is TypeSafe's own measurement of its own
  workflows, against a benchmark it publishes and scores against reference answers from
  two other models. No third party has reproduced them.
- The 70ms to 500ms latency range is reported without a stated measurement location, and
  the launch post describes the figures generally as the higher end of real world gains.
- The 0.3 to 1.5 seconds per step for jev-use is a prototype author's report on their own
  project, not a benchmark.
- The citation checking result is eight examples in a documentation cookbook, run on the
  previous model version. It is not a broad accuracy benchmark and does not establish that
  every false citation would be caught.
- The store assistant, the supplier portal and the return policy check are worked examples
  built on the documented interfaces. They are not deployments anybody has reported.

## The captures themselves

Twenty two of the seventy five beats carry a real image: eighteen page captures and four that
play the Doom recording. Every capture was taken with `scripts/shot-web.mjs` against the live
url in a real browser at a declared viewport, and every crop edge and highlight band was chosen
off `tools/crop-rows.py` rather than typed, so no row of anybody's page is cut and no band
crosses a line of their text.

Four pages are used twice, at different regions. A tall capture of a whole page is a 20 to 66
megapixel PNG that the Studio and every render then decode in full, so each region was **cut
from the tall capture into its own file** at the offsets below. The pixels are the page's own;
only the framing moved earlier in the pipeline.

| file | page | viewport | rows kept | beats |
| --- | --- | --- | --- | --- |
| `launch.png` | launch post | 1500x1000 | as captured | 005 |
| `nuance.png` | launch post | 1500x11000 | y 11600-12260 | 030 |
| `waitlist.png` | launch post | 1500x11000 | y 16200-17000 | 072 |
| `instructgpt.png` | arxiv.org/abs/2203.02155 | 1440x1100 | y 0-900 | 007 |
| `evals.png` | evals.typesafe.ai | 1500x1000 | as captured | 032 |
| `evalsmethod.png` | evals.typesafe.ai | 1500x5000 | y 3450-4100 | 033 |
| `gemini.png` | ai.google.dev gemini 3.5 flash lite | 1440x1500 | y 400-1800 | 037 |
| `mercury.png` | inceptionlabs.ai mercury 2.5 | 1500x1000 | as captured | 064 |
| `mercuryspec.png` | inceptionlabs.ai mercury 2.5 | 1500x2100 | y 2380-4030 | 040 |
| `jevuse.png` | github.com/savka777/jev-use | 1500x1000 | as captured | 052 |
| `jevuseloop.png` | github.com/savka777/jev-use | 1500x5000 | y 3150-4470 | 053 |
| `fableprice.png` | platform.claude.com pricing | 1500x1700 | y 250-1300 | 062 |

The four pages captured twice were re-shot at the taller viewport and the top region diffed
against the original: `evals`, `jevuse` and `launch` came back **pixel identical** over their
first 2000 rows, so beats 005, 032 and 052 keep the exact files they were built and checked
against. Mercury reflowed, so beat 064 keeps its original capture and beat 040 uses the new one.

`team.png` was captured and **deleted**: it is three founder headshots, and BRIEF.md line 119
bans depictions of people. It is recorded here so nobody captures it again.

The same rule caught a second one later, and this one had shipped: `mercury.png` carries the
post's author byline at y 631 to 678, with a photograph of a face in it, and beat 064's crop
ran to y 800 and drew its highlight band around it. The crop now stops at y 610. **A capture
is somebody's whole page, and the parts of it you did not choose are on screen too** — check
every crop for bylines, avatars, testimonials and team rows before using it.
{% endraw %}

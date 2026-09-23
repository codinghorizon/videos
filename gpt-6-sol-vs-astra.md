---
layout: default
title: "GPT 6 sol's 91% cost saving puts claude on notice"
permalink: /gpt-6-sol-vs-astra/
date: 2026-09-23
---

# GPT 6 sol's 91% cost saving puts claude on notice

{% raw %}
Every figure, price, date and benchmark score this video states, chased to a primary
source. Where a number is somebody's own reported result rather than an independent
measurement, that is said here and the reporter is named, because several of the
comparisons in this video are a vendor's own comparison of itself against a rival.

Three kinds of number appear and they are not sourced the same way.

A **published score** is a figure on a leaderboard or a model page, cited here at the page
that carries it. A **vendor comparison** is one lab's claim about another lab's model, and
is cited to the lab that made the claim rather than presented as neutral. An
**illustration** is arithmetic the video does itself out of published per token rates; it
is not a measured price for any real piece of work, and the script says so where it
appears.

Prices are the standard API rates for requests under the long context threshold, as listed
on 23 September 2026. Several of them are introductory or promotional and will move.

## The two releases, and the week they landed in

- **GPT 6 sol** and **GPT 6 luna** launched **22 September 2026**, at API prices 50 per
  cent below the GPT 5.6 generation. They are available in the **API**, in **Codex**, and
  in **ChatGPT Work** for Plus, Pro, Business, Enterprise and Edu; Free and Go users get
  luna in the desktop app. <https://openai.com/index/introducing-gpt-6-sol-and-luna/>
- **GPT 6 astra** arrived earlier the same month, **3 September 2026**, with a
  **1,050,000** token context window.
  <https://www.marktechpost.com/2026/09/03/openai-releases-gpt-6-astra-a-1-05m-context-computer-use-model-gated-behind-a-critical-cyber-threshold/>
- **Claude opus 5.5** was released by Anthropic on the **same day as sol**, 22 September
  2026. <https://www.anthropic.com/claude-opus-5-5>
- **Gemini 3.8 flash** is current at introductory rates through 31 December 2026.
  <https://ai.google.dev/gemini-api/docs/latest-model>

The script's "sol launched on september twenty second, joining astra, which arrived
earlier in the month" and "anthropic released opus 5.5 the same day as sol" are both
correct.

## Prices, per million tokens

All from OpenAI's own pricing table, standard processing, short context.
<https://developers.openai.com/api/docs/pricing>

| model | input | cached input | output |
| --- | --- | --- | --- |
| gpt-6-astra | $10.00 | $1.00 | $50.00 |
| gpt-6-sol | $2.00 | $0.20 | $10.00 |
| gpt-6-luna | $0.10 | $0.01 | $0.50 |
| gpt-5.6-sol | $4.00 | $0.40 | $20.00 |

Claude opus 5.5 is **$4.00** input, **$20.00** output, **$0.20** cache read and **$5.00**
cache write. <https://www.anthropic.com/claude-opus-5-5>

Gemini 3.8 flash is **$0.75** input and **$3.75** output at its introductory rate, moving
to **$1.50** and **$7.50** on 1 January 2027. <https://ai.google.dev/gemini-api/docs/latest-model>

Every ratio the script states follows from that table:

- Astra is **five times** sol on both uncached rates. 10 ÷ 2 = 5, and 50 ÷ 10 = 5.
- Sol **halves** the previous GPT 5.6 sol rates. $4 to $2, and $20 to $10.
- Luna is **one twentieth** of sol. 0.10 ÷ 2.00 and 0.50 ÷ 10.00 are both 1/20.
- Opus 5.5 is **twice sol's uncached rates** and carries the **same twenty cent cached
  input rate**. $4 against $2, $20 against $10, and $0.20 against $0.20.

## Context window and the long context threshold

- Both sol and astra list a **1,050,000** token context window, with a maximum output of
  128,000 tokens. <https://developers.openai.com/api/docs/pricing>
- Above **272,000 input tokens** the **whole request** moves to long context rates.
  Input doubles and output rises by half: sol goes from $2 and $10 to **$4 and $15**, and
  astra from $10 and $50 to **$20 and $75**.
  <https://developers.openai.com/api/docs/pricing>

## Prompt caching

Cached input is priced at **one tenth** of standard input on every GPT 6 model, which is
the **ninety per cent** discount the script states: astra $10 to $1.00, sol $2 to $0.20,
luna $0.10 to $0.01. **Output is not discounted** at any cache rate, and **cache writes
carry their own price**, listed separately, at $12.50 per million for astra.
<https://developers.openai.com/api/docs/pricing>

## The worked example

This is the video's own arithmetic on the published rates, not a measured bill, and the
script says so where it appears.

At 100,000 uncached input tokens and 20,000 output tokens, standard short context rates:

- **sol**: 0.1 × $2.00 = $0.20, plus 0.02 × $10.00 = $0.20. Total **$0.40**.
- **astra**: 0.1 × $10.00 = $1.00, plus 0.02 × $50.00 = $1.00. Total **$2.00**.
- Twenty identical jobs: **$8.00** against **$40.00**.

Token charges only. It excludes tool calls, cache writes, and every retry a real job
takes, which is the point the script makes immediately afterwards.

## FrontierCode

Cognition's benchmark for whether a change is **mergeable**, not merely whether it passes.
Tasks are written by the open source maintainers of the repositories they come from, and
submissions are scored for **correctness, tests, scope, style and maintainability**
against maintainer authored rubrics. <https://cognition.com/blog/frontier-code>
<https://cognition.com/frontiercode>

OpenAI reports that GPT 6 sol **matches Claude fable 5.1 at extra high effort** on
FrontierCode at substantially lower cost per task.
<https://openai.com/index/introducing-gpt-6-sol-and-luna/>

That is a vendor comparison and it is the form the script uses. **Sol's own FrontierCode
percentage is not put on screen in this video**: Cognition's public leaderboard loads its
table dynamically and the GPT 6 entries could not be read off it directly, and the figures
circulating in secondary write ups could not be confirmed against Cognition's own page.
The claim that survives sourcing is the one OpenAI makes, so that is the one the picture
carries.

## DeepSWE v1.1

Datacurve's benchmark: 113 long horizon engineering tasks across 91 repositories and five
languages, with agents committing changes that are then verified in isolated containers so
the environment cannot be gamed. <https://deepswe.datacurve.ai/blog/deepswe-v1-1>

Leaderboard, pass@1 with the stated uncertainty and average cost per task:

| model | pass@1 | avg cost per task |
| --- | --- | --- |
| GPT 6 astra | 74% ±3% | $4.43 |
| Gemini 3.8 flash | 74% ±1% | $2.36 |
| Claude opus 5 | 74% ±4% | $11.84 |
| GPT 5.6 sol | 73% ±3% | $6.46 |
| Claude fable 5 | 70% ±3% | $13.41 |
| GLM 5.3 | 69% ±3% | $3.99 |
| Kimi K3 | 69% ±5% | $4.65 |

<https://deepswe.datacurve.ai/blog/deepswe-v1-1>

- Astra's precise published figure is **74.1%**. <https://benchlm.ai/models/gpt-6-astra>
- **GPT 6 sol scores 68.8%** at maximum effort. This is **OpenAI's own reported figure**;
  sol is not yet listed on Datacurve's public leaderboard.
  <https://www.vellum.ai/blog/gpt-6-sol-and-luna-benchmarks-explained>
- The gap the script states, **5.3 points**, is 74.1 − 68.8.
- Sol is **1.1 points** behind Claude fable 5 at extra high effort, 69.9%, at roughly
  **80 per cent less cost per task**, as OpenAI reports it.
  <https://www.vellum.ai/blog/gpt-6-sol-and-luna-benchmarks-explained>
- Gemini and astra **both round to 74** and their uncertainties overlap: ±1 against ±3.
  Gemini's average cost per task, **$2.36**, is lower than astra's **$4.43**.
- GLM 5.3 and Kimi K3 both sit at **69%**.

## Terminal Bench 4.0 and Terminal Bench Science 0.1

Anthropic publishes both tables with its competitors' scores beside its own.
<https://www.anthropic.com/claude-opus-5-5>

| model | Terminal Bench 4.0 | Terminal Bench Science 0.1 |
| --- | --- | --- |
| Claude opus 5.5 | **66.4%** | **58.7%** |
| GPT 6 astra | **57.9%** | **64.6%** |
| Claude fable 5.1 | 55.8% | 52.6% |
| Claude opus 5 | 52.3% | 29.0% |
| GPT 5.6 sol | **37.3%** | 22.4% |

- Astra's 57.9 against GPT 5.6 sol's 37.3 is a gap of **20.6 points**, which is the
  script's "more than twenty percentage points".
- Opus 5.5's **66.4%** is above astra's published score on Terminal Bench 4.0, and the
  order **reverses** on the science variant, where astra's 64.6 leads opus 5.5's 58.7.
- The script's caution about that reversal is warranted: Terminal Bench Science is
  reported as noisy at roughly **±3.5 to 5 points** per model, and the 5.9 point gap sits
  close to that band. <https://www.vellum.ai/blog/claude-opus-5-5-benchmarks-explained>

### The fallback models caveat

Anthropic states it directly: "Claude Opus 5.5 was evaluated with its production
safeguards enabled. When they intervened, cybersecurity tasks were completed by Claude
Opus 4.8, and biology and frontier LLM development tasks were completed by Claude Opus 5."
<https://www.anthropic.com/claude-opus-5-5>

That is what the script means by the delivered setup rather than an isolated contest
between two raw models, and it is Anthropic's own disclosure rather than an outside
criticism of it.

## AutomationBench 1.0.6

Zapier's benchmark. Each task boots a simulated company across **47 simulated business
tools** spanning sales, marketing, operations, support, finance and HR, hands the agent a
request, and then **grades the resulting state of that environment** rather than the
agent's own account of what it did. There is no model acting as judge. Scoring is strict
pass or fail per task, **1.0 only if every assertion passes**, and the pass rate is the
average across tasks. <https://zapier.com/benchmarks>
<https://zapier.com/blog/introducing-automationbench/>

| model | pass rate |
| --- | --- |
| GPT 6 astra | **41.4%** |
| Claude opus 5.5 | **40.0%** |
| GPT 6 sol, extra high effort | **33.2%** |
| Claude fable 5.1 | 31.4% |
| GPT 5.6 sol | 28.8% |
| Claude opus 5 | **26.9%** |

Zapier's own leaderboard also publishes a cost per task column: **astra $1.73**, **opus
5.5 $1.28**, and **sol $0.27**. <https://zapier.com/benchmarks>

<https://www.anthropic.com/claude-opus-5-5>
<https://www.vellum.ai/blog/gpt-6-sol-and-luna-benchmarks-explained>

This is the "published automation test" of the opening line. **Sol's 33.2% does beat
Claude opus 5's 26.9%**, and sol runs the suite at **$0.27 per task**, which OpenAI
reports as roughly **nine per cent** of what Claude opus 5 spends on it.
<https://www.vellum.ai/blog/gpt-6-sol-and-luna-benchmarks-explained>

The nine per cent is OpenAI's own comparison. Claude opus 5's per task cost on this suite
is not separately published, so the ratio rests on OpenAI's reporting rather than on two
figures that can be divided by each other here. Sol's own $0.27 is published.

The script's later point that sol sits **below** opus 5.5 and astra on the same suite is
the same table read honestly: 33.2 against 40.0 and 41.4. The opening compares sol with
opus **5**, and the later chapter compares it with opus **5.5**, which is a different
model released three weeks later.

## Generation speed

Artificial Analysis measures **GPT 6 sol at about 126 output tokens per second** and
**GPT 6 astra at about 53**, roughly a **2.4** ratio, which is the script's "more than
twice the rate".
<https://artificialanalysis.ai/models/releases/comparisons/gpt-6-sol-vs-gpt-6-astra>

Two details on that page are worth stating exactly, because they are close to the
script's wording without matching it. Its own summary line reads "For output speed, GPT 6
Sol is fastest: GPT 6 Sol (max) at **125 t/s**, against GPT 6 Astra (**xhigh**) at 53 t/s."
So the sol figure is 125 rather than 126, and the astra figure is listed at extra high
effort rather than at maximum. These are live measurements that move between samples, and
the script says "about" on both numbers; the ratio is what the beat is actually about.
Because the page's own wording differs from the narration, **the effort labels are kept
off screen on that beat** and the drawing carries the two rates and the credit.

This measures generation only. It does not measure reasoning time, tool calls, or the
rounds an agent spends correcting itself, which is the distinction the script draws
immediately afterwards.

## Changing the job while it is running

- **Mid turn steering** is available across the **GPT 6 model family**, over a WebSocket
  connection to the Responses API. Completed work is preserved and the new instruction
  arrives as a continuation. The documentation is explicit about what it does not do:
  "Steering does not rewrite output already sent to your application, undo earlier
  actions, or cancel tools that have already started."
  <https://developers.openai.com/api/docs/guides/steering>
- **Asynchronous tool calling** lets the model keep reasoning, call other tools, or answer
  independent parts of a request while the application runs a tool. It is switched on with
  `async: true` on a function or custom tool, and the result is returned when ready using
  the original `call_id`. <https://developers.openai.com/api/docs/guides/latest-model>

Both of those are the basis for the script's point that a new requirement belongs inside
the current job rather than forcing a restart.

## Subscriptions against API billing

Sol reaches ChatGPT Work and Codex through plan tiers, and the API separately on metered
per token rates. <https://openai.com/index/introducing-gpt-6-sol-and-luna/>
<https://developers.openai.com/api/docs/pricing>

These are two different billing systems, which is the script's point that an API price cut
does not automatically halve a subscription. No figure is stated for any subscription and
none is put on screen.

## Not checked

- The **nine per cent** cost ratio in the opening line is OpenAI's own comparison against
  Claude opus 5 on AutomationBench. Sol's $0.27 per task is published; opus 5's per task
  cost on the same suite is not, so the ratio cannot be recomputed from two public figures.
- **Sol's FrontierCode percentage** could not be confirmed against Cognition's own
  leaderboard, which loads dynamically. Only OpenAI's "matches fable 5.1 at extra high
  effort" claim is used, and no FrontierCode number for sol appears on screen.
- The **Terminal Bench 4.0** figures for astra and GPT 5.6 sol are attributed in the script
  to OpenAI. They are quoted here from Anthropic's comparison table, which publishes the
  same values. Both labs report them; the video's attribution is loose rather than wrong.
- **Gemini 3.8 flash's $0.75 and $3.75** are introductory rates that expire on 31 December
  2026, after which the published standard rates are $1.50 and $7.50. The video states
  them as introductory.
- **Claude fable 5's DeepSWE result** was run with 73 of 2,260 trials incomplete, which
  Datacurve attributes to access being suspended by a United States government directive.
  This does not affect any figure the video states, and is noted because it sits on the
  same leaderboard the video shows.
- **Anthropic's Claude Opus 5.5 page cannot be captured.** It is a scroll driven page that
  paints only what is in view, so a headless capture returns its opening image and a cookie
  notice at any viewport height. Its figures are therefore DRAWN in this video with the
  page credited, rather than shown in its own chrome. Every number taken from it was read
  off the live page and is listed in the tables above.
- **Artificial Analysis lists sol at 125 tokens per second and astra's 53 at extra high
  effort**, where the narration says "about 126" and "the maximum effort versions". The
  figures update between samples. The effort labels are kept off screen on that beat.
- The **booking application** is an illustration written for this video. It is not a real
  product, no agent was run against it, and no figure in the video is measured from it.
{% endraw %}

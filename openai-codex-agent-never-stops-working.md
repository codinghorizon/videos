---
layout: default
title: "OpenAI Codex Can Now Work For Twenty Four Hours"
permalink: /openai-codex-agent-never-stops-working/
date: 2026-09-01
---

# OpenAI Codex Can Now Work For Twenty Four Hours

{% raw %}
Every figure, date and benchmark the finished picture puts on screen, chased to a source.
Checked 2026-08-31.

## Compaction and the long session

GPT 5.1 Codex Max was announced on 19 November 2025 as the first Codex model trained
natively to operate across multiple context windows through compaction, coherently working
over millions of tokens in a single task. As a session approaches its context limit the
model compacts its history, keeping the parts that matter, and continues in a fresh
context window.

- Building more with GPT 5.1 Codex Max, OpenAI: https://openai.com/index/gpt-5-1-codex-max/

OpenAI states that in internal evaluations GPT 5.1 Codex Max worked on a single task for
more than twenty four hours, persistently iterating on its implementation, fixing test
failures and delivering a successful result.

- Building more with GPT 5.1 Codex Max, OpenAI: https://openai.com/index/gpt-5-1-codex-max/

## GPT 5.1 Codex Max benchmark figures

Rendered on screen in beats 040, 041 and 042 as a two column comparison per benchmark.

| Benchmark | GPT 5.1 Codex | GPT 5.1 Codex Max |
|---|---|---|
| SWE bench Verified (extra high reasoning) | 73.7% | 77.9% |
| SWE Lancer IC SWE | 66.3% | 79.9% |
| Terminal Bench 2.0 | 52.8% | 58.1% |

- Building more with GPT 5.1 Codex Max, OpenAI: https://openai.com/index/gpt-5-1-codex-max/
- Model comparison table, LLM Stats: https://llm-stats.com/models/compare/claude-opus-5-vs-gpt-5.1-codex

## Token efficiency

On SWE bench Verified at medium reasoning effort, GPT 5.1 Codex Max outperforms GPT 5.1
Codex at the same reasoning effort while using 30% fewer thinking tokens. Rendered in
beat 097.

- Building more with GPT 5.1 Codex Max, OpenAI: https://openai.com/index/gpt-5-1-codex-max/

## GPT 5.6 and the Coding Agent Index

GPT 5.6 Sol at max reasoning scores 80 on the Artificial Analysis Coding Agent Index,
setting a new state of the art and leading all three of the index's evaluations. It sits
2.8 points above Claude Fable 5, which places Fable 5 at 77.2. Rendered in beat 047.

Artificial Analysis publishes the GPT 5.5 (xhigh) Coding Agent Index score as 76 following
the index revision that replaced SWE Bench Pro with Datacurve's DeepSWE. The narration's
76.4 is within rounding of the published figure but the extra decimal could not be
re-found at the source, so the on screen figure for GPT 5.5 is rendered as 76.

- GPT 5.6 benchmarks across Intelligence, Speed and Cost, Artificial Analysis:
  https://artificialanalysis.ai/articles/gpt-5-6-has-landed
- Coding Agent Index revision, Artificial Analysis:
  https://x.com/ArtificialAnlys/status/2065328920514515037

## Terminal Bench 2.1

GPT 5.6 Sol reaches 88.8% on Terminal Bench 2.1 and GPT 5.6 Sol Ultra reaches 91.9%.
Rendered in beat 048.

- GPT 5.6 benchmarks across Intelligence, Speed and Cost, Artificial Analysis:
  https://artificialanalysis.ai/articles/gpt-5-6-has-landed

## Ultra and parallel agents

OpenAI describes Ultra as a setting that coordinates four agents in parallel by default for
harder work. Artificial Analysis compares Ultra's default four agent configuration against a
one agent baseline on BrowseComp, SEC Bench Pro and Terminal Bench 2.1, and reports that
adding parallel agents moves the score against latency frontier up and to the left on all
three. Rendered in beat 075.

- GPT 5.6, OpenAI: https://openai.com/index/gpt-5-6/
- GPT 5.6 benchmarks across Intelligence, Speed and Cost, Artificial Analysis:
  https://artificialanalysis.ai/articles/gpt-5-6-has-landed

## GPT 5.6 API pricing

The narration's pricing figures are the launch rates and are out of date. They are rendered
on screen as spoken, so that the picture and the voice agree; the current rates are recorded
here and the discrepancy is listed under caveats.

Current published rates, per million tokens:

| Model | Input | Output |
|---|---|---|
| GPT 5.6 Sol | $4.00 | $20.00 |
| GPT 5.6 Terra | $2.00 | $12.00 |
| GPT 5.6 Luna | $0.20 | $1.20 |

Sol launched at $5.00 and $30.00. On 22 August 2026 the standard input, cached input and
cache write rates fell 20% and output fell 33.3%, which OpenAI describes as promotional and
says will remain available until at least 21 November 2026. Luna's rates fell by 80% with
effect from 30 July 2026.

- Advancing the price performance frontier with GPT 5.6, OpenAI:
  https://openai.com/index/advancing-the-price-performance-frontier-with-gpt-5-6/
- GPT 5.6 Sol model page, Artificial Analysis: https://artificialanalysis.ai/models/gpt-5-6-sol
- GPT 5.6 Terra API pricing, OpenRouter: https://openrouter.ai/openai/gpt-5.6-terra
- GPT 5.6 Luna API pricing, OpenRouter: https://openrouter.ai/openai/gpt-5.6-luna

## Anthropic's Claude Code session research

Anthropic analysed close to four hundred thousand Claude Code sessions recorded between
October 2025 and April 2026. Users make about 70% of planning decisions, which answer what
to build, while Claude makes about 80% of execution decisions, which answer how to build it.
Rendered in beats 052 and 053.

- How Claude Code is used in practice, Anthropic:
  https://www.anthropic.com/research/claude-code-expertise

## Claude Code on the web

Once Claude Code on the web has started a task the page can be closed and the work
continues; when it finishes it opens a pull request against the connected GitHub repository
for review. Rendered in beat 055.

- Claude Code on the web, Anthropic Help Center:
  https://support.claude.com/en/articles/12618689-claude-code-on-the-web

## Cursor Cloud Agents

Cursor Cloud Agents launched on 24 February 2026 and run in isolated virtual machines, each
with a full Linux development environment, terminal, browser and cloned repositories. An
agent can select multiple repositories in one environment, make coordinated changes across
them, run tests and open pull requests, and it keeps running with the laptop closed.
Rendered in beat 057.

The narration's "more than forty percent" figure is not supported. The picture renders the
published figure instead. That figure is 35% of merged internal pull requests as of
April 2026, up from 30% at the February 2026 launch. A separate Cursor figure states that
sandboxed cloud agents stop 40% less often than unsandboxed ones, which is a different
measurement.

- Cloud environment setup, Cursor Docs: https://cursor.com/docs/cloud-agent/setup
- Cursor Cloud Agents get their own computers, DevOps.com:
  https://devops.com/cursor-cloud-agents-get-their-own-computers-and-35-of-internal-prs-to-prove-it/

## Google Antigravity

Antigravity runs parallel agents and dynamic subagents with scheduled background tasks. The
orchestrator monitors every active subagent and surfaces a failure in the terminal, and any
subagent's progress can be opened from the subagent panel. The CLI and the desktop app share
the same agent harness. Rendered in beats 060 and 134.

- Subagents, Google Antigravity Docs: https://antigravity.google/docs/subagents/
- Background tasks and subagents, Google Antigravity Docs:
  https://antigravity.google/docs/cli/subagents/
- Antigravity CLI, Google Antigravity: https://antigravity.google/product/antigravity-cli/

## Codex adoption

Codex passed five million weekly active users, more than six times its total at the February
desktop app launch, with knowledge workers making up roughly 20% of them. Rendered in
beat 066.

95% of OpenAI engineers use Codex, and engineers who adopted it open about 70% more pull
requests than their peers. This is a company reported internal figure rather than an
independent measurement, which the narration says explicitly. Rendered in beat 067.

- Codex is becoming a productivity tool for everyone, OpenAI:
  https://openai.com/index/codex-for-knowledge-work/
- OpenAI touts broadening Codex usage with 5 million weekly active users, Constellation
  Research:
  https://www.constellationr.com/insights/news/openai-touts-broadening-codex-usage-5-million-weekly-active-users

## Sandbox and review posture

Codex runs in a sandbox by default. File writes are limited to the workspace and network
access is disabled unless the developer enables it. OpenAI recommends reviewing the agent's
work before deploying it. Rendered in beats 106 and 107.

- Building more with GPT 5.1 Codex Max, OpenAI: https://openai.com/index/gpt-5-1-codex-max/

## Caveats

Figures that were recorded before they could be checked, and how the picture handles them.

- **GPT 5.6 pricing.** The narration gives Sol at five and thirty dollars, Terra at two
  dollars fifty and fifteen dollars, and Luna at one dollar and six dollars. Sol's figures
  were correct at launch and were cut on 22 August 2026. Terra's published rates are two
  dollars and twelve dollars. Luna's are twenty cents and one dollar twenty, after an 80%
  cut on 30 July 2026. Beats 098 and 099 render the figures as spoken, so the six prices on
  screen are the launch rates rather than the rates in force at the time of writing.
- **Cursor's share of internal pull requests.** The narration says more than forty percent.
  The published figure is 35% of merged internal pull requests as of April 2026, and that is
  what beat 058 renders, so the screen and the narration differ on this one figure.
- **GPT 5.5 on the Coding Agent Index.** The narration says 76.4. Artificial Analysis
  publishes 76. Beat 047 renders 76.
{% endraw %}

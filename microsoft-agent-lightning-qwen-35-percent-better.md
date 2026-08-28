---
layout: default
title: "A 9B Qwen Model Just Added 14.6 SWE Bench Points"
permalink: /microsoft-agent-lightning-qwen-35-percent-better/
date: 2026-08-28
---

# A 9B Qwen Model Just Added 14.6 SWE Bench Points

{% raw %}
Every figure, name and claim the finished picture puts on screen, chased to a primary
source. Sources appear on screen bottom left as `Source: ...`.

## The headline result

| Claim | Value | Source |
| --- | --- | --- |
| Model trained | Qwen3.5 9B | Agent Lightning v1.0 paper, arXiv 2608.17528 |
| SWE bench Verified before RL | 41.8% | Agent Lightning v1.0 paper, arXiv 2608.17528 |
| SWE bench Verified after RL | 56.4% | Agent Lightning v1.0 paper, arXiv 2608.17528 |
| Absolute gain | 14.6 points | Agent Lightning v1.0 paper, arXiv 2608.17528 |
| Relative lift | 34.9%, spoken as "about thirty five percent" | 56.4 / 41.8 = 1.349, derived |
| Training examples | approximately 6,000 | Agent Lightning v1.0 paper, arXiv 2608.17528 |
| Framework size | approximately 3,500 lines of code | Agent Lightning v1.0 paper and repository README |
| Algorithm | GRPO | Agent Lightning v1.0 paper, arXiv 2608.17528 |

Paper: Agent Lightning v1.0: Towards Harnessed Agentic RL. Zhiyuan He, Siwei Zhang,
Zhiwen Zhou, Yuqing Yang, Yu Kang, Yuge Zhang, Luna K. Qiu, Tin Yan Tsui, Jiahang Xu,
Chong Luo. Submitted 18 August 2026.
https://arxiv.org/abs/2608.17528

Repository: https://github.com/microsoft/agent-lightning

## The other two agents in the same paper

Used on screen only as supporting context for the coding number, never as the headline.

| Task | Model | Before | After | Gain |
| --- | --- | --- | --- | --- |
| Coding, SWE bench Verified | Qwen3.5 9B | 41.8% | 56.4% | 14.6 points |
| Search, HotpotQA | Llama 3.2 3B | 25.1% | 41.7% | 16.6 points |
| Instruction following | Qwen3 4B | 51.9% | 70.2% | 18.3 points |

Source: Agent Lightning v1.0 paper, arXiv 2608.17528.

## The data pipeline

| Claim | Value | Source |
| --- | --- | --- |
| Raw source | SWE smith | SWE-bench/SWE-smith dataset card, Hugging Face |
| Raw task count | 59,136 rows | Hugging Face dataset card, "Number of rows: 59,136" |
| Repositories | 128 | Hugging Face dataset card and SWE-smith paper, arXiv 2504.21798 |
| Removed, empty problem statement | 18,033 | Agent Lightning v1.0 paper |
| Removed, missing branch | 1,265 | Agent Lightning v1.0 paper |
| Removed, oversized test suites | tasks requiring more than 200 tests | Agent Lightning v1.0 paper |
| Difficulty probe | Qwen3.5 9B run four times per candidate | Agent Lightning v1.0 paper |
| Kept | tasks with both successes and failures across the four probes | Agent Lightning v1.0 paper |
| Added back | approximately 1,000 consistently failed tasks | Agent Lightning v1.0 paper |
| Final training set | approximately 6,000 training and 400 test examples | Agent Lightning v1.0 paper |

Note on 59,136. The SWE-smith dataset card carries two figures: the prose says
"a training dataset of 50137 task instances from 128 GitHub repositories" and the dataset
viewer reports "Number of rows: 59,136". The larger figure is the current row count and is
the one the narration uses. Both are recorded here so the discrepancy is not hidden.

SWE smith paper: SWE-smith: Scaling Data for Software Engineering Agents.
https://arxiv.org/abs/2504.21798
Dataset card: https://huggingface.co/datasets/SWE-bench/SWE-smith

## The architecture

Four components, named as the paper names them:

| Component | What it does |
| --- | --- |
| API Gateway | Stateful service storing rollouts, models and events. Exposes a REST API with rollout and proxy endpoints, and proxies the agent's model calls so the interaction data is captured |
| Rollout Controller | Runs agent executions as Kubernetes Jobs or in a local process pool, reconciling gateway state against actual executions |
| Trainer | Built on verl. Registers rollouts, waits for completion, retrieves events and assembles training samples |
| Inference endpoints | Model servers registered with the gateway, queried by the harness through the proxy |

Source: Agent Lightning v1.0 paper, arXiv 2608.17528, and
https://github.com/microsoft/agent-lightning/blob/main/docs/30-controller-configuration.md

The coding harness used in the coding example is mini SWE agent. The paper also names
OpenHands, OpenCode, Claude Code, Codex, OpenClaw and Hermes as harnesses the proxy
approach can sit behind, because integration needs only an OpenAI compatible endpoint
switch rather than framework specific code.

Source: Agent Lightning v1.0 paper, arXiv 2608.17528.

## Agent frameworks

The narration says the framework can work with common agent stacks including the OpenAI
Agents SDK, LangChain and AutoGen. That wording comes from the original Agent Lightning
paper, whose abstract states "seamless integration with existing agents developed via
diverse ways (e.g., using frameworks like LangChain, OpenAI Agents SDK, AutoGen, and
building from scratch)".

Source: Agent Lightning: Train ANY AI Agents with Reinforcement Learning,
https://arxiv.org/abs/2508.03680

The v1.0 repository ships an AutoGen example (Calc-X, "POC math reasoning example with
AutoGen and MCP calculator tools"). LangChain and the OpenAI Agents SDK are named in the
earlier paper rather than shipped as v1.0 examples, so the shot shows AutoGen as the
example that exists and the other two as stated compatibility.

Source: https://github.com/microsoft/agent-lightning

## The hardware

| Claim | Value | Source |
| --- | --- | --- |
| GPUs for the coding example | 4x B200 | Coding agent example doc, hardware table |
| Model | Qwen/Qwen3.5-9B | Coding agent example doc |
| Controller mode | Kubernetes | Coding agent example doc |
| Machines | Two: a Kubernetes controller machine and a GPU training machine | Coding agent example doc |

Source:
https://github.com/microsoft/agent-lightning/blob/main/docs/75-example-coding-agent.md

The published table reads:

| GPU | Model | Controller Mode | Trainer Mode |
| --- | --- | --- | --- |
| 4x B200 | `Qwen/Qwen3.5-9B` | K8s | Sync and async |

Each rollout runs as a Kubernetes Job inside a repository specific image, edits an
isolated checkout, runs tests and reports the reward to the gateway.

## Reward hacking prevention

Four safeguards are documented:

- Git commands disabled and the `.git` directory hidden, so the agent cannot read the fix
  out of history.
- Tasks whose test suites are unreasonably large are excluded, for example a
  python-jsonschema task requiring more than 7,000 tests.
- A Kubernetes network policy blocks general outbound network access and permits
  connections only to explicitly whitelisted services, so the agent cannot fetch the
  upstream fix.
- Rollouts and logs are recorded and reviewed for automated detection of reward hacking.

The example documentation states the reason plainly: "Without this restriction, an agent
may retrieve upstream source code or other external information and obtain reward without
solving the task as intended."

Sources: Agent Lightning v1.0 paper, arXiv 2608.17528, and
https://github.com/microsoft/agent-lightning/blob/main/docs/75-example-coding-agent.md

## SWE bench Verified

SWE bench Verified is a 500 problem subset of SWE bench, screened by human annotators for
solvability, drawn from real GitHub issues in Python repositories. A task gives the agent
a repository at a given commit and an issue, and scores it on whether the repository's
tests pass after its patch.

Source: https://openai.com/index/introducing-swe-bench-verified/

## Not checked

- Whether the 41.8 percent baseline was measured with the same harness, scaffold and
  sampling settings as the 56.4 percent trained result. The paper reports both figures
  together, which implies the same setup, but the narration's framing of the jump as a
  like for like comparison rests on that implication rather than on a separate statement.
- The relative lift is spoken as "about thirty five percent". The exact figure is 34.9
  percent, which rounds to 35, but no source states 35 percent directly.
- "About six thousand training examples" and "about five thousand" plus "about one
  thousand" are the paper's own approximations. No exact final count is published.
{% endraw %}

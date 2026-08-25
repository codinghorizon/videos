---
layout: default
title: "Your AI Agent Is Forgetting The Most Expensive Part"
permalink: /openviking-turns-agent-memory-into-a-database/
date: 2026-08-25
---

# Your AI Agent Is Forgetting The Most Expensive Part

{% raw %}
Sources for every figure, version, licence and benchmark this video puts on screen.
Checked 2026-08-25.

## What OpenViking is

OpenViking is an open source context database for AI agents, published by ByteDance's
Volcengine team at `github.com/volcengine/OpenViking`. It stores memory, resources and
skills as one virtual filesystem addressed by a `viking://` URI, so an agent browses its
own context rather than querying an opaque vector store.

- Repository: https://github.com/volcengine/OpenViking
- Documentation: https://docs.openviking.ai/en/getting-started/01-introduction
- Package: https://pypi.org/project/openviking/

## The three loading tiers

The project documents three levels of context, loaded on demand:

| Level | What it holds |
| --- | --- |
| L0 | the abstract, for deciding whether a directory is relevant at all |
| L1 | the overview, enough to understand what is inside without opening every file |
| L2 | the detail, the original source, loaded only when the task earns it |

L0 and L1 are directory sidecars written alongside the content as `.abstract.md` and
`.overview.md`. Parent summaries are generated bottom up: the semantic processor walks
the tree upward so a directory's summary incorporates its children.

- https://github.com/volcengine/OpenViking
- https://docs.openviking.ai/en/getting-started/01-introduction
- https://blog.openviking.ai/post/openviking-context-database-architecture/

## Version tested

The published evaluations were run on **0.3.22**.

- https://github.com/volcengine/OpenViking

## LoCoMo, long conversation memory accuracy

Native baseline against the same agent with OpenViking attached:

| Integration | Baseline | With OpenViking | Change |
| --- | --- | --- | --- |
| OpenClaw | 24.20% | 82.08% | up 57.88 points |
| Hermes | 33.38% | 82.86% | up 49.48 points |
| Claude Code | 57.21% | 80.32% | up 23.11 points |

- https://github.com/volcengine/OpenViking

## Input tokens and latency

Across the three agent integrations the project reports input tokens falling by
**34.3% to 91.0%** and query latency improving by **58.45% to 66.10%**. The
documentation separately reports an **83%** token cost reduction for OpenClaw
specifically (4.3M tokens against a 24.6M baseline).

- https://github.com/volcengine/OpenViking
- https://volcengine-openviking.mintlify.app/

## tau2 bench, task success on multi turn work

| Domain | Baseline | With OpenViking | Change |
| --- | --- | --- | --- |
| retail | 70.94% | 77.81% | up 6.87 points |
| airline | 54.38% | 66.25% | up 11.87 points |

- https://github.com/volcengine/OpenViking

## Maturity and licence

The published package classifier is **Development Status :: 3 - Alpha**, and the licence
is **AGPL-3.0**. The repository notes exceptions: `crates/ov_cli` and the examples are
Apache 2.0. AGPL section 13 covers remote network interaction, which is the clause that
makes it a question for commercial codebases rather than a formality.

- https://pypi.org/project/openviking/
- https://github.com/volcengine/OpenViking
- https://www.gnu.org/licenses/agpl-3.0.en.html

## Hosting

Alongside self hosting, a managed SaaS is offered on ByteDance's **Volcano Engine**, in
personal and enterprise tiers.

- https://github.com/volcengine/OpenViking
- https://docs.openviking.ai/en/getting-started/01-introduction

## Observability

The project lists visualised retrieval trajectories as its answer to context opacity:
the route a retrieval took, the scope and path at each hop, and which level was loaded.

- https://volcengine-openviking.mintlify.app/

## Mem0

Mem0 exposes a small memory API, `add()` and `search()`, embedding content into a vector
store for semantic retrieval. Its Pro tier additionally builds a knowledge graph of
entities and relationships for multi hop queries. It is framework agnostic.

- https://docs.mem0.ai/
- https://mem0.ai/blog/graph-memory-solutions-ai-agents

## Zep

Zep builds a **temporal knowledge graph**, which its documentation calls the Context
Graph, out of messages and documents. It extracts entities, relationships and facts, and
produces episodes, thread summaries and user summaries. Facts carry validity dates: as
new data arrives, outdated facts are invalidated with a timestamp rather than deleted,
so history is preserved.

- https://help.getzep.com/

## Letta

Letta is a stateful agent framework rather than a memory store. Agents run inside the
Letta runtime, which owns the agent loop, tool execution, state persistence and tiered
memory, with core memory held in the context window.

- https://vectorize.io/articles/mem0-vs-letta
- https://aicoolies.com/comparisons/mem0-vs-letta

## Not verified

- **Input tokens falling by 63% for Claude Code specifically.** The narration states
  this figure for the Claude Code row. The project publishes a *range* across its three
  integrations (34.3% to 91.0%) and an 83% figure for OpenClaw; a per integration figure
  of 63% for Claude Code appears in OpenViking's own summary copy but could not be
  chased to a primary table. The video therefore shows the published range on screen and
  does not render 63 anywhere.
- **"Protected fields", "stable sampling" and "freshness"** as named documentation
  concepts. Sidecar metadata and bottom up parent summary generation are both attested;
  these three terms are named in the narration but were not found in the published docs,
  so the shot draws the mechanisms that could be sourced instead of listing them.
- **All accuracy, token and task success figures above are vendor reported**, measured
  and published by the project itself. No independent reproduction was found.
{% endraw %}

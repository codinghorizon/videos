---
layout: default
title: "Why AI Agents Are Turning Into Graphs Instead of Loops"
permalink: /ai-agents-are-moving-from-loops-to-graphs/
date: 2026-08-08
---

# Why AI Agents Are Turning Into Graphs Instead of Loops

Every figure, name and claim the finished picture puts on screen, chased back to where it
came from. One link each, all of them public.

The video is an explainer about how agent architectures are changing. Nothing here was
tested or benchmarked first hand; everything below is somebody else reporting on their own
work, and it is cited as such.


## The four agentic design patterns

The video attributes four patterns to Andrew Ng: reflection, tool use, planning and
multi-agent collaboration. That is his own framing and his own wording.

- **The four patterns.** "Last week, I described four design patterns for AI agentic
  workflows that I believe will drive significant progress this year: Reflection, Tool use,
  Planning and Multi-agent collaboration."
  Andrew Ng, 28 March 2024 — https://x.com/AndrewYNg/status/1773393357022298617
- **The letter series they come from.** *Agentic Design Patterns*, Parts 1 to 5, in The
  Batch. Part 5 is the multi-agent one —
  https://www.deeplearning.ai/the-batch/agentic-design-patterns-part-5-multi-agent-collaboration

**The four job titles on screen** (software engineer, product manager, designer, QA
engineer) are Ng's own example, not a paraphrase: "Given a complex task like writing
software, a multi-agent approach would break down the task into subtasks to be executed by
different roles — such as a software engineer, product manager, designer, QA (quality
assurance) engineer, and so on."
Andrew Ng, 18 April 2024 — https://x.com/AndrewYNg/status/1780991671855161506

The open source project that letter points at, where language models are prompted to act as
a CEO, designer, product manager or tester and build software together, is ChatDev —
https://github.com/OpenBMB/ChatDev


## Breaking a process into steps, then adding autonomy

The chapter that draws a business process being cut into steps, tested step by step and
then given autonomy by degrees is Ng's own teaching material rather than a quotation.

- **Degrees of autonomy, and task decomposition.** Ng's *Agentic AI* course opens on
  identifying the steps in a workflow and on autonomy as a range rather than a switch:
  "You'll learn to deconstruct business processes into agentic workflows, identifying where
  human-like iteration and tool interaction can automate complex tasks."
  https://www.deeplearning.ai/courses/agentic-ai/


## What LangChain means by an agent

The shot that has a model choosing which branch runs next is built on LangChain's own
definition.

- "An AI agent is a system that uses an LLM to decide the control flow of an application."
  Harrison Chase, *What is an AI agent?* —
  https://www.langchain.com/blog/what-is-an-agent

The same piece is where the idea of a spectrum rather than a category comes from: a system
is more agentic the more of its behaviour the model decides.

- **LangGraph**, the framework named on screen, is LangChain's graph based agent runtime —
  https://www.langchain.com/langgraph


## Managed Deep Agents

- **What it is.** An API first hosted runtime for creating, running and operating deep
  agents, introduced in private beta.
  https://www.langchain.com/blog/introducing-managed-deep-agents
- **The capabilities the machine room shot draws**, one bay each: durable threads,
  checkpointing, streaming, human in the loop, persistent context, sandboxes and tracing.
  All of them are listed as what the managed runtime handles.
  https://docs.langchain.com/langsmith/managed-deep-agents-overview
- **"Your repo / managed runtime", and the private beta seal.** The agent definition stays
  in the developer's own repository while LangSmith provides the durable runs, sandboxes,
  context, memory and traces. Private beta, LangSmith Cloud, US region.
  https://www.langchain.com/blog/introducing-managed-deep-agents

**Deep Agents** itself, the open source harness underneath it that gives an agent planning,
tools, a file system and subagents — https://github.com/langchain-ai/deepagents


## The survey figures

Four figures on screen, all from the same survey, which LangChain ran and published itself.

| On screen | Figure | Source |
|---|---|---|
| `1,300+ PEOPLE SURVEYED` | more than 1,300 professionals | LangChain, State of AI Agents |
| `57% ALREADY IN PRODUCTION` | 57% have agents in production | as above |
| `QUALITY 32%` | quality cited as a top barrier by 32% | as above |
| `OBSERVABILITY 89%` | nearly 89% have implemented observability | as above |
| `EVALUATIONS 52%` | evals adoption at 52% | as above |

https://www.langchain.com/stateofaiagents

The comparison the video draws out of the last two rows — that observability is far ahead of
evaluation — is the report's own framing rather than an inference: it presents 89 per cent
observability as "outpacing evals adoption at 52%".


## Deep Agents 0.7

- **Roughly 65 per cent fewer base harness input tokens, at comparable performance.** The
  release simplifies the base harness: the base system prompt is removed, builtin tool
  descriptions are trimmed by 43 per cent, and todos become opt in. Input tokens on a
  default agent turn drop 65 per cent, from 5,395 to 1,895, validated against a revamped
  evaluation suite with no quality regression.
  https://www.langchain.com/blog/deep-agents-v0-7
- The release history — https://github.com/langchain-ai/deepagents/releases


## Where agent systems fail

The chapter that lights a fault at every stage of one task — planning, memory, retrieval,
delegation and tool use — reflects published work on failure modes across an agent's whole
trajectory rather than at a single step.

- *Beyond Black-Box Benchmarking: Observability, Analytics, and Optimization of Agentic
  Systems* — https://arxiv.org/abs/2503.06745


## The marks on screen

Real products are drawn with their real marks, taken from simple-icons and used in their
published brand colours: Claude, LangChain, LangGraph, Python, JavaScript, Git, Docker,
PostgreSQL, Kubernetes, GraphQL, Zendesk, Intercom, Grafana, Datadog, Sentry, OpenTelemetry
and X. https://simpleicons.org/

The tools shown on the observability wall (Grafana, Datadog, Sentry, OpenTelemetry) are
illustrations of the category the survey figure describes. The survey does not name them.


## Further reading

- **Agentic Design Patterns, Part 1** — the whole argument for why an agentic loop beats a
  single generation, in about six hundred words.
  https://www.deeplearning.ai/the-batch/how-agents-can-improve-llm-performance/
- **LangGraph's own explanation of why a graph** — what branching, checkpoints and human in
  the loop actually buy you. https://langchain-ai.github.io/langgraph/concepts/why-langgraph/
- **Deep Agents 0.7** is worth reading even if you never use it, because it is a rare public
  writeup of taking complexity back out of an agent framework rather than adding it.
  https://www.langchain.com/blog/deep-agents-v0-7

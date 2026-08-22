---
layout: default
title: "Alibaba Just Made AI Agents Much Harder To Hide"
permalink: /alibaba-agentsight-makes-ai-agents-feel-dangerous/
date: 2026-08-22
---

# Alibaba Just Made AI Agents Much Harder To Hide

{% raw %}
Sources for every figure, version, requirement and capability the finished picture puts
on screen. Chased to a primary source and cited.

## What AgentSight is

Alibaba documents AgentSight as an agent observability component inside ANOLISA, its
system analysis toolkit for Anolis OS. The documentation opens:

> "AgentSight is a zero-instrumentation AI Agent observability tool based on eBPF. It
> captures LLM API calls, Token consumption, and process behavior at the kernel level
> without modifying Agent code."

Source: `alibaba/anolisa`, `docs/user-guide/en/agent-observability/agentsight.md`
https://github.com/alibaba/anolisa/blob/main/docs/user-guide/en/agent-observability/agentsight.md

The upstream project of the same name is an open source research tool from the
eunomia-bpf group, MIT licensed, first published July 2025, with an accompanying paper.

- Repository: https://github.com/eunomia-bpf/agentsight
- Paper: *AgentSight: System-Level Observability for AI Agents Using eBPF*, arXiv:2508.02736
  https://arxiv.org/abs/2508.02736
- Also published at the 4th Workshop on Practical Adoption Challenges of ML for Systems,
  DOI 10.1145/3766882.3767169

## Capabilities on screen

The ANOLISA documentation lists these capabilities in a table, and the video's shots
follow it item for item.

| On screen | Documented as |
|---|---|
| token consumption analysis | "Multi-dimensional Token accounting by agent, task, and model" |
| behaviour audit | "Complete tracing of LLM calls and process execution" |
| dashboard | "Web UI for real-time Token trends, Agent health, and session traces" |
| agent discovery | "Automatic detection of running AI Agent processes" |
| interruption detection | "Detection of LLM errors, SSE truncation, context overflow, and crashes" |
| external log export | "Supports exporting structured events to external log services" |

Source: as above.

## The five interruption types

The documentation gives the type names and their default severities, which the shot
renders exactly:

| Type | Condition | Default severity |
|---|---|---|
| `llm_error` | HTTP status >= 400, or an SSE body containing an error | high |
| `sse_truncated` | SSE stream ended without `finish_reason=stop` | high |
| `context_overflow` | context length exceeded | high |
| `agent_crash` | agent process disappeared mid session | critical |
| `token_limit` | `finish_reason=length` with output near max | medium |

Source: as above.

## Requirements, which the video states as the catch

| On screen | Documented as |
|---|---|
| Linux only | "OS: Linux" |
| kernel 5.8 or newer, with BTF | "Kernel: >= 5.8 (BTF support required)" |
| root or CAP_BPF | "Privileges: root or CAP_BPF (for eBPF probes)" |
| a system service | `sudo systemctl enable --now agentsight.service` is the recommended deployment |
| data under a system log path | "stores data under `/var/log/sysak/.agentsight`", root owned, private umask |
| dashboard port | `http://localhost:7396` |

Source: as above.

The upstream repository states a lower kernel floor for its own binary ("Linux kernel:
4.1+ with eBPF support (5.0+ recommended)"), because it ships a different set of commands.
The video quotes the Alibaba documentation, which is the packaging being discussed, and
that documentation says 5.8 with BTF.

## The macOS limitation

> "On macOS, AgentSight provides two commands: `trace` (trajectory collector that scans
> local JSONL session files, no eBPF) and `serve` (Dashboard viewer). All other
> eBPF-dependent commands are Linux-only."

Source: as above. The shot shows `trace` and `serve` lit and the remaining documented
commands (`token`, `audit`, `discover`, `interruption`) dark.

## What an event actually carries

The video renders an audit event with `pid`, `comm`, `command`, `argv`, `model`,
`input_tokens` and `output_tokens`, and states that command line arguments can be
exposed. The upstream snapshot schema documents those fields, and flags `argv` explicitly:

> `argv` — array of strings — "Yes; may include user data, paths, tokens, or secrets."

It also documents `command` ("may contain the executable or command text"), `comm`, `pid`,
`ppid`, `root_pid`, and a `model` identifier on token records.

Source: `eunomia-bpf/agentsight`, `docs/snapshot-schema.md`
https://github.com/eunomia-bpf/agentsight/blob/master/docs/snapshot-schema.md

## The comparison the video draws

The upstream README makes the same comparison the script makes, naming the tools:

> "Application-level tools such as LangSmith, Langfuse, and Phoenix are great for traces,
> prompts, tokens, evals, and latency when you own the application code... AgentSight
> focuses on the layer those tools often miss: what the agent actually does at the system
> boundary."

It also states the mechanism: plaintext is captured at SSL/TLS call boundaries rather than
through a proxy, and process execution and file access are correlated with it.

Source: https://github.com/eunomia-bpf/agentsight

## Overhead

The paper reports the boundary tracing approach costs "less than 3% performance overhead".
The video does not put this number on screen, because the narration does not claim it.

Source: arXiv:2508.02736.

## Not checked

- **"Alibaba just published AgentSight."** The narration attributes the tool to Alibaba.
  Alibaba packages, documents and ships AgentSight as an ANOLISA component, and the
  capability list, requirements and macOS limitation the video shows all come from
  Alibaba's own documentation. The upstream project of the same name is an independent
  open source research project from the eunomia-bpf group, first published in July 2025.
  Both are true at once, and the video's picture cites whichever source it is drawing.
- **"It keeps metadata like provider and model version."** A `model` identifier is
  documented on token and LLM records. A separate *provider* field is not documented in
  either source read, so no shot renders one.
- The dollar figures, token counts, session timings, file counts and process ids in the
  shots are illustrative of the shape of a run. They are not measurements of a real
  AgentSight session and nothing on screen presents them as published figures.
{% endraw %}

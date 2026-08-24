---
layout: default
title: "MCP Just Became The AI Agent Control Layer War"
permalink: /mcp-is-becoming-agent-infrastructure/
date: 2026-08-24
---

# MCP Just Became The AI Agent Control Layer War

{% raw %}
Sources for every figure, date, name and quotation the finished picture puts on screen.

## The roadmap

The roadmap page is dated **2026-08-22** and states five priority areas, in this order:

1. Agentic Messaging Primitives
2. HTTP-Native Transport Unification and Hardening
3. Agent Identity and Enterprise-Ready Security
4. Improved Primitives
5. Improved SDK Developer Experience

The roadmap ranks nothing and gives no relative weighting, which is why the picture draws
the five as equal columns rather than as a bar chart.

The deliverables named on screen for each area are the ones the page lists for this roadmap
period:

- **Agentic Messaging Primitives**: server-initiated events (channels and subscriptions for
  push delivery, including webhooks) from the Triggers and Events Working Group; a
  composition review across the Agents, Transports and Triggers and Events groups. Continued
  work on Tasks is tracked as SEP-2663.
- **HTTP-Native Transport**: HTTP over stdio, described as "Streamable HTTP as the single
  binding, spoken over stdin/stdout for local servers", using HTTP/2 over stdio; caching
  work extending `ttlMs` and `cacheScope` (SEP-2549) toward ETags.
- **Agent Identity and Enterprise-Ready Security**: DPoP (Demonstrating Proof of
  Possession); agent identity and delegation built on Workload Identity Federation
  (SEP-1933), the Identity Assertion JWT Authorization Grant (ID-JAG) used by
  Enterprise-Managed Authorization, and RFC 8693 token exchange, coordinated with the IETF
  OAuth and WIMSE working groups.
- **Improved Primitives**: tool result shape (redesigning the `tools/call` interface);
  progressive discovery; primitive annotations.
- **Improved SDK Developer Experience**: the extension contract; the generated-artifacts
  experiment; conformance testing.

Source: https://modelcontextprotocol.io/development/roadmap

The roadmap page states the problem it is solving in agent identity as: "MCP authorization
assumes a person with a browser at consent time. Increasingly the caller is an agent: a
cloud workload with its own identity, acting for a user who isn't present, or spawning
sub-agents that should get narrower authority than their parent."

Source: https://modelcontextprotocol.io/development/roadmap

## The two quotations rendered on screen

Both are quoted verbatim from the roadmap announcement of 22 August 2026.

- "Connecting to a server with a hundred tools means the model pays for that entire surface
  before the user has asked a single question."
- "A remote MCP server is now no different from any other HTTP workload, making it easy to
  host and operate one on any infrastructure that developers and organizations already use
  for their APIs and services."

Source: https://blog.modelcontextprotocol.io/posts/mcp-roadmap/

## The 2026-07-28 specification release

The changelog entries the picture renders are quoted from the specification's own list of
major and minor changes:

- Protocol-level sessions and the `Mcp-Session-Id` header were removed from the Streamable
  HTTP transport; list endpoints no longer vary per connection (SEP-2567).
- MCP was made stateless: the `initialize` / `notifications/initialized` handshake was
  removed, and every request now carries its protocol version and client capabilities in
  `_meta` (SEP-2575).
- `server/discover` was added, which servers must implement to advertise supported protocol
  versions, capabilities and identity (SEP-2575).
- SSE stream resumability and message redelivery, including the `Last-Event-ID` header, were
  removed (SEP-2575).
- Tasks moved out of the core protocol into an official extension,
  `io.modelcontextprotocol/tasks`. The redesigned extension replaces the blocking
  `tasks/result` method with polling via `tasks/get`, adds `tasks/update` for
  client-to-server input, removes `tasks/list`, and allows servers to return task handles
  unsolicited (SEP-2663).
- Multi Round-Trip Requests were introduced. A server returns an `InputRequiredResult`
  (`resultType: "input_required"`) whose `inputRequests` field carries what it needs; the
  client responds with `inputResponses` on a retry of the original request (SEP-2322).
- The standard MCP request headers `Mcp-Method` and `Mcp-Name` are required on Streamable
  HTTP POST requests (SEP-2243). This is what the picture shows a gateway reading.
- `ttlMs` and `cacheScope` are required on results returned by `tools/list`,
  `prompts/list`, `resources/list`, `resources/read` and `resources/templates/list`, via a
  new `CacheableResult` interface. `cacheScope` is `"public"` or `"private"` and controls
  whether shared intermediaries may cache the response (SEP-2549).

Source: https://modelcontextprotocol.io/specification/2026-07-28/changelog

## Figures that appear on screen

Every number the picture renders is computed from the thing it is drawn beside rather than
typed next to it, so the figure and the drawing cannot disagree:

- The agent population in the intro is the length of the grid that is drawn.
- The tool counts in the discovery chapter are the number of tiles rendered.
- The countdown timers, progress bars and meters are all read off the beat's own progress.

The three sizes used to make the catalog argument (ten, fifty, two hundred) are the script's
own wording and are illustrative rather than measured; they are drawn as the exact counts
the narration says.

### Not verified

- The names, timings and contents of the example tools drawn on the imagined engineering
  org's server (`repo.search`, `ci.logs`, `incidents.timeline` and the rest) are invented for
  the illustration. No real organisation's MCP server is depicted.
- The example agent activity, audit lines, pull request titles and task identifiers shown in
  interface mockups are invented for the illustration.
- The script's characterisation of how much automation teams currently allow, and the
  proportion of a tool surface that goes unused on a given task, are the writer's argument
  rather than a measured figure. The picture draws them as an illustration and prints no
  sourced percentage.
{% endraw %}

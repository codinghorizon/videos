---
layout: default
title: "Your AI Agent Needs A Tiny Prison Before It Codes"
permalink: /ai-agents-need-a-tiny-prison/
date: 2026-08-21
---

# Your AI Agent Needs A Tiny Prison Before It Codes

{% raw %}
Every figure, version, date and named behaviour the finished picture puts on screen,
chased to a primary source. Claims the narration makes that could not be chased are
listed under **Not checked** at the end, and the picture does not draw those as figures.

## The Model Context Protocol

**Tools in MCP are model controlled.** The specification states it directly: "Tools in MCP
are designed to be **model-controlled**, meaning that the language model can discover and
invoke tools automatically based on its contextual understanding and the user's prompts."
The same page carries the safety note that there SHOULD always be a human in the loop able
to deny an invocation.

- Model Context Protocol specification, Tools. https://modelcontextprotocol.io/docs/concepts/tools

Drawn in beat 032, which shows the model scanning a tool menu and picking one.

**A tool definition is a name, a description and a schema, and the description is read by
the model.** The specification lists `name`, `title`, `description`, `inputSchema`,
`outputSchema` and `annotations` as the fields of a tool definition, and warns that clients
"MUST consider tool annotations to be untrusted unless they come from trusted servers".

- Model Context Protocol specification, Tools, Data Types. https://modelcontextprotocol.io/docs/concepts/tools

Drawn in beats 035 and 036.

**A server's tool list can change after a client has connected.** The set of tools returned
by `tools/list` "MAY change over time", and a server that declares the `listChanged`
capability sends `notifications/tools/list_changed` when it does.

- Model Context Protocol specification, Tools, Capabilities and List Changed Notification.
  https://modelcontextprotocol.io/docs/concepts/tools

Drawn in beats 024 and 100, which are the "can the tool list change after you approve it"
beats.

**MCP exposes tools, resources and prompts.** The three primitive kinds are what beat 026
names as it collapses the bespoke connectors into one shape.

- Model Context Protocol specification. https://modelcontextprotocol.io/docs/concepts/tools

## Tool poisoning

**Tool poisoning is an attack on the tool description rather than on the code.** Invariant
Labs disclosed it in April 2025, showing that instructions embedded in an MCP tool's
description are read by the model when it decides what to call, while typically not being
shown to the user by the client. Their published experiments include exfiltrating data
using a poisoned tool description.

- Invariant Labs, MCP Security Notification: Tool Poisoning Attacks.
  https://invariantlabs.ai/blog/mcp-security-notification-tool-poisoning-attacks
- Reproduction code: https://github.com/invariantlabs-ai/mcp-injection-experiments

Drawn in beats 037 and 038. The on screen framing follows the description based
definition, which is what the narration describes.

**OWASP catalogues MCP Tool Poisoning as an indirect prompt injection attack against
agents connected to MCP servers**, and locates the root cause in a trust gap between
connect time and runtime: "Tool descriptions are reviewed once, when the agent first
connects to a server. Tool responses go straight into the LLM context with no equivalent
check."

- OWASP, MCP Tool Poisoning. https://owasp.org/www-community/attacks/MCP_Tool_Poisoning

Worth noting that OWASP's entry emphasises poisoned tool **responses** where the Invariant
Labs disclosure emphasises poisoned **descriptions**. The video describes the description
route, which is the one the narration sets out, and both are documented.

## Containers, and what Docker actually ships

**Docker packages MCP servers as signed container images with a bill of materials.**
Servers in the Docker MCP Catalog are built by Docker with build attestations, source
provenance and "Signed SBOMs: Software Bill of Materials with cryptographic signatures",
and signatures can be verified at run time with
`docker mcp gateway run --verify-signatures`.

- Docker, Introducing MCP Catalog and Toolkit. https://www.docker.com/blog/introducing-docker-mcp-catalog-and-toolkit/
- Docker Docs, MCP Toolkit FAQs. https://docs.docker.com/ai/mcp-catalog-and-toolkit/faqs/

Drawn in beats 056 and 058.

**Each server runs isolated, rather than on the host.** Docker's announcement states the
servers run "with built-in memory, network and disk isolation", and contrasts this with
"launching tools with full host access via npx or uvx".

- Docker, Introducing MCP Catalog and Toolkit. https://www.docker.com/blog/introducing-docker-mcp-catalog-and-toolkit/

Drawn in beats 054, 057 and 060.

**Docker's own security guidance is to cap resources and mount as little as possible:**
"Run servers in containers (not on the host) with CPU/memory caps and a read only file
system where possible. Treat each server as untrusted code with the least privilege
necessary."

- Docker, MCP Security: Risks, Challenges, and How to Mitigate. https://www.docker.com/blog/mcp-security-explained/

Drawn in beat 055.

## WebAssembly and WASI

**WASI 0.3.0 was released on 11 June 2026, and it moves async into the Component Model
itself.** The release defines three native primitives, `async func`, `stream<T>` and
`future<T>`, and removes the `wasi:io` package entirely, absorbing its `pollable`,
`input-stream` and `output-stream` types into the Component Model's Canonical ABI. This is
what solves composing async work across component boundaries.

- WASI.dev, WASI 0.3. https://wasi.dev/releases/wasi-p3
- Bytecode Alliance, wasi.dev roadmap. https://github.com/bytecodealliance/wasi.dev/blob/main/docs/roadmap.md

Drawn in beat 083, which carries the date on screen as its source line. Beats 084 and 085
draw the consequence: a real tool waits on streams and composes, rather than being one
synchronous function.

**The WASI interfaces a host grants are named, separate things.** WASI 0.3 defines
`wasi:cli` (stdin, stdout, stderr, exit), `wasi:filesystem`, `wasi:sockets`, `wasi:clocks`,
`wasi:random`, `wasi:http` and `wasi:tls`.

- WASI.dev, WASI 0.3. https://wasi.dev/releases/wasi-p3

Drawn in beats 071 and 079, which name files, folders, one network target, a clock,
randomness and standard in and out, and in beat 082, whose WIT imports `wasi:cli/stdio`.

**Runtime support.** WASI 0.3 is supported in Wasmtime 43 and later, and in jco.

- WASI.dev, WASI 0.3. https://wasi.dev/releases/wasi-p3

## Not checked

- **The one CPU and two gigabytes figure in beat 061** is the narration's own example of
  what a policy can say, and the shot draws it as a pair of dials with no vendor mark
  attached. Several secondary write ups state that Docker's MCP Toolkit defaults each
  server container to 1 CPU and 2 GB, but that figure could not be found in Docker's own
  documentation, so the beat does not attribute it to Docker.
- **Terminal output, code, file trees, lockfile versions and log lines throughout** are
  illustrative mockups built for the shot, not captures of a real session. Package counts
  such as "added 411 more", the dependency graph size in beats 040 to 043, and the row and
  token counts in beats 023 and 052 are drawn to make the mechanism legible and are not
  measurements of a specific incident.
- **The npm supply chain story in beats 039 to 042** is told in the shape the narration
  uses, a maintainer account compromise spreading through a transitive dependency tree. No
  single named incident is shown on screen and none is cited, because the narration names
  none.
- **"Thousands of small tools" in beat 115** follows the narration. The counter is drawn
  from the tiles in the shot rather than from a registry count, and no registry total is
  claimed.
- **The curves in beats 093, 105, 106, 114 and 149** are shape diagrams of an argument the
  narration makes, not plotted datasets. They carry axis labels but no figures, so nothing
  on screen states a measured value.
{% endraw %}

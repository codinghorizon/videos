---
layout: default
title: "The Local AI Repo Everyone Is Quietly Moving To"
permalink: /open-webui-local-ai-control-room/
date: 2026-08-24
---

# The Local AI Repo Everyone Is Quietly Moving To

{% raw %}
Sources for every figure, name, path and quotation the finished picture puts on screen.
Checked 24 August 2026.

## The repository

**Open WebUI star count.** 149,780 stars, 21,849 forks, at the time of checking. The
narration says "almost one hundred and fifty thousand", which is what the count supports.
Created 6 October 2023.

- https://api.github.com/repos/open-webui/open-webui
- https://github.com/open-webui/open-webui

**What the project calls itself.** The repository description is "User-friendly AI
Interface (Supports Ollama, OpenAI API, ...)". The project site is https://openwebui.com.

- https://github.com/open-webui/open-webui

**Latest release at the time of checking.** v0.11.0, published 27 July 2026.

- https://api.github.com/repos/open-webui/open-webui/releases/latest

## What it connects to

**Ollama and OpenAI compatible endpoints.** The README states it can "Connect any
OpenAI-compatible API alongside local Ollama models", and names LM Studio, GroqCloud,
Mistral, OpenRouter and vLLM as examples of providers that speak that API shape.

- https://github.com/open-webui/open-webui#readme

**Ollama's default address.** "Ollama binds 127.0.0.1 port 11434 by default." The bind
address is changed with the `OLLAMA_HOST` environment variable. This is the endpoint the
connection settings shot fills in.

- https://docs.ollama.com/faq

## Retrieval and vector databases

**Nine vector databases.** The README states retrieval works against "9 vector databases
and multiple content-extraction engines". The nine named are Chroma, PGVector, Qdrant,
Milvus, Elasticsearch, OpenSearch, Pinecone, S3Vector and Oracle 23ai. These are the nine
the retrieval shot cycles through.

- https://github.com/open-webui/open-webui#readme

**Web search providers.** The README names SearXNG, Google PSE, Brave Search, Kagi, Mojeek
and Tavily among "dozens of providers". The three marks on screen are SearXNG, Brave and
DuckDuckGo.

- https://github.com/open-webui/open-webui#readme

## Users, models and tools

**Roles and groups.** The README describes "Granular RBAC & User Groups", where
administrators "define detailed roles, groups, and permissions". This is what the
permission matrix shot draws.

**Model presets.** The README describes wrapping "any base model with custom instructions,
tools, and knowledge", and lists "Filters, Actions, Pipes, Tools, and Skills" as the
extension points.

**Speech and images.** Speech to text is listed as local Whisper, OpenAI, Deepgram and
Azure. Text to speech is listed as Azure, ElevenLabs, OpenAI, Transformers and WebAPI.
Image generation is listed as OpenAI DALL·E, Gemini, ComfyUI (local) and AUTOMATIC1111
(local).

**Evaluation.** The README describes a "built-in arena, A/B testing, and ELO-based
leaderboards", which is what the arena leaderboard shot sorts.

- https://github.com/open-webui/open-webui#readme

## Running it

**The install commands and ports on screen.** The documented default run is:

```
docker run -d -p 3000:8080 -v open-webui:/app/backend/data \
  --name open-webui ghcr.io/open-webui/open-webui:main
```

The bundled Ollama image is `ghcr.io/open-webui/open-webui:ollama` and the GPU image is
`ghcr.io/open-webui/open-webui:cuda`. Every documented variant maps host port 3000 to
container port 8080 and mounts a named volume at `/app/backend/data`.

- https://docs.openwebui.com/getting-started/quick-start/

**The data folder.** `/app/backend/data` is the path the documented volume mount targets,
which is why the narration's point about the data folder mattering is drawn as that mount.

- https://docs.openwebui.com/getting-started/quick-start/

## Licensing and branding

**What the licence is.** Open WebUI ships a modified BSD-3-Clause licence. From v0.6.6,
effective 19 April 2025, it adds a branding clause, and the project's own documentation
says v0.6.6 and later "is not an OSI-approved 'open source' license". Everything up to and
including v0.6.5 remains under the original BSD-3-Clause with no branding requirement.

**The clause itself.** Condition 4 of the licence prohibits "altering, removing, obscuring,
or replacing any 'Open WebUI' branding, including but not limited to the name, logo, or any
visual, textual, or symbolic identifiers", in any deployment or distribution.

**The exemptions.** The same clause exempts deployments where "the total number of end
users ... does not exceed fifty (50) within any rolling thirty (30) day period", licensees
with "specific prior written permission from the copyright holder", and licensees holding
an enterprise licence that expressly permits the modification.

These three figures, the fifty users, the thirty day window and the v0.6.6 boundary, are
the ones the licence shot puts on screen.

- https://github.com/open-webui/open-webui/blob/main/LICENSE
- https://docs.openwebui.com/license/

## Ollama, for the comparison the video draws

**Ollama's own repository.** 179,334 stars at the time of checking. The video does not put
this figure on screen; it is here because the video's argument compares the two projects'
roles and it is worth knowing they are the same order of magnitude.

- https://api.github.com/repos/ollama/ollama

## Not put on screen

Figures the narration states that are not rendered as text or numbers in any shot, so that
nothing unsourced appears large:

- The "thirty seconds" of the first demo, and the "hundredth time" of the closing
  argument, are rhetorical rather than measured. The shots use them as sequence markers
  rather than as claims.
- "A hundred tiny friction points" is a figure of speech. The friction shot counts pins
  rather than asserting a number.
- No model file size, download size or tokens per second figure appears anywhere in the
  picture, because none of them is stated in the narration and none would be true across
  machines.
{% endraw %}

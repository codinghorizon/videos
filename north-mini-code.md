---
layout: default
title: "North Mini Code: The Cheap Worker Model Arrived"
permalink: /north-mini-code/
date: 2026-08-16
---

# North Mini Code: The Cheap Worker Model Arrived

{% raw %}
Every figure, name and claim this video puts on screen, chased to a primary source.

---

## The model

### 30B total parameters, 3B active

A mixture-of-experts model: 30 billion total parameters, 3 billion active per token. This is
the distinction the whole video turns on, and it is the model card's own framing.

- Cohere docs — North Mini Code 1.0: https://docs.cohere.com/docs/north-mini-code-1.0
- Hugging Face — CohereLabs/North-Mini-Code-1.0:
  https://huggingface.co/CohereLabs/North-Mini-Code-1.0
- Cohere docs, changelog: https://docs.cohere.com/changelog/north-mini-code-1-0

### 128 experts, 8 activated per token

A decoder-only transformer with sparse MoE layers, 128 experts in total and 8 activated per
token. That ratio is what the expert board on screen draws: 8 of 128 cells lit, re-rolling,
because routing is per token rather than fixed.

- Hugging Face — CohereLabs/North-Mini-Code-1.0:
  https://huggingface.co/CohereLabs/North-Mini-Code-1.0

### 256K context window, 64K output limit

Context length is 256K input and 64K output.

- Hugging Face — CohereLabs/North-Mini-Code-1.0:
  https://huggingface.co/CohereLabs/North-Mini-Code-1.0
- Cohere docs, changelog: https://docs.cohere.com/changelog/north-mini-code-1-0

### Apache 2.0

Released under Apache 2.0. The four rights the video lists — commercial use, modification,
private deployment, and wrapping into internal tooling — are the terms of that licence.

- Hugging Face — CohereLabs/North-Mini-Code-1.0:
  https://huggingface.co/CohereLabs/North-Mini-Code-1.0
- Apache License 2.0: https://www.apache.org/licenses/LICENSE-2.0

### An agentic coding model, aimed at local or controlled deployment

Cohere describes it as its first agentic coding model, optimised for code generation,
agentic software engineering and terminal tasks rather than autocomplete, and publishes
weights in three formats (bf16, fp8, w4a16) through Hugging Face, the Cohere API, Model
Vault, OpenRouter and OpenCode.

- Cohere — Introducing North Mini Code: https://cohere.com/blog/north-mini-code
- Hugging Face — CohereLabs/North-Mini-Code-1.0:
  https://huggingface.co/CohereLabs/North-Mini-Code-1.0
- Hugging Face — the quantized build:
  https://huggingface.co/CohereLabs/North-Mini-Code-1.0-w4a16

### The hardware story

The video says the local part is more complicated than the headline, and that is grounded in
Cohere's own minimum: a single H100 at FP8 or FP4. That is a data centre accelerator, which
is why "local" is not treated here as free, fast or automatically private. The quantized
w4a16 build is what brings the requirement down.

- Cohere — Introducing North Mini Code, minimum GPU configuration
  ("1x H100 @ FP8, 1x H100 @ FP4"): https://cohere.com/blog/north-mini-code

---

## Figures that are illustrative, and are marked as such on screen

The argument of this video is about how a coding agent spends turns and money. Several shots
draw that argument as a chart. Those charts come from the argument, not from a published
measurement, and they carry a note on screen saying so:

- The comparison between raw intelligence and disciplined delegation.
- The three setup comparison: frontier-everything, worker-only, and the hybrid.
- The share of a thirty turn run billed at the top rate, which is computed from the turn
  strip drawn beside it rather than typed next to it.
- The fifty per cent saving in premium turns, which is the video's own proposed target for
  the test, not a measured result.

## The worked example

The repository the video walks through — the broken export button, the mismatch between the
client field and the server validator, the file counts and the git history — is a worked
example built to show what the agent loop actually has to do. It is not a real repository,
and no figure in it is a claim about one.

---

## Not checked

- No independent benchmark of North Mini Code was used. What Cohere says the model was
  trained for is reported as Cohere's own claim.
- Real world throughput, latency and running cost on any particular hardware were not
  measured, and neither was the hybrid setup the video proposes as a test.
- Cohere publishes a minimum for FP8 and FP4 only, so no BF16 hardware figure is stated.
- The claim that licensing changes adoption for developer tools is an argument about how
  teams buy, not a sourced study.
{% endraw %}

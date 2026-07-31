---
layout: default
title: "10 Open Source AI Tools That Feel Illegal To Know"
permalink: /10-open-source-ai-tools-that-feel-illegal-to-know/
date: 2026-07-31
---

# 10 Open Source AI Tools That Feel Illegal To Know

Every figure, price, licence and version this video puts on screen, chased to a primary
source. Checked 31 July 2026. Prices are US dollars, monthly billing, individual plans.

---

## The bill in the opening

Four paid subscriptions a working developer might hold at once. They are the four the
video adds up, and the total drives the closing counter.

| Product | Price | Source |
| --- | --- | --- |
| Claude Pro | $20 per month | [claude.com/pricing](https://claude.com/pricing) — "$20 if billed monthly", $17 per month on an annual subscription |
| GitHub Copilot Pro | $10 per month | [github.com/features/copilot/plans](https://github.com/features/copilot/plans) — "$10 USD per user / month" |
| Cursor Pro | $20 per month | [cursor.com/pricing](https://cursor.com/pricing) — Individual (Pro) $20/month |
| Devin Pro | $20 per month | [devin.ai/pricing](https://devin.ai/pricing) — Pro "$20 per month" |

**$70 a month, $840 a year.** Arithmetic on the four rows above. Annual billing would
lower the Claude line to $17; the video quotes the monthly rate throughout, which is the
rate someone paying month to month actually sees.

---

## 01 Ollama

- **MIT licence.** [github.com/ollama/ollama](https://github.com/ollama/ollama) — the
  repository is published under the MIT licence.
- **Llama 3.2 3B is a 2.0 GB download.**
  [ollama.com/library/llama3.2](https://ollama.com/library/llama3.2) — the `3b` tag is
  listed at 2.0GB with a 128K context window. That is the quantised weight file Ollama
  pulls, not the size of the model in full precision.
- **Nothing is billed and nothing leaves the machine.** Ollama runs the weights locally
  and needs no API key, so the per request cost of the hosted alternative goes to zero.
  The $0.00 counter on screen is that comparison against the $70 monthly figure above.

## 02 LibreChat

- **MIT licence.** [github.com/danny-avila/LibreChat](https://github.com/danny-avila/LibreChat)
  — the repository is published under the MIT licence.
- **Self hosted, multi user, any provider.** The project describes itself as
  "open-source for self-hosting" with "Multi-User, Secure Authentication with OAuth2,
  LDAP, & Email Login Support", is "Compatible with Local & Remote AI Providers"
  including Ollama, and supports "Custom Endpoints: Use any OpenAI-compatible API with
  LibreChat, no proxy required."
- **Five seats, $1,200 a year.** Five people on a $20 per month hosted plan
  (Claude Pro, above) for twelve months. Self hosting removes the per seat multiplier;
  the model calls are still paid for separately unless the models are local.

## 03 Continue

- **Apache 2.0 licence.** [github.com/continuedev/continue](https://github.com/continuedev/continue)
  — "Apache 2.0 © 2023-2026 Continue Dev, Inc."
- **VS Code and JetBrains.** The project ships a VS Code extension (VS Code Marketplace
  and OpenVSX), a JetBrains plugin via GitHub Releases, and a CLI. The project itself
  currently recommends the CLI over the JetBrains plugin.
- **Any model, local or hosted.** Providers are set in the project's config file, and
  local runners such as Ollama are among them.
- **$120 a year.** Twelve months of GitHub Copilot Pro at $10, from the plans page above.

## 04 Aider

- **Apache 2.0 licence.** [github.com/Aider-AI/aider](https://github.com/Aider-AI/aider)
- **Works with almost any model.** The README states aider "can connect to almost any
  LLM, including local models."
- **Edits the real files and writes the commit.** "Aider automatically commits changes
  with sensible commit messages", leaving the work to be reviewed with ordinary git
  tooling.

## 05 OpenHands

- **MIT licence.** [github.com/All-Hands-AI/OpenHands](https://github.com/All-Hands-AI/OpenHands)
- **Shell, browser, pull requests.** The project documents agents that execute shell
  commands, interact with web browsers, and create and manage pull requests.
- **The paid ladder it stands against: $0, $20, $200 a month.**
  [devin.ai/pricing](https://devin.ai/pricing) — Free $0, Pro "$20 per month", Max
  "$200 per month", with team plans from $80 per month plus $40 per additional
  developer. The rung heights on screen are not to scale with the prices.

## 06 ComfyUI

- **GPL 3.0 licence.** [github.com/comfyanonymous/ComfyUI](https://github.com/comfyanonymous/ComfyUI)
- **The graph is the mechanism.** A workflow is a node graph: load the checkpoint,
  encode the prompt, sample for a set number of steps, decode the latent to an image.
  The shot draws that order because it is the order the graph runs in.
- No hosted image generation price is quoted anywhere in this video. See **Not sourced**
  below.

## 07 faster-whisper

- **MIT licence.** [github.com/SYSTRAN/faster-whisper](https://github.com/SYSTRAN/faster-whisper)
- **Up to four times faster, using less memory.** The README states: "This
  implementation is up to 4 times faster than openai/whisper for the same accuracy while
  using less memory." The on screen figure carries the "up to" from the source.
- **Word level timestamps.** The library returns segment and word level timings, which
  is what the transcript in the shot is built from.

## 08 Kokoro

- **Apache 2.0 licence.** [huggingface.co/hexgrad/Kokoro-82M](https://huggingface.co/hexgrad/Kokoro-82M)
  — "With Apache-licensed weights, Kokoro can be deployed anywhere from production
  environments to personal projects."
- **82 million parameters.** The model card describes it as "an open-weight TTS model
  with 82 million parameters."

## 09 Browser Use

- **MIT licence.** [github.com/browser-use/browser-use](https://github.com/browser-use/browser-use)
- **87.4% average on the Odysseys leaderboard.** The README states Browser Use is "#1 on
  the Odysseys leaderboard with an 87.4% average, ahead of computer-use agents from
  OpenAI, Anthropic, Google, and Microsoft." The leaderboard itself is at
  [odysseysbench.com/leaderboard](https://odysseysbench.com/leaderboard). This is the
  project's own reported placing, and leaderboards move.

## 10 Unsloth

- **Apache 2.0 for the package.** [github.com/unslothai/unsloth](https://github.com/unslothai/unsloth)
  — the core Unsloth package is Apache 2.0. Some optional components, including the
  Unsloth Studio UI, are AGPL 3.0. The chip on screen names the licence of the package
  the video is talking about.
- **Up to 2x faster with 70% less VRAM.** The README states: "Train and RL 500+ models
  up to 2x faster with 70% less VRAM; MoE up to 12x faster." Long context training is
  quoted separately at "3x faster, 30% less VRAM and 500K+ context."
- **A frozen base with a low rank adapter.** The mechanism drawn in the shot is LoRA
  style fine tuning: the base weights are held fixed and only a small pair of low rank
  matrices is trained, which is what brings the memory requirement down far enough for a
  single consumer card.

---

## Not sourced, and therefore not on screen

- **No hosted image generation price.** An earlier cut carried a monthly figure for a
  hosted image generator in the opening bill and again against ComfyUI. That vendor's
  pricing pages could not be read to confirm the figure, so both were removed: the
  opening bill is now four subscriptions whose prices were read directly, and the
  ComfyUI comparison says "billed per image" with no number attached.
- **No SWE-bench score for OpenHands.** The project's repository does not publish a
  resolve rate, and no current figure could be attributed to a primary source, so the
  benchmark gauge was cut and replaced with what the licence and the container actually
  give you.
- **Model call costs are not free.** Every tool here is free to run. Aider, Continue,
  OpenHands and Browser Use still need a model behind them, and that model is only free
  if it is one of the local ones from part one. Hardware and electricity are not counted
  anywhere in this video.
- **Licences change.** Every licence above was read on 31 July 2026 from the project's
  own repository or model card. One of the tools originally planned for this video was
  dropped during this pass because its licence had moved from a standard open source
  licence to a source available one with a branding condition, which is a reminder that
  the chip on screen is a snapshot.

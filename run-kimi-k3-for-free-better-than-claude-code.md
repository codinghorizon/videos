---
layout: default
title: "Three Ways To Run Kimi K3, And Only One Of Them Is Free"
permalink: /run-kimi-k3-for-free-better-than-claude-code/
date: 2026-08-02
---

# Three Ways To Run Kimi K3, And Only One Of Them Is Free

Every figure this video puts on screen, and where it came from.

---

## The model

**2.8 trillion total parameters, 104 billion activated per token.**
Moonshot AI's model card gives Total Parameters 2.8T and Activated Parameters 104B.
https://huggingface.co/moonshotai/Kimi-K3

**896 experts, 16 selected per token.**
Same model card: Number of Experts 896, Selected Experts per Token 16. It also gives 93
layers, 96 attention heads and a 160K vocabulary.
https://huggingface.co/moonshotai/Kimi-K3

**Context length 1,048,576 tokens.**
Stated on the model card as the context length, and repeated in the vLLM serving recipe as
`1,048,576 ctx`.
https://huggingface.co/moonshotai/Kimi-K3
https://recipes.vllm.ai/moonshotai/Kimi-K3

**Licence: Kimi K3 License.**
The model card names the licence. It is Moonshot's own licence rather than a standard
open source one, which is why the video calls it that and nothing else.
https://huggingface.co/moonshotai/Kimi-K3

**Released 16 July 2026; weights published 27 July 2026.**
The model launched first as an API and the downloadable weights followed eleven days
later.
https://venturebeat.com/technology/chinas-moonshot-ai-releases-kimi-k3-the-largest-open-source-model-ever-rivaling-top-u-s-systems

**Largest open weight model shipped.**
Moonshot bills it as the first openly released model in the three trillion parameter
class. The comparison bars are the next largest open weight releases: Kimi K2 at 1T,
DeepSeek V3 at 671B and Qwen3 Coder at 480B, each from its own model card.
https://venturebeat.com/technology/chinas-moonshot-ai-releases-kimi-k3-the-largest-open-source-model-ever-rivaling-top-u-s-systems

---

## The weights

**1.56 TB across 96 safetensors shards.**
The Hugging Face file browser reports the repository at 1.56 TB, and the shards are named
`model-00001-of-000096.safetensors` through `model-00096-of-000096.safetensors`. Most
shards are 17 GB.
https://huggingface.co/moonshotai/Kimi-K3/tree/main

**MXFP4 weights, MXFP8 activations, applied in training.**
The model card gives the quantisation as "MXFP4 weights / MXFP8 activations
(quantization-aware training)". This is what Moonshot trained and shipped, not a community
quantisation applied afterwards.
https://huggingface.co/moonshotai/Kimi-K3

**5.6 TB at bf16.**
Arithmetic, shown as a comparison rather than as a released artefact: 2.8 trillion
parameters at two bytes each is 5.6 TB. The point on screen is the difference between that
and the 1.56 TB actually published.

**6h 56m to download 1.56 TB over a 500 Mbps line.**
Arithmetic on the published repository size: 1.56 TB is 12,480 gigabits, and at 0.5
gigabits per second that is 24,960 seconds, or 6 hours 56 minutes.

---

## Serving it yourself

**At least 8x GB300.**
The vLLM recipe for the model gives "At least 8x GB300" as the minimum, and notes
"Multi-node for real production traffic". It gives 8x MI355X or MI350X as the ROCm
alternative.
https://recipes.vllm.ai/moonshotai/Kimi-K3

**24 GB on a single consumer card.**
The comparison line on screen. It is the ceiling of the common consumer parts, and it is
there to show the gap rather than to describe any particular card.

---

## The free route

**Kimi Code installs from a shell script.**
The repository gives `curl -fsSL https://code.kimi.com/kimi-code/install.sh | bash` for
macOS and Linux, and a PowerShell equivalent for Windows.
https://github.com/MoonshotAI/kimi-code

**Authentication is `/login`, with two choices.**
Run `/login` inside the CLI and pick either Kimi Code OAuth or a Moonshot AI Open Platform
API key.
https://github.com/MoonshotAI/kimi-code

**The plan ladder: Adagio free, Moderato $19, Allegretto $39, Allegro $99, Vivace $199.**
https://www.codeagentswarm.com/en/guides/kimi-code-plans-and-pricing

**The free allowance is not published.**
This is the caveat the video puts on screen rather than a number. Moonshot does not
document a request allowance, window length, concurrency or rate limit for the free rung.
Coverage describes it as "the entry point to Kimi, with tight limits" and notes that
specific allowance metrics are not publicly documented.
https://www.codeagentswarm.com/en/guides/kimi-code-plans-and-pricing
https://apidog.com/blog/how-to-use-kimi-k3-for-free/

---

## The paid route

**OpenAI compatible, at https://api.moonshot.ai/v1, model id `kimi-k3`.**
The platform documents an OpenAI format endpoint, so an existing client changes its base
URL, key and model string and nothing else.
https://platform.kimi.ai/docs/api/overview

**$3.00 per million input tokens, $15.00 per million output tokens.**
The same prices apply on the first party API and on the aggregators that carry the model.
https://artificialanalysis.ai/models/kimi-k3/providers

**$0.30 per million on a cache hit, a 90% discount on input.**
Automatic prompt caching drops the input price by an order of magnitude.
https://kimi-k2.org/blog/37-kimi-k3-api-pricing-cost-control

**There is no free API for this model.**
This is why the video calls the middle route the one you pay for. No provider currently
serves `kimi-k3` through a free OpenAI compatible endpoint; free access is the consumer
tier and the weights, not the API.
https://freellm.net/blog/is-kimi-k3-free-api-pricing-openrouter-alternatives

**Rate limiting under load.**
Capacity has been constrained across both the first party API and the aggregators, with
intermittent 429 responses reported as upstream capacity catches up.
https://freellm.net/blog/is-kimi-k3-free-api-pricing-openrouter-alternatives

---

## Benchmarks

**Moonshot's reported scores: GPQA Diamond 93.5, BrowseComp 91.2, Terminal-Bench 2.1 88.3,
OSWorld-Verified 84.8.**
All four are from the model card. The card also gives DeepSWE 67.5 and SWE-Marathon 42.0.
https://huggingface.co/moonshotai/Kimi-K3

**The same model scored 85 on Terminal-Bench 2.1 under an independent harness.**
Against Moonshot's own 88.3. The 3.3 point gap is the same model on the same benchmark
with a different scaffold, which is the caveat the video makes.
https://apidog.com/blog/kimi-k3-benchmarks/

---

## The window in practice

**90.4 with the full 1,048,576 token window and no context management.**
Moonshot's own long context result for the model.
https://www.kimi.com/blog/kimi-k3

**Usable capacity runs 60 to 70 per cent of the advertised maximum.**
The general finding across long context leaderboards, which is why the video draws the
advertised window and the usable part of it as two different bars.
https://awesomeagents.ai/leaderboards/long-context-benchmarks-leaderboard/

---

## Measured speed

**Moonshot's own endpoint: 35 tokens per second, 2.85 seconds to first token.**
**Modal: 157.3 tokens per second, 13.98 seconds to first token.**
**Databricks: 214.8 tokens per second, 10.45 seconds to first token.**
The same weights, hosted by different people, measured on the same harness. Together AI is
the quickest to start at 1.04 seconds.
https://artificialanalysis.ai/models/kimi-k3/providers

---

## Claude Code, for the comparison

**200,000 tokens of context on the subscription plans.**
Enterprise reaches 500,000, and Opus can go to a million. The 200,000 figure on screen is
the subscription default, which is what the comparison is against.
https://www.cloudzero.com/blog/claude-code-pricing/

**Max 20x at $200 per month.**
Max 5x is $100 and Pro is $20.
https://www.cloudzero.com/blog/claude-code-pricing/

---

## Caveats

- Moonshot does not publish what the free Adagio tier actually allows. The video says so
  on screen rather than estimating it.
- Every benchmark score attributed to Moonshot is Moonshot's own run. Only the
  Terminal-Bench 2.1 figure has an independent number beside it.
- Provider throughput and time to first token move as capacity changes. The figures here
  are a snapshot.
- Claude Code's context window depends on the plan and the model behind it. A million
  tokens is reachable on Opus; the comparison in this video uses the subscription default.
- The hardware minimum is what the serving recipe calls a minimum, not a comfortable
  configuration, and it is for the model as Moonshot shipped it.

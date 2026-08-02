---
layout: default
title: "Run Kimi K3 For Free And Pay 70% Less Than Claude"
permalink: /run-kimi-k3-for-free-better-than-claude-code/
date: 2026-08-02
---

# Run Kimi K3 For Free And Pay 70% Less Than Claude

Every figure this video puts on screen, with where it comes from.

## The model

**2.8T total parameters, 104B active per token.** Stated on the Kimi K3 model card.
https://huggingface.co/moonshotai/Kimi-K3

**Context window of 1,048,576 tokens.** Stated on the model card as `1048576`, and described
as a 1M token context window in the Open Platform quickstart.
https://huggingface.co/moonshotai/Kimi-K3
https://platform.kimi.ai/docs/guide/kimi-k3-quickstart

**MXFP4 weights, MXFP8 activations.** The model card gives the published precision as
"MXFP4 weights / MXFP8 activations".
https://huggingface.co/moonshotai/Kimi-K3

**96 safetensors shards, 1.56 TB.** The repository file listing shows 96 safetensors files
and a total repository size of 1.56 TB, with most shards around 16.6 to 17 GB.
https://huggingface.co/moonshotai/Kimi-K3/tree/main

**Kimi K3 License.** The licence named on the model card.
https://huggingface.co/moonshotai/Kimi-K3

**Parameter counts used for comparison.** Llama 3.1 405B, DeepSeek V3 671B and Kimi K2 1T
are the counts published on each model's own card. They are on screen only to give the
2.8T figure a scale to sit against.

## The published scores

All five come from the Kimi K3 model card, which notes they were obtained with reasoning
effort set to `max` and temperature 1.0.
https://huggingface.co/moonshotai/Kimi-K3

| Benchmark | Kimi K3 |
| --- | --- |
| Terminal Bench 2.1 | 88.3 |
| SWE Marathon | 42.0 |
| FrontierSWE | 81.2 |
| DeepSWE | 67.5 |
| GPQA Diamond | 93.5 |

## Price

**Kimi K3: $3.00 input, $0.30 cached input, $15.00 output, per million tokens.** The Open
Platform price list for `kimi-k3`, which states the figures are the cost per 1M tokens
consumed and prices cache hits separately from cache misses.
https://platform.kimi.ai/docs/pricing/chat-k3

**Claude Fable 5: $10 input, $50 output, per million tokens, with a 1M token context
window.** Anthropic's own model documentation.
https://platform.claude.com/docs/en/about-claude/models/overview

**70% less per token.** Arithmetic from the two price lists above, and it holds on both
sides: $3 against $10 is a 70% reduction on input, and $15 against $50 is a 70% reduction
on output.

**$1 minimum top up.** The quickstart states the flagship model is "unlocked after a
successful top-up (minimum $1)".
https://platform.kimi.ai/docs/guide/kimi-k3-quickstart

**OpenAI compatible.** The quickstart documents calling the model through the OpenAI SDK
pointed at the Moonshot endpoint.
https://platform.kimi.ai/docs/guide/kimi-k3-quickstart

## The command line tool

**Install.** The documented routes are a shell script on macOS and Linux
(`curl -fsSL https://code.kimi.com/kimi-code/install.sh | bash`), a PowerShell equivalent
on Windows, and an npm install covered in the getting started guide.
https://github.com/MoonshotAI/kimi-code

**Rebuilt on Node.js.** The documentation describes the tool "moving from Python/uv to
Node.js", with a simpler install, faster startup and a redesigned terminal interface.
https://www.kimi.com/code/docs/en/

**Agent Client Protocol.** "Kimi Code CLI speaks the Agent Client Protocol, so
ACP-compatible editors and IDEs (Zed, JetBrains, …) can drive a session over stdio."
https://github.com/MoonshotAI/kimi-code

**Video input.** "Drop a screen recording or demo clip into the chat and let the agent
watch what is hard to describe in words."
https://github.com/MoonshotAI/kimi-code

**Signing in.** Running `/login` offers either Kimi Code OAuth or a Moonshot AI Open
Platform API key.
https://github.com/MoonshotAI/kimi-code

**About 300 to 1,200 requests per 5 hour window, up to 30 concurrent.** The usage
allowance described in the Kimi Code documentation.
https://www.kimi.com/code/docs/en/

## Running the weights yourself

**32 x H100 across four nodes, 2,560 GB.** The published serving recipes put the Hopper
minimum at four 8-GPU H100 80GB nodes, which is 32 GPUs and 2,560 GB of aggregate GPU
memory.

**Or 16 x H200.** The alternative published configuration, at 141 GB per card.

**Every published configuration is multi node.** No single 8-GPU node holds the model: the
checkpoint alone is 1.56 TB, and a mixture of experts model needs every expert resident in
GPU memory during inference even though only a fraction of the parameters are active for
any one token, so the memory requirement covers the whole checkpoint plus the KV cache and
activations on top.

## What is not settled

**There is no head to head benchmark comparison in this video, and that is deliberate.**
Anthropic does not publish benchmark scores for Claude Fable 5 in its model documentation.
Numbers circulating for it come from third party write ups rather than from the vendor, so
the only comparisons made here are the two that both vendors state themselves: the price
per million tokens and the size of the context window.

**The published scores are the vendor's own.** Kimi K3's five scores are self reported on
its model card at a specific reasoning effort and temperature, and have not been
independently reproduced here.

**The terminal session shown is illustrative.** The file names, match counts, diff and test
output on screen stand in for a real session; they are not a recording of one.

**Pricing and allowances move.** The API prices, the top up minimum and the request
allowance are as published at the time of writing and are not contractual.

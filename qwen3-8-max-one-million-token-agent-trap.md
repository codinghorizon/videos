---
layout: default
title: "Qwen3.8 Max: The One Million Token Agent Trap Now"
permalink: /qwen3-8-max-one-million-token-agent-trap/
date: 2026-08-16
---

# Qwen3.8 Max: The One Million Token Agent Trap Now

{% raw %}
Every figure, capability and named product this video puts on screen, chased to a primary
source and cited.

The script for this video was supplied finished and was recorded before a shot existed, so
the checking below ran against a narration that could no longer be changed. Where a claim
could not be confirmed as worded, the shot was changed so it does not render the
unconfirmed part, and the gap is listed under **Not checked** at the end.

## Qwen3.8-Max: what the documentation states

**Context window: 1,000,000 tokens.** The QwenCloud text generation model table lists
`qwen3.8-max` with a 1M context. The Alibaba Cloud Model Studio reference gives the exact
figures: context window 1,000,000, maximum input 991,808 tokens, maximum output 131,072
tokens.

- https://docs.qwencloud.com/developer-guides/getting-started/text-generation-models
- https://www.alibabacloud.com/help/en/model-studio/qwen3-8-max
- https://www.qwencloud.com/models/qwen3.8-max

**Thinking: supported.** The QwenCloud table lists thinking support for `qwen3.8-max`, with
a 256k thinking budget. The model page states maximum reasoning of 262,144 tokens, which is
256k.

- https://docs.qwencloud.com/developer-guides/getting-started/text-generation-models
- https://www.qwencloud.com/models/qwen3.8-max

**Function calling: supported.** Listed as supported in both the QwenCloud table and the
Model Studio reference.

- https://docs.qwencloud.com/developer-guides/getting-started/text-generation-models
- https://www.alibabacloud.com/help/en/model-studio/qwen3-8-max

**Built in tools: supported.** The QwenCloud documentation lists built in tools for
`qwen3.8-max` and names them as web search, code interpreter and web extractor. Those three
are the ones drawn on screen.

- https://docs.qwencloud.com/developer-guides/getting-started/text-generation-models
- https://www.qwencloud.com/models/qwen3.8-max

**Very large output limits.** The narration says the model table points at very large output
limits in the family rather than naming a number, and the shot follows it: the maximum
output is documented at 131,072 tokens, and the screen states "very large" rather than a
figure that the narration does not give.

- https://www.alibabacloud.com/help/en/model-studio/qwen3-8-max

**Released 3 August 2026**, with API access through Alibaba Cloud Model Studio. Alibaba
describes it as the most capable model in the Qwen family to date, with improvements across
coding, work, research and long horizon tasks.

- https://www.alibabacloud.com/blog/alibaba-unveils-qwen3-8-max-its-largest-and-most-capable-flagship-model-to-date_603420
- https://www.alibabacloud.com/blog/qwen3-8-max-a-new-bar-for-coding-and-cowork_603421

## North Mini Code

Chapter eight names North Mini Code as the opposite question, and the shot puts that name
on screen. It is Cohere's first model for developers: a 30B total, 3B active parameter
sparse Mixture of Experts model trained for agentic coding, released under Apache 2.0 with
a 256K context window. No figure for it is stated in this video; only the name and the role
it plays in the comparison.

- https://docs.cohere.com/docs/north-mini-code-1.0
- https://cohere.com/blog/north-mini-code
- https://huggingface.co/blog/CohereLabs/introducing-north-mini-code

The 256K context shown beside it on the model table shot is that documented figure.

- https://docs.cohere.com/docs/north-mini-code-1.0

## Not checked

- The narration calls it "qwen3.8 max preview" and says the documentation recommends that
  preview for complex reasoning and coding. The recommendation in the documentation is for
  the released `qwen3.8-max`, and no separate preview row appears in the text generation
  model table, so the identifier shown on screen is `qwen3.8-max`. The narration's wording
  was already recorded and could not be changed.
- The three way test proposed in chapter five is a test the script proposes, not one that
  has been run. Nothing on screen reports a result for it, and the three lanes are drawn as
  a design for an experiment rather than as measurements.
- The repositories, files, diffs, test runs, tool output, timings and per turn costs used
  throughout are worked examples built for this video. They describe no real codebase and
  no measurement of any real tool.
- The context health percentages in chapter eleven are an illustration of what such a
  readout would show. They are not a measurement of any product, and no product is named
  beside them.
- No benchmark score is printed for any model anywhere in the video.
{% endraw %}

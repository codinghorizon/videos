---
layout: default
title: "Tencent Hy4 Just Put Qwen And DeepSeek On Notice"
permalink: /tencent-hy4-770b-open-model/
date: 2026-08-28
---

# Tencent Hy4 Just Put Qwen And DeepSeek On Notice

{% raw %}
Every figure, date, price and benchmark this video puts on screen, chased to a primary
source. Sources are Tencent's own release, the model card and the model repository.

## Primary sources

- Tencent, "Tencent Releases and Open-Sources Tencent Hy4 preview"
  https://www.tencent.com/tencent-releases-and-open-sources-tencent-hy4-preview/
- Model card, `tencent/Hy4-preview` on Hugging Face
  https://huggingface.co/tencent/Hy4-preview
- Model repository, `Tencent-Hunyuan/Hy4-preview` on GitHub
  https://github.com/Tencent-Hunyuan/Hy4-preview
- FP8 weights, `tencent/Hy4-preview-FP8` on Hugging Face
  https://huggingface.co/tencent/Hy4-preview-FP8
- Serving recipe, `tencent/Hy4-preview` on recipes.vllm.ai
  https://recipes.vllm.ai/tencent/Hy4-preview

## Release

- Released and open sourced on 28 August 2026. (Tencent release)
- Licence: Apache License 2.0. (Model card; GitHub repository)
- Available through WorkBuddy and CodeBuddy, and through Yuanbao and ima, with API access
  via Tencent Cloud TokenHub and OpenRouter. (Tencent release)
- The team publishes as Tencent Hy; the repository and the organisation are still named
  Tencent-Hunyuan. (GitHub repository, Hugging Face organisation)

## Architecture

- 770B total parameters, 49B activated per token. (Tencent release; model card)
- 78 layers. The first layer uses a standard dense feed forward network; the remaining 77
  replace it with a mixture of experts layer. (Model card)
- Each expert layer holds 256 routed experts plus 1 shared expert. Each token activates the
  top 8 routed experts along with the shared expert. (Model card)
- One native MTP layer for speculative decoding, 10B total parameters of which 0.7B are
  activated. (Model card)
- Attention: "inspired by DeepSeek and GLM, the attention module employs Gated DeepSeek
  Sparse Attention (Gated DSA) with IndexCache for cross-layer sparse index reuse."
  (Model card, quoted)
- 64 attention heads, query compression dimension 2048, key value compression dimension
  512, vocabulary size 120,832. (Model card)
- Context length 1M tokens; Tencent's own release states a context window exceeding 1M
  tokens, and the vLLM recipe lists 1024K. (Model card; Tencent release; vLLM recipe)

## Pricing

Per million tokens, as published with the release:

| | USD per million tokens |
| --- | --- |
| Input | 0.834 |
| Output | 2.501 |
| Cache hit | 0.042 |

(Tencent release)

## Serving and controls

- Two official serving paths, vLLM and SGLang, both offering OpenAI compatible endpoints.
  (Model card; GitHub repository)
- Tool calling is supported on both paths. (Model card)
- Reasoning effort defaults to high. It can be turned off per request with
  `reasoning_effort: "no_think"`. (Model card)

## The blind evaluation

163 internal experts rated model outputs on 203 engineering tasks, blind.

| Model | Average, out of 4 |
| --- | --- |
| Hy4 preview | 2.99 |
| Kimi K3 | 2.94 |
| GLM 5.3 | 2.92 |

Head to head, as published:

| Against | Wins | Ties | Losses |
| --- | --- | --- | --- |
| Kimi K3 | 51.2% | 7.9% | 40.9% |
| GLM 5.3 | 46.8% | 12.8% | 40.4% |

(Tencent release; model card)

## Where it is aimed

Tencent names coding, office work and scientific research as the headline areas, and lists
software engineering, game development, financial analysis, molecular dynamics, physics and
mathematics among the target tasks. (Tencent release)

## Stated limitations

Tencent publishes three, in its own words:

- "real headroom left in both pre-training and post-training"
- "spending longer than necessary reasoning through complex tasks"
- "a tendency to over-verify its own work"

(Model card)

## Caveats

- The 163 expert, 203 task evaluation is Tencent's own internal evaluation of its own
  model. It is reported here as Tencent reports it, and it is not an independent result.
- Kimi K3 and GLM 5.3 figures in that table are Tencent's measurements of those models
  under its own harness, not those labs' published numbers.
- The published API prices are the prices at release and are not fixed.
- Characterisations of Qwen's ecosystem breadth and DeepSeek's price pressure are the
  video's argument about the field rather than a figure from any of the sources above.
{% endraw %}

---
layout: default
title: "DeepSeek V4.1 Flash Makes Claude Earn Your Money"
permalink: /deepseek-v4-1-flash-makes-premium-ai-prove-it/
date: 2026-09-12
---

# DeepSeek V4.1 Flash Makes Claude Earn Your Money

{% raw %}
Every figure the picture puts on screen, chased to a primary source. Checked 2026-09-11.

## DeepSeek V4.1 Flash benchmark table

Source: DeepSeek V4.1 Flash technical report, Table 3, and the model card benchmark table.
- https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash/blob/main/DeepSeek_V41_Tech_Report.pdf
- https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash

All figures are publisher reported by DeepSeek, at maximum reasoning effort, in DeepSeek's
own agent configuration.

| Benchmark | V4.1 Flash | V4 Flash | Claude Opus 5 | GPT 5.6 Sol | Kimi K3 | GLM 5.3 |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| DeepSWE v1.1 (resolved) | 74.2 | 54.4 | 74.0 | 73.0 | 67.5 | 66.9 |
| Terminal Bench 2.1 (pass@1) | 90.6 | 82.7 | 89.1 | 88.8 | 88.3 | 88.2 |
| Terminal Bench 4.0 (pass@1) | 31.2 | 7.0 | 51.8 | 39.9 | 12.6 | 37.9 |
| AutomationBench (pass@1) | 54.8 | 37.7 | 50.3 | 45.8 | 46.7 | 48.8 |

Derived figures shown on screen, computed from the table:
- Flash over Claude Opus 5 on DeepSWE: 74.2 minus 74.0 = 0.2 points.
- V4.1 Flash over V4 Flash on DeepSWE: 74.2 minus 54.4 = 19.8 points.
- Flash over Kimi K3 on DeepSWE: 74.2 minus 67.5 = 6.7 points. Over GLM 5.3: 74.2 minus 66.9 = 7.3 points.
- Claude Opus 5 over Flash on Terminal Bench 4.0: 51.8 minus 31.2 = 20.6 points.

The small DeepSWE difference against Opus 5 does not establish a statistically
significant lead; the script describes it as neck and neck.

## Architecture

Source: model card and technical report abstract and architecture sections (links above).
- Backbone parameters: 552B.
- Engram conditional memory (lookup) parameters: 196B.
- Activated parameters: 8B during prefill (reading input), 16B during decode (generating).
- Context length: up to 1M tokens.
- Native vision: DeepSeek ViT encoder, images processed jointly with text.
- Global KV cache: "890 bytes per token, roughly 1/4 of DeepSeek V4 Flash" (model card).

Arithmetic shown on screen: 890 bytes times 1,000,000 tokens = 890,000,000 bytes, about
890 MB (decimal). This is the global attention cache only, not weights, other caches or
runtime memory. The V4 Flash per token figure is not printed on screen; the picture draws
the old block at about four times the height, as the model card states.

## Reasoning effort

Source: technical report, section 5.3 (effort control), printed page 34.
- Reasoning effort is a continuously controllable integer setting from 1 to 100.
- "The 60–80 range already recovers most of the accuracy of the maximum setting at less
  than half of its token budget."
- Raising effort from 25 to 100 lifts DeepSWE v1.1 from 66.0 to 74.2 at roughly 2.5x more
  output tokens; the last step to 100 lengthens agent trajectories 1.6 to 1.8x.

The chart in the effort beat is qualitative (accuracy rising and flattening, tokens rising
steeply) with the 60 to 80 band shaded; no y axis values are printed.

## API pricing

Source: DeepSeek API pricing page, https://api-docs.deepseek.com/quick_start/pricing
- V4.1 Flash, per 1M tokens: input (cache miss) $0.30 peak / $0.15 off peak; output $1.20
  peak / $0.60 off peak; cache hit $0.006 peak / $0.003 off peak.
- Peak hours 01:00 to 04:00 and 06:00 to 10:00 UTC, Monday to Friday; all other hours are
  off peak. Off peak is half the peak rate.

The $10 versus $5 example is arithmetic on identical billable usage at half rate, not a
measured agent run.

## License and weights

Source: model repository, https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash
- Repository and weights are under the MIT License.

## Reference inference configuration

Source: https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash/blob/main/inference/README.md
- Model parallel size MP=8, one converted checkpoint per tensor parallel rank.
- Expert weights can be converted to FP4 (`--expert-dtype fp4`).
- Described by DeepSeek as "a readable reference implementation rather than a production
  serving engine". Eight way parallelism is the published example, not a stated minimum.

## Kimi K3

Source: https://huggingface.co/moonshotai/Kimi-K3
- 2.8T total parameters; 16 of 896 experts active, about 104B activated parameters per
  token.
- Moonshot's own card reports DeepSWE 67.5 and Terminal Bench 2.1 at 88.3, matching the
  DeepSeek table.

## GLM 5.3

Source: https://huggingface.co/zai-org/GLM-5.3
- Open weights. Its own card reports DeepSWE v1.1 at 66.9 and Terminal Bench 2.1 at 88.2,
  matching the DeepSeek table.

## Qwen 3.8 27B

Source: https://huggingface.co/Qwen/Qwen3.8-27B
- 27B dense model with native vision.
- Reports DeepSWE v1.1 at 42.2 and Terminal Bench 2.1 (Terminus) at 73.0, evaluated in the
  Claude Code harness with a 256K context window. These are Qwen's own results and are
  not from the DeepSeek comparison table; the picture keeps them in a separate lane.

Arithmetic shown on screen: 27 billion parameters at 4 bits each = 27e9 x 4 / 8 =
13.5e9 bytes, about 13.5 GB, before vision components, quantisation metadata, caches and
runtime overhead.

## Not checked

- Whether any of the DeepSeek comparison scores for third party models match those
  models' own published harness settings beyond Kimi and GLM, which were cross checked.
- Real world hardware needed to self host V4.1 Flash; only the published MP=8 reference
  configuration is described.
{% endraw %}

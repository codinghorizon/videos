---
layout: default
title: "Qwen 3.8 27B Just Made GPT 5.6 Look Wasteful Now"
permalink: /qwen-3-8-27b-open-model-beats-gpt-5-6/
date: 2026-08-24
---

# Qwen 3.8 27B Just Made GPT 5.6 Look Wasteful Now

{% raw %}
Every figure this video puts on screen, with where it comes from.

## The model

| Claim | Value | Source |
| --- | --- | --- |
| Parameters | 27B | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Licence | Apache 2.0 | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Native context | 262,144 tokens | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Extended context | up to 1,000,000 tokens, via YaRN | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Modality | native vision language model, images and video | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Thinking mode | on by default, can be disabled per request | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Reasoning effort | `reasoning_effort`, with low, medium and xhigh | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Weights on disk | 55.6 GB of BF16 safetensors across 18 shards | [files and versions](https://huggingface.co/Qwen/Qwen3.8-27B/tree/main) |
| Published | 14 August 2026, by the Qwen team at Alibaba Cloud | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |

The model card's own framing of what it is for: "comprehensive improvements across coding,
professional work, research, and long-horizon agentic tasks", and "stronger autonomous
planning and better handling of environment feedback, leading to more reliable end-to-end
task completion".

## The head to head

Artificial Analysis, comparing Qwen3.8 27B at xhigh against GPT 5.6 Luna at xhigh:

| Metric | Qwen3.8 27B (xhigh) | GPT 5.6 Luna (xhigh) | Better |
| --- | --- | --- | --- |
| Intelligence Index | 52 | 50 | Qwen |
| Blended price, per 1M tokens | $0.43 | $0.17 | GPT |
| Output speed, tokens per second | 54 | 145 | GPT |
| Time to first token | 2.98s | 52.74s | Qwen |
| Context window | 256k | 1000k | GPT |

Source: [Artificial Analysis, Qwen3.8 27B vs GPT-5.6 Luna
(xhigh)](https://artificialanalysis.ai/models/comparisons/qwen3-8-27b-vs-gpt-5-6-luna-xhigh).

The score depends on which GPT 5.6 Luna configuration is compared. At low reasoning effort
the same index puts Luna at 34, against Qwen3.8 27B's 52:
[comparison](https://artificialanalysis.ai/models/comparisons/qwen3-8-27b-vs-gpt-5-6-luna-low).
The video compares the xhigh configuration in both directions, which is the closest of the
published matchups.

## The Hugging Face ranking

Qwen3.8 27B reached number one on Hugging Face's global trending models board on 17 August
2026, three days after release, and passed three million downloads in the same window.

- [Alibaba's Qwen 3.8-27B tops Hugging Face global model trend](https://www.gurufocus.com/news/9037602/alibabas-qwen-3827b-tops-hugging-face-global-model-trend)
- [Qwen3.8-27B arrives free, already downloaded over 3 million times](https://cybernews.com/tech/qwen-38-27b-ai-model-debuts-with-million-downloads/)
- [Qwen 3.8 27B scores 52 on the Artificial Analysis Intelligence Index](https://simonwillison.net/2026/Aug/17/qwen-38-27b-scores-52/)

## What is illustrative rather than measured

Some shots draw a shape rather than a published figure, and are labelled on screen as what
they are rather than carrying a number:

- The split of developer work between "the middle band" and "the frontier tail", and the
  share of premium calls that did not need premium intelligence, are illustrations of the
  argument, not survey results.
- The eight axis profile comparing the two models is a shape drawn to show that one index
  flattens several dimensions. Only the four rows in the table above are measured.
- The share of an agent's turns that an open model could take is an illustration.
- Local setup time against a hosted call is an illustration of the tradeoff.

## Not verified

- Whether Qwen3.8 27B is genuinely better inside an agent loop than smaller open models
  before it. The model card claims stronger planning and environment feedback handling;
  there is no independent harness result behind that claim here.
- GPT 5.6 Luna's parameter count is not published, so the size comparison in the video is
  made against the fact that it is hosted rather than against a number.
{% endraw %}

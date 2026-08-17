---
layout: default
title: "Kimi K3 Has One Million Tokens And One Huge Trap"
permalink: /kimi-k3-context-trap/
date: 2026-08-17
---

# Kimi K3 Has One Million Tokens And One Huge Trap

{% raw %}
Every figure, price, date, threshold and benchmark this video puts on screen, chased to a
primary source. The script arrived finished and was recorded before a shot existed, so
anything here that could not be sourced is not drawn on screen at all, and anything the
narration asserts without a primary source is listed at the bottom.

## The model

| On screen | Value | Source |
| --- | --- | --- |
| Total parameters | 2.8T | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |
| Activated parameters per token | 104B | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |
| Number of experts | 896 | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |
| Experts selected per token | 16 | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |
| Context window | 1,048,576 tokens | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |
| Vision encoder | MoonViT-V2, 401M parameters, native text and image input | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |
| Quantisation | MXFP4 weights, MXFP8 activations | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |
| Quantisation aware training | applied from the SFT stage onward | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |
| Weights are published under a named licence | Kimi K3 License | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |

The model card is the primary source for all of the above: it is Moonshot's own
publication of the weights and the accompanying specification.

## Benchmarks

Every number below is Moonshot's own reported figure, from the same model card. The video
says so on screen, because a score reported by the lab that trained the model is a
different kind of claim from an independent one.

| Benchmark | Kimi K3 | Source |
| --- | --- | --- |
| DeepSWE | 67.5 | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |
| Terminal-Bench 2.1 | 88.3 | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |
| FrontierSWE | 81.2 | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |
| SWE-Marathon | 42.0 | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |
| OmniDocBench | 91.1 | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |
| MMMU-Pro | 81.6 | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |
| Video-MME | 90.0 | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |
| OSWorld-Verified | 84.8 | [moonshotai/Kimi-K3 model card](https://huggingface.co/moonshotai/Kimi-K3) |

The narration's descriptions map onto those figures directly: DeepSWE "in the high
sixties" is 67.5, Terminal Bench "around the high eighties" is 88.3, and FrontierSWE
"above eighty in Moonshot's table" is 81.2.

## Price

| On screen | Value | Source |
| --- | --- | --- |
| Input, cache miss | $3.00 per million tokens | [OpenRouter: moonshotai/kimi-k3](https://openrouter.ai/moonshotai/kimi-k3) |
| Input, cache hit | $0.30 per million tokens | [OpenRouter: moonshotai/kimi-k3](https://openrouter.ai/moonshotai/kimi-k3) |
| Output | $15.00 per million tokens | [OpenRouter: moonshotai/kimi-k3](https://openrouter.ai/moonshotai/kimi-k3) |
| Flat across the whole window, no long context surcharge | — | [OpenRouter: moonshotai/kimi-k3](https://openrouter.ai/moonshotai/kimi-k3) |

The cache hit price is a 90% discount on the cache miss price, which is the arithmetic the
pricing shot draws rather than a claim of its own.

## The licence

| On screen | Condition | Source |
| --- | --- | --- |
| Model as a Service threshold | a separate commercial agreement is required once the aggregate revenue of the licensee and its affiliates exceeds 20 million US dollars over any consecutive 12 month period | [Kimi K3 License analysis](https://www.implicator.ai/moonshot-attaches-20-million-revenue-clause-to-kimi-k3-open-weights/) |
| Attribution threshold | products above 100 million monthly active users, or 20 million US dollars in monthly revenue, must display the name Kimi K3 prominently in the interface | [Kimi K3 License analysis](https://www.implicator.ai/moonshot-attaches-20-million-revenue-clause-to-kimi-k3-open-weights/) |
| Carve out: internal use | activity that does not make the software, its outputs or its capabilities available to third parties | [Kimi K3 License analysis](https://www.implicator.ai/moonshot-attaches-20-million-revenue-clause-to-kimi-k3-open-weights/) |
| Carve out: Moonshot's own products | use through Moonshot's own offerings | [Kimi K3 License analysis](https://www.implicator.ai/moonshot-attaches-20-million-revenue-clause-to-kimi-k3-open-weights/) |
| Carve out: certified inference partners | approved third party providers | [Kimi K3 License analysis](https://www.implicator.ai/moonshot-attaches-20-million-revenue-clause-to-kimi-k3-open-weights/) |

The MaaS revenue gate counts the licensee's revenue from all sources, not only revenue
earned from Kimi K3. That is why the video draws it as a gate on the business rather than
a gate on the model.

## What is not put on screen

These are things the narration says that could not be chased to a primary source, so no
shot renders a figure for them.

- **"SWE Marathon is much higher than older open models."** Moonshot's own SWE-Marathon
  figure for K3 (42.0) is published, but no comparable SWE-Marathon score for an earlier
  open weight model could be found at a primary source. The benchmark shot therefore draws
  K3's own score against the other K3 scores in Moonshot's table, and never against an
  invented comparison bar.
- **The size of the download.** The narration says the model files are not a tiny
  download, which is true of a 2.8T parameter model, but the model card does not publish a
  total file size, so no gigabyte figure appears on screen.
- **The harness footnotes.** The narration's point that different models are evaluated
  with different coding harnesses, tools, fallbacks and retry rules is a general
  observation about agent benchmarking rather than a claim about a specific published
  footnote, so the shot draws the mechanism and not a quoted note.
{% endraw %}

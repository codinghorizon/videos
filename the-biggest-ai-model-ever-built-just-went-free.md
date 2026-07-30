---
layout: default
title: "The Biggest AI Model Ever Built Just Went Free (Kimi K3)"
permalink: /the-biggest-ai-model-ever-built-just-went-free/
---

# The Biggest AI Model Ever Built Just Went Free (Kimi K3)

Every figure quoted in the video, where it came from, and how it was checked. Where
sources disagree, the disagreement is written down rather than resolved silently.

Checked on 30 July 2026.

---

## The release

| Claim | Figure | Source |
| --- | --- | --- |
| Developer | Moonshot AI, Beijing | [Model card](https://huggingface.co/moonshotai/Kimi-K3) |
| API available | 16 July 2026 | [VentureBeat](https://venturebeat.com/technology/chinas-moonshot-ai-releases-kimi-k3-the-largest-open-source-model-ever-rivaling-top-u-s-systems) |
| Open weights published | 26 July 2026 | [roo.beehiiv.com](https://roo.beehiiv.com/p/kimi-k3-open-weights-license-benchmarks) |
| Date Moonshot had promised | 27 July 2026 | Same |

The ten day gap between the API opening and the weights being published is the
difference between those first two dates. The weights landed roughly one day ahead of
the 27 July date Moonshot had given.

## The record it broke

Kimi K3 is the largest open weight model published to date at 2.8 trillion total
parameters. The previous largest was DeepSeek V4 Pro at 1.6 trillion, which makes the
increase about 1.2 trillion parameters.

- [yellow.com, Kimi K3 becomes the largest open weight model ever](https://yellow.com/news/kimi-k3-largest-open-weight-model)
- [Tom's Hardware](https://www.tomshardware.com/tech-industry/artificial-intelligence/moonshot-releases-2-8-trillion-parameter-kimi-k3)

## Architecture

All from the [model card](https://huggingface.co/moonshotai/Kimi-K3) and the
[Kimi K3 tech blog](https://www.kimi.com/blog/kimi-k3).

| Property | Value |
| --- | --- |
| Total parameters | 2.8T |
| Activated parameters per token | 104B |
| Experts | 896 total, 16 active per token |
| Layers | 93 (69 Kimi Delta Attention, 24 Gated MLA) |
| Context length | 1,048,576 tokens |
| Vocabulary | 160K |
| Vision encoder | MoonViT-V2 |
| Modalities | text, images and video in one model |
| Weight format | MXFP4 weights, MXFP8 activations |
| Optimizer | Per Head Muon |

Moonshot's tech blog claims roughly a 2.5 times improvement in overall scaling
efficiency compared with Kimi K2.

One caveat worth stating: some coverage described the active compute as "roughly 50
billion parameters" by multiplying 16 of 896 experts against the total. The 104B
figure used in the video is the one Moonshot publishes on the model card, and it is
the higher of the two because attention and shared parameters are active on every
token regardless of which experts are routed to.

## The size, and the 594 GB figure

This is the number most coverage got wrong, so it is worth setting out in full.

**What the repository actually contains.** The Hugging Face repository lists a total
size of **1.56 TB across 96 safetensors shards**.
[Repository file listing](https://huggingface.co/moonshotai/Kimi-K3/tree/main)

**Why 594 GB cannot be the model.** 2.8 trillion parameters at four bits each is
1.4 terabytes before anything else is added. 594 GB would work out at under two bits
per parameter, which does not match a model shipped in MXFP4.

**Where 594 GB came from.** It is the size of a community produced one bit dynamic
quantization of the model, published by Unsloth, measured between 594 GB and 620 GB
across same day revisions. The figure was picked up as though it were the release
itself.
[Run Kimi K3 locally, hardware reality check](https://www.modemguides.com/blogs/ai-news/run-kimi-k3-locally-hardware-reality-check)

**The rest of the ladder**, from the same source:

| Build | Size |
| --- | --- |
| One bit dynamic | 594 GB to 620 GB |
| Two bit dynamic | 711 GB |
| Four bit | 1.51 TB |
| Eight bit | 1.56 TB |

**At full precision.** At the 16 bit precision most models ship in, 2.8 trillion
parameters would come to roughly 5.6 terabytes. Moonshot never shipped that: the model
was trained with quantization aware training from the supervised fine tuning stage
onward, so the four bit version is the model rather than a compressed copy of one.
[Kimi K3 tech blog](https://www.kimi.com/blog/kimi-k3)

**A note on 1.4 TB versus 1.56 TB.** Both figures appear in coverage and both are
right about different things. 1.4 TB is the weights themselves at four bits. 1.56 TB
is the total size of the repository as Hugging Face reports it, which includes
everything else in it. The video uses 1.56 TB when talking about what you download and
1.4 TB when talking about what has to fit in memory.

## Running it

| Claim | Figure | Source |
| --- | --- | --- |
| Accelerators needed to hold the weights | around eighteen 80 GB cards | [TECHi](https://www.techi.com/kimi-k3-open-weights-inference-economics/) |
| Newest single node | 8 cards at 192 GB, about 1.5 TB total | Same |
| Production serving | 64 or more accelerators | Same |
| Memory floor for the one bit build | about 650 GB of combined RAM and VRAM | [modemguides](https://www.modemguides.com/blogs/ai-news/run-kimi-k3-locally-hardware-reality-check) |
| Reported consumer path | a 512 GB Mac Studio paired with a second machine | Same |
| One bit build on data center cards | more than 100 tokens per second on B200 class hardware | Same |

TECHi's framing of the binding constraint, that it is memory capacity and bandwidth
rather than floating point throughput, and that inference cost is increasingly
measured in tokens per megawatt, is quoted in the video as their analysis rather than
as a measurement.

## The licence

This is the second claim most coverage got wrong.

**Kimi K2** shipped under a Modified MIT licence whose only additional condition was
attribution at very large scale.

**Kimi K3 does not.** The file in the repository is a bespoke document titled the Kimi
K3 License, not a variant of MIT, and it adds a condition K2 never had.
[LICENSE](https://huggingface.co/moonshotai/Kimi-K3/blob/main/LICENSE)

The two thresholds, as written:

1. **Model as a service.** If revenue from using the model to provide a service
   exceeds 20 million US dollars in total over any consecutive twelve months, a
   separate commercial agreement with Moonshot AI is required before commercial use.
2. **Attribution.** If a product or service built on the model exceeds 100 million
   monthly active users, or 20 million US dollars in monthly revenue, "Kimi K3" must
   be displayed prominently in the user interface.

The licence explicitly carves out internal use that is not accessible to third
parties, and access through Moonshot AI's own products or its certified inference
partners. That is why the video describes the first threshold as aimed at resellers
rather than at users: modifying, distributing, building products on and running the
model inside a company all remain permitted without a separate agreement.

The distinction between "open weight" and "open source" matters here, and the video
does not call the model closed. It is freely downloadable and freely usable by the
overwhelming majority of people who would want it. It is not unconditionally free for
a business whose product is reselling it.

[Comparison of the K2 and K3 terms](https://roo.beehiiv.com/p/kimi-k3-open-weights-license-benchmarks)

## Benchmarks

Independent measurements from
[Artificial Analysis](https://artificialanalysis.ai/models/kimi-k3):

| Measure | Kimi K3 |
| --- | --- |
| Intelligence Index | 57 |
| Rank among open weights models | 1st of 98 |
| Output speed | 34.4 tokens per second |
| Time to first token | 3.36 seconds |

Artificial Analysis describe K3's intelligence as comparable to Claude Opus 4.8 and
GPT 5.5, and behind Claude Fable 5 and GPT 5.6 Sol. The two published index scores
above K3 are Fable 5 at 60 and GPT 5.6 Sol at 59, which is where the three point gap
quoted in the video comes from.
[Artificial Analysis writeup](https://artificialanalysis.ai/articles/kimi-k3-achieves-3-in-the-artificial-analysis-intelligence-index-comparable-to-opus-4-8-and-gpt-5-5)

Because Artificial Analysis do not publish separate index scores for Opus 4.8 and
GPT 5.5 alongside K3's, the video shows those two as a comparable band around 57
rather than assigning them numbers.

Scores from Moonshot's own [model card](https://huggingface.co/moonshotai/Kimi-K3):

| Benchmark | Score |
| --- | --- |
| GPQA Diamond | 93.5 |
| Terminal-Bench 2.1 | 88.3 |
| BrowseComp | 91.2 |
| DeepSWE | 67.5 |
| OSWorld 2.0 | 58.3 |

**Agentic work.** Artificial Analysis report a rating of 1668 on their professional
task evaluation, up from 1190 for K2.6. One other summary of the same evaluation
quoted 1687; the video uses the lower and more widely reported 1668, and the point
being made, that this is a large single generation jump, holds either way.

**Front end code arena.** K3 was ranked first at 1679, ahead of Claude Fable 5.
[Tom's Hardware](https://www.tomshardware.com/tech-industry/artificial-intelligence/moonshot-releases-2-8-trillion-parameter-kimi-k3).
Only the leading score is published, which is why the video shows the models below it
in position without scores. Arena rankings measure human preference on a particular
kind of task and move around; the video flags this rather than treating the ranking as
settled.

## Hallucination and accuracy

From [Artificial Analysis](https://artificialanalysis.ai/models/kimi-k3):

| Measure | Kimi K2.6 | Kimi K3 |
| --- | --- | --- |
| Hallucination rate | 39% | 51% |
| Accuracy rate | 33% | 46% |

Both moved in the same direction, and that is the point. The model answers more
questions correctly than its predecessor, and it also declines to answer less often,
which produces more confident wrong answers alongside the extra right ones. These are
two different measures on the same evaluation, not two halves of one number.

## Pricing

| Model | Input, cache miss | Input, cache hit | Output |
| --- | --- | --- | --- |
| Kimi K2.6 | $0.95 | $0.16 | $4.00 |
| Kimi K3 | $3.00 | $0.30 | $15.00 |
| Claude Sonnet 5 | $3.00 | | $15.00 |
| Claude Fable 5 | $10.00 | | $50.00 |

All per million tokens.
[the-decoder](https://the-decoder.com/kimis-open-model-k3-nears-gpt-5-6-sol-and-fable-5-while-signaling-the-end-of-super-cheap-chinese-ai/),
cross checked against [Artificial Analysis](https://artificialanalysis.ai/models/kimi-k3).

K3's input price is roughly three times K2.6's, and lands at exactly the same headline
figures as Claude Sonnet 5. The cache hit price of 30 cents remains substantially
cheaper than the western equivalents. The wider argument, that Chinese frontier models
are no longer priced at a steep discount to western ones, is the-decoder's and is
presented as such.

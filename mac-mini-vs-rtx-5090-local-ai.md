---
layout: default
title: "Mac mini vs RTX 5090: don't buy the wrong AI machine"
permalink: /mac-mini-vs-rtx-5090-local-ai/
date: 2026-09-20
---

# Mac mini vs RTX 5090: don't buy the wrong AI machine

{% raw %}
Sources for every figure, price, date and benchmark the picture puts on screen.

The script was written and recorded before the shots existed, so a claim the narration
makes cannot be corrected by changing a shot. Anything below that could not be chased to a
primary source is **not rendered on screen at all**, and is listed under "Not put on
screen" at the foot of this file.

Every figure the picture renders, through all seventy one beats, is below. Beat numbers in
this file are this cut's, and the `SHOT:` lines in BEATS.md are the index back into it.

## Mac mini, M5 Pro and M4 Pro

| Fact | Value | Source |
| --- | --- | --- |
| M5 Pro Mac mini starting price | $1,699 | [Apple Newsroom, 25 August 2026](https://www.apple.com/newsroom/2026/08/apple-unveils-a-more-powerful-mac-mini-featuring-the-all-new-m6-and-m5-pro/) |
| M5 Pro standard unified memory | 24GB | [Apple, Mac mini technical specifications](https://www.apple.com/mac-mini/specs/) |
| M5 Pro maximum unified memory | 64GB | [Apple, Mac mini technical specifications](https://www.apple.com/mac-mini/specs/) |
| M5 Pro memory bandwidth | 307GB/s | [Apple, Mac mini technical specifications](https://www.apple.com/mac-mini/specs/) |
| **M4 Pro memory bandwidth** | **273GB/s** | [Apple, Mac mini (2024) technical specifications](https://support.apple.com/en-us/121555) |
| **M4 Pro maximum unified memory** | **64GB** | [Apple, Mac mini (2024) technical specifications](https://support.apple.com/en-us/121555) |
| M6 Mac mini starting price | $899 | [Apple Newsroom, 25 August 2026](https://www.apple.com/newsroom/2026/08/apple-unveils-a-more-powerful-mac-mini-featuring-the-all-new-m6-and-m5-pro/) |
| M6 maximum unified memory | 32GB | [Apple, Mac mini technical specifications](https://www.apple.com/mac-mini/specs/) |
| Mac mini maximum continuous power | 155W | [Apple, Mac mini technical specifications](https://www.apple.com/mac-mini/specs/) |

Memory is part of the system on a chip package and is configured at order. Apple lists no
user accessible memory slot for any Mac mini configuration, which is what beats 010 and 055
draw as a cutaway rather than assert as a sentence.

**The M4 Pro is the load bearing one in chapter 6** (beats 053 and 054): it holds the same
64GB as the M5 Pro and moves it at 273GB/s against 307, which is the 11 per cent the
narration calls "a little less speed". Both figures are Apple's own.

## GeForce RTX 5090

| Fact | Value | Source |
| --- | --- | --- |
| Launch price | $1,999 MSRP, January 2025, card only | [NVIDIA, GeForce RTX 5090](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/) |
| Memory | 32GB GDDR7 on a 512 bit bus | [NVIDIA, GeForce RTX 5090](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/) |
| Memory bandwidth | 1,792GB/s | [NVIDIA, GeForce RTX 5090](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/) |
| Total graphics power | 575W | [NVIDIA, GeForce RTX 5090](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/) |
| Recommended system power supply | 1000W | [NVIDIA, GeForce RTX 5090](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/) |

575W is the board's total graphics power, which is a peak rating rather than the draw of
any particular workload. Nothing in the sources states a per query figure, so beat 061
draws the rating as a ceiling with a varying trace under it and prints no inference watts.

The 1,792 against 307 comparison in beat 045 needs no separate sourcing: both numbers are
in the two tables above, from NVIDIA's and Apple's own specifications. The multiple between
them, 5.8, is computed from the pair in the shot rather than typed, and beat 046 strikes it
out **as a speed claim** while leaving the bandwidth figure standing.

## Qwen3.8-27B

| Fact | Value | Source |
| --- | --- | --- |
| Parameters | 27 billion | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| SWE bench Pro | 61.7 | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| SWE bench Pro, Qwen3.6-27B, same card | 53.5 | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Vision | native vision language model, understands images and video | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |
| Context length | 262,144 native, extensible to 1,000,000 | [Qwen/Qwen3.8-27B model card](https://huggingface.co/Qwen/Qwen3.8-27B) |

Both figures are the developer's own published evaluations, run with an agent harness and a
large context window. They describe that setup, not a four bit download on a desk, which is
what beat 008 labels in amber.

## The llama.cpp team's GGUF conversion

| File | Size | Source |
| --- | --- | --- |
| `Qwen3.8-27B-Q4_K_M.gguf` | 19GB | [ggml-org/Qwen3.8-27B-GGUF](https://huggingface.co/ggml-org/Qwen3.8-27B-GGUF) |
| `Qwen3.8-27B-Q8_0.gguf` | 28.6GB | [ggml-org/Qwen3.8-27B-GGUF](https://huggingface.co/ggml-org/Qwen3.8-27B-GGUF) |
| `Qwen3.8-27B-BF16.gguf` | 53.8GB | [ggml-org/Qwen3.8-27B-GGUF](https://huggingface.co/ggml-org/Qwen3.8-27B-GGUF) |

`ggml-org` is the organisation the llama.cpp maintainers publish under. The 19GB figure is
the weights file only. Conversation history, image tokens and intermediate state are
additional and runner dependent, which is why beat 013 draws the parts and never sums them.

## Mistral Devstral Small 2, and Devstral 2

| Fact | Value | Source |
| --- | --- | --- |
| Devstral Small 2 parameters | 24,011,361,840, the 24 billion the narration says | [mistralai/Devstral-Small-2-24B-Instruct-2512](https://huggingface.co/mistralai/Devstral-Small-2-24B-Instruct-2512) |
| Devstral Small 2, SWE bench Verified | 68.0% | [the same model card's benchmark table](https://huggingface.co/mistralai/Devstral-Small-2-24B-Instruct-2512) |
| Devstral Small 2 context length | 256k | [the same model card](https://huggingface.co/mistralai/Devstral-Small-2-24B-Instruct-2512) |
| **Devstral 2 parameters** | **123B, dense** | [Mistral AI, Introducing Devstral 2 and Mistral Vibe CLI](https://mistral.ai/news/devstral-2-vibe-cli/) |
| **Devstral 2, SWE bench Verified** | **72.2%** | [Mistral AI, Introducing Devstral 2 and Mistral Vibe CLI](https://mistral.ai/news/devstral-2-vibe-cli/) |
| Devstral 2, SWE bench Multilingual | 61.3% | [the same announcement](https://mistral.ai/news/devstral-2-vibe-cli/) |
| Devstral 2 context length, licence | 256K, modified MIT | [mistralai/Devstral-2-123B-Instruct-2512](https://huggingface.co/mistralai/Devstral-2-123B-Instruct-2512) |

**Both Devstral figures are on SWE bench Verified, so beat 017 may put them on one axis.**
That is the opposite of beat 008's situation and it is why the two beats are drawn
differently: 68.0 against 72.2 is one ruler, and 61.7 on SWE bench Pro is another.

Five times the parameters for 4.2 points is arithmetic on the pair (123 / 24 = 5.1; 72.2
minus 68.0 = 4.2), computed in beat 018 from the two sourced figures rather than typed.

## Google Gemma 4 12B

| Fact | Value | Source |
| --- | --- | --- |
| Parameters | 11,959,730,224 | [google/gemma-4-12B-it](https://huggingface.co/google/gemma-4-12B-it) |
| Input modalities | text, image and audio | [the same model card](https://huggingface.co/google/gemma-4-12B-it) |
| Context length | 256K | [the same model card](https://huggingface.co/google/gemma-4-12B-it) |

Audio is native on the 12B rather than an add on, which is what makes the narration's spoken
bug report in beats 036 and 037 a real example rather than a hypothetical one, and what beat
038 is contrasting when a larger model drops the feature.

## z.AI GLM 4.7 Flash

| Fact | Value | Source |
| --- | --- | --- |
| Total parameters | 30B, a 30B A3B mixture of experts | [zai-org/GLM-4.7-Flash](https://huggingface.co/zai-org/GLM-4.7-Flash) |
| Activated per token | 3B | [the same model card](https://huggingface.co/zai-org/GLM-4.7-Flash) |
| **SWE bench Verified** | **59.2** | [the model card's own comparison table](https://huggingface.co/zai-org/GLM-4.7-Flash) |
| **Qwen3-30B-A3B-Thinking-2507, same table** | **22.0** | [the model card's own comparison table](https://huggingface.co/zai-org/GLM-4.7-Flash) |
| Routing | 64 routed experts plus 1 shared | [the same repository's config.json](https://huggingface.co/zai-org/GLM-4.7-Flash/raw/main/config.json) |
| Licence | MIT | [the same model card](https://huggingface.co/zai-org/GLM-4.7-Flash) |

**59.2 against 22.0 is z.AI's own published comparison of its model against somebody
else's**, which the narration says out loud ("in z.AI's evaluation") and beat 022 labels on
screen. Both models are about thirty billion parameters, which is the beat's whole point,
so the two rows carry the same size qualifier.

The 3 billion active against 30 billion held is what beats 021 and 023 draw as a lit
fraction of a grid: cheaper to run, and no cheaper to hold.

## Qwen3 Coder Next

| Fact | Value | Source |
| --- | --- | --- |
| Total parameters | 79,674,391,296, stated as 80B on the card | [Qwen/Qwen3-Coder-Next](https://huggingface.co/Qwen/Qwen3-Coder-Next) |
| Activated per token | 3B | [the same model card](https://huggingface.co/Qwen/Qwen3-Coder-Next) |
| **SWE bench Verified** | **70.6** | [the same model card's evaluation table](https://huggingface.co/Qwen/Qwen3-Coder-Next) |
| SWE bench Pro | 44.3 | [the same model card's evaluation table](https://huggingface.co/Qwen/Qwen3-Coder-Next) |
| Terminalbench 2 | 36.2 | [the same model card's evaluation table](https://huggingface.co/Qwen/Qwen3-Coder-Next) |
| Four bit MLX conversion | **44.9GB** across nine safetensors shards | [mlx-community/Qwen3-Coder-Next-4bit](https://huggingface.co/mlx-community/Qwen3-Coder-Next-4bit) |
| Context length | 256k | [the same model card](https://huggingface.co/Qwen/Qwen3-Coder-Next) |

70.6 and Devstral Small 2's 68.0 are **both on SWE bench Verified**, so the gap is real and
comparable as a number. What is not comparable is the harness each vendor ran it under, and
that is the distinction beat 031 makes: the bars are drawn on one axis, and the qualifier
under each names whose evaluation it is.

44.9GB is the weights only, which is what beat 028 puts inside the 64GB rail and beat 029
runs off the end of the 32GB one.

## Qwen3.8 Flash Next

| Fact | Value | Source |
| --- | --- | --- |
| **Main model parameters** | **125B** | [Qwen, Qwen3.8-Flash-Next: A New Architecture](https://qwen.ai/blog?id=qwen3.8-flash-next) |
| **N-gram embedding tables, on top of the main model** | **51B** | [the same announcement](https://qwen.ai/blog?id=qwen3.8-flash-next) |
| Activated per token | 6B | [the same announcement](https://qwen.ai/blog?id=qwen3.8-flash-next) |
| Layers, hidden dimension | 48 layers, hidden 2560 | [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) |
| A published four bit MLX conversion, whole repository | **104GB** across eleven shards | [pipenetwork/Qwen3.8-Flash-Next-MLX-4bit](https://huggingface.co/pipenetwork/Qwen3.8-Flash-Next-MLX-4bit) |

**The 62GB in beat 035 is arithmetic, and the narration says so: "four bit arithmetic puts
the main model alone around sixty two gigabytes".** 125 billion parameters at four bits is
62.5GB. It is the MAIN MODEL on its own, before the embedding tables and before any working
state, and the shot labels it `the main model, on its own` for that reason.

The published four bit conversion of the whole repository is **104GB**, which is the figure
a viewer would actually meet on disk. It is not in the narration, so it is not asserted as a
headline, but it is what beat 034's embedding tables sitting on top of the main bar are
drawing, and the shot carries a grey caveat rather than implying 62GB is the download.

## Not put on screen

- **The price of the 64GB upgrade on the M5 Pro Mac mini.** Apple publishes the $1,699
  starting configuration at 24GB and sells 64GB as a build to order option; no source
  consulted states the upgrade price on its own. The narration says only that it costs
  more, and beat 059 draws it as a labelled headroom rather than inventing a figure.
- **Any running memory total at a given context length**, for any model here. The
  components are real and the total is runner dependent, so the rails draw the parts and
  never sum them into one number.
- **Any watt figure for the RTX 5090 during inference.** Only the 575W board rating is
  published, and the narration's point in beat 061 is precisely that the two are not the
  same.
- **Any figure for used prices.** Beat 063's asking prices and completed sales are drawn to
  show the SHAPE of the difference and are labelled in amber on screen as exactly that. No
  marketplace was sampled and no axis is numbered.
- **Tokens per second, for either machine, for any model.** Nothing in the sources states
  one for these pairings, and the narration never claims one. Beat 047's blocks are labelled
  as a condition rather than as a measurement.
{% endraw %}

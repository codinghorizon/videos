---
layout: default
title: "Your 12GB GPU can run AI you might be overlooking"
permalink: /best-local-ai-12gb-vram/
date: 2026-09-23
---

# Your 12GB GPU can run AI you might be overlooking

{% raw %}
Every figure, price, date, version and benchmark this video puts on screen, chased to a
primary source. Publisher pages are cited at the page the claim actually appears on, and
the video shows that page rather than redrawing it wherever the claim is still theirs.

## The machine

**RTX 3060 12GB.** 12GB GDDR6 on a 192 bit bus, about 360 GB/s of memory bandwidth.
**Desktop RTX 4070.** Also a 12GB configuration, GDDR6X on a 192 bit bus, about 504 GB/s.

Equal capacity, different bandwidth: the 4070 moves roughly 1.4 times the bytes per second
at the same 12GB. That is the whole of the script's "equal capacity doesn't mean equal
speed" and it is why the figure on screen is bandwidth rather than capacity.

- <https://www.nvidia.com/en-gb/geforce/graphics-cards/30-series/rtx-3060-3060ti/>
- <https://www.nvidia.com/en-gb/geforce/graphics-cards/40-series/rtx-4070-family/>

## The arithmetic the script does

**Nine billion weights at four bits is about 4.5 billion bytes.** 9e9 weights x 4 bits =
36e9 bits = 4.5e9 bytes. The script states this as "a rough four bit calculation" and
"before extra data and runtime overhead", which is correct: a real GGUF carries embeddings,
some tensors at higher precision, and the KV cache and context are on top of it again. The
gap between that 4.5 and Ollama's actual 6.6GB download is the honest illustration of it.

**$1,000 shown, $200 refunded, $800 expected net.** Arithmetic, and the fixture the whole
video returns to.

**40 tokens per second with 2,000 tokens of thinking is roughly 50 seconds.** 2000/40 = 50.
The script labels it "example numbers" in the same breath, and the shot carries that label.

## Qwen 3.5 9B

Alibaba's model, 9B parameters, text and image in, 256K context as Ollama lists it.

| claim | value | where |
|---|---|---|
| Ollama download size | **6.6GB** for `qwen3.5:9b` | Ollama library page |
| LiveCodeBench v6 | **65.6** | Qwen's own model card table |
| MMLU Pro | **82.5** | same table |
| GPT OSS 20B, MMLU Pro | **74.8** | same table, comparison column |
| GPT OSS 20B, LiveCodeBench v6 | **74.6** | same table, and it LEADS qwen there |

That last row is the script's "In that same table, GPT OSS leads it on livecodebench", and
it is the reason the beat draws both rows of the same table rather than only the one qwen
quotes.

- <https://ollama.com/library/qwen3.5>
- <https://huggingface.co/Qwen/Qwen3.5-9B>

**One contradiction found and resolved.** A secondary write up (XDA) reports LiveCodeBench
v6 of 82.7 for this model. Qwen's own card says 65.6. The card is the primary source and
65.6 is what goes on screen; the 82.7 figure is not used anywhere.

## Gemma 4 12B

Google's model. Encoder free, so text, image AND audio go into one decoder.

| claim | value | where |
|---|---|---|
| LiveCodeBench v6 | **72.0** | Google's Gemma 4 model card |
| Audio input on the 12B | **yes**, up to 30s | same card |
| Four bit GGUF size | **7.22GB**, `gemma-4-12B-it-Q4_0.gguf` | ggml-org repo |
| Separate vision file | `mmproj`, 0.16 to 0.18GB | same repo |
| Visual token budget | "A higher token budget preserves more visual detail at the cost of additional compute" and higher budgets are recommended "for tasks like OCR, document parsing, or reading small text" | same card |

- <https://ai.google.dev/gemma/docs/core/model_card_4>
- <https://huggingface.co/ggml-org/gemma-4-12B-it-GGUF/tree/main>

**A note on which repo.** `ggml-org/gemma-4-12B-GGUF` (the base) carries only BF16 and
Q8_0. The four bit file is in `ggml-org/gemma-4-12B-it-GGUF`, the instruction tuned repo,
which is the one anybody running a coding assistant would pull. The script's "about 7.2GB"
is 7.22GB exactly.

## Ministral 3 14B Reasoning

Mistral's model, in the 2512 release.

| claim | value | where |
|---|---|---|
| Bartowski four bit file | **8.24GB**, `...Q4_K_M.gguf` | bartowski's GGUF repo |
| Separate vision component | `mmproj`, 0.88 to 0.89GB | same repo |
| LiveCodeBench | **64.6** | Ministral 3 paper, Table 5 |
| Qwen 3 14B comparison | **59.3** | same table, same row |
| Protocol | pass@16 throughout, **except LiveCodeBench at pass@5** | same paper |

- <https://huggingface.co/bartowski/mistralai_Ministral-3-14B-Reasoning-2512-GGUF/tree/main>
- <https://arxiv.org/html/2601.08584v1>
- <https://huggingface.co/mistralai/Ministral-3-14B-Reasoning-2512>

**Two things the shot has to be careful about.** Table 5's 14B column is headed **Qwen 3
14B**, which is the Qwen 3 generation and not Qwen 3.5, and the script says exactly that
("That's the older qwen 3, not qwen 3.5"). The paper's 8B and 4B columns are headed
Qwen3-VL; only the 14B pair is the one this video draws. And the score belongs to the REASONING
model: Mistral ships a separate instruct variant, so the benchmark is not a score for every
file carrying the ministral name, which is the point the beat makes.

## Ternary Bonsai 2 27B

PrismML's compression of Qwen3.8 27B. Released **17 September 2026**, Apache 2.0.

| claim | value | where |
|---|---|---|
| Release date | **17 September 2026** | PrismML launch post |
| Retention | **98.2%** of FP16 aggregate, 84.78 against 86.32 across 14 thinking mode benchmarks | model card and launch post |
| Measured against | **Qwen3.8 27B** full precision | both |
| Packings | **5.95GB** (TQ1_0, 1.75 bpw) and **7.21GB** (PQ2_0, 2.13 bpw) | model card |
| Separate vision file | `mmproj`, **0.63GB** Q8_0, optional | model card |
| Peak throughput | **up to 143 tok/s on an RTX 5090** | launch post |
| Runtime | the **PrismML-Eng llama.cpp fork**; "stock llama.cpp will not run these files" | model card |

- <https://prismml.com/news/bonsai-2-27b>
- <https://huggingface.co/prism-ml/Ternary-Bonsai-2-27B-gguf>

### The compression comparison, which is the chapter's real point

The model card's own table, all four variants of the same parent:

| Variant | bpw | Footprint | Thinking avg | vs FP16 | **LiveCodeBench** |
|---|---|---|---|---|---|
| Qwen3.8-27B FP16 | 16.0 | 54 GB | 86.32 | 100% | **90.05** |
| Qwen3.8-27B UD-Q4_K_XL | 5.2 | 17.6 GB | 85.18 | 98.7% | **87.96** |
| Qwen3.8-27B IQ2_XXS | 2.8 | 9.4 GB | 72.59 | 84.1% | **56.40** |
| Ternary Bonsai 2 27B | 1.72 | 5.9 GB | 84.78 | 98.2% | **90.07** |

That is the script's "bonsai scores about 90 on livecodebench, while a conventional, very
low bit version of the same parent scores about 56", exactly, and it is two compressions of
ONE model behaving completely differently at a similar bit width.

**The version caveat is real and the script is right to make it.** This table's row is
labelled only `LiveCodeBench`, with no version. Google's 72 and Qwen's 65.6 are both
explicitly v6. So these numbers cannot be dropped into the same chart, and the video does
not draw them on one axis.

## Ollama's context default

Ollama picks a default from available VRAM: **4096 tokens below 24GiB**, 32768 from 24 to
48GiB, 262144 at 48GiB and above. Any 12GB card is in the first tier.

- <https://docs.ollama.com/context-length>

**A documentation inconsistency worth knowing.** Ollama's FAQ says 4096, the Modelfile
reference says `num_ctx` defaults to 2048, and the context length page describes the VRAM
tiers. The context length page is the current and most specific one, and it is what the
video cites and shows.

## Derived on screen, and where from

- **"July 2026, the first Bonsai 27B" (beat 049).** Not stated as a date by any publisher.
  It is read off the launch post the very next beat puts on screen: dated 17 September
  2026, it opens "Two months ago, we released our first Bonsai 27B models". The timeline
  node is that sentence drawn as a date.
- **RTX 5090, 1,792 GB/s and 32GB (beat 104).** NVIDIA's published specification for the
  card, used only to show why 143 tok/s does not transfer to a 3060. The 5x and the 20GB
  beside it are computed from those two figures and the 3060's own row in chapter 1.
- **10.4GB, "the session that runs it" (beats 014 and 016).** THIS IS THE VIDEO'S OWN
  WORKED EXAMPLE, in the same way the $1,000 / $200 / $800 refund case is, and no
  publisher states it. Beat 015 draws what it is made of and prints no number at all. The
  source credit in beat 016 names the 6.6GB download only, because that is the half
  ollama.com publishes.

## Not chased to a primary source

- **The 8,000 token starting context.** The script offers it as "a reasonable experiment"
  for a focused workflow, not as a published recommendation, and no publisher states that
  number. It is presented on screen as a suggestion rather than as a figure with a source.
- **"Bonsai also provides an optional vision component."** The mmproj file exists and the
  card names it optional. Whether every front end exposes it is not documented anywhere
  primary, so the shot does not claim tool support.
- **The two hypothetical outcomes in chapter 7** (one model taking longer and passing, one
  printing instantly and needing three rounds) are explicitly hypothetical in the
  narration. Nothing on screen presents them as measured.
{% endraw %}

---
layout: default
title: "Bonsai 2 shrinks local AI to 5.9 GB. What survives?"
permalink: /bonsai-2-low-vram-local-ai/
date: 2026-09-21
---

# Bonsai 2 shrinks local AI to 5.9 GB. What survives?

{% raw %}
Every figure this video puts on screen, chased to the publisher that issued it.

All prices, sizes and scores checked 20 September 2026. Ternary Bonsai 2 27B was released
on 17 September 2026, so everything here is three days old and worth rechecking before any
of it is quoted elsewhere.

---

## The model, and what it is

**Ternary Bonsai 2 27B** is PrismML's ternary compression of Qwen3.8 27B. Weights are
stored as one of three values, negative one, zero and positive one, with FP16 group wise
scaling.

| | |
| --- | --- |
| Publisher | PrismML |
| Released | 17 September 2026 |
| Base model | Qwen3.8 27B |
| Licence | Apache 2.0 |
| Context window | 262,144 tokens |
| Inputs | text and image |

Sources:
- PrismML model card, <https://huggingface.co/prism-ml/Ternary-Bonsai-2-27B-gguf>
- PrismML announcement, <https://prismml.com/news/bonsai-2-27b>

---

## File sizes

The released GGUF builds, from PrismML's own file listing.

| Build | Size | Bits per weight |
| --- | --- | --- |
| `PTQ1_0` (the smallest) | **5.95 GB** | 1.76 |
| `PQ2_0` (the demo's default) | **7.21 GB** | 2.16 |
| `F16` (the full precision reference) | **53.8 GB** | 16 |
| `mmproj` Q8_0 (the vision component) | **0.63 GB** | |
| `mmproj` BF16 (its reference) | 0.93 GB | |

Source: <https://huggingface.co/prism-ml/Ternary-Bonsai-2-27B-gguf>

Hugging Face's own hardware compatibility widget on that page normalises the two build
names to `TQ1_0` and `Q2_0`, which are llama.cpp's standard quantisation names rather than
PrismML's. The names used on screen are PrismML's own, `PTQ1_0` and `PQ2_0`, because those
are what the formats page documents and what a reader would type. The distinction matters:
the same page warns that a stock `Q2_0` file is a different thing that loads without a
warning and produces gibberish. The file sizes agree either way.

PrismML's formats page gives 5.93 GB and 7.25 GB for the same two builds, and its demo
README describes the default as 7.8 GB. The figures used on screen are the model card's,
because that is the page that lists the actual files. The spread is small and is recorded
here rather than smoothed over.

Source: <https://docs.prismml.com/download/formats>

**The demo downloads the larger build by default.** PrismML's own README: "A second
packing, `PQ2_0`, trades 1.3 GB for faster prompt processing and is what this demo
downloads by default."

Source: <https://github.com/PrismML-Eng/Bonsai-demo/blob/main/README.md>

---

## The fourteen benchmark comparison

PrismML evaluated the builds against each other across fourteen benchmarks in six skill
categories, in thinking mode, with the same evaluation setup.

| Build | Footprint | 14 benchmark average |
| --- | --- | --- |
| FP16 baseline | 54 GB | **86.32** |
| `UD-Q4_K_XL`, the four bit build | 17.6 GB | **85.18** |
| **Ternary Bonsai 2 27B** | 5.9 GB | **84.78** |
| `IQ2_XXS`, the conventional two bit build | 9.4 GB | **72.59** |
| Ternary Bonsai 27B, the previous generation | 5.75 GB | **80.98** |

84.78 against 86.32 is **98.2 per cent** of the full precision average, which is the figure
PrismML leads with. 84.78 against the previous generation's 80.98 is a gain of **3.8
points**.

The two bit row is the one that carries the argument: it is **larger** than Bonsai 2 at
9.4 GB and scores **twelve points lower**, so on this table storage size does not predict
the result and the compression method does.

Source: <https://huggingface.co/prism-ml/Ternary-Bonsai-2-27B-gguf>

### Coding

| | LiveCodeBench |
| --- | --- |
| FP16 | 90.05 |
| Ternary Bonsai 2 27B | **90.07** |

A gap of 0.02 points, which is why the video treats them as level.

### Reading difficult images

| | OCRBench v2 |
| --- | --- |
| `UD-Q4_K_XL`, four bit | **65.45** |
| FP16 | 60.99 |
| Ternary Bonsai 2 27B | **56.88** |

This is the one place in the table where Bonsai 2 gives up real ground, 8.57 points behind
the larger four bit build. Note also that the four bit build scores **above** full
precision here, which is the sort of result a single benchmark can produce and a reason not
to read any one row too hard.

Source: <https://huggingface.co/prism-ml/Ternary-Bonsai-2-27B-gguf>

---

## The alternatives

### Qwen3.5 9B

Qwen reports **65.6** on LiveCodeBench v6. Native context 262,144 tokens. It accepts image
and video input.

Source: <https://huggingface.co/Qwen/Qwen3.5-9B>

### Gemma 4

Google reports LiveCodeBench v6 of **52.0** for Gemma 4 E4B and **80.0** for Gemma 4 31B.
E4B takes text, image **and audio**; the 31B does not take audio. E4B's context is 128K
tokens, the 31B's is 256K.

Google's own memory table gives **4.5 GB** for Gemma 4 E4B at Q4_0, and states plainly that
the estimates "only account for the memory required to load the static model weights. They
don't include the additional VRAM needed for supporting software or the context window."
That caveat is why the video draws the conversation cache growing off the end of that bar.

Sources:
- <https://ai.google.dev/gemma/docs/core/model_card_4>
- <https://ai.google.dev/gemma/docs/core>

### Why these are not one ranking

PrismML's table does not state which LiveCodeBench version it used, while Qwen and Google
both state v6. Three different publishers also ran three different evaluation setups. The
figures are comparable as capability signals and not as a ranking, which is what the video
says and why it draws the version tags rather than sorting the rows.

---

## How the compression works

Weights are transformed before they are quantised and the transform is undone at
inference: "each matrix is transformed blockwise by an orthogonal Hadamard rotation before
the ternary assignment, and the runtime applies the matching transform to activations." The
rotation redistributes unusually large values that would otherwise be clipped by a three
value representation, and it is folded into the stored weights, so it costs no extra bits.

That is also why the released formats need PrismML's own build. From the formats page: "Do
not run Ternary Bonsai 2 on stock llama.cpp. `PQ2_0` and `PTQ1_0` are refused outright, but
a `Q2_0` file loads without a warning and outputs gibberish."

Source: <https://docs.prismml.com/download/formats>

---

## The earlier Bonsai models

PrismML announced the Ternary Bonsai family on 16 April 2026 at 8B, 4B and 1.7B, and had
previously shipped one bit builds. Bonsai 27B, the one bit and ternary builds of Qwen3.6
27B, followed on 14 July 2026.

| Earlier model | Footprint | Against FP16 |
| --- | --- | --- |
| Ternary Bonsai 8B | ~1.75 GB | ~16.4 GB |
| Ternary Bonsai 4B | ~0.86 GB | ~8 GB |
| Ternary Bonsai 1.7B | ~0.37 GB | ~3.4 GB |

These are separate models on separate bases, so the 27B results do not describe them.
PrismML also ships **Bonsai Image 4B**, a compressed image generation family, released
26 May 2026, which is why generating an image is a different model's job.

Sources:
- <https://www.prnewswire.com/news-releases/prismml-introduces-ternary-bonsai-model-family-302745151.html>
- <https://www.morningstar.com/news/pr-newswire/20260526sf68206/prismml-releases-bonsai-image-4b>

---

## The runtime, and what it can do

The official demo supplies the matching fork and, from its README and TOOLS notes:

- Vision on both the llama.cpp fork and MLX: photos, screenshots and PDFs.
- Native OpenAI style `tool_calls` with full round trips.
- An MCP client, with Hugging Face and DeepWiki preconfigured.
- A server side Python code interpreter through Jupyter, for plots and data.
- A reasoning effort control per conversation: **Off, Low (512), Medium (2048),
  High (8192), Max (unlimited)**.
- `BONSAI_MMPROJ_CPU=1` keeps the vision projector in system RAM instead of VRAM, which
  "frees ~0.9 GiB of VRAM" at the cost of slower image prompts.
- An OpenAI compatible server on `localhost:8080`.

Source: <https://github.com/PrismML-Eng/Bonsai-demo/blob/main/README.md>

---

## Speed

PrismML reports, for the larger `PQ2_0` build on an Apple M5 Pro laptop: "approximately
**28.1 tokens/second** for token generation over 128 tokens and **387 tokens/second** for
prompt processing over 512 tokens."

Two things that measurement is not. It is a 128 token generation, so it does not describe a
long answer; and it is measured without the vision component loaded and without a long
conversation already in the cache. A thousand tokens at 28.1 per second is about 36
seconds of generation alone, before prompt processing, before any tool call, and before a
reasoning model's thinking.

PrismML's announcement also reports 143 tokens/second on an RTX 5090 and 46.8 on an M5 Max,
neither of which is the machine this video is about.

Sources:
- <https://huggingface.co/prism-ml/Ternary-Bonsai-2-27B-gguf>
- <https://prismml.com/news/bonsai-2-27b>

---

## Not checked

Recorded here because the video says them and they could not be chased to a primary source.

- **Bits per weight for `PTQ1_0`.** PrismML's formats page and model card give 1.76; the
  announcement gives 1.72 and describes the scheme as 1.58 bit. The video uses 1.76,
  from the page that describes the format itself.
- **The eight gigabyte card targets.** No publisher states that an RTX 3060 Ti or an 8 GB
  RTX 4060 runs this build at a given speed. The video says so itself: it is a capacity
  estimate from the file size and a modest context, not a measured result, and no speed
  figure is put on screen beside those cards.
- **Sixteen gigabytes of system RAM for CPU execution.** A planning figure, not a published
  minimum. PrismML states no system RAM requirement.
- **Partial offloading on a four or six gigabyte card.** Layer offloading is a standard
  llama.cpp capability and the fork carries it, but no published measurement covers these
  cards with this build, so no figure appears on screen.
- **Where a 262,000 token context stops fitting on an 8 GB card.** Nothing published gives
  that point, so the shot marks it as an uncertain region labelled `Not measured` rather
  than drawing a line at a number.
- **The M5 Pro figure is a single reported measurement** from the publisher of the model,
  not an independent one.
{% endraw %}

---
layout: default
title: "The largest local AI model is bigger than you think"
permalink: /largest-local-ai-model/
date: 2026-09-22
---

# The largest local AI model is bigger than you think

{% raw %}
The script arrived finished and was recorded before a shot existed, so this file is not a
plan for the narration. It is the list of figures the SHOTS may render, each chased to the
page that publishes it.

**The asymmetry that makes this step heavier here.** The voice has already said every
claim below. Where a figure turns out to be wrong the picture can be corrected and the
recording cannot, so the rule is: a figure that cannot be sourced is not drawn, and the
shot is changed so it does not render the number rather than printing an unsourced figure
large.

Checked 21 September 2026. Every figure the script asserts was chased; none of them had to
be dropped, and the one that looked wrong on a secondary source turned out to be right on
the primary one (see "The one that nearly went wrong" at the foot).

---

## Qwen3.8-27B

Primary: <https://huggingface.co/Qwen/Qwen3.8-27B> (model card)

| figure | value | where the script says it |
|---|---|---|
| parameters | 27 billion (27.78B) | `Start with qwen 3.8 27B. That's twenty seven billion parameters` |
| vision | native vision language model, understands images and video | `it already understands images as well as text` |
| coding and agents | stronger autonomous planning, environment feedback, end to end task completion | `designed for coding and tasks with multiple steps` |
| native context | 262,144 tokens, extensible to 1,000,000 | not asserted in the script |
| licence | Apache 2.0 | not asserted |
| published | 14 August 2026, Alibaba Cloud | not asserted |

**At four bits, 27 billion parameters is 13.5 GB.** 27e9 × 0.5 bytes = 13.5 GB. This is the
script's own arithmetic and the script labels it `on paper`, which is the honest framing:
it is a lower bound on the weights and not a download size. Draw it as arithmetic, with the
caveat line §13 asks for, never as a measured file size.

## LongCat-2.0 (Meituan)

Primary: <https://huggingface.co/meituan-longcat/LongCat-2.0> (model card)

| figure | value | where the script says it |
|---|---|---|
| total parameters | 1.6 trillion | `a model with 1.6 trillion total parameters` |
| activated per token | approximately 48 billion | `longcat activates about forty eight billion parameters per token` |
| native context | 1 million tokens | `Its million token context support` |
| built for | code understanding, repository level edits, agentic workflows | `built for long context, coding, and tool use` |
| licence | MIT | not asserted |

**59 times Qwen.** 1.6e12 / 27e9 = 59.3. The script says `roughly fifty nine times` and then
immediately says it does not mean fifty nine times the intelligence, which is the claim the
beat is actually making. Draw the ratio; let the correction be the verdict on it.

## Kimi K3 (Moonshot AI)

Primary: <https://huggingface.co/moonshotai/Kimi-K3> (model card)

| figure | value | where the script says it |
|---|---|---|
| total parameters | 2.8 trillion (2.78T) | `It has 2.8 trillion parameters` |
| activated per token | 104 billion | `It activates 104 billion parameters per token` |
| context | 1,048,576 tokens | `supports a million token context` |
| vision | native, MoonViT-V2 vision encoder (401M) | `has native vision` |
| quantization | MXFP4 weights, MXFP8 activations, quantization aware training from SFT onward | `four bit weights with quantization aware training` |
| repository on disk | about 1.56 TB | `The published repository is about 1.56 terabytes` |
| at sixteen bits | about 5.6 TB | `At sixteen bits, it would be 5.6 terabytes` |
| released | 16 July 2026, weights under a modified MIT licence | not asserted |

**1.4 terabytes of raw arithmetic.** 2.8e12 × 0.5 bytes = 1.4 TB. The script calls it
`the raw arithmetic ... before overhead` and then gives the real published figure of 1.56 TB
beside it, which is the correct shape: the arithmetic is the floor and the repository is
the fact. Both may be drawn, and they must be drawn as two different kinds of number.

**104 times Qwen, and 75 per cent more than LongCat.** 2.8e12 / 27e9 = 103.7, and
2.8 / 1.6 = 1.75. Both are the script's own arithmetic off sourced totals.

### Terminal Bench 2.1

From the same model card's benchmark table:

| model | score |
|---|---|
| GPT 5.6 Sol | 88.8 |
| Kimi K3 | 88.3 |
| Claude Fable 5 | 88.0 |

**The caveat is load bearing and the script already carries it.** The model card states that
Kimi K3 was evaluated with the Kimi Code harness while the other scores are the best score
across harnesses. The script says `Those results use different agent setups, so they aren't
a controlled comparison of the weights alone`, which is the same caveat in the same beat.
The picture must carry it too: these three bars are not a controlled comparison and the
frame has to say so, per §13.

## The serving path

Primary: <https://docs.sglang.io/cookbook/autoregressive/Moonshotai/Kimi-K3> (SGLang cookbook)

As of 5 September 2026 the cookbook marks the **B300 1×8 Unified Low-Latency** and
**Balanced** configurations as verified for a speed round on final weights. Other
configurations remain in final verification.

The script says `sglang marks its eight b300 GPU configurations for low latency and balanced
serving as verified`, which matches. It then says `Context and concurrency still determine
the remaining memory budget`, which matches the cookbook's own framing that the matrix is
deployment starting points rather than guaranteed minimum specs.

## NVIDIA DGX B300

Primary: <https://www.nvidia.com/en-us/data-center/dgx-b300/>

| figure | value | where the script says it |
|---|---|---|
| GPUs | 8 Blackwell Ultra SXM | `puts eight blackwell ultra GPUs together` |
| total GPU memory | 2.1 TB | `with 2.1 terabytes of total GPU memory` |
| per GPU | 288 GB HBM3e | not asserted |

## NVIDIA GeForce RTX 5090

Primary: NVIDIA product page, corroborated by board partner spec sheets
(<https://www.asus.com/us/motherboards-components/graphics-cards/tuf-gaming/tuf-rtx5090-32g-gaming/techspec/>)

| figure | value | where the script says it |
|---|---|---|
| VRAM | 32 GB GDDR7 | `An RTX 5090 has thirty two gigabytes of VRAM` |
| memory bandwidth | 1,792 GB/s | not asserted, but see below |

**Bandwidth is available and is deliberately not drawn as a figure.** Chapter 4's claim is
`Memory capacity is how much you can hold. Memory bandwidth is how much you can move each
second`, which is a distinction rather than a measurement. Printing 1,792 GB/s beside it
would answer a question the narration does not ask and would invite a comparison against
the B300 that the script never makes.

---

## The hypothetical, and why it is labelled

`Take a hypothetical one trillion parameter model` is the script's own word, and the two
figures under it are arithmetic on a number that is not a real model:

- 1e12 × 2 bytes = **2 TB** at sixteen bits
- 1e12 × 0.5 bytes = **500 GB** at four bits

These are drawn as an equation building term by term with a grey caveat under it, per
§10.12 and §13, and the caveat says it is an example rather than a measured model. It must
never be drawn as a spec sheet, because there is no product behind it.

---

## The two panels that must stay out of frame

Hugging Face's Safetensors sidebar widget counts parameters off the tensor files, and it
does not agree with either model card's own prose:

| model | card says | sidebar widget says |
|---|---|---|
| Qwen3.8-27B | 27 billion | **28B params** |
| LongCat-2.0 | 1.6 trillion total | **1.8T params** |

Neither widget is wrong; it is counting something else, including tensors the headline
figure excludes. But the narration says `twenty seven billion` and `1.6 trillion`, so a
capture framed to include that sidebar puts a number on screen that contradicts the voice
saying a different one, in the same frame, sourced to the same page.

**So both captures are cropped to the left hand column**, which is what the declared
rectangle in each shot does. This is the §8 rule about an annotation contradicting its own
picture, arriving through the framing rather than through a caption, and no checker can see
it: the asset resolves, the window renders, and the figure is real.

## The one that nearly went wrong

A secondary write-up put Claude Fable 5 at **84.6** on Terminal Bench 2.1 rather than the
88.0 the script asserts, which would have made the narration wrong on a figure the picture
was about to print large.

Moonshot's own model card gives 88.0, and the difference is the harness: the card's own note
says non Kimi scores are the best across harnesses, so a single harness number and a best
of number are two different measurements of the same model. The script is right, the
secondary source was reporting something else, and the resolution is why the figure is taken
off the model card rather than off a comparison article.

It is also the reason this video's bar chart beat carries the harness caveat inside the
frame rather than under it.

---

## The photographs and the captures, and where they came from

Section 13.1 makes a photograph house wherever it is EVIDENCE rather than illustration, and
names this exact case: a drawn box reading `RTX 5090` is a labelled rectangle wearing a
product name. Section 13 says the same about a page. Both now carry no ceiling and a high
expected frequency, so every beat that rests on somebody's object or somebody's page shows
it rather than asserting it.

### Photographs

| beat | object | file | source |
|---|---|---|---|
| 037 | GeForce RTX 5090 Founders Edition | `photo/rtx-5090.jpg` | NVIDIA's own gallery shot, `nvidia.com/en-gb/geforce/graphics-cards/50-series/rtx-5090/`, retrieved 22 Sep 2026 |
| 050 | DGX systems in a data centre aisle | `photo/dgx-superpod.jpg` | NVIDIA's own photograph, `nvidia.com/en-us/data-center/dgx-b300/`, retrieved 22 Sep 2026 |
| 052 | NVIDIA DGX B300 | `photo/dgx-b300.jpg` | NVIDIA's own product image, `nvidia.com/en-us/data-center/dgx-b300/`, retrieved 22 Sep 2026 |

Each is the maker's own image of the named thing, not a photograph of something like it,
which is section 13.1's first rule and the same reasoning section 9 applies to marks. Each
is credited and dated on screen by the beat's own source line at the frame edge, because
the house has no eyebrow line to put it on, and each carries a short caption naming what it
is under its frame.

The 5090 image is the gallery shot rather than the page's social image. The social image
looks down the top edge of the card and shows the fin stack; a viewer who owns one
recognises it by its two fans, and the gallery shot is the one with them in it.

**None of them is cut out.** Section 13.1's fifth rule was reversed: a photograph keeps its
own background and is framed, because a cut out object has been retouched by us and reads
as something we drew, which is the opposite of what a photograph is brought in to do. All
three happen to be photographed on the maker's own black, so the frame is doing the work of
separating them from the room rather than a mask.

### Captures

| beat | claim it carries | file, and the region shown |
|---|---|---|
| 006 | Qwen3.8-27B is 27 billion parameters and multimodal | `web/qwen-card.png`, the model card's introduction |
| 019 | LongCat 2.0 is 1.6 trillion total parameters | `web/longcat-card.png`, the model card's introduction |
| 070 | Kimi K3 is 2.8 trillion parameters | `web/kimi-card.png`, the model card's introduction |
| 072 | context length 1,048,576, and what the model accepts | `web/kimi-bench.png`, the Model Summary rows from Vocabulary Size to Modality |
| 074 | 88.3 on Terminal-Bench 2.1, against 88.0 and 88.8 | `web/kimi-bench.png`, the Evaluation Results table, four columns, header through Terminal-Bench 2.1 |
| 078 | the published repository is 1.56 TB | `web/kimi-files.png`, the header and branch rows carrying the size badge |
| 079 | sglang marks the eight B300 configurations verified | `web/sglang-tall.png`, the configuration matrix |
| 081 | the weight files themselves | `web/kimi-files.png`, five shard rows with their sizes |

Every crop is read off the capture's own pixels and lands on row borders, so no row of a
page is cut through the middle. Where a crop shows more than the beat needs — 074 carries
the Reasoning and Knowledge rows above the Coding block — that is deliberate: a crop that
jumped from the table header to one row would be choosing which benchmarks the viewer sees.

One capture was taken and REJECTED, which is the step section 13 asks for and the reason
it asks for it. The model card's "Evaluation results" sidebar widget was captured for beat
074; it lists Apex Agents, GPQA Diamond, Deep Swe and a long horizon terminal benchmark,
and it does not carry a Terminal-Bench 2.1 score at all. A capture that does not show what
the beat claims is worse than the drawing it would replace, so the beat uses the model
card's own Evaluation Results TABLE further down the page instead, which does carry it.

Two things the captures corrected rather than merely cited:

- **Beat 081 was drawing invented filenames.** It rendered `model-00001.safetensors` and a
  line reading "and the rest of the shards". The repository's real names carry the shard
  count in every one of them, `model-00001-of-000096.safetensors`, so the drawing was
  presenting plausible made up filenames as the contents of a published repository.
- **Beat 072 was claiming video input.** Our table read `text, images and video` under a
  note promising every figure on it came from the model card. The card's Modality row says
  `Text, Image`, and the narration says "native vision" and never says video. The row now
  reads `text and images`.

**What stays drawn.** The GPU in beats 045 and 046, the SSD in 047 and the system RAM are
CATEGORIES rather than named products, and section 13.1's test is the actual thing the beat
names. An image of a particular vendor's DIMM standing in for "system RAM" would be the
stand in that rule exists to prevent, so those stay drawn.

## The three paragraphs added after the first recording

The source script gained three paragraphs on 21 September, after take 3 had already been
cut and measured, and the video was re-recorded against the new file. They are at source
lines 21, 75 and 115 and became beats 015/016, 053/054 and 081/082.

**None of the three carries a figure**, which is why this section is short:

- Line 21, the fix that half works, is about the assistant revising its explanation. The
  test names, the status column and the three lines of checkout code on screen are the
  video's own running fixture, invented by the script itself at line 7 and elaborated at
  line 17 (`a change in authentication, a stale API response, or a database migration`).
  Beat 016 takes both of its candidate explanations from that list rather than inventing a
  second bug to be wrong about.
- Line 75, the eight GPUs cooperating, refers back to the DGX B300's eight accelerators,
  which are sourced under **NVIDIA DGX B300** above. Beat 053 prints no figure at all; beat
  054 names the two things the division affects and deliberately does not rank them,
  because the sentence does not.
- Line 115, what the download contains, refers back to the published repository size
  already sourced under **Kimi K3**. Beat 081 draws four named shards and a muted `and the
  rest of the shards`: the shard COUNT and the exact byte total at that precision could not
  be chased to a primary source, so no count is printed. Beat 082 prints no figure either.

## Not checked

Everything the script asserts was chased to a primary source. Two things are unverifiable
in principle rather than unchecked, and they are opinions the script marks as opinions:

- `My view is that the next leap for local AI is dependable delegation.` Stated as a view.
- `my pick is kimi k3` Stated as a pick.

One figure is arithmetic on a hypothetical rather than a measurement, and is labelled as
such on screen:

- The one trillion parameter model at 2 TB and 500 GB. There is no such published model;
  the script says `hypothetical` and the frame says `Example, not a measured model`.
{% endraw %}

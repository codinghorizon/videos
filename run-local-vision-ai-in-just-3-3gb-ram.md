---
layout: default
title: "The Local AI That Reads Your Screen Without Uploading It"
permalink: /run-local-vision-ai-in-just-3-3gb-ram/
date: 2026-08-14
---

# The Local AI That Reads Your Screen Without Uploading It

Every figure this video puts on screen, chased to a primary source. Where a number
appears in a shot it appears here with the document it came from.

## The 3.3 gigabyte model

**Gemma 3 4B is a 3.3 GB download.** The `gemma3:4b` tag is 3.3 GB, quantised Q4_K_M,
4.3B parameters, with a 128K token context window, and the Gemma 3 family is multimodal
rather than text only.

> Source: Ollama model library, `gemma3:4b` — https://ollama.com/library/gemma3:4b

**Gemma 3 is a multimodal addition to the Gemma family, 1B to 27B parameters, with at
least a 128K token context.** The 1B model is the exception at 32K.

> Source: Gemma Team, Google DeepMind, *Gemma 3 Technical Report*, arXiv:2503.19786,
> 12 March 2025 — abstract and §2 — https://arxiv.org/abs/2503.19786

**Parameter split for the 4B model: a 417M vision encoder, 675M embedding parameters
and 3,209M non-embedding parameters.**

> Source: *Gemma 3 Technical Report*, Table 1

## How the model actually looks at an image

**The vision encoder is a 400M variant of SigLIP, taking square images resized to
896 x 896.** It is frozen during training and shared across the 4B, 12B and 27B models.

**Each image is condensed into 256 vectors, the "soft tokens" the language model reads.**
The 896 resolution encoder average pools its output down to those 256 tokens.

**Pan & Scan (P&S)** is an adaptive windowing algorithm applied at inference time only.
It segments an image into non-overlapping crops of equal size covering the whole image
and resizes each to 896 x 896, which addresses the artifacts the fixed resolution
produces on non-square and high resolution images: unreadable text and small objects
disappearing.

> Source: *Gemma 3 Technical Report*, §2.1 Vision modality

## Why the file size is not the whole story

**Memory footprint for the 4B model, in gigabytes, weights only and then with a KV cache
at a 32,768 token context:**

| Format | Weights | With 32K KV cache |
|---|---|---|
| bf16 (raw) | 8.0 | 12.7 |
| Int4 | 2.6 | 7.3 |
| Int4 (blocks=32) | 2.9 | 7.6 |
| SFP8 | 4.4 | 9.1 |

The Int4 4B checkpoint is 2.6 GB of weights and 7.3 GB once a 32K KV cache is in memory
with it. That gap is the working memory the model needs on top of the file.

> Source: *Gemma 3 Technical Report*, Table 3

Note on the two numbers this video uses: 3.3 GB is the size of the `gemma3:4b` Q4_K_M
download, and 2.6 GB is Google's own figure for an Int4 4B checkpoint. They are different
quantisations of the same model, which is why they differ.

## The older, larger way of doing vision

**LLaVA-1.5's headline checkpoint is 13B, using a CLIP ViT-L 336px vision encoder.** It
was trained on 1.2M publicly available samples in roughly one day on a single 8 x A100
node.

> Source: Haotian Liu, Chunyuan Li, Yuheng Li, Yong Jae Lee, *Improved Baselines with
> Visual Instruction Tuning*, arXiv:2310.03744 — https://arxiv.org/abs/2310.03744

The Gemma 3 report cites LLaVA directly as the inspiration for handling flexible
resolutions with Pan & Scan.

> Source: *Gemma 3 Technical Report*, §1 Introduction

## Where a small vision model gets worse

**Low resolution input measurably degrades reading accuracy.** Encoder input resolution
against benchmark score, from a short schedule 2B Gemma model:

| Encoder input | DocVQA | InfoVQA | TextVQA |
|---|---|---|---|
| 256 px | 31.9 | 23.1 | 44.1 |
| 448 px | 45.4 | 31.6 | 53.5 |
| 896 px | 59.8 | 33.7 | 58.0 |

DocVQA nearly doubles between 256 px and 896 px input. This is the mechanism behind the
video's claim that these models do worse on low resolution images.

> Source: *Gemma 3 Technical Report*, Table 7

**Dense and awkwardly shaped images are where the windowing matters most.** Pan & Scan on
the 4B model, 4-shot evaluation on the validation set:

| Benchmark | Without P&S | With P&S | Change |
|---|---|---|---|
| DocVQA | 72.8 | 81.0 | +8.2 |
| InfoVQA | 44.1 | 57.0 | +12.9 |
| TextVQA | 58.9 | 60.8 | +1.9 |

The report attributes the gains to tasks involving reading text on images and to images
with varying aspect ratios.

> Source: *Gemma 3 Technical Report*, Table 8

**A small local model is behind frontier cloud models on multimodal reasoning.** MMMU
(val), zero shot, instruction tuned models:

| Model | MMMU (val) |
|---|---|
| Gemma 3 4B | 48.8 |
| Gemma 3 12B | 59.6 |
| Gemma 3 27B | 64.9 |
| Gemini 1.5 Flash | 62.3 |
| Gemini 1.5 Pro | 65.9 |
| Gemini 2.0 Flash | 71.7 |
| Gemini 2.0 Pro | 72.7 |

The 4B model scores 48.8 against 72.7 for Gemini 2.0 Pro, on Google's own comparison.
That is the size of the gap the video describes.

> Source: *Gemma 3 Technical Report*, Table 6

## Not chased to a primary source

- That a screenshot typically carries file names, tabs, mail, terminal output and
  customer names is an observation about what is on a working screen, not a measured
  claim, and nothing on screen states a figure for it.
- The five jobs, and how well a small vision model does each of them in practice, are
  described qualitatively. Only the reading accuracy and multimodal reasoning figures
  above are measured, and only those appear as numbers.
- The agent loop where a vision model checks a rendered page and hands the result back
  to a coding model is presented as where this is going, not as a measured result. No
  figure is put on screen for it.
- No claim is made about how much time any of this saves, and no such figure appears.

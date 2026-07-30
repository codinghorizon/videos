---
layout: default
title: "Ex OpenAI CTO Shipped a 975B Model Free: Can You Run It?"
permalink: /ex-openai-cto-just-shipped-a-975b-model-for-free/
---

# Ex OpenAI CTO Shipped a 975B Model Free: Can You Run It?

Every figure quoted in this video, with where it came from and how it was checked.
Written after the script, so it reflects the version that was recorded.

Checked on 30 July 2026. Anything that moves after that date is not reflected here.

## The release

**Inkling was released on 15 July 2026 by Thinking Machines Lab.**
Thinking Machines Lab is the company founded by Mira Murati, previously Chief
Technology Officer at OpenAI. Inkling is the lab's first fully trained open weights
foundation model, and the full weights went up on Hugging Face under
`thinkingmachines/Inkling` on the day of the announcement.

Sources: Thinking Machines Lab, "Inkling: Our Open-Weights Model"
(thinkingmachines.ai/news/introducing-inkling/); the Hugging Face repository listing.

**The licence is Apache 2.0.**
This is the permissive end of the licence spectrum: the weights can be downloaded,
modified, redistributed and used commercially without a royalty or a separate
agreement. It is confirmed on the model card
(thinkingmachines.ai/model-card/inkling/) and was reported independently at launch.

The video is careful to say "open weights" rather than "open source". The published
artifact is the trained model. The pretraining data and the training code were not
published alongside it.

## Parameters and architecture

| Figure | Value | Source |
| --- | --- | --- |
| Total parameters | 975B | Thinking Machines Lab model card |
| Active parameters per token | 41B | Thinking Machines Lab model card |
| Layers | 66, decoder only | Thinking Machines Lab model card |
| Routed experts per layer | 256 | Thinking Machines Lab model card |
| Routed experts fired per token | 6 | Thinking Machines Lab model card |
| Shared experts, always on | 2 | Thinking Machines Lab model card |
| Context window | up to 1M tokens | Thinking Machines Lab model card |
| Pretraining tokens | 45 trillion | Thinking Machines Lab announcement |

**The "8 of 258" figure** in the video is 6 routed experts plus 2 shared experts, out
of 256 routed plus 2 shared. That arithmetic is the video's own, from the counts above.

**"4.2 percent" and "24 times smaller"** are also the video's own arithmetic:
41 divided by 975 is 4.2 percent, and 975 divided by 41 is roughly 23.8, rounded to 24
in the narration. The claim being made is specifically about the compute done per
token, not about memory.

**Attention layout: 55 local, 11 global, a 5 to 1 ratio.**
Of the 66 layers, 55 use a small sliding local attention window and 11 attend across
the whole sequence. Inkling also replaces rotary position embeddings with a learned,
input dependent relative position bias, which the lab describes as extrapolating
better to longer sequences than rotary embeddings do. That extrapolation claim is the
lab's, restated as such in the video, not an independent measurement.

Source: Sebastian Raschka, "Inkling: A New Open-Weight 975B MoE with a Few Surprises"
(sebastianraschka.com), which reads these off the released configuration; the expert
and layer counts agree with the model card.

## Comparison models

| Model | Total | Active |
| --- | --- | --- |
| Inkling | 975B | 41B |
| Kimi K2.5 | 1T | 32B |
| GLM 5.2 | 744B | 40B |

These are the comparison figures given in Raschka's architecture notes. The point the
video makes with them is only that the total to active ratio is a shared pattern
across recent large mixture of experts models, not that the three are otherwise
equivalent.

## Benchmarks

| Benchmark | Score | Note |
| --- | --- | --- |
| AIME 2026 | 97.1% | at reasoning effort 0.99 |
| SWE-bench Verified | 77.6% | at reasoning effort 0.99 |

Inkling exposes a controllable reasoning effort setting; the scores above are the ones
published at the top of that range, which is how the lab reported them. Scores at
lower effort settings will be lower.

**Inkling Small scores 83.4 on IFBench against the larger model's 79.8.**
That instruction following comparison is from the launch announcement, which
attributes the smaller model's advantage to improvements in its pretraining data and
recipe.

All benchmark numbers here are self reported by Thinking Machines Lab. They have not
been independently reproduced for this video.

## Training

Pretraining ran on NVIDIA GB300 NVL72 systems. Post training used large scale
asynchronous reinforcement learning with more than 30 million rollouts.

Source: Thinking Machines Lab, Inkling announcement.

## What it takes to run

**BF16, the full precision release: 2 TB of aggregated video memory, on 8x B300 or
16x H200.**
**NVFP4, the four bit release: 600 GB of aggregated video memory, on 4x B300 running
W4A4, or 8x H200 running W4A16.**

These are stated directly on the Thinking Machines Lab model card, which is unusually
specific about hardware. The video quotes them as published.

**On disk, the BF16 repository is roughly 1.9 TB and the NVFP4 repository roughly
592 GB.** These are file sizes totalled from the published repositories: 1,904,755,463,940
bytes for BF16 and 592,005,609,232 bytes for NVFP4, which round to 1.90 TB and 592 GB
in decimal units.

**Why memory is set by the total and not the active count.**
This is the central argument of the video and it follows from the routing scheme
above rather than from a quoted figure. The router selects 6 experts out of 256 per
token, and the selection depends on the token. Over any real sequence the selections
spread across the full expert bank, so every expert has to be resident to serve the
next token without stalling. Compute per token scales with the 41B that fire; resident
memory scales with the 975B that might.

The corollary the video also makes: because the weights are loaded once and every
request in a batch draws on the same resident experts, a server amortises that memory
across concurrent users. This is a property of how batched mixture of experts serving
works, not a figure quoted from a source.

**The context cache is on top of the weights.** A 1M token context window builds a
key and value cache during generation, and that cache grows with the sequence. No
specific size for it is quoted in the video, because Thinking Machines Lab did not
publish one.

## Quantisation

Community quantisations from Unsloth, with the memory each needs and the top one
accuracy each retains:

| Precision | Memory needed (RAM plus VRAM) | Accuracy retained |
| --- | --- | --- |
| 8 bit | 870 GB | 99.8% |
| 4 bit | 600 GB | 94.4% |
| 3 bit | 450 GB | 88.7% |
| 2 bit | 325 GB | 81.0% |
| 1 bit (UD-IQ1_S) | around 290 GB | 74.2% |
| BF16 | 1,900 GB | 100% |

Source: Unsloth's Inkling local run guide (unsloth.ai/docs/models/inkling). The 1 bit
dynamic quant occupies about 270 GB on disk and the guidance is that total available
memory should exceed the file size by a comfortable margin, which is where the roughly
290 GB figure in the video comes from.

**What "74.2 percent accuracy retained" means.** It is a top one agreement figure: the
share of next token predictions where the quantised model's first choice matches the
full precision model's first choice. It is not an error rate on tasks. The video makes
that distinction explicitly because the number is easy to misread.

**The 512 GB threshold.** The 1 bit build needs roughly 290 GB of combined memory,
which clears a 512 GB Apple Silicon Mac Studio and does not clear a 256 GB one. Unsloth
names a Mac Studio Ultra, or any machine with at least around 290 GB of RAM plus VRAM,
as the entry point.

**Consumer graphics cards.** Current consumer cards carry video memory in the tens of
gigabytes. Against the 600 GB the four bit build asks for, that is a gap of roughly two
orders of magnitude. No specific card model or capacity is quoted in the video, because
the top of the consumer range moves.

## Runtimes and hosting

Day one support: vLLM, SGLang, llama.cpp, Unsloth, and Hugging Face transformers.
Launch hosting partners named by the lab: Together AI, Fireworks, Modal and
Databricks, alongside the lab's own Tinker platform.

Sources: Thinking Machines Lab model card and announcement.

## Inkling Small

276B total parameters, 12B active. At the time of the launch announcement its weights
had not been released; the lab said they would follow once testing was complete, and
gave no date. It matches or beats the larger model on several benchmarks, including
the IFBench figure above.

Source: Thinking Machines Lab, Inkling announcement.

## Caveats

- Every benchmark figure in this video is self reported by Thinking Machines Lab.
  None has been independently reproduced here.
- The hardware requirements are the vendor's stated minimums. Real throughput, batch
  size and context length will all change what a deployment actually needs, and none
  of that was measured for this video.
- The Unsloth accuracy retention figures come from that project's own evaluation.
- Inkling Small's weights were unreleased when this was written. If they have landed
  since, that has not been checked here.
- The video quotes decimal terabytes and gigabytes throughout, matching how the
  repositories and the model card report them. Software that reports in binary units
  will show smaller numbers for the same files.

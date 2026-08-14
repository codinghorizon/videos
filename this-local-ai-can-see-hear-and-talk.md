---
layout: default
title: "The Truth About Local AI That Sees And Hears You"
permalink: /this-local-ai-can-see-hear-and-talk/
date: 2026-08-14
---

# The Truth About Local AI That Sees And Hears You

Every figure, name and capability the finished video states, chased to a primary source.

---

## Gemma 3n

### What it takes in, and what it gives back

**Gemma 3n natively supports image, audio, video and text inputs, and text output.**

> "Gemma 3n natively supports image, audio, video, and text inputs and text outputs."

Source: Google Developers Blog, *Introducing Gemma 3n: The developer guide*
<https://developers.googleblog.com/en/introducing-gemma-3n-developer-guide/>

This is the claim the whole video rests on, and it is worth being precise about what it
does and does not say. The inputs are multimodal. The output is text. Nothing in Google's
own description says the model produces audio.

### The two sizes, and what they cost to hold

**E2B and E4B, with raw parameter counts of 5B and 8B, running in roughly 2GB and 3GB of
memory.**

> "While their raw parameter count is 5B and 8B respectively, architectural innovations
> allow them to run with a memory footprint comparable to traditional 2B and 4B models,
> operating with as little as 2GB (E2B) and 3GB (E4B) of memory."

Source: Google Developers Blog, *Introducing Gemma 3n: The developer guide*
<https://developers.googleblog.com/en/introducing-gemma-3n-developer-guide/>

Google's own model documentation puts the same idea a second way: E2B loads over 5 billion
parameters in standard execution but carries "an effective memory load of just under 2
billion (1.91B) parameters."

Source: Google AI for Developers, *Gemma 3n model overview*
<https://ai.google.dev/gemma/docs/gemma-3n>

### Languages

**140 languages for text, and multimodal understanding of 35.**

> "Gemma 3n delivers quality improvements across multilinguality (supporting 140 languages
> for text and multimodal understanding of 35 languages)"

Source: Google Developers Blog, *Introducing Gemma 3n: The developer guide*
<https://developers.googleblog.com/en/introducing-gemma-3n-developer-guide/>

The two numbers are not the same number and the video keeps them apart. Text support is
much wider than multimodal support.

### The vision encoder

**MobileNet-V5.**

> "High-performance MobileNet-V5 encoder"

Source: Google AI for Developers, *Gemma 3n model overview*
<https://ai.google.dev/gemma/docs/gemma-3n>

The developer guide adds that it "processes up to 60 frames per second on a Google Pixel"
and "natively supports resolutions of 256x256, 512x512, and 768x768 pixels."

Source: Google Developers Blog, *Introducing Gemma 3n: The developer guide*
<https://developers.googleblog.com/en/introducing-gemma-3n-developer-guide/>

### Context

**32K tokens.**

Source: Google AI for Developers, *Gemma 3n model overview*
<https://ai.google.dev/gemma/docs/gemma-3n>

---

## Speech output is a separate system

The video's central correction is that the model writes text and something else turns that
text into sound. Both named engines are real, separately maintained projects that run
locally and are not part of Gemma 3n.

### Kokoro

**82 million parameters, Apache-2.0, 54 voices across 8 languages, 24 kHz output.**

Source: hexgrad/Kokoro-82M model card, Hugging Face
<https://huggingface.co/hexgrad/Kokoro-82M>

The model card describes it as an open-weight text-to-speech model that "delivers
comparable quality to larger models while being significantly faster and more
cost-efficient." Published 27 January 2025.

### Piper

**A fast, local neural text-to-speech engine that embeds espeak-ng for phonemization.
GPL-3.0.**

> "A fast and local neural text-to-speech engine that embeds espeak-ng for phonemization."

Source: OHF-Voice/piper1-gpl
<https://github.com/OHF-Voice/piper1-gpl>

---

## Multimodal models running locally today

Ollama's own library documents Gemma 3 as multimodal, processing text and images, with a
128K context window and support for over 140 languages, requiring Ollama 0.6 or later.

Source: Ollama model library, gemma3
<https://ollama.com/library/gemma3>

This is the practical evidence for the video's claim that taking images into a local model
is something you can do now rather than something that is coming.

---

## Not checked

- **The comparative claim that cloud systems are "still ahead in many tasks."** This is a
  general statement about the state of the field rather than a result from a named
  benchmark, and no single source establishes it across the range of tasks the video is
  talking about.
- **The claim that local multimodal models "can be slower than the cloud."** True in the
  ordinary case, and dependent enough on hardware, quantization and which cloud model is
  being compared against that no single figure describes it.
- **Terminal sessions and interface renders shown on screen** are illustrations of the
  failure modes and workflows being described, not captures of a specific run.
- **The claim that speech quality "may feel uneven if the text to speech engine is weak."**
  A judgement about perceived quality, not a measured one.

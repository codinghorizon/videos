---
layout: default
title: "Your AI Writing Now Carries A Mark You Cannot See"
permalink: /claude-is-hiding-watermarks-in-your-ai-text/
date: 2026-08-14
---

# Your AI Writing Now Carries A Mark You Cannot See

Every figure, date, name and mechanism the finished picture puts on screen, chased to a
primary source. Checked 14 August 2026.

## What Claude actually marks

**Claude output carries machine-readable marking, and the marking differs by output type.**
Text carries an embedded watermark woven into the text itself, which travels with the text
when it is copied and pasted elsewhere. Supported files carry signed provenance metadata
instead.
Source: Anthropic, *How Claude marks AI-generated content*.
https://support.claude.com/en/articles/16266773-how-claude-marks-ai-generated-content

**File provenance uses C2PA, and the supported formats are SVG, PNG and JPG.** The metadata
follows the Coalition for Content Provenance and Authenticity open standard, which is used
across the industry to record where content came from.
Source: as above.

**Claude models launched in the EU on or after 2 August 2026 support machine-readable
marking at launch.** Support for models released before that date is described as in
progress.
Source: as above.

**The marking applies wherever Claude is offered, worldwide,** not only in the EU. This is
the point the video makes about a compliance system built for one jurisdiction reaching
everyone, and it is the provider's own description rather than an inference.
Source: as above.

**Marking spans Claude Platform (the API), Claude, Claude Code, Claude Cowork and Claude
Tag.**
Source: as above.

**A detected mark does not prove Claude authored the content, and an absent mark does not
prove the content is human.** Anthropic states that a detected mark indicates the content
may have been *processed* by Claude, not that Claude wrote it, and that marks can be lost
through editing, paraphrasing, format conversion or screenshots.
Source: as above. This caveat is load-bearing for the video's argument that a detector
flattens the difference between writing something and touching it, and it is the provider's
own wording rather than the video's characterisation.

## The regulation

**Article 50(2) of the EU AI Act requires providers of AI systems generating synthetic
audio, image, video or text content to ensure outputs are marked in a machine-readable
format and detectable as artificially generated or manipulated.** The obligation is
qualified as applying where technically feasible, and excludes assistive editing functions
and systems authorised by law to detect or prevent criminal activity.
Source: European Commission AI Act Service Desk, Article 50.
https://ai-act-service-desk.ec.europa.eu/en/ai-act/article-50

**The four media types named on screen — audio, image, video, text — are the four the
article names.**
Source: as above.

**Article 50(1) covers informing people they are interacting with an AI system, and
Article 50(4) covers deployers disclosing deepfakes and AI-generated text published to
inform the public on matters of public interest.** The video stays on paragraph 2; the
neighbouring paragraphs are noted here only so the citation on screen is not read as
covering the whole article.
Source: as above.

## How a text watermark works

**Text watermarking works by modulating the probability of the tokens a model generates,
rather than by inserting a stamp or a hidden character.** The system adjusts the
probability scores assigned to candidate next tokens; the resulting pattern across the
model's actual choices is the watermark, and it is detectable afterwards without being
visible to a reader.
Source: Google DeepMind, *Watermarking AI-generated text and video with SynthID*.
https://deepmind.google/blog/watermarking-ai-generated-text-and-video-with-synthid/

**Longer output is easier to mark and detect.** Detection works best when a model generates
longer responses with genuine variety, because a longer passage offers more token choices
to adjust.
Source: as above.

**Heavy rewriting and translation weaken the signal.** Confidence scores can be greatly
reduced when watermarked text is thoroughly rewritten or translated into another language.
Source: as above.

**Short factual answers are harder to watermark.** A prompt with only one correct answer
leaves little room to adjust token probabilities without damaging accuracy, so there is
less signal to embed.
Source: as above.

## Model collapse

**Training generative models on recursively generated data degrades them, and the damage
falls first on the tails of the original distribution.** The paper distinguishes early
collapse, where the model drifts from the true distribution as errors accumulate, from late
collapse, where low-frequency events disappear permanently. Indiscriminate use of
model-generated content in training causes irreversible defects.
Source: Shumailov, Shumaylov, Zhao, Papernot, Anderson and Gal, *AI models collapse when
trained on recursively generated data*, Nature 631, 755–759 (2024).
https://www.nature.com/articles/s41586-024-07566-y

This is the source for the beat that draws a distribution losing its tails and drifting off
the human one, and for the claim that the risk is volume of synthetic data rather than any
single AI-written paragraph.

## Not checked

- **Whether Claude's text watermark uses the same token-probability biasing the video
  describes.** Anthropic states that an embedded watermark is woven into the text but has
  not published the mechanism. The explanation on screen is the established approach to
  text watermarking, sourced to SynthID above, and the video does not claim it is
  specifically Anthropic's implementation. No shot attributes the mechanism to Anthropic.
- **"Trillion-dollar AI companies"** is used as a category rather than a measurement. No
  valuation figure is printed on screen, and no specific company is named at that beat.
- **The named consequences for developers** — repository scanning for AI-generated code,
  maintainers rejecting AI-assisted contributions, employers measuring developers by
  AI-origin signal, legal teams using watermark evidence in copyright disputes, future
  coding models downweighting model-written code — are stated as open questions about what
  could follow, not as things that have happened. Nothing on screen presents any of them as
  a documented event.

  A review pointed out that drawing them as ordinary working screens made them *read* as
  documented anyway, whatever the narration said, so the two beats that mock up a system —
  the repository scan with its maintainer queue, and the performance dashboard with the
  watermarked exhibit — are now held inside a dashed frame, carry the question the
  narration actually asks, and are stamped "not yet · an open question" for the whole beat.
  The drawing and the sourcing say the same thing now.
- **No detection accuracy rate, false-positive rate or confidence score appears anywhere in
  the video.** None could be sourced for Anthropic's implementation, so none is drawn.

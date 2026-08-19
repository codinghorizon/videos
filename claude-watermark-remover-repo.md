---
layout: default
title: "Claude Watermarks Already Have A Removal Problem"
permalink: /claude-watermark-remover-repo/
date: 2026-08-19
---

# Claude Watermarks Already Have A Removal Problem

{% raw %}
Every figure, name, version and quoted phrase the finished picture puts on screen, chased
to a primary source. Checked 18 August 2026.

## The repository

**Name and author.** `guillaumemeyer/watermarks-remover`, by Guillaume Meyer.
Source: <https://github.com/guillaumemeyer/watermarks-remover>

**Created 11 August 2026.** Reported alongside the star trajectory: 4,102 stars by
13 August, two days after creation on 11 August.
Source: <https://www.implicator.ai/github-tool-targets-claude-watermarks/>

**Stars and forks.** 14.3k stars and 1.6k forks as of 18 August 2026, read off the
repository page. The narration says fourteen thousand stars and fifteen hundred forks,
which were the counts when the script was written; the picture therefore renders
`14,000+ stars` and `1,500+ forks` with the read date, so the screen stays true as the
counts continue to climb.
Source: <https://github.com/guillaumemeyer/watermarks-remover>

**What it is, in the repository's own words.** "Agent skill + stdlib Python service to
strip multi-vendor AI provenance marks from text and files — for privacy and hygiene on
content you own."
Source: <https://github.com/guillaumemeyer/watermarks-remover>

**Repository description.** "Strip multi-vendor AI provenance marks: Unicode text hygiene,
statistical rewrite hooks, and C2PA/metadata from PNG/JPEG/SVG/PDF/DOCX/HTML/MD"
Source: <https://github.com/guillaumemeyer/watermarks-remover>

**Scope has widened past Claude.** It began as a Claude only agent skill and now advertises
coverage of Claude, Gemini and SynthID-Text, OpenAI provenance surfaces, and open weight
models carrying Kirchenbauer style marks.
Sources: <https://www.implicator.ai/github-tool-targets-claude-watermarks/>,
<https://x.com/guillaumemeyer/status/2087275734608007415>

## The three layers

The repository documents exactly three, with these targets and methods:

| Layer | Target | Method |
| --- | --- | --- |
| A | Invisible Unicode, exotic spaces, bidi, tag chars | Deterministic Python scripts |
| B | Statistical (token sampling) text watermarks | Agent rewrite plus optional `rewrite_text.py` hook |
| Files | C2PA / EXIF / XMP / doc props | PNG, JPEG, SVG, PDF, DOCX, HTML, MD and more |

Source: <https://github.com/guillaumemeyer/watermarks-remover>

**Rewrite backends.** Layer B's `rewrite_text.py` hook supports Ollama and OpenAI
compatible endpoints, selected through the `WATERMARKS_REWRITE_BACKEND` and
`WATERMARKS_REWRITE_BASE_URL` environment variables.
Source: <https://github.com/guillaumemeyer/watermarks-remover>

**How much rewriting Layer B needs.** "Stripping a statistical mark requires rewriting a
substantial fraction of the text — sentence by sentence, not section by section."
Source: <https://github.com/guillaumemeyer/watermarks-remover>

**Harnesses, not oracles.** The repository describes optional MarkLLM and MarkDiffusion
integrations as "verification harnesses, not an oracle", and states they cannot certify
that a vendor detector will fail.
Source: <https://github.com/guillaumemeyer/watermarks-remover>

## How Claude's text mark actually works

**It is a change in sampling, not an insertion.** "Nothing is added to the text and there
are no hidden characters." The mechanism biases the randomness used when the model picks
between acceptable next tokens: "the words that Claude picks are still random, but now, one
can check the sequence of words and see if it's consistent with the choices Claude would
make if it was using the key."
Source: <https://www.anthropic.com/news/claude-text-watermark>

**It carries no identity.** "Watermarking carries no identifying information and can't be
traced to a specific person, organization, or chat." And: "There's nothing in the watermark,
or its key, that would allow anyone to recover any information about the user, their
organization, or their chats with Claude."
Source: <https://www.anthropic.com/news/claude-text-watermark>

**It signals processing, not authorship.** "A detected mark provides a signal that content
was processed by Claude, but is not fully conclusive." And: "Lack of a detected mark doesn't
mean the content wasn't AI-generated or processed." Anthropic also notes Claude "may not be
the original author. People often use Claude to proofread, translate, summarize, or convert
files."
Source: <https://support.claude.com/en/articles/16266773-how-claude-marks-ai-generated-content>

**Scope and date.** Applies to Claude models released on or after 2 August 2026, across
Anthropic's access channels and worldwide rather than only in the EU, with a transition
period for models launched before that date. The approach is based on Google DeepMind's
SynthID-Text.
Sources: <https://www.anthropic.com/news/claude-text-watermark>,
<https://techcrunch.com/2026/08/11/anthropic-says-it-will-watermark-text-generated-by-its-ai-models/>,
<https://www.axios.com/2026/08/12/anthropic-claude-watermarks-ai-detection>

**Driven by Article 50 of the EU AI Act.** The transparency obligation is the stated reason
for the rollout.
Source: <https://interestingengineering.com/ai-robotics/anthropic-claude-text-invisible-watermarks>

## The detector is not public yet

**Anthropic's own wording.** "We will soon be offering a watermark detection API. We're in
the process of working out the details of its implementation." The support article adds:
"We'll share details on detection mechanisms in forthcoming technical documentation."
Sources: <https://www.anthropic.com/news/claude-text-watermark>,
<https://support.claude.com/en/articles/16266773-how-claude-marks-ai-generated-content>

**Which is why removal claims cannot be settled.** Reporting on the repo makes the same
point: the claims cannot currently be checked because Anthropic has not released the
detector that would show whether a cleaned document still carries the mark, so no tool can
honestly certify that a document fails the official check.
Sources: <https://www.implicator.ai/github-tool-targets-claude-watermarks/>,
<https://www.bleepingcomputer.com/news/security/ai-watermark-removers-flood-the-web-almost-none-can-prove-they-work/>

## Paraphrase and back translation are known attacks

**Established in the literature, not invented by this repo.** Watermark robustness is
routinely evaluated against word deletion, synonym substitution, paraphrasing and roundtrip
translation. MarkLLM ships word level tampering (random deletion, WordNet synonym
substitution, context aware BERT substitution) and document level paraphrasing via the
Dipper model or an API paraphraser.
Sources: <https://arxiv.org/html/2405.10051v2>,
<https://aclanthology.org/2024.emnlp-demo.7.pdf>

**Back translation specifically.** Translating watermarked English into a pivot language and
back is a standard removal attack, and meaning preserving attacks of this family measurably
degrade detectability. Cross lingual summarisation with optional back translation is
reported as stronger still.
Sources: <https://arxiv.org/html/2510.24789>,
<https://arxiv.org/html/2508.20228v1>

**SynthID robustness has been assessed directly**, which is what makes a SynthID style test
bench a meaningful stand in even though it is not Anthropic's detector.
Source: <https://arxiv.org/html/2508.20228v1>

## The file side: what the metadata standards are

**C2PA** is the Coalition for Content Provenance and Authenticity's content credentials
standard, an attached manifest rather than anything embedded in wording.
Source: <https://c2pa.org/specifications/specifications/2.1/index.html>

**EXIF and XMP** are the long established attached metadata formats for images and
documents, which is the basis for the point that scrubbing attached metadata is decades old
practice rather than new capability.
Sources: <https://www.cipa.jp/std/documents/download_e.html?DC-008-Translation-2019-E>,
<https://developer.adobe.com/xmp/docs/XMPSpecifications/>

## Invisible Unicode carriers

Zero width characters, exotic spaces, bidirectional controls and tag characters are all real
Unicode codepoint classes, which is why Layer A can be deterministic: the set to search for
is finite and specified.
Source: <https://www.unicode.org/versions/latest/>

## Not checked

- **Claude declining to help install the tool.** The rewritten script asserts this in its
  own voice rather than attributing it to another video, which raises the bar on it, and it
  still cannot be chased to a primary source. No Anthropic policy document names this
  repository or this class of tool, refusals are not deterministic and vary with the
  session and the wording of the request, and a refusal observed once does not establish a
  rule. The picture therefore shows a terminal exchange with an on screen credit that says
  only what is verifiable, that no Anthropic policy document names this repository, and the
  script is explicit that it is not evidence of a hardcoded blacklist.
- **What the public explanation artifacts show about comments versus code.** The claim that
  worked examples tend to put the visible change in comments rather than in program
  behaviour is a characterisation of those artifacts, not something a primary source states
  about them.
- **Exact live star and fork counts.** Both move hourly. The figures on screen carry the
  date they were read, and the narration's rounder numbers were correct when written.
{% endraw %}

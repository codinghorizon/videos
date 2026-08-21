---
layout: default
title: "This AI Answers The Questions ChatGPT Still Refuses"
permalink: /this-ai-has-no-refusal-button/
date: 2026-08-21
---

# This AI Answers The Questions ChatGPT Still Refuses

{% raw %}
Every figure, name and quotation the finished picture puts on screen, chased to a
primary source.

## The model

**Venice Uncensored is a Venice AI model built with the Dolphin AI team.**
The Venice model page credits both. The Hugging Face card for the model is published
under the AskVenice organisation.
- https://venice.ai/models/venice-uncensored-1-2
- https://huggingface.co/AskVenice/venice-uncensored

**It is based on Mistral Small 24B Instruct and on Dolphin Mistral 24B Venice Edition.**
The Hugging Face card gives the lineage explicitly: built on
`mistralai/Mistral-Small-24B-Base-2501`, fine tuned through
`mistralai/Mistral-Small-24B-Instruct-2501`, and further fine tuned from
`dphn/Dolphin-Mistral-24B-Venice-Edition`.
- https://huggingface.co/AskVenice/venice-uncensored
- https://huggingface.co/cognitivecomputations/Dolphin-Mistral-24B-Venice-Edition

**24 billion parameters.**
Stated as `24B params` on the Hugging Face card and as a
"24-billion-parameter open-weights text and vision model" on the Venice model page.
- https://venice.ai/models/venice-uncensored-1-2

**128K context window, on Venice Uncensored 1.2.**
The Venice model page lists a 128K token context window. Version 1.2 is dated
1 April 2026 and is published under Apache 2.0.
- https://venice.ai/models/venice-uncensored-1-2

## The three words on the model card

The card describes the model with exactly the three words the video quotes, and
gives each a one line definition:

- **Steerable** — "You set the system prompt. You decide the alignment."
- **Private** — "It does not log or judge your queries."
- **Unrestricted** — "It declines no requests based on moralizing refusals."

It also states that the model "has no hard-coded alignment, it relies on **you** to
tell it how to behave."
- https://huggingface.co/AskVenice/venice-uncensored

The Dolphin card behind it makes the same argument in its own words: "Dolphin does
not impose its ethics or guidelines on you. You are the one who decides the
guidelines," and "the system prompt is what you use to set the tone and alignment of
the responses."
- https://huggingface.co/cognitivecomputations/Dolphin-Mistral-24B-Venice-Edition

## Plans and price

**Free plan: 10 text prompts per day. Pro plan: $18 per month.**
The Venice pricing tiers list a Free plan at $0 per month including "10 text prompts
per day", and a Pro plan at "$18/mo" with unlimited text prompts and 1,000 images per
day. Higher tiers exist above it (Pro Plus at $68 per month, Max at $200 per month)
and are not discussed in the video.
- https://venice.ai/uncensored

**API token pricing** for Venice Uncensored 1.2 is $0.20 per million input tokens and
$0.90 per million output tokens. The video does not state these, and they are recorded
here only because the price of running it is the obvious next question.
- https://venice.ai/models/venice-uncensored-1-2

## The API

**It implements the OpenAI API specification.**
The documentation states: "Venice's API implements the OpenAI API specification,
ensuring compatibility with existing OpenAI clients and tools," and describes
integrating "using the familiar OpenAI interface".
- https://docs.venice.ai/api-reference/api-spec

**The surface the video lists.** The published documentation index covers, as separate
endpoint groups: image generation and editing; text to speech and speech to text;
music and sound effects; text to video and image to video; embeddings; character
personas; document processing ("Extract text from PDF, DOCX, XLSX, and plain text
files"); and web tools covering search, scraping and text parsing. Chat completions
carry text, and code is produced through them rather than through an endpoint of its
own.
- https://docs.venice.ai/llms.txt
- https://docs.venice.ai/api-reference/api-spec

Venice specific request behaviour, including `enable_web_search` and
`enable_web_scraping`, is set through `venice_parameters` on an otherwise standard
request.
- https://docs.venice.ai/overview/getting-started

## The privacy tiers

Venice documents four tiers, each building on the one before it:

- **Anonymous** — "Venice proxies the request without sending your Venice identity to
  the model provider. Prompt content is still visible to that provider."
- **Private** — "Prompt and response content is processed for inference only and is
  not retained after the request completes." This is the zero data retention tier.
- **TEE** — "Supported models run inside a Trusted Execution Environment with remote
  attestation support."
- **E2EE** — "Your client encrypts the prompt before sending it. Venice relays
  ciphertext, and only the verified TEE decrypts it."

- https://docs.venice.ai/overview/privacy

## Not checked

- **The first tier is documented as "Anonymous".** The narration calls it
  "Anonymized". The four tiers, their order and their definitions are as published;
  only that one label differs, and the shot is drawn with the documented wording.
- **"Code" as a platform capability.** Venice serves code through chat completions
  rather than through a dedicated code endpoint. The other seven capabilities the
  video names each map to a documented endpoint group.
- **How Venice Uncensored compares with frontier models.** The video says it probably
  will not beat Claude Opus, GPT, Gemini or Grok at everything. No published head to
  head benchmark covering that set was found, and the comparison shot is drawn as the
  claim it is rather than as a measured result.
- **Whether the privacy guarantees hold in practice.** The tier definitions above are
  Venice's own description of its product. Zero data retention on the Private tier is
  described as contract enforced, and the TEE and E2EE tiers rest on remote
  attestation. None of that was independently verified, which is the point the video
  makes when it says trusting the stack is a separate question.
- **Consumer plan prices change.** The $18 per month Pro figure and the ten prompt
  free allowance were read from the Venice pricing tiers in August 2026.
{% endraw %}

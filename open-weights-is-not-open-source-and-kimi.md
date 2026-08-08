---
layout: default
title: "Open Weights Is Not Open Source And Kimi Proved It"
permalink: /open-weights-is-not-open-source-and-kimi/
date: 2026-08-08
---

# Open Weights Is Not Open Source And Kimi Proved It

Every figure, licence term and definition stated in this video, chased to the place it
was published. Checked 8 August 2026.

---

## Kimi K3, and what Moonshot calls it

**Moonshot describes Kimi K3 as an open-weight model, not an open-source one.** The model
card opens by calling it an "open-weight, native multimodal agentic model", and says the
full model weights are released under the Kimi K3 License.

- Model card: <https://huggingface.co/moonshotai/Kimi-K3>
- Repository: <https://github.com/MoonshotAI/Kimi-K3>

**The architecture figures.**

| | |
|---|---|
| Total parameters | 2.8 trillion |
| Active parameters per token | 104 billion |
| Routing | 16 of 896 experts per token |
| Context window | 1,048,576 tokens |
| Weights published | 27 July 2026 |

Source: the Kimi K3 model card, <https://huggingface.co/moonshotai/Kimi-K3>

---

## The previous release said something different

**Kimi K2.5 was described as open-source.** Its model card calls it "an open-source,
native multimodal agentic model", and states that "both the code repository and the model
weights are released under the Modified MIT License."

That is the change the video turns on: the same lab, one release apart, moved from
"open-source" to "open-weight" in its own words.

- Kimi K2.5 model card: <https://huggingface.co/moonshotai/Kimi-K2.5>

---

## What the Kimi K3 License actually grants

For most of its length the licence is permissive. It grants, free of charge, the rights to
use, copy, modify, publish, distribute, sublicense and sell the software, and to deploy,
run, fine-tune and build derivative works from the model weights.

Two conditions sit on top of that.

**The Model-as-a-Service threshold.** A licensee running a Model-as-a-Service business,
meaning giving third parties inference or fine-tuning access with meaningful control over
inputs, parameters or training data, must reach a separate agreement with Moonshot once
revenue across the licensee and its affiliates passes **20 million US dollars over any
consecutive twelve month period**.

**The attribution threshold.** A commercial product or service using Kimi K3 that exceeds
**100 million monthly active users**, or **20 million US dollars in monthly revenue**, must
display "Kimi K3" prominently in its interface, subject to the licence's own exceptions.
Internal use, and use through Moonshot's official products or certified inference partners,
are exempt.

- Licence text: <https://github.com/MoonshotAI/Kimi-K3/blob/main/LICENSE>
- Reporting on the terms: <https://venturebeat.com/technology/kimi-k3s-full-weights-are-here-but-theyre-open-with-a-caveat-what-enterprises-should-know>

---

## The Open Source Initiative's definition

**The four freedoms.** Version 1.0 of the Open Source AI Definition says an Open Source AI
system must grant the freedoms to:

1. **Use** the system for any purpose and without having to ask for permission.
2. **Study** how the system works and inspect its components.
3. **Modify** the system for any purpose, including to change its output.
4. **Share** the system for others to use with or without modifications, for any purpose.

The first of those is the one that does the work in this video: *for any purpose and
without having to ask for permission*.

**The preferred form to make modifications.** The definition requires all three of:

- **Data Information** — sufficiently detailed information about the data used to train the
  system so that a skilled person can build a substantially equivalent system.
- **Code** — the source code used to train and run the system.
- **Parameters** — the model parameters, including weights and configuration settings.

Weights are one of the three, which is the distinction the video is built on.

**What Data Information has to cover.** The definition asks for the complete description of
all data used for training, including unshareable data, "disclosing the provenance of the
data, its scope and characteristics, how the data was obtained and selected, the labeling
procedures, and data processing and filtering methodologies", plus a listing of publicly
available training data and where to obtain it, and a listing of training data obtainable
from third parties, including for a fee.

It does not require every individual training sample to be downloadable, which is why
datasets containing copyrighted, licensed, private or otherwise non-redistributable
material do not automatically put a system outside the definition.

- Definition: <https://opensource.org/ai/open-source-ai-definition>
- On the concept of Data Information: <https://opensource.org/blog/explaining-the-concept-of-data-information>

---

## The comparison in ordinary software

Linux publishes the source used to build the kernel, not only the built kernel, and it is
distributed under the GNU General Public License version 2, which grants the rights to
inspect, modify, compile and redistribute.

- Source tree: <https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/>
- Licence: <https://www.kernel.org/doc/html/latest/process/license-rules.html>

Apache License 2.0, named in the video as the permissive end of the model licensing range,
is an OSI-approved licence with no commercial-use threshold.

- <https://opensource.org/license/apache-2-0>

---

## Alibaba and the licensing spectrum

**Reuters, 7 August 2026.** Alibaba plans to require large commercial users of the
open-weight version of its next Qwen model to share a portion of the revenue they generate
from it, with the measure intended to arrive alongside the open-weight release. The rate
was reported as not yet finalised.

The report draws the comparison to Moonshot directly: Moonshot's terms require any party
selling Kimi K3 as a service and generating more than 20 million dollars in annual revenue
to reach a commercial agreement, which can include a revenue share of up to 30 per cent.

Small developers and researchers are not affected by the reported change.

- Reuters via Yahoo Finance: <https://finance.yahoo.com/technology/ai/articles/alibaba-plans-revenue-sharing-next-131417995.html>
- Reuters via Investing.com: <https://ng.investing.com/news/stock-market-news/alibaba-plans-revenuesharing-for-commercial-users-of-next-qwen-ai-model--reuters-2646420>

---

## Caveats

- The revenue-share figure of up to 30 per cent attaches to Moonshot's separate commercial
  agreements as described in the Reuters report. It is a reported figure rather than a
  number stated in the published licence text, and it is not claimed on screen.
- Alibaba's licensing change is a plan reported by Reuters, not a published licence. The
  terms may differ from the report when the release actually lands.
- The Kimi K3 licence conditions above are as published at the time of checking. A licence
  can be amended after a release, and the version that governs any particular use is the
  one shipped with the weights that were downloaded.
- The Open Source AI Definition is the Open Source Initiative's position and is itself
  contested. This video uses it as the reference point for what "open source" claims,
  rather than as the only possible reading of the phrase.

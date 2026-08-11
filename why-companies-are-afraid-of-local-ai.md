---
layout: default
title: "The Best Open AI Models Are The Ones Nobody Trusts"
permalink: /why-companies-are-afraid-of-local-ai/
date: 2026-08-11
---

# The Best Open AI Models Are The Ones Nobody Trusts

Every figure, name, date and price the finished picture puts on screen, chased to a
source. Anything that could not be chased is listed at the bottom and is not rendered.

## The warning the video opens on

**Arena CEO Anastasios Angelopoulos says enterprises do not know which models to trust,
and are as wary of Chinese open weight models as they are of the frontier labs.**

His words: "It's not only true that they're terrified of working with the frontier labs,
but they're also terrified of working with the Chinese open source." He also said
enterprises are "in a really tricky situation ... just the way that the cards have
landed".

- Business Insider, Brent D. Griffiths, 8 August 2026:
  https://www.businessinsider.com/arena-ai-ceo-enterprises-dont-know-which-ai-models-trust
  (syndicated copy read at
  https://finance.yahoo.com/technology/ai/articles/arena-ai-ceo-says-enterprises-093601636.html)

Arena is the evaluation company behind the public model arena, which is why its CEO sees
which models enterprises are actually shortlisting.

## The Chinese open weight labs the video names

**Moonshot AI, DeepSeek, Alibaba and Z.ai.** All four publish downloadable weights.

### Kimi K3 (Moonshot AI)

2.8 trillion total parameters as a mixture of experts, 16 of 896 experts active per token,
a 1,000,000 token context window, open weights released 27 July 2026. At release it was
the largest open weight model published.

- Nathan Lambert, Interconnects, "Kimi K3: the open-weights escalation":
  https://www.interconnects.ai/p/kimi-k3-the-open-weights-escalation
- Model overview on Hugging Face:
  https://huggingface.co/blog/ResterChed/kimi-k3-model-overview-mxfp4-quantization-open-wei
- Tom's Hardware on the release:
  https://www.tomshardware.com/tech-industry/artificial-intelligence/moonshot-ai-releases-weights-for-kimi-k3-firing-a-shot-across-the-bow-of-openai-and-anthropic-open-weight-model-performs-almost-as-well-as-frontier-models-while-being-2-3x-easier-to-run

### DeepSeek R1

Released 20 January 2025 and the moment open weight reasoning became a mainstream
enterprise question rather than a research one.

- DeepSeek R1 model card and release: https://huggingface.co/deepseek-ai/DeepSeek-R1

### Qwen (Alibaba)

Passed 700 million cumulative downloads on Hugging Face, announced by Alibaba on
13 January 2026, overtaking Llama as the most downloaded open model family. Derivative
models built on Qwen checkpoints passed 200,000 later the same month.

- Reported from Alibaba's announcement:
  https://www.arturmarkus.com/alibabas-qwen-hits-700-million-downloads-on-hugging-face-overtakes-metas-llama-as-worlds-most-popular-open-source-ai-model/
- Qwen organisation on Hugging Face, 458 published models: https://huggingface.co/Qwen

### GLM 5.2 (Z.ai)

Open weights under the MIT licence, 1,000,000 token context window, built for long horizon
coding and agent work, released June 2026.

- VentureBeat on the release:
  https://venturebeat.com/technology/z-ais-open-weights-glm-5-2-beats-gpt-5-5-on-multiple-long-horizon-coding-benchmarks-for-1-6th-the-cost
- Weights on Hugging Face: https://huggingface.co/zai-org

## The price gap the cost chapter draws

**GLM 5.2 is listed at $4.40 per million output tokens. GPT 5.5 is listed at $30.00 per
million output tokens.** That is roughly a seven times difference on the same unit, which
is the shape of the price pressure the video describes.

- Z.ai published API pricing, tracked at https://pricepertoken.com/pricing-page/model/z-ai-glm-5.2
  and https://www.aipricing.guru/models/z-ai-glm-5-2/
- OpenAI GPT 5.5 pricing, tracked at https://www.morphllm.com/openai-api-pricing
  and https://promptcost.org/en/blog/gpt-55-pricing-guide-2026/

## The policy fight

**Whether Chinese open weight models should be restricted in the US is unsettled and is
being argued in public by the industry and by Washington at the same time.**

On 24 July 2026, twenty five companies including Nvidia, Microsoft, Meta, IBM and Palantir
published an open letter, "Open Weights and American AI Leadership", urging policymakers
not to impose broad restrictions on open weight models. Anthropic has argued the other
way, for tighter restrictions on Chinese AI. China's own commerce ministry has separately
been drafting export controls on model weights.

- TechCrunch, 24 July 2026:
  https://techcrunch.com/2026/07/24/as-us-weighs-response-to-chinese-ai-industry-urges-against-broad-open-weight-restrictions/
- Lawfare, "Knives Are Out for Open-Weight AI Models":
  https://www.lawfaremedia.org/article/knives-are-out-for-open-weight-ai-models
- Rest of World on the split between Silicon Valley and Washington:
  https://restofworld.org/2026/silicon-valley-debate-chinese-open-weight-ai-models/

## Why downloaded weights do not phone home

**Weights are data, not a program.** A downloaded checkpoint has no network client in it
and no way to initiate a connection; whatever talks to the network is the runtime you
chose and the dependencies you installed around it. That is why the video puts the risk in
the deployment rather than in the file.

The qualification that matters, and the reason the video keeps insisting the stack is the
real surface: loading a model can execute code. Python pickle based checkpoints run
arbitrary code at load time, and malicious models exploiting exactly that have been found
on public model hubs. The safetensors format exists to remove that path by storing only
tensors.

- Hugging Face on pickle risk and the safetensors format:
  https://huggingface.co/docs/hub/security-pickle
- safetensors: https://github.com/huggingface/safetensors
- JFrog, malicious models with a silent backdoor found on a public hub:
  https://jfrog.com/blog/data-scientists-targeted-by-malicious-hugging-face-ml-models/
- ReversingLabs on the same class of attack:
  https://www.reversinglabs.com/blog/rl-identifies-malware-ml-model-hosted-on-hugging-face

## Running weights locally

The pull the video shows on screen is the real command form for a local runtime.

- Ollama: https://ollama.com
- vLLM: https://docs.vllm.ai

## Not chased to a primary

- **Kimi K3's exact licence terms.** Reporting at release describes a modified MIT licence,
  but the licence text was still being finalised alongside the weight drop in the coverage
  read here, so the video shows the model and its size and does not put a licence on screen
  for it.
- **The GPT 5.5 price.** OpenAI has moved its published pricing page on to the GPT 5.6
  family, so the $30.00 figure is taken from third party trackers of the price while it was
  published rather than from OpenAI's live page.
- **Aggregate enterprise AI spend.** The video says serious usage adds up quickly and draws
  a rising cost curve, and deliberately puts no total on it, because no figure for what a
  representative company spends could be chased to a primary.

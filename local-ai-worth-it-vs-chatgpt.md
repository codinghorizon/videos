---
layout: default
title: "Is ChatGPT Level Local AI Finally Worth It?"
permalink: /local-ai-worth-it-vs-chatgpt/
date: 2026-10-31
---

# Is ChatGPT Level Local AI Finally Worth It?

{% raw %}
Every price was read live on 30 October 2026 (US listings). Every speed is a published run by
someone else, never our own testing; tok/s means generation (decode) speed. Benchmark scores are
the publishers' own.

## How the video measures each rung

- **Months of ChatGPT Plus** = the machine's price divided by Plus at $20 a month, rounded to whole
  months: $799.99 / 20 = 40, $1,099 / 20 = 55, $1,778 / 20 = 89, $3,499.99 / 20 = 175.
- **Dollars per GB** = the price divided by the memory a model can use (the card's own memory on a
  graphics card, the shared pool on a Mac or Strix Halo machine): $899 / 16 = $56.19,
  $1,099 / 24 = $45.79, $799.99 / 16 = $50, $1,778 / 24 = $74.08, $3,499.99 / 128 = $27.34.
- **Electricity:** US average residential price **18.16 cents/kWh** (August 2026, EIA Electric
  Power Monthly Table 5.6.A). A year = watts x 4 hours a day x 365 / 1000 x $0.1816. The 4 hours is
  our assumption and the watts are rated maximums, so these are ceilings: Mac mini 70 W = $19,
  RTX 3090 350 W = $93, EVO-X2 140 W peak = $37.
  https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_5_6_a
- **Arena win rate:** Arena ratings are Bradley-Terry on an Elo scale, so a 40 point gap gives the
  lower model an expected share of 1 / (1 + 10^(40/400)) = 0.443, about 44 times in 100. Our
  arithmetic on their method. https://lmsys.org/blog/2023-12-07-leaderboard/
- **Tokens:** a token is about 3/4 of a word (OpenAI). https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them

## ChatGPT

- Plans: Free $0, Go **$8**, Plus **$20**, Pro **$100 / $200 / $500** a month. A year of Go = $96.
  https://learn.chatgpt.com/docs/pricing
- Free: "Unlimited text chats with GPT-6"; Pro is powered by GPT-6 Astra; every personal plan:
  "Content is used to train our models, Opt-out available" (read 30 October 2026).
  https://chatgpt.com/pricing
- Training opt-out: https://help.openai.com/en/articles/7730893-data-controls-faq

## How close local AI is

- Artificial Analysis Intelligence Index v5: GPT-6 Astra (Max) **57**. https://artificialanalysis.ai/models
- Best open-weights model **32**; Qwen 3.8 27B (Xhigh) **20**. https://artificialanalysis.ai/models/open-source
- Arena text leaderboard (updated 27 October 2026): GPT-6 Astra (Max) **1476**, Qwen3.8-27B **1436**.
  https://arena.ai/leaderboard/text

## The free apps

- LM Studio is free for home and work. https://lmstudio.ai/blog/free-for-work
- LM Studio offline: "Nothing you enter into LM Studio when chatting with LLMs leaves your device."
  https://lmstudio.ai/docs/app/offline
- LM Studio has no built-in web search; tools come through MCP. https://lmstudio.ai/docs/app/mcp
- Ollama local use is free; its web search needs a free account and API key.
  https://ollama.com/pricing and https://docs.ollama.com/capabilities/web-search
- Jan is Apache 2.0 and runs offline; web search is on by default with no API key; it labels which
  models fit. https://docs.jan.ai/desktop , https://docs.jan.ai/desktop/web-search ,
  https://docs.jan.ai/desktop/manage-models
- Windows shows installed RAM under Settings > System > About.
  https://support.microsoft.com/en-us/windows/find-information-about-your-windows-device-a66d52c8-3323-44fd-8f34-a9497bb935e1

## Rung one: the laptop you own ($0)

- Qwen3.5 4B Q4_K_M **2.74 GB**; Qwen3.5 9B Q4_K_M about **5.7 GB** (Unsloth).
  https://huggingface.co/unsloth/Qwen3.5-4B-GGUF , https://huggingface.co/unsloth/Qwen3.5-9B-GGUF
- LocalScore, Llama 3.1 8B Q4_K_M: Ryzen 7 4800H about **7 tok/s**, Apple M5 16 GB **20.2 tok/s**.
  https://www.localscore.ai/model/1
- A 2011 Dell E6420 with 8 GB, CPU only, Llama 2 7B Q4_0: **1.90 tok/s**.
  https://www.mgroeber.de/benchmarking-llamacpp-on-legacy-hardware-2.html
- Gaming laptop (RTX 4070 8 GB + 32 GB RAM): Qwen3.6 35B-A3B, about 3B active, Q4 file about
  **22 GB** (Unsloth) https://huggingface.co/unsloth/Qwen3.6-35B-A3B-GGUF ; one RTX 3050 6 GB owner
  with 24 GB RAM reports **30 tok/s** at Q4_K_M (llamaperf). https://llamaperf.com/gpu/rtx-3050-6gb
- The viewer comments shown are real, under https://youtu.be/whrm2Dnjzlk .

## The skip: Mac mini M6 16 GB ($899) and MacBook Air M5 ($1,299)

- Mac mini M6 16GB/256GB **$899** (Apple). https://www.apple.com/shop/buy-mac/mac-mini/m6-chip-12-core-cpu-12-core-gpu-16gb-memory-256gb-storage
- MacBook Air 13" M5 16 GB from **$1,299** (Apple). https://www.apple.com/shop/buy-mac/macbook-air

## Rung two: Mac mini M6 24 GB ($1,099)

- **$1,099** (Apple). https://www.apple.com/shop/buy-mac/mac-mini/m6-chip-12-core-cpu-12-core-gpu-24gb-memory-256gb-storage
- ComputerBase review, LM Studio: Qwen3 14B just under **18 tok/s**; Qwen 3.8 27B 4-bit about
  **9.5 tok/s**. https://www.computerbase.de/artikel/pc-systeme/apple-mac-mini-m6-test.99469/seite-2
- llamaperf, Qwen 3.8 27B 4-bit **9.83 tok/s** (mlx-vlm). https://llamaperf.com/gpu/m6-24gb
- 70 W maximum (Apple). https://support.apple.com/en-us/103253

## Rung three: RTX 5060 Ti 16 GB ($799.99)

- Cheapest new **$799.99** on Newegg (MSI Ventus 3X OC and ASUS Dual).
  https://www.newegg.com/p/pl?d=rtx+5060+ti+16gb&N=4131&Order=1
- In a whole tower: ABS Cyclone Aqua, Core i7-14700F, **$1,599.99** (Newegg).
  https://www.newegg.com/abs-cyclone-aqua-gaming-pc-geforce-rtx-5060-ti-intel-core-i7-14700f-16gb-1tb-ssd-c1a47n56t1-black/p/N82E16883360993
- Hardware Corner, llama.cpp at 4K: Qwen3 14B Q4_K **41.1 tok/s**, gpt-oss-20b 92.1 tok/s.
  https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-5060-ti-16gb/
- gpt-oss-20b 111.51 tok/s (llama.cpp discussion). https://github.com/ggml-org/llama.cpp/discussions/15396
- Qwen 3.8 27B only at 3-bit: median **28.8 tok/s**; IQ4_XS reports 25-30 (llamaperf).
  https://llamaperf.com/gpu/rtx-5060-ti-16gb

## Rung four: used RTX 3090 24 GB ($1,778)

- Median asking price **$1,778** across 99 listings (RigPrice, 30 October 2026). https://rigprice.com/gpu/rtx-3090/
- Qwen 3.8 27B: **40.31 tok/s** at 4K, 33.95 at 64K (Hardware Corner).
  https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/
- 350 W board power (NVIDIA compare page). https://www.nvidia.com/en-us/geforce/graphics-cards/compare/

## Top rung: GMKtec EVO-X2 128 GB ($3,499.99)

- Ryzen AI Max+ 395, 128 GB / 1 TB, **$3,499.99**, 120 W sustained, 140 W peak (GMKtec).
  https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc
- gpt-oss-120b **53.4 tok/s** (visorcraft strix-halo-llm-perf).
  https://github.com/visorcraft/strix-halo-llm-perf/blob/main/BENCHMARKS.md

## Caveats

- Prices move weekly; the RTX 3090 figure is a median asking price, not a sale price.
- Electricity figures assume 4 hours a day at rated maximum power, so they are upper bounds.
- The 44-in-100 figure is our arithmetic on Arena's published method, not a number Arena prints.
- Speeds come from different testers, apps, quantisations and context lengths; they show a rung's
  scale, not a controlled comparison.
{% endraw %}

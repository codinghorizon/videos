---
layout: default
title: "Everything You Need To Know About Running AI At Home"
permalink: /everything-you-need-to-know-about-local-ai/
date: 2026-11-03
---

# Everything You Need To Know About Running AI At Home

{% raw %}
Every price was opened live on 2026-11-03, before recording (the table is in PRICES.md). Figures
marked "our maths" are our own arithmetic from the cited numbers, not a source's claim. We ran
no benchmarks of our own: every speed below is someone else's published run.

## The apps

- LM Studio is free for home and for work. https://lmstudio.ai/blog/free-for-work
- LM Studio, offline: "Nothing you enter into LM Studio when chatting with LLMs leaves your
  device." https://lmstudio.ai/docs/app/offline
- LM Studio system requirements: 16GB of RAM recommended, 4GB of VRAM on Windows.
  https://lmstudio.ai/docs/app/system-requirements
- LM Studio's download advice: "Choose a 4-bit option or higher."
  https://lmstudio.ai/docs/app/basics/download-model
- LM Studio runs tools through MCP. https://lmstudio.ai/docs/app/mcp
- Ollama: local use is free and unlimited. https://ollama.com/pricing
- Ollama's default context is 4k on machines under 24 GiB of VRAM; it advises at least 64000
  for agents and coding tools. https://docs.ollama.com/context-length
- Jan is open source (Apache 2.0) and runs offline. https://docs.jan.ai/desktop
- Jan's web search is on by default. https://docs.jan.ai/desktop/web-search

## Model sizes and the memory rule

- Qwen3.5 9B GGUF (Unsloth): BF16 17.9GB, Q8_0 9.53GB, Q4_K_M 5.68GB.
  https://huggingface.co/unsloth/Qwen3.5-9B-GGUF
- Our maths: 5.68GB / 9 billion = about 0.63GB per billion parameters at 4-bit, which the video
  rounds to "about two thirds of a gigabyte per billion".
- Qwen3.6 35B-A3B (Unsloth): 35B total, 3B activated, UD-Q4_K_M 22.1GB.
  https://huggingface.co/unsloth/Qwen3.6-35B-A3B-GGUF
- A user report on llamaperf: an RTX 3050 6GB with 24GB of system RAM runs Qwen3.6 35B-A3B
  Q4_K_M at 30 tok/s. https://llamaperf.com/gpu/rtx-3050-6gb

## Speed

- A token is about 3/4 of a word (OpenAI). https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them
- Average adult silent reading: 238 words a minute (Brysbaert 2019).
  https://doi.org/10.1016/j.jml.2019.104047. Our maths: 238 / 60 / 0.75 = about 5 tokens a second.
- LocalScore, Llama 3.1 8B Q4_K_M on a Ryzen 7 4800H laptop CPU: about 7 tok/s.
  https://www.localscore.ai/model/1
- Llama 2 7B Q4_0 on a 2011 Dell E6420 with 8GB, CPU only: 1.90 tok/s.
  https://www.mgroeber.de/benchmarking-llamacpp-on-legacy-hardware-2.html
- Hardware Corner, Qwen 3.8 27B Q4_K_S on an RTX 3090: 40.31 tok/s at 4K context, 33.95 at 64K.
  VRAM: 18GB at 4K, 22GB at 64K, 26GB at 128K.
  https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/
- llamaperf, Mac mini M6 24GB, Qwen 3.8 27B 4-bit in mlx-vlm: 9.83 tok/s.
  https://llamaperf.com/gpu/m6-24gb
- Memory bandwidth: RTX 3090 936 GB/s (https://rigprice.com/gpu/rtx-3090/); Mac mini M6 153GB/s
  at 16GB, 170GB/s at 24GB and 32GB (https://www.apple.com/mac-mini/specs/). Our maths: 936 / 170
  = 5.5x the bandwidth, 40.31 / 9.83 = 4.1x the speed.
- RTX 5060 Ti 16GB: 448 GB/s, Qwen3 14B Q4_K 41.1 tok/s at 4K (Hardware Corner),
  https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-5060-ti-16gb/; Qwen 3.8 27B 3-bit
  median 28.8 tok/s (llamaperf), https://llamaperf.com/gpu/rtx-5060-ti-16gb
- RTX 3060 12GB, llama.cpp CUDA scoreboard (Llama 2 7B Q4_0, tg128):
  https://github.com/ggml-org/llama.cpp/discussions/15013
- RTX 5080 16GB: 960 GB/s. https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5080/
- GMKtec EVO-X2 128GB, gpt-oss-120b: 53.4 tok/s (visorcraft).
  https://github.com/visorcraft/strix-halo-llm-perf/blob/main/BENCHMARKS.md

## How good the free models are

- Artificial Analysis Intelligence Index: top model Gemini 4 Carbon (High) 59.
  https://artificialanalysis.ai/models. Best open-weights model 32; Qwen 3.8 27B (Xhigh) 20.
  https://artificialanalysis.ai/models/open-source
- Arena text leaderboard, October 27, 2026: Gemini 4 Carbon (High) 1528, Qwen3.8-27B 1436, a
  92 point gap. https://arena.ai/leaderboard/text. Our maths with Arena's own rating method,
  1/(1+10^(92/400)): about 37 wins in 100. https://lmsys.org/blog/2023-12-07-leaderboard/
- The viewer question in chapter J is a real comment left on our video HRLhJjaCu-E on
  2026-10-04, quoted as written.

## Prices and running costs (2026-11-03)

| Machine | Price | Per GB (our maths) | Source |
|---|---|---|---|
| Used RTX 3060 12GB | $370 | $30.83 | https://rigprice.com/gpu/rtx-3060-12gb/ |
| RTX 5060 Ti 16GB, new | $799.99 | $50.00 | https://www.newegg.com/p/pl?d=rtx+5060+ti+16gb&N=4131&Order=1 |
| Mac mini M6 16GB/256GB | $899 | $56.19 | https://www.apple.com/shop/buy-mac/mac-mini/m6-chip-12-core-cpu-12-core-gpu-16gb-memory-256gb-storage |
| Mac mini M6 24GB/256GB | $1,099 | $45.79 | https://www.apple.com/shop/buy-mac/mac-mini/m6-chip-12-core-cpu-12-core-gpu-24gb-memory-256gb-storage |
| Used RTX 3090 24GB | $1,799 | $74.96 | https://rigprice.com/gpu/rtx-3090/ |
| GMKtec EVO-X2 128GB/1TB | $3,499.99 (sale; regular $3,999.99) | $27.34 | https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc |

- The used RTX 3090 moved from $1,796 to $1,799 between writing and recording; the script was
  corrected before the voice was recorded.
- ChatGPT Plus: $20 a month. https://learn.chatgpt.com/docs/pricing
- RTX 3090 rated graphics card power 350W. https://www.nvidia.com/en-us/geforce/graphics-cards/compare/
- US average residential electricity 18.16 cents per kWh (EIA).
  https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_5_6_a. Our maths: 0.35kW x
  4 hours a day x 365 x $0.1816 = about $93 a year.

### Not checked

- Used prices move daily; the RigPrice figures are that day's "used price today", not a quote.
- The 0.63GB per billion rule is from one model's file sizes; other models and quant recipes
  differ by a little.
- The 4 hours a day of full load behind the $93 a year is our own assumption, not a measurement.
{% endraw %}

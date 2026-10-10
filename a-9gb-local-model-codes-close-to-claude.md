---
layout: default
title: "Claude Grade Coding On A Cheap 12GB GPU (Local AI)"
permalink: /a-9gb-local-model-codes-close-to-claude/
date: 2026-10-10
---

# Claude Grade Coding On A Cheap 12GB GPU (Local AI)

{% raw %}
Every figure in the video, with where it was published. Checked 2026-10-10.

## The model and its official scores

- Qwen3.8-27B is a 27 billion parameter open model from Alibaba's Qwen team. Native context 262,144 tokens, extensible to 1,000,000.
  Source: Qwen3.8-27B model card, https://huggingface.co/Qwen/Qwen3.8-27B
- From the same card's benchmark table (Qwen3.8-27B vs Opus4.6 Max):
  - SWE-bench Pro: 61.7 vs 53.4 (Qwen ahead by 8.3)
  - LiveCodeBench v6: 90.3 vs 88.8 (Qwen ahead by 1.5)
  - Terminal Bench 2.1 (Terminus): 73.0 vs 78.2 (Claude ahead by 5.2)
- The card's SWE-bench footnote: all models are evaluated with the Claude Code harness at temperature 1.0, top_p 0.95 and a 256K context window, except Opus4.6 Max, which uses its officially reported score.
  Source: https://huggingface.co/Qwen/Qwen3.8-27B
- Claude Opus 4.8 scores 69.2 on SWE-bench Pro (Anthropic system card; also reported by third-party summaries).
  Sources: https://www.anthropic.com/news/claude-opus-4-8, https://vellum.ai/blog/claude-opus-4-8-benchmarks-explained

## The 8.4 GB file

- ISTA-DASLab's GSQ-RCO GGUF builds of Qwen3.8-27B assign a quantization type to every tensor, chosen by per-tensor sensitivity.
- IQ2_XS: 2.50 bits per weight, 8.4 GB, LiveCodeBench v6 76.57.
- BF16 baseline on the same table: 53.8 GB, LiveCodeBench v6 85.71. Difference: 9.14 points.
- IQ3_S: 3.50 bits per weight, 11.8 GB, LiveCodeBench v6 85.71 (the recommended build).
- Unsloth UD-IQ2_S at the same 8.4 GB: LiveCodeBench v6 72.00.
- The optional MTP builds are about 0.35 GB larger (they carry the multi-token prediction head).
  Source: https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF

## Aider

- The official Aider Polyglot leaderboard lists no current Qwen3.8 entry and no matched Claude row for this model.
  Source: https://aider.chat/docs/leaderboards/
- An independent run in a public benchmark repository: Qwen3.8-27B on aider-polyglot, thinking off, 32k slot: pass@1 25.8%, pass@2 68.9%, 225 of 225 tasks, 2 malformed responses, median 12.3 minutes per task. The page has no Claude result.
  Source: https://github.com/ccarokh/AI-Model-Benchmark-Runs/blob/main/use-cases/coding.md

## Speeds reported by owners

- RTX 4060 8 GB: Unsloth IQ4_XS, about 14 GB, roughly 7 GB on the card (26 layers) and the rest in system RAM; 70,000 token context target; about 4.2 to 5 tokens per second, falling as the context fills.
  Source: https://brainwagon.org/blog/2026-08-24-running-the-qwen-3-8-27b-dense-model-on-8gb-vram
- RTX 3060 12 GB: about 10 tok/s with IQ3_XXS; 8 to 9 tok/s with Q4_K_M, falling to 4 or 5 past 30K context (community thread).
  Source: https://www.reddit.com/r/LocalLLM/comments/1wldram/qwen38_27b_what_is_realistic_tokens_per_second/
- RTX 3060 12 GB, patched build with multi-token prediction: almost 30 tok/s on a fixed C++ task at 64K context.
  Source: https://www.reddit.com/r/unsloth/comments/1w0cn86/qwen3827b_30_toks_at_64k_on_one_rtx_3060_12_gb/
- RTX 5060 Ti 16 GB: around 40 to 50 tok/s at 32K context with a 3 bit quant and MTP; another owner a little over 20 tok/s on a similar size quant with a different context and runtime.
  Source: https://www.reddit.com/r/LocalLLM/comments/1wldram/qwen38_27b_what_is_realistic_tokens_per_second/

## Prices, checked 2026-10-10

- Claude Pro $20 a month; Claude Max from $100 a month. https://claude.com/pricing
- Used RTX 3060 12 GB: RigPrice going rate (median ask) $370, 62 active listings; the cheapest screened pick was $340 in the October 10 morning snapshot and $350 later that day. https://rigprice.com/gpu/rtx-3060-12gb/
- GIGABYTE RTX 5060 8 GB, new: $459.99 at Newegg, the lowest new RTX 5060 sorted by price. https://www.newegg.com/p/pl?d=rtx+5060+8gb&N=100007709&Order=1
- RTX 5060 Ti 16 GB, new: $789 in PC Gamer's October 8 price watch; $799.99 lowest new on Newegg on October 10. https://www.pcgamer.com/hardware/graphics-cards/graphics-card-price-watch-deals/, https://www.newegg.com/p/pl?d=rtx+5060+ti+16gb&N=100007709&Order=1

## Our arithmetic

Card price divided by plan price, before power, the rest of the computer and the value of a hosted service:

| card | price | at $20 a month | at $100 a month |
|---|---|---|---|
| GIGABYTE RTX 5060 8 GB | $460 | 23 months | 4.6 months |
| used RTX 3060 12 GB, going ask | $370 | 18.5 months | 3.7 months |
| used RTX 3060 12 GB, screened pick | $340 | 17 months | 3.4 months |
| RTX 5060 Ti 16 GB | $789 | about 40 months | about 8 months |

### Not checked

- The Reddit owner reports (RTX 3060 and RTX 5060 Ti speeds) could not be opened from our side on the day; they are quoted as the script's writer cited them.
- Opus 4.8's 69.2 is taken from summaries of Anthropic's system card; the PDF itself was too large to read here.
{% endraw %}

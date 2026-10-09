---
layout: default
title: "Kimi K3 At Home Costs 240 Months Of Claude Max!"
permalink: /what-a-claude-opus-5-class-ai-costs-to-run-at-home/
date: 2026-10-09
---

# Kimi K3 At Home Costs 240 Months Of Claude Max!

{% raw %}
Every figure on screen, with its primary source, checked on 2026-10-09.

## Model scores (Artificial Analysis)

- Intelligence Index v4.3.2: Claude Opus 5 (xhigh) 50, Kimi K3 (max) 44.
  https://artificialanalysis.ai/models/comparisons/claude-opus-5-xhigh-vs-kimi-k3
- AA-LCR v1.1 (long context recall): Kimi K3 89%, Opus 5 80%. SciCode: Kimi K3 59%, Opus 5 56%.
  Terminal-Bench 4.0: Opus 5 46%, Kimi K3 13%. Same page.
- Output speed, hosted: Opus 5 50 tokens/s, Kimi K3 41 tokens/s. Same page (these move day to day).
- Qwen3.8 Max (0902): 45 on the same Intelligence Index.
  https://artificialanalysis.ai/models/qwen3-8-max
- Qwen's own model card table: Terminal Bench 2.1, Qwen3.8-Max 86.6 vs Claude Opus 4.8 84.6
  (vendor reported, Qwen's harness). https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B

## Kimi K3

- 2.8T total parameters, 104B activated per token, 896 experts (16 routed + 2 shared active).
  https://huggingface.co/moonshotai/Kimi-K3
- Unsloth's 1-bit UD-IQ1_S file: about 594 GB. https://unsloth.ai/docs/models/kimi-k3
- Community IQ1_S conversion: 330.2 GB (330,167,807,328 bytes), HumanEval 94.5% (155/164),
  reported as matching the full model's 94.5%.
  https://huggingface.co/vcruz305/Kimi-K3-GGUF/blob/main/README.md
- Three DGX Spark (GB10) nodes, TP3, SparkInfer patch series: 12.5492 decode tok/s on the
  structured, repeat-heavy K=8/P8 profile; freeform prose 6.5893 tok/s; four-request mix
  9.7937 tok/s. The page says it is not a general chat or prose claim.
  https://github.com/vcruz305/kimi-k3-neuron-tp3-dgxspark-recipe

## Qwen 3.8 Max (Qwen3.8-2.4T-A95B)

- 2.4T total, 95B active per token. https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B
- Unsloth files: UD-Q1_0 397 GB, UD-IQ1_S 508 GB. https://huggingface.co/unsloth/Qwen3.8-2.4T-A95B-GGUF
- Four DGX Spark nodes (121 GB usable each), llama.cpp RPC with native MTP speculative decoding:
  about 8 tok/s prose, about 11 structured; 3.5 tok/s without MTP.
  https://github.com/meinknee/qwen3.8-2.4t-4x-dgx-spark

## Prices (PRICES.md has the full table)

- GIGABYTE AI TOP ATOM (GB10, 128 GB, 4 TB): $7,999.99 at Newegg.
  https://www.newegg.com/gigabyte-atagb10-9000-thin-client/p/N82E16859252047
- Claude Max: $100 (5x) and $200 (20x) a month. https://claude.com/pricing
- GMKtec EVO-X3 (Strix Halo, 128 GB, 2 TB): $3,799.99; 19.5 V / 11.8 A DC input, about 230 W.
  https://www.gmktec.com/products/gmktec-evo-x3-ai-mini-pc-amd-ryzen-ai-max-395
- Mac Studio M5 Ultra from $5,499 (96 GB); "512GB memory option for M5 Ultra coming late
  October", no price. https://www.apple.com/shop/buy-mac/mac-studio
- Tom's Hardware's M5 Ultra review unit, 256 GB and 4 TB: $12,299; tested Qwen 3.8 27B Q4_K_M.
  https://www.tomshardware.com/desktops/mini-pcs/apple-mac-studio-m5-ultra-review
- Mac Studio M5 Ultra maximum power consumption 385 W. https://support.apple.com/en-au/102027
- Used workstation, 2x EPYC 9355, 736 GB DDR5 (768 GB as built, one failed stick), one RTX PRO
  6000: $40,776 asking. https://www.craigslist.org/view/d/chattanooga-ai-workstation-768gb-rtx/pHKHZ7v9LkxAoiUwqWAECc
- New dual EPYC 9654 workstation, 768 GB DDR5: $57,000 Buy It Now. https://www.ebay.com/itm/257376063159
- NVIDIA RTX PRO 6000 Blackwell Workstation Edition, 96 GB, 600 W maximum power: $16,699.99 sold
  by Newegg. https://www.newegg.com/p/N82E16814132106

## Strix Halo

- 128 GB maximum memory on Ryzen AI Max+ 395 systems.
  https://www.amd.com/en/products/processors/desktops/ryzen-ai-halo/ryzen-ai-max-plus-395.html
- A tuned 128 GB Strix Halo runs Qwen 3.8 Flash Next (125B MoE, 6B active) at 15 to 20 tok/s decode.
  https://sleepingrobots.com/dreams/qwen38-flash-next-strix-halo/

## EPYC speed

- Dual EPYC 7282, DeepSeek R1 Distill Llama 70B (built on Llama 3.3 70B), Q4_K_M: 2.88 tok/s
  (tg128); Llama 3.3 70B Instruct Q4_K_M on the same machine: 2.83 tok/s.
  https://ahelpme.com/ai/llamacpp-ai/llama-bench-the-deepseek-r1-distill-llama-70b-and-dual-amd-epyc-7282/
- 2x EPYC 9175F, Llama 3.1 70B F16: 4.30 tok/s (tg128). https://github.com/ggml-org/llama.cpp/discussions/11733

## Electricity

- US residential average, July 2026: 18.31 cents per kWh (EIA Electric Power Monthly, table ES1.A).
  https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_es1a
- Arithmetic at that rate over 30 days of 24 hours (720 h): 100 W = $13.18; 385 W = $50.75;
  2 x 230 W = $60.64; 3,000 W = $395.50.

## Arithmetic on screen

- 3 x $7,999.99 = $23,999.97; 4 x $7,999.99 = $31,999.96; 5 x $16,699.99 = $83,499.95;
  6 x $16,699.99 = $100,199.94; 2 x $3,799.99 = $7,599.98.
- Months of Max: $23,999.97 / $100 = 240, / $200 = 120; $31,999.96 / $100 = 320, / $200 = 160;
  $7,599.98 / $100 = 76, / $200 = 38; $40,776 / $100 = 408, / $200 = 204; $57,000 / $100 = 570,
  / $200 = 285; $83,499.95 / $100 = 835, / $200 = 417.5.
- Hardware dollars per output token per second: $23,999.97 / 12.5 = $1,920; $31,999.96 / 8 = $4,000.
- $32,000 / $200 = 160 months = 13 years and 4 months.

## Not checked

- The Qwen recipe's "sixty four thousand token context" is not stated on its README.
- Newegg's own $16,699.99 offer for the RTX PRO 6000 sold out later on 2026-10-09; the same
  page then showed a marketplace seller at $26,900.
{% endraw %}

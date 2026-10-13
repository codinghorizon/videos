---
layout: default
title: "The 8GB GPU Trap For Real Time Voice AI (RTX 5060)"
permalink: /the-gpu-you-need-for-real-time-voice-ai/
date: 2026-10-13
---

# The 8GB GPU Trap For Real Time Voice AI (RTX 5060)

{% raw %}
Every figure the narration says and the shots put on screen, with its primary source, checked 2026-10-13.

## Moshi (Kyutai)

- **8GB is not possible, 12GB is possible following issue #54.** Moshi FAQ: "For a 12GB GPU, this is possible
  following instructions in issue #54. For 8GB GPU, this is not possible at the moment."
  https://github.com/kyutai-labs/moshi/blob/main/FAQ.md
- **24GB for the PyTorch version.** README: "At the moment, we do not support quantization for the PyTorch version,
  so you will need a GPU with a significant amount of memory (24GB)." The server example loads
  `kyutai/moshika-pytorch-bf16` (unquantized). https://github.com/kyutai-labs/moshi
- **7B parameters, 160ms theoretical, 200ms practical on an L4.** README: "a large, 7B-parameter Temporal Transformer
  ... Moshi achieves a theoretical latency of 160ms ... with a practical overall latency as low as 200ms on an L4 GPU."
  Paper abstract: "a theoretical latency of 160ms, 200ms in practice". https://arxiv.org/abs/2410.00037
- **MLX path for Mac.** README: "MLX: for on-device inference on iPhone and Mac." Tested on a MacBook Pro M3.

## Issue #54: an RTX 3060 12GB

https://github.com/kyutai-labs/moshi/issues/54
- Opened by the owner of an RTX 3060 (12288MiB) running the Rust q8 config; CUDA out of memory.
- Maintainer (LaurentMazare): "The weights are ~8.17GB but when in q8 mode we pre-allocate a kv-cache that is for
  4096 steps (~5 mins of conversation) in f32 ... the kv-cache is ~4GB, and activations + the mimi parts also have to
  be stored ... So overall we're a bit above 12GB here." Suggested lowering the cache steps (~1000).
- Owner: "Thanks! It did work, but the speed was pretty low. I trust 3060 isn't enough to run this."

## PersonaPlex (NVIDIA)

- Based on Moshi: "PersonaPlex is based on the Moshi architecture and weights." https://github.com/NVIDIA/personaplex
- 7B: the released checkpoint is `nvidia/personaplex-7b-v1`.
- Released checkpoint, Full Duplex Bench (preprint Table 6): smooth turn taking latency 0.170s, user interruption
  latency 0.240s. https://research.nvidia.com/labs/adlr/files/personaplex/personaplex_preprint.pdf ,
  https://arxiv.org/abs/2602.06053

## Modal chained pipeline

https://modal.com/blog/low-latency-voice-bot
- Parakeet (parakeet-tdt-0.6b-v3) speech recognition, Qwen3 4B Instruct on vLLM, Kokoro (82M) speech generation.
- "when the client and the Modal containers are near each other, our app can hit a median voice-to-voice latency of
  one second". The test client was in the SF Bay Area.

## Prices (PRICES.md has every row)

| item | price | source |
|---|---|---|
| RTX 5060 8GB, cheapest new | $459.99 | https://componentprices.com/gpu |
| RTX 3060 12GB used, cheapest screened / going rate | $350 / $370 | https://rigprice.com/gpu/rtx-3060-12gb/ |
| RTX 3060 12GB new, cheapest | $459.99 | Newegg (GIGABYTE WINDFORCE OC) |
| RTX 5060 Ti 16GB new | $799.99 (from $779.99) | https://www.newegg.com/p/N82E16814137954 |
| RTX 3090 24GB used, going rate | $1,600 (79 listings) | https://rigprice.com/gpu/rtx-3090/ |
| Mac Studio M5 Max, 36GB, 512GB | $2,499 | https://www.apple.com/mac-studio/ |
| GMKtec EVO X2 128GB + 1TB | $3,499.99 (sale; variant shown sold out on the day) | https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc?variant=48746069262490 |
| ChatGPT Plus | $20/month, includes voice, limits apply | https://help.openai.com/en/articles/6950777-what-is-chatgpt-plus |

## Our arithmetic

- Two years (24 months), before electricity: $350 -> $14.58/mo; $1,600 -> $66.67/mo; $2,500 -> $104.17/mo;
  $3,500 -> $145.83/mo. ChatGPT Plus over two years: $480.
- Months of $20 payments to reach each price: $1,600 = 80 months (6.7 years); $2,500 = 125 (10.4 years);
  $3,500 = 175 (14.6 years).

## Corrected in the script before recording

The supplied script said 3 / 5 / 12 years (it divided by $480 two-year blocks), "very low" for the owner's
"pretty low", "the maintainer's own thread" for the owner's thread, and dropped the client from Modal's "client and
containers near each other". Each was corrected to its source before the take (CUT.md header).

### Not checked

- No source gives a latency for Moshi or PersonaPlex on an RTX 3090, an RTX 5060 Ti, a Mac Studio M5 Max or Strix
  Halo; the video says so and shows none.
- The EVO X2 128GB was listed at $3,499.99 but marked sold out on 2026-10-13.
- ChatGPT Plus's US $20 comes from OpenAI's help article; the pricing page served this machine a UK price.
{% endraw %}

---
layout: default
title: "Qwen 125B On Strix Halo Runs, But At What Speed?"
permalink: /125b-qwen-strix-halo/
date: 2026-10-02
---

# Qwen 125B On Strix Halo Runs, But At What Speed?

{% raw %}
Checked 2 October 2026. Benchmark results are the publisher's own evaluations or one
person's published measurements on their own machine; none is an independent reproduction.

## The model: Qwen3.8 Flash Next

- [Qwen3.8-Flash-Next model card](https://huggingface.co/Qwen/Qwen3.8-Flash-Next):
  "Number of Parameters: 125B with 6B activated, plus 51B n-gram embedding and 4B MTP".
  Mixture of experts: "Number of Experts: 512", "Number of Activated Experts: 10 Routed + 1
  Shared". The card's Safetensors panel lists the model size as 180B parameters, which is
  125B + 51B + 4B. Context: 262,144 tokens natively, extensible to 1,000,000.
- Hosted version, same card: "Qwen3.8-Flash is the official version based on
  Qwen3.8-Flash-Next with more production features, e.g., 1M context length by default,
  official built-in tools."
- Publisher coding table, same card (higher is better):

  | Benchmark | Flash Next | Qwen3.8 27B | DeepSeek V4 Flash 0731 |
  | --- | ---: | ---: | ---: |
  | DeepSWE 1.1 | 58.7 | 42.2 | 54.4 |
  | SWE-bench Pro | 62.5 | 61.7 | 56.0 |
  | NL2Repo-Bench | 48.1 | 42.3 | 54.2 |

  58.7 minus 42.2 is the 16.5 point DeepSWE lead. On NL2Repo-Bench the leader is DeepSeek V4
  Flash 0731 at 54.2; Qwen3.8 27B scores 42.3, below Flash Next's 48.1.
- [On the Design of Qwen3.8-Next Architecture](https://arxiv.org/abs/2608.30320), submitted
  31 August 2026: "a sparse mixture-of-experts model with 125B parameters, 6B activated per
  token, and additional 51B parameters of n-gram embedding tables held off the
  accelerator", with "a single n-gram embedding layer whose tables are prefetched from host
  memory", and Qwen Sparse Attention scoring context with "a compressed lightweight indexer".

## Quantized downloads

- [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF)
  lists the quantizations by size, including UD-IQ4_XS at 93.7 GB and UD-Q4_K_XL at 111 GB,
  and separate MTP draft files (Q8_0 2.79 GB, BF16 7.77 GB).
- Four bit arithmetic: 125 billion parameters × 4 bits ÷ 8 bits per byte = 62.5 GB. This is a
  floor on the core weights alone, not a file size.

## The machine: AMD Strix Halo

- [AMD Ryzen AI Halo developer platform](https://www.amd.com/en/products/processors/desktops/ryzen/ryzen-ai-halo/ryzen-ai-max-plus-395.html):
  AMD Ryzen AI Max+ 395 (16 cores, 32 threads, Zen 5); Radeon 8060S integrated graphics, 40
  CUs, RDNA 3.5; memory LPDDR5x, 128GB, 8000MT/s; memory bandwidth 256GB/s; TDP 120W;
  150 × 150 × 45.4 mm.

## Measured speed on Strix Halo

- [Qwen3.8-Flash-Next on Strix Halo, Vulkan only](https://github.com/ggml-org/llama.cpp/discussions/28512),
  llama.cpp discussion #28512. A Bosgame M5 (Ryzen AI Max+ 395, Radeon 8060S, 128 GB) on
  Vulkan with RADV, the stock UD-IQ4_XS quant and a Q8_0 draft head. Single stream, greedy.
  Ten real agent conversations replayed: median decode 25 → 33 tokens per second after
  tuning. Time to first token on a fresh 18K prompt 67 s → 44 s. Tuned decode at 8K: short
  code 58.1, new code 41.6 (30.7 before tuning), prose 30.1, file rewrite 55.4 (63.2 with
  n-max 6); at 32K new code 37.8, file rewrite 48.5 (55.2 with n-max 6). The biggest gain:
  "Upstream sizes the expert-count shader for 256 experts, and this model has 512 … Lifting
  the limit gave +19 % prefill." Long drafts: "n-max 6 is the setting for file rewrites …
  but it halves prose".
- [vulkan: raise the hoisted row-id limit for mul_mat_id from 256 to 512 experts](https://github.com/ggml-org/llama.cpp/pull/28501),
  llama.cpp pull request #28501, merged: prefill on Qwen3.8-Flash-Next Q5_K from 426 to 507
  tokens per second for an 8K prompt (+19%), token generation unchanged.
- [Qwen3.8-Flash-Next on Strix Halo (gfx1151): 17 → 47 tok/s](https://github.com/ggml-org/llama.cpp/discussions/27950),
  llama.cpp discussion #27950, ROCm 7.1, UD-IQ4_XS, single stream, greedy. No speculation →
  full stack: file rewrite at 8K 16.8 → 47.1; new code at 8K 16.8 → 31.7; file rewrite at 24K
  about 15 → 28.6; new code at 24K about 15 → 25.4. The QSA indexer's top-k "falls back to
  CPU past ne=1024"; fixing it gave "+38–53% end-to-end at 24k". Native MTP speculative
  decoding.

## Other hardware and hosted options

- [NVIDIA GeForce RTX 5090](https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/):
  32 GB of GDDR7. 93.7 GB of weights plus a 2.79 GB draft head is about 96.5 GB, which does
  not fit in 32 GB without offloading.
- [DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731): NL2Repo
  54.2 on its own card.
- [DeepSeek-V4.1-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash): a separate,
  later release, a multimodal mixture of experts with a 552B backbone and contexts up to one
  million tokens. Qwen's table compares V4 Flash 0731, not V4.1.

## Not checked, or not as stated

- The narration says Qwen3.8 27B leads NL2Repo-Bench 54.2 to 48.1, and later refers to "its
  NL2Repo lead". Qwen's own card gives Qwen3.8 27B 42.3 on NL2Repo-Bench, below Flash Next's
  48.1; the 54.2 belongs to DeepSeek V4 Flash 0731.
- "30 for new code at 8K context" matches the Vulkan author's pre-tuning figure (30.7); after
  tuning the same row reads 41.6.
- How much of the 128 GB a given Strix Halo system lets the graphics side use depends on its
  firmware and settings; no single figure is claimed.
- Benchmarks are the publisher's own, and DeepSWE is reported as a model plus agent harness
  score.
{% endraw %}

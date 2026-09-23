---
layout: default
title: "Qwen 3.8 flash passed 125 tok/s with this speed trick"
permalink: /qwen-3-8-flash-125-tokens/
date: 2026-09-23
---

# Qwen 3.8 flash passed 125 tok/s with this speed trick

{% raw %}
Every figure, name, version and benchmark the finished picture puts on screen, chased to a
primary source. Checked 22 September 2026.

## The model

| Claim | Value | Source |
| --- | --- | --- |
| Total parameters | 125B | [Qwen/Qwen3.8-Flash-Next model card](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) — "Number of Parameters: 125B with 6B activated, plus 51B n-gram embedding and 4B MTP" |
| Active per token | 6B | same line |
| The separate lookup table | 51B n-gram embedding table, 128 shards, held in BF16 | same card; shard count from [primitive-ai/Qwen3.8-Flash-Next-NVFP4](https://huggingface.co/primitive-ai/Qwen3.8-Flash-Next-NVFP4) |
| Experts | 512 total, 11 activated per token, 48 layers | Qwen model card |
| Architecture | Gated DeltaNet plus Qwen Sparse Attention, mixture of experts | Qwen model card |
| Context | 262,144 native, extensible to 1,000,000 | Qwen model card |
| MTP | "MTP: 1 layer, trained with multi-steps" | Qwen model card |
| Release date | 26 August 2026 | [BenchLM comparison](https://benchlm.ai/compare/deepseek-v4-flash-0731-vs-qwen3-8-flash-next), specification table |
| A hosted flash service exists beside the weights | "the official Qwen API service is provided by Qwen Cloud. In particular, Qwen3.8-Flash is the official version based on Qwen3.8-Flash-Next" | Qwen model card, opening callout |

The script's "about six billion active per token" and "a separate lookup table adds
capacity too, so the active count isn't the download size" are both exactly what the card
says. The card's own model size badge reads 180B params, which is the 125B plus the 51B
table plus the 4B MTP head, and is why the download is far larger than 125B implies.

## The benchmark figures the video states

| Benchmark | Qwen3.8 Flash Next | Qwen3.8 27B | DeepSeek V4 Flash 0731 | Source |
| --- | --- | --- | --- | --- |
| SWE bench Pro | 62.5 | 61.7 | 52.6 | [Flash Next card](https://huggingface.co/Qwen/Qwen3.8-Flash-Next), [27B card](https://huggingface.co/Qwen/Qwen3.8-27B), [BenchLM](https://benchlm.ai/compare/deepseek-v4-flash-0731-vs-qwen3-8-flash-next) |
| DeepSWE 1.1 | 58.7 | 42.2 | 54.4 | Flash Next card, 27B card, BenchLM |
| NL2Repo (repository generation) | 48.1 | not published | 54.2 | [BenchLM](https://benchlm.ai/compare/deepseek-v4-flash-0731-vs-qwen3-8-flash-next) |

- The 27B's two scores are both stated on its own card as measured "using the Claude Code
  harness", which is why the video says "qwen's published" results rather than presenting
  them as its own measurement.
- 58.7 minus 42.2 is 16.5, which is the gap the script names.
- NL2Repo is the "published repository generation comparison" the script points at, and it
  is the one row in that set where DeepSeek V4 Flash leads. The video says so.

## DeepSeek, for the comparison the video keeps open

| Claim | Value | Source |
| --- | --- | --- |
| V4 Flash 0731 release | 31 July 2026, 284B parameters | [DeepSeek V4 Flash official release](https://huggingface.co/blog/ResterChed/deepseek-v4-flash-official-release), [BenchLM specification table](https://benchlm.ai/compare/deepseek-v4-flash-0731-vs-qwen3-8-flash-next) |
| V4 Flash documented context | 1M | BenchLM specification table |
| V4.1 Flash release | 10 September 2026, 552B parameters | [V4.1 Flash against V4 Flash](https://regolo.ai/deepseek-v4-1-flash-vs-v4-flash-which-open-weight-model-should-your-company-run/) |
| V4.1 Flash DeepSWE 1.1 | 74.2 | same |
| V4.1 Flash native context | 1M | same |

**Worth stating plainly, because the video's own argument rests on it.** V4.1 Flash scores
74.2 on DeepSWE 1.1 against Flash Next's 58.7. The narration never claims Flash Next is the
best local coding model; it says the older chart does not settle a whole repository build,
and that another local model is worth keeping. The picture is built to agree with that and
never draws Flash Next as an outright winner.

## Installing it

| Claim | Value | Source |
| --- | --- | --- |
| Unsloth Desktop runs on macOS, Windows and Linux | yes | [Unsloth: Qwen3.8 Flash Next, how to run locally](https://unsloth.ai/docs/models/qwen3.8-next) |
| The GGUF release | `unsloth/Qwen3.8-Flash-Next-GGUF` | [the repository](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) |
| Quants and sizes | UD-IQ1_S 72.5 GB · UD-IQ1_M 74.5 GB · UD-Q2_K_XL 78.9 GB · UD-IQ3_XXS 82 GB · UD-Q3_K_XL 90 GB · UD-IQ4_XS 93.7 GB · UD-Q4_K_XL 111.3 GB · UD-Q5_K_XL 158 GB · UD-Q6_K_XL 169 GB · Q8_0 192 GB · BF16 354 GB | Unsloth docs and the GGUF repository's hardware compatibility table |
| File size is not the whole requirement | "You will need at least 75 GB of RAM or unified memory to run the model", and 1 to 2 GB extra headroom for MTP | Unsloth docs |
| Recommended generation settings | thinking: temperature 1.0, top-p 0.95, top-k 20 · instruct: temperature 0.7, top-p 0.80, top-k 20 · context up to 262,144 | Unsloth docs |
| 1 bit is 79% smaller than BF16 and retains a top-1 accuracy of 80% | stated | Unsloth docs |

## MTP, and what switching it on does

| Claim | Value | Source |
| --- | --- | --- |
| Unsloth configures speculative decoding automatically | "Unsloth Studio automatically sets the ideal MTP settings optimized for your specific hardware"; MTP enabled by default in Unsloth Desktop | [Unsloth MTP guide](https://unsloth.ai/docs/models/mtp) |
| The advanced settings expose it | MTP / Ngram speculative decoding and the number of draft tokens, in the right sidebar | Unsloth MTP guide |
| Do not start at the maximum draft length | "The best starting point is `--spec-draft-n-max 2`, however, do not assume 2 is optimal … Try any value from 1 through 6" | Unsloth MTP guide |
| What Unsloth measures for this model | 1.3 to 1.7x faster, "170 tokens/s on 1x RTX 6000 PRO GPU compared to the 100 token baseline" | [Unsloth docs](https://unsloth.ai/docs/models/qwen3.8-next) |
| A draft mechanism proposes, the main model verifies | that is what multi token prediction is; the model ships an MTP layer for it | Qwen model card, Unsloth MTP guide |

## The 142 token recipe

The page the narration names is
[primitive-ai/Qwen3.8-Flash-Next-mixed-NVFP4-FP8](https://huggingface.co/primitive-ai/Qwen3.8-Flash-Next-mixed-NVFP4-FP8),
and its own formats line reads **NVFP4 + FP8 + BF16**, which is exactly the mix the script
describes. primitive publishes a plain
[NVFP4 build](https://huggingface.co/primitive-ai/Qwen3.8-Flash-Next-NVFP4) beside it, and
that one is NVFP4 experts with a BF16 tail and no FP8 at all; both report the same
speculative comparison.

| Claim | Value |
| --- | --- |
| Without speculation | 91.2 tokens per second |
| With MTP at three speculative tokens | 142.6 tokens per second, reported as +56% |
| The speculative configuration | `{"method":"mtp","num_speculative_tokens":3}` |
| The docker image | `vllm/vllm-openai:qwen38-flash-next` |
| The launch command's own flags | `--distributed-executor-backend mp`, `--gpu-memory-utilization 0.92`, `--max-model-len 32768 --max-num-seqs 36`, with `VLLM_PLE_CPU_OFFLOAD=1`, `VLLM_PLE_OFFLOAD_READY_TIMEOUT=1800` and `VLLM_GDN_DECODE_KERNEL=triton` |
| The startup overlays | `connector_mrv2.py`, which fixes a startup race, and `worker_image_disk.py` for disk backed table offloading |
| The hardware | one RTX PRO 6000 Blackwell, 96 GB, with about 100 GB of host RAM |
| How it was measured | single stream, real prompts, thinking enabled, output tokens over wall time, prefix cache free, distinct seeds per run |
| What is quantised to what | routed experts, 120.8B, NVFP4 group 16 · QSA attention, 12 layers, FP8 E4M3 per channel · GDN linear attention, 36 layers, FP8 E4M3 per channel · the n gram table and everything else BF16 |
| The compressed lookup table recipe | a separate [PLE-quant repository](https://huggingface.co/primitive-ai/Qwen3.8-Flash-Next-PLE-quant): FP8 per row 49 GB, INT4 group 16 32 GB, NVFP4 style e2m1 group 16 28.8 GB, against about 95 GB |

142.6 divided by 91.2 is 1.564, so "about 56 percent faster" is right.

**One figure on that page that is NOT the one the video states.** The card's own header
badges read `84.4 tok/s @ 1` and `526 tok/s @ 32`, which are a different measurement from
the 91.2 against 142.6 in its body: a different prompt set at two concurrencies rather
than the speculation on and off comparison. The video quotes the body's pair and draws
only that pair, and neither badge figure appears anywhere on screen.

## Arithmetic the video states

- "At 125 tokens per second, a thousand generated tokens takes eight seconds." 1000 ÷ 125 = 8.
- "142.6 tokens per second … faster than most people can read." Adult silent reading runs
  about 200 to 300 words a minute, which is roughly 4 to 7 tokens a second.
- 58.7 − 42.2 = 16.5.
- 142.6 ÷ 91.2 = 1.564.

## Not checked

- **"The july release of deepseek V4 flash"** is dated 31 July 2026 by secondary coverage
  and by BenchLM's specification table rather than by a DeepSeek page reachable today.
- **"Qwen also sells a hosted flash service."** The model card names Qwen Cloud and
  Qwen3.8-Flash as the hosted version; the commercial terms of that service were not chased.
- **Reading speed.** The comparison to reading speed is a commonplace rather than a figure
  taken from a study, and nothing on screen states a words per minute number.
- **Unsloth's own 170 tokens/s against a 100 token baseline** is a different machine and a
  different engine from primitive's 91.2 and 142.6. The video never mixes the two, and only
  primitive's pair is drawn.
{% endraw %}

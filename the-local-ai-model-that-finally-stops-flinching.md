---
layout: default
title: "The Local AI Model That Finally Stops Flinching"
permalink: /the-local-ai-model-that-finally-stops-flinching/
date: 2026-09-09
---

# The Local AI Model That Finally Stops Flinching

{% raw %}
Every figure, benchmark, quantisation size and architecture claim the video puts on
screen, chased to a primary source. Checked September 2026.

## Abliteration, what it is

Abliteration edits a refusal direction out of a model's weights rather than steering the
model at inference time. Maxime Labonne's write up describes computing a refusal direction
from hidden states and orthogonalising it out of the residual stream, which changes the
released file rather than the prompt.

- Maxime Labonne, "Uncensor any LLM with abliteration": https://huggingface.co/blog/mlabonne/abliteration
- mlabonne/gemma-3-27b-it-abliterated model card: https://huggingface.co/mlabonne/gemma-3-27b-it-abliterated

## Llama 3.3 70B

Meta's own model card, benchmark tables:

| Benchmark | Reported |
|---|---|
| MMLU (0-shot, CoT) | 86.0 |
| IFEval | 92.1 |
| HumanEval (pass@1) | 88.4 |
| MATH (0-shot, CoT) | 77.0 |

- https://huggingface.co/meta-llama/Llama-3.3-70B-Instruct

Abliterated GGUF sizes, bartowski's quantisations of huihui-ai's abliterated build:

| Quant | Size |
|---|---|
| Q4_K_M | 42.52 GB |
| Q5_K_M | 49.95 GB |
| Q6_K | 57.89 GB |

- https://huggingface.co/bartowski/Llama-3.3-70B-Instruct-abliterated-GGUF
- Base abliterated model: https://huggingface.co/huihui-ai/Llama-3.3-70B-Instruct-abliterated

mradermacher's separate conversion of the same model lists 42.6 / 50.0 / 58.0 GB, so the
figures are stable to within about a tenth of a gigabyte across repackagers.

- https://huggingface.co/mradermacher/Llama-3.3-70B-Instruct-abliterated-GGUF

## Qwen 2.5 32B

Qwen2.5 Technical Report, Table 7, instruction tuned results for Qwen2.5-32B-Instruct:

| Benchmark | Reported |
|---|---|
| MMLU-Pro | 69.0 |
| MATH | 83.1 |
| HumanEval | 88.4 |
| LiveCodeBench | 51.2 |
| Arena-Hard | 74.5 |

- https://arxiv.org/html/2412.15115v2 (Qwen2.5 Technical Report, Qwen Team)
- Model card: https://huggingface.co/Qwen/Qwen2.5-32B-Instruct

Abliterated GGUF sizes, tensorblock's quantisations of huihui-ai's abliterated build:

| Quant | Size |
|---|---|
| Q4_K_S | 17.494 GB |
| Q4_K_M | 18.488 GB |
| Q5_K_S | 21.084 GB |
| Q5_K_M | 21.665 GB |

- https://huggingface.co/tensorblock/Qwen2.5-32B-Instruct-abliterated-GGUF

Repackagers disagree more here than they do on Llama. mradermacher's conversion of the same
abliterated model lists Q4_K_M at 20.0 GB and Q5_K_M at 23.4 GB. The video uses the
tensorblock figures, which are the smaller of the two sets.

- https://huggingface.co/mradermacher/Qwen2.5-32B-Instruct-abliterated-GGUF

## Mistral Small 3.2 24B

Mistral's own model card, 3.2 against 3.1:

| Benchmark | Small 3.1 | Small 3.2 |
|---|---|---|
| Arena Hard v2 | 19.56% | 43.1% |
| HumanEval Plus (pass@5) | 88.99% | 92.90% |
| Internal instruction following accuracy | 82.75% | 84.78% |

The card also states Small 3.2 "is better at following precise instructions" and that its
"function calling template is more robust".

- https://huggingface.co/mistralai/Mistral-Small-3.2-24B-Instruct-2506

Abliterated Q4_K_M GGUF is about 14.3 to 14.4 GB depending on the repackager. mradermacher's
conversion of huihui-ai's abliterated build lists Q4_K_M at 14.4 GB, with 16.9 GB for
Q5_K_M and 19.4 GB for Q6_K.

- https://huggingface.co/huihui-ai/Huihui-Mistral-Small-3.2-24B-Instruct-2506-abliterated
- https://huggingface.co/mradermacher/Huihui-Mistral-Small-3.2-24B-Instruct-2506-abliterated-llamacppfixed-GGUF

## Gemma 3 27B

Google's own model card:

| Benchmark | Reported |
|---|---|
| MMLU (5-shot) | 78.6 |
| MBPP (3-shot) | 65.6 |
| MMMU (pt) | 56.1 |

Context window 128K tokens for the 4B, 12B and 27B sizes. Multimodal, accepting image and
text input. Multilingual support in over 140 languages.

- https://huggingface.co/google/gemma-3-27b-it

Abliteration. Maxime Labonne's model card states Gemma 3 was much more resilient to
abliteration than Qwen 2.5, and that the release computes a refusal direction per layer
independently, with a refusal weight of 1.5, rather than applying one direction globally.

- https://huggingface.co/mlabonne/gemma-3-27b-it-abliterated

Abliterated GGUF sizes, published in the same author's GGUF repo:

| Quant | Size |
|---|---|
| q3_k_m | 13.4 GB |
| q4_k_m | 16.5 GB |
| q5_k_m | 19.3 GB |
| q6_k | 22.2 GB |

- https://huggingface.co/mlabonne/gemma-3-27b-it-abliterated-GGUF

## Qwen 3.8 27B

Qwen's own model card:

| Benchmark | Reported |
|---|---|
| Terminal Bench 2.1 | 73.0 |
| SWE-bench Pro | 61.7 |
| QwenSWEBench | 79.0 |
| LiveCodeBench v6 | 90.3 |

Context window 262,144 tokens natively, extensible to 1,000,000. A native vision language
model that understands images and video. Thinking mode on by default and disableable per
request, with reasoning depth tunable. Hybrid architecture of Gated DeltaNet linear
attention layers interleaved with full attention layers.

- https://huggingface.co/Qwen/Qwen3.8-27B

### Not chased to a primary source

Two figures the narration states could not be confirmed, so **neither appears on screen**.

**The abliterated MTPLX quantisation sizes.** The script gives 30.4 GB at 8 bit, 23.7 GB at
6 bit and 16.9 GB at 4 bit. No published abliterated build lists those. MTPLX is a real
project, a native MTP speculative decoding runtime for MLX on Apple Silicon, but it
publishes no abliterated build: its Qwen 3.8 27B releases are Optimized Speed, Bare Speed
and Optimized Quality, none of them abliterated. The nearest real abliterated MLX build is
PocketAiHub's, which lists 27.50 GB at 8 bit, 21.24 GB at 6 bit and 14.98 GB at 4 bit.

- https://github.com/youssofal/MTPLX
- https://huggingface.co/Youssofal/Qwen3.8-27B-MTPLX-Optimized-Speed
- https://huggingface.co/PocketAiHub/Qwen3.8-27B-Abliterated-MLX

**The M3 Ultra Mac Studio speed.** The script gives roughly 46 tokens per second for the
6 bit build on a 24,000 token agentic prompt, and over 50 for the 4 bit build. No source
reports either. PocketAiHub's abliterated MLX card measures on an Apple M5 Max with 128 GB
of unified memory at a 4,105 token prompt, giving 33.2 tokens per second at 4 bit and 24.7
at 6 bit, and calls these single local runs rather than guarantees. MTPLX reports relative
speedups, 1.6x on a 16 GB M4 Mac mini and 2.24x on an M5 Max, and no absolute figure on an
M3 Ultra.

The claim that a 27B class model runs at usable interactive speed on Apple Silicon is well
supported. The specific numbers are not, so the shots covering those two lines draw the
mechanism and print no figure.
{% endraw %}

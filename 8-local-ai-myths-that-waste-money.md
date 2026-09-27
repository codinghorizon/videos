---
layout: default
title: "8 local AI myths that make you buy the wrong upgrade"
permalink: /8-local-ai-myths-that-waste-money/
date: 2026-09-27
---

# 8 local AI myths that make you buy the wrong upgrade

{% raw %}
Every source below was accessed on 2026-09-27. Quoted text is copied from the publisher's own page. Where the video rounds a figure or paraphrases a sentence, the note under the quote says so.

## Intro

### An RTX 3060 comes with 12GB

Source: NVIDIA, GeForce RTX 3060 Family, https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3060-3060ti/

Specs table, RTX 3060 column:

> Memory Size · 12 GB / 8 GB
> Memory Type · GDDR6

Verdict: confirmed. NVIDIA lists the RTX 3060 in both a 12 GB and an 8 GB configuration, so the 12GB card named in the video is one of two official memory sizes.

## Chapter 1 · A bigger model is always a better assistant

### Qwen 3.5 has a nine billion parameter model with image understanding and optional thinking

Source: Qwen, Qwen3.5-9B model card, https://huggingface.co/Qwen/Qwen3.5-9B

> Type: Causal Language Model with Vision Encoder
> Number of Parameters: 9B

> **Unified Vision-Language Foundation**: Early fusion training on multimodal tokens achieves cross-generational parity with Qwen3 and outperforms Qwen3-VL models across reasoning, coding, agents, and visual understanding benchmarks.

> Qwen3.5 models operate in thinking mode by default, generating thinking content signified by `<think>\n...</think>\n\n` before producing the final responses. To disable thinking content and obtain direct response, refer to the examples here.

Verdict: confirmed. Thinking is on by default and can be switched off per request (the card's examples pass `"enable_thinking": False`), which is what "optional" means here. The language model is listed at 9B; the Hugging Face file summary shows 10B parameters in total because the vision encoder is included.

### Ministral 3 has an eight billion parameter instruct model built for compact assistants, with vision

Source: Mistral AI, Ministral 3 8B Instruct 2512 model card, https://huggingface.co/mistralai/Ministral-3-8B-Instruct-2512

> A balanced model in the Ministral 3 family, **Ministral 3 8B** is a powerful, efficient tiny language model with vision capabilities.

> This model is the instruct post-trained version in **FP8**, fine-tuned for instruction tasks, making it ideal for chat and instruction based use cases.

> The Ministral 3 family is designed for edge deployment, capable of running on a wide range of hardware. Ministral 3 8B can even be deployed locally, capable of fitting in 12GB of VRAM in FP8, and less if further quantized.

> **Vision**: Enables the model to analyze images and provide insights based on visual content, in addition to text.

Use cases listed on the card include:

> Chat interfaces in constrained environments
> Local daily-driver AI assistant
> Image/document description and understanding

Verdict: confirmed. "Compact" is the video's word for Mistral's "tiny language model" and "edge deployment". The card splits the model into an 8.4B language model and a 0.4B vision encoder.

### Qwen 3.8 has a 27 billion parameter model, and its publisher emphasizes stronger planning and complex tasks

Source: Qwen, Qwen3.8-27B model card, https://huggingface.co/Qwen/Qwen3.8-27B

> Number of Parameters: 27B

> Built on the architectural foundation of Qwen3.5, Qwen3.8 delivers substantial gains across coding, professional work, research, and long-horizon agentic tasks. Qwen3.8-27B brings these advances to a compact, deployment-friendly dense model: a native vision-language model that understands images and videos, with flexible thinking control, designed to carry complex, multi-step tasks through to completion with greater reliability.

> **Agent Execution**: Stronger autonomous planning and better handling of environment feedback, leading to more reliable end-to-end task completion.

Verdict: confirmed. Note that Qwen itself calls the 27B model "compact"; the video uses "compact" only for the 8B and 9B options, as a relative comparison.

## Chapter 2 · Active parameters tell you how much memory to buy

### Gemma 4 has a 26 billion parameter model with four billion active parameters, and all 26 billion are loaded

Source: Google AI for Developers, Gemma 4 model overview, https://ai.google.dev/gemma/docs/core

> **The MoE Architecture (26B A4B):** The 26B is a Mixture of Experts model. While it only activates 4 billion parameters per token during generation, **all 26 billion parameters** must be loaded into memory to maintain fast routing and inference speeds. This is why its baseline memory requirement is much closer to a dense 26B model than a 4B model.

Memory table on the same page:

> Gemma 4 26B A4B · BF16 (16-bit) 57.7 GB · SFP8 (8-bit) 28.8 GB · Q4_0 (4-bit) 14.4 GB

Source: Google, gemma-4-26B-A4B-it model card, https://huggingface.co/google/gemma-4-26B-A4B-it

> Total Parameters · 25.2B
> Active Parameters · 3.8B
> Expert Count · 8 active / 128 total and 1 shared

> The "A" in 26B A4B stands for "active parameters" in contrast to the total number of parameters the model contains. By only activating a 4B subset of parameters during inference, the Mixture-of-Experts model runs much faster than its 26B total might suggest.

Verdict: confirmed. The video's sentence matches Google's documentation. The model card gives the exact counts as 25.2B total and 3.8B active; "26 billion" and "four billion" are the rounded figures in the model's name and in Google's own prose.

### System RAM and graphics memory are separate pools, and splitting work across them is not the same speed

Source: Ollama FAQ, https://docs.ollama.com/faq

> * `100% GPU` means the model was loaded entirely into the GPU
> * `100% CPU` means the model was loaded entirely in system memory
> * `48%/52% CPU/GPU` means the model was loaded partially onto both the GPU and into system memory

Source: Ollama, Context length, https://docs.ollama.com/context-length

> For best performance, use the maximum context length for a model, and avoid offloading the model to CPU. Verify the split under `PROCESSOR` using `ollama ps`.

Verdict: confirmed. Ollama describes GPU memory and system memory as two places a model can be loaded, and advises against offloading to the CPU for best performance.

### Ollama can report whether a model is on the GPU, the CPU, or split between them

Source: Ollama FAQ, "How can I tell if my model was loaded onto the GPU?", https://docs.ollama.com/faq

> Use the `ollama ps` command to see what models are currently loaded into memory.

> The `Processor` column will show which memory the model was loaded into

Verdict: confirmed. The three states are quoted in the previous section.

## Chapter 3 · Compression ruins the model

### Weight memory scales with bits per parameter

Source: Hugging Face Transformers, Optimizing LLMs for Speed and Memory, https://huggingface.co/docs/transformers/main/en/llm_tutorial_optimization

> *Loading the weights of a model having X billion parameters requires roughly 2 \* X GB of VRAM in bfloat16/float16 precision*

> It has been found that model weights can be quantized to 8-bit or 4-bits without a significant loss in performance

> While we see very little degradation in accuracy for our model here, 4-bit quantization can in practice often lead to different results compared to 8-bit quantization or full `bfloat16` inference. It is up to the user to try it out.

Source: Hugging Face Transformers, Quantization overview, https://huggingface.co/docs/transformers/main/en/quantization/overview

> Quantization lowers the memory requirements of loading and using a model by storing the weights in a lower precision while trying to preserve as much accuracy as possible.

Arithmetic used in the video: 8 billion parameters × 16 bits = 128 billion bits = 16 GB. 8 billion parameters × 4 bits = 32 billion bits = 4 GB. This agrees with the Hugging Face rule of thumb (2 × 8 = 16 GB at 16 bits) and with the one quarter ratio in Google's Gemma 4 table (57.7 GB at 16 bits against 14.4 GB at 4 bits).

Verdict: confirmed. The arithmetic is simplified weight math, as the video says.

### Actual files add overhead, and running the model takes more memory again

Source: Google AI for Developers, Gemma 4 model overview, https://ai.google.dev/gemma/docs/core

> **Table 1.** Approximate GPU or TPU memory required to load Gemma 4 models based on parameter count, quantization level and 20% overhead of loading additional things.

> **Base Weights Only:** The estimates in the preceding table *only* account for the memory required to load the static model weights. They don't include the additional VRAM needed for supporting software or the context window.

Verdict: confirmed.

### Precision loss depends on the model, the method and the task

The Hugging Face guide quoted above says 4 bit results "can in practice often lead to different results" and that "It is up to the user to try it out." Google's Gemma 4 page says lower precision models "have less capabilities, but may be sufficient for your AI task."

Verdict: confirmed as a general statement. No source measures the effect for a particular document task.

## Chapter 4 · The maximum context setting gives the best answers

### Reading a conversation creates working data, including the KV cache, and more context can require more memory

Source: Hugging Face Transformers, How caching works, https://huggingface.co/docs/transformers/main/en/cache_explanation

> A key-value (KV) cache eliminates this inefficiency by storing kv pairs derived from the attention layers of previously processed tokens.

> attention cost per step is **linear** with sequence length (memory grows linearly, but compute/token remains low)

Source: Google AI for Developers, Gemma 4 model overview, https://ai.google.dev/gemma/docs/core

> **Context Window (KV Cache):** Memory consumption will increase dynamically based on the total number of tokens in your prompt and the generated response. Larger context windows require significantly more VRAM on top of the base model weights.

Source: Ollama, Context length, https://docs.ollama.com/context-length

> Setting a larger context length will increase the amount of memory required to run a model. Ensure you have enough VRAM available to increase the context length.

Verdict: confirmed.

### Different model architectures handle that differently

Source: Qwen3.5-9B model card, https://huggingface.co/Qwen/Qwen3.5-9B

> Hidden Layout: 8 × (3 × (Gated DeltaNet → FFN) → 1 × (Gated Attention → FFN))

Source: gemma-4-26B-A4B-it model card, https://huggingface.co/google/gemma-4-26B-A4B-it

> The models employ a hybrid attention mechanism that interleaves local sliding window attention with full global attention, ensuring the final layer is always global. [...] To optimize memory for long contexts, global layers feature unified Keys and Values

Verdict: confirmed. Qwen 3.5 mixes linear attention layers with full attention layers, and Gemma 4 mixes sliding window layers with global layers; both are design choices aimed at long context cost.

### A 256K label describes a supported context window

Model cards in this video's set:

* Qwen3.5-9B: "Context Length: 262,144 natively and extensible up to 1,010,000 tokens." https://huggingface.co/Qwen/Qwen3.5-9B
* Ministral 3 8B Instruct: "**Large Context Window**: Supports a 256k context window." https://huggingface.co/mistralai/Ministral-3-8B-Instruct-2512
* Gemma 4 26B A4B: "Context Length · 256K tokens" https://huggingface.co/google/gemma-4-26B-A4B-it
* Qwen3.8-27B: "Context Length: 262,144 natively and extensible up to 1,000,000 tokens." https://huggingface.co/Qwen/Qwen3.8-27B

262,144 tokens is 256 × 1,024, which is why it is written as 256K.

Ollama shows that the supported window and the window actually allocated are different settings:

> Ollama defaults to the following context lengths based on VRAM:
> \< 24 GiB VRAM: 4k context
> 24-48 GiB VRAM: 32k context
> \>= 48 GiB VRAM: 256k context

Verdict: confirmed.

### A tiny context budget can undermine extended reasoning

Source: Qwen3.5-9B model card, https://huggingface.co/Qwen/Qwen3.5-9B

> The model has a default context length of 262,144 tokens. If you encounter out-of-memory (OOM) errors, consider reducing the context window. However, because Qwen3.5 leverages extended context for complex tasks, we advise maintaining a context length of at least 128K tokens to preserve thinking capabilities.

> **Adequate Output Length**: We recommend using an output length of 32,768 tokens for most queries. For benchmarking on highly complex problems, such as those found in math and programming competitions, we suggest setting the max output length to 81,920 tokens.

Source: Qwen3.8-27B model card, https://huggingface.co/Qwen/Qwen3.8-27B

> Reasoning Content: Set the maximum output length to 262,144 tokens.
> Final Response: Set the maximum output length to 131,072 tokens.

Verdict: confirmed. Qwen's own guidance ties thinking quality to a large context budget, which is the tension the video describes against the memory cost above.

## Chapter 5 · Your documents belong inside the model

### LM Studio includes short documents in full and retrieves sections from longer ones

Source: LM Studio Docs, Chat with Documents, https://lmstudio.ai/docs/app/basics/rag

> If the document is short enough (i.e., if it fits in the model's context), LM Studio will add the file contents to the conversation in full.

> If the document is very long, LM Studio will opt into using "Retrieval Augmented Generation", frequently referred to as "RAG". RAG means attempting to fish out relevant bits of a very long document (or several documents) and providing them to the model for reference. This technique sometimes works really well, but sometimes it requires some tuning and experimentation.

Verdict: confirmed. LM Studio's own note that retrieval "sometimes requires some tuning" supports the video's point that retrieval can miss the right passage.

## Chapter 6 · More tokens per second means less waiting

### llama.cpp's benchmark separates prompt processing from text generation

Source: ggml-org/llama.cpp, tools/llama-bench/README.md, https://github.com/ggml-org/llama.cpp/blob/master/tools/llama-bench/README.md

> llama-bench can perform three types of tests:
> - Prompt processing (pp): processing a prompt in batches (`-p`)
> - Text generation (tg): generating a sequence of tokens (`-n`)
> - Prompt processing + text generation (pg): processing a prompt followed by generating a sequence of tokens (`-pg`)

The README's own example tables report pp and tg rows separately for the same model, with very different tokens per second figures.

Verdict: confirmed.

### The twenty second and five second example

Arithmetic from the video: 20 s + 5 s = 25 s against 5 s + 10 s = 15 s, a difference of 10 seconds. The video labels these figures as hypothetical.

### Qwen 3.5 and Qwen 3.8 can generate reasoning before the final reply

Qwen3.5-9B model card, https://huggingface.co/Qwen/Qwen3.5-9B

> Qwen3.5 models operate in thinking mode by default, generating thinking content signified by `<think>\n...</think>\n\n` before producing the final responses.

Qwen3.8-27B model card, https://huggingface.co/Qwen/Qwen3.8-27B

> Qwen3.8 models operate in thinking mode by default, generating thinking content signified by `<think>\n...</think>\n\n` before producing the final response.

> `xhigh` (default): for complex tasks demanding thorough analysis
> `medium`: balancing accuracy and speed
> `low`: efficient reasoning optimizing for speed and cost

Verdict: confirmed.

### Ollama exposes separate loading, prompt processing and generation timings

Source: Ollama API, Usage, https://docs.ollama.com/api/usage

> * `total_duration`: How long the response took to generate
> * `load_duration`: How long the model took to load
> * `prompt_eval_count`: How many input tokens were in the prompt
> * `prompt_eval_duration`: How long it took to evaluate the uncached prompt tokens
> * `eval_count`: How many output tokens were processes
> * `eval_duration`: How long it took to generate the output tokens

> All timing values are measured in nanoseconds.

Verdict: confirmed.

## Chapter 7 · A local app means everything stays local

### Ollama supports cloud models as well as local ones

Source: Ollama, Cloud, https://docs.ollama.com/cloud

> Run models in Ollama's cloud from your apps or terminal. No model or app download required.

> In the Ollama app or CLI, use `gemma4:cloud`. Cloud models do not need to be downloaded.

Source: Ollama FAQ, https://docs.ollama.com/faq

> Ollama runs locally. We don't see your prompts or data when you run locally. When using cloud-hosted models, we process your prompts and responses to provide the service but do not store or log that content and never train on it.

Verdict: confirmed. The same app and CLI address both local and cloud models; a cloud model is selected by name.

### Search tools can introduce more connections

Source: Ollama FAQ, https://docs.ollama.com/faq

> By turning off Ollama's cloud features, you will lose the ability to use Ollama's cloud models and web search.

Verdict: confirmed for Ollama's own web search, which is part of its cloud features.

### Ollama documents a setting for disabling its cloud features

Source: Ollama FAQ, "How do I disable Ollama Cloud features?", https://docs.ollama.com/faq

> Ollama can run in local only mode by disabling Ollama's cloud features.

> Set `disable_ollama_cloud` in `~/.ollama/server.json`:
> `{ "disable_ollama_cloud": true }`

> You can also set the environment variable: `OLLAMA_NO_CLOUD=1`

> Restart Ollama after changing configuration. Once disabled, Ollama's logs will show `Ollama cloud disabled: true`.

Verdict: confirmed. The setting is `disable_ollama_cloud`, with `OLLAMA_NO_CLOUD=1` as the environment variable equivalent.

### LM Studio documents offline model chat and local document processing after the required downloads

Source: LM Studio Docs, Offline Operation, https://lmstudio.ai/docs/app/offline

> In general, LM Studio does not require the internet in order to work. This includes core functions like chatting with models, chatting with documents, or running a local server, none of which require the internet.

> Once you have an LLM onto your machine, the model will run locally and you should be good to go entirely offline. Nothing you enter into LM Studio when chatting with LLMs leaves your device.

> When you drag and drop a document into LM Studio to chat with it or perform RAG, that document stays on your machine. All document processing is done locally, and nothing you upload into LM Studio leaves the application.

The same page lists what does need a connection: searching for models, downloading models, the model catalog, downloading runtimes and checking for app updates.

Verdict: confirmed.

## Chapter 8 · No subscription means it pays for itself

### Twelve hundred dollars against twenty dollars a month

Arithmetic: $1,200 ÷ $20 per month = 60 months = 5 years. The video presents these as example numbers and says the figure excludes electricity, maintenance and the value of time.

Verdict: arithmetic correct. No external source applies; the prices are illustrative.

### The audition candidates

Qwen3.5-9B and Ministral 3 8B Instruct are the two compact options sourced in Chapter 1. Mistral publishes Ministral 3 8B Instruct in FP8 and states it fits "in 12GB of VRAM in FP8, and less if further quantized", which matches the 12GB card used throughout the video.

### Not checked

* Whether any particular quantized download of these models answers document questions correctly. The video recommends testing this and makes no claim about the outcome.
* The claim that fine tuning suits consistent behavior or response patterns better than changing facts. This is presented as the video's recommendation and was not traced to a single primary source.
* The 32GB system RAM figure. It describes a hypothetical desktop, not a product.
* Whether third party extensions or plugins transmit data when a machine reconnects. The video states this is not proven by an offline test, and no source was checked for it.
{% endraw %}

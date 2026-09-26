---
layout: default
title: "Local AI is free until you see this hardware bill"
permalink: /the-real-cost-of-local-ai/
date: 2026-09-26
---

# Local AI is free until you see this hardware bill

{% raw %}
Checked on 25 September 2026. Each figure below is taken from the maker's or publisher's own page where one exists.

## Model download sizes (Qwen 3.5)

Source: Ollama library, qwen3.5 tags. https://ollama.com/library/qwen3.5/tags

Ollama describes the family as "Qwen 3.5 is a family of open-source multimodal models". The default tag for each size is the q4_K_M quantization, and the listed sizes are:

| Tag | Listed size |
|---|---|
| qwen3.5:4b (same file as qwen3.5:4b-q4_K_M) | 3.4GB |
| qwen3.5:9b (same file as qwen3.5:9b-q4_K_M, also qwen3.5:latest) | 6.6GB |
| qwen3.5:27b (same file as qwen3.5:27b-q4_K_M) | 17GB |

The same page lists other packages of the same models, for example qwen3.5:4b-q8_0 at 5.3GB, qwen3.5:4b-bf16 at 9.3GB, qwen3.5:9b-q8_0 at 11GB, qwen3.5:9b-bf16 at 19GB and qwen3.5:27b-bf16 at 56GB. That spread is what the narration means by a quantized download being much smaller than a full precision file. All sizes are the download sizes shown by Ollama, not memory use while running.

The original weights are published by Qwen on Hugging Face: https://huggingface.co/Qwen/Qwen3.5-27B (the page reports the checkpoint as 28B params in BF16, since the model includes a vision component).

Verdict: matches (3.4GB, 6.6GB, 17GB).

## NVIDIA GeForce RTX 5090

Source: NVIDIA product page, https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/ and NVIDIA's comparison table, https://www.nvidia.com/en-us/geforce/graphics-cards/compare/

* Standard Memory Config: 32 GB GDDR7, 512 bit interface.
* Memory chips: a GDDR7 device has a 32 bit interface (JEDEC JESD239, https://www.jedec.org/standards-documents/docs/jesd239), so a 512 bit interface is 16 devices, and 32 GB across 16 devices is 2 GB each. This is arithmetic on NVIDIA's own figures.
* Total Graphics Power (W): 575.
* Required System Power (W): 1000. NVIDIA's footnote: "Minimum is based on a PC configured with a Ryzen 9 9950X processor."
* The product page shows "Starting at $1999".

NVIDIA's launch press release (6 January 2025), https://nvidianews.nvidia.com/news/nvidia-blackwell-geforce-rtx-50-series-opens-new-world-of-ai-computer-graphics, says: "the GeForce RTX 5090 GPU with 3,352 AI TOPS and the GeForce RTX 5080 GPU with 1,801 AI TOPS will be available on Jan. 30 at $1,999 and $999, respectively."

Verdict: matches (32 GB, 575 W, 1000 W). The narration's wording "recommended 1000 watt power supply for its reference system" is a fair reading of "Required System Power" with the Ryzen 9 9950X footnote.

On price, the narration says the card "can cost thousands of dollars". NVIDIA's own starting price is $1,999, so "thousands" is accurate only in the sense of roughly two thousand dollars at list price. Retail prices above list have been widely reported, but that is not a maker figure.

## Electricity arithmetic

Assumption: a 30 day month.

575 W × 4 h per day = 2.3 kWh per day. 2.3 kWh × 30 days = 69 kWh. 69 kWh × $0.18 = $12.42 per month.

With an average month of 30.44 days the result is $12.59. The narration's "about twelve dollars and forty cents" matches the 30 day figure.

This is the card's rated total graphics power held for four hours, not a measured draw of a whole computer during inference.

Reference rate: U.S. Energy Information Administration, Electric Power Monthly, Table 5.6.A, https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_5_6_a (data for July 2026, released 24 September 2026). U.S. Total residential average price: 18.31 cents per kWh in July 2026 (17.45 in July 2025). Table 5.6.B, https://www.eia.gov/electricity/monthly/epm_table_grapher.php?t=epmt_5_6_b, gives the year to date average through July 2026 as 18.19 cents per kWh (17.01 a year earlier).

Verdict: 18 cents is a reasonable rounded U.S. residential rate for 2026. State rates vary widely, from about 12 to 13 cents in several states to over 30 cents in California and over 40 cents in Hawaii, in the same table.

## AMD Ryzen AI Max+ 395

Source: AMD product page, https://www.amd.com/en/products/processors/laptop/ryzen/ai-300-series/amd-ryzen-ai-max-plus-395.html

* 16 CPU cores (16x Zen 5), 32 threads.
* System Memory Type: 256 bit LPDDR5x. Max. Memory: 128 GB. Max Memory Speed: LPDDR5x 8000.
* Graphics Model: Radeon 8060S Graphics, 40 graphics cores.
* Form Factor: Laptops, Desktops.

AMD blog, https://www.amd.com/en/blogs/2025/amd-ryzen-ai-max-395-processor-breakthrough-ai-.html: "The Ryzen™ AI MAX+ 395 is available today with system memory options ranging from 32GB all the way up to 128GB of unified memory – out of which up to 96GB can be converted to VRAM through AMD Variable Graphics Memory."

A named system using it: the Framework Desktop, https://frame.work/desktop, lists a "Max+ 395 - 128GB" configuration with "128GB LPDDR5x-8000" memory and Radeon 8060S graphics.

Verdict: matches (up to 128 GB, up to 96 GB allocatable to graphics).

## gpt-oss-120b on Ryzen AI Max+

Source: AMD blog, "How To Run OpenAI's GPT-OSS 20B and 120B Models on AMD Ryzen AI Processors and Radeon Graphics Cards", 5 August 2025, https://www.amd.com/en/blogs/2025/how-to-run-openai-gpt-oss-20b-120b-models-on-amd-ryzen-ai-radeon.html

Exact wording:

> "The GGML converted MXFP4 weights require roughly 61GB of VRAM and fit effortlessly into the 96GB dedicated graphics memory of the AMD Ryzen™ AI Max+ 395 processor. Note that a driver version equal or higher than AMD Software: Adrenalin™ Edition 25.8.1 WHQL is required to unlock this capability."

> "With speeds of up to 30 tokens per second, not only do AMD customers have access to a datacenter-class, state-of-the-art model, but the performance is very usable thanks to the bandwidth of the Ryzen™ AI Max+ platform and the mixture-of-experts architecture of the OpenAI GPT-OSS 120B."

Test conditions, endnote SHO-39:

> "Testing as of August 2025 by AMD. All tests conducted on LM Studio 0.3.21b4 . Llama.cpp runtime 1.44. Tokens/s : Sustained performance average of multiple runs with specimen prompt "How long would it take for a ball dropped from 10 meter height to hit the ground?". Models tested: OpenAI GPT-OSS 120B. AMD Ryzen™ AI MAX+ 395 on an ASUS ROG Flow Z13 with 128GB 8000 MT/s memory, Windows 11 Pro 24H2 and Adrenalin 25.8.1 WHQL. Performance may vary."

The demo graphic in the same post states "AMD Ryzen AI Max+ 395 (128GB) and AMD Software: Adrenalin Edition 25.8.1 WHQL, VGM: 96GB", and a Task Manager screenshot shows 61.0 of 96.0 GB dedicated GPU memory in use.

Verdict: matches (roughly 61 GB, up to 30 tokens per second, tied to one model format, runtime, driver, laptop and prompt).

## gpt-oss-120b itself

Source: OpenAI, "Introducing gpt-oss", 5 August 2025, https://openai.com/index/introducing-gpt-oss/ and the model card on Hugging Face, https://huggingface.co/openai/gpt-oss-120b

* OpenAI: "The gpt-oss-120b model achieves near-parity with OpenAI o4-mini on core reasoning benchmarks, while running efficiently on a single 80 GB GPU." Released under the Apache 2.0 license.
* Hugging Face model card: "gpt-oss-120b — for production, general purpose, high reasoning use cases that fit into a single 80GB GPU (like NVIDIA H100 or AMD MI300X) (117B parameters with 5.1B active parameters)". The MoE weights are post trained in MXFP4.

Verdict: exists as described. It is a 117B parameter mixture of experts model with 5.1B active parameters.

## Apple Mac Studio

Sources: https://www.apple.com/mac-studio/specs/, https://www.apple.com/shop/buy-mac/mac-studio and https://www.apple.com/mac-studio/

What Apple lists today (U.S. store):

* "Mac Studio now with M5 Max and M5 Ultra."
* M5 Max: 36GB unified memory, configurable to 48GB, 64GB or 128GB. Price $2499.
* M5 Ultra: 96GB unified memory, configurable to 256GB or 512GB. Price $5499.

Verdict: DIFFERS. The narration names "an M4 Max configuration with 36 gigabytes of unified memory at $1,999" and "M3 Ultra configurations ... up to 512 gigabytes". Apple's current U.S. pages no longer list the M4 Max or M3 Ultra Mac Studio. The current entry configuration is M5 Max with 36GB at $2,499, and the 512GB ceiling now belongs to the M5 Ultra. The $1,999 M4 Max 36GB figure was Apple's list price for the previous generation Mac Studio, which is not shown on apple.com today. The 36GB entry memory and the 512GB top memory are unchanged.

## Apple MLX and Metal

* MLX, https://github.com/ml-explore/mlx: "MLX: An array framework for Apple silicon", MIT license.
* Metal, https://developer.apple.com/metal/: Apple's GPU programming framework; the page says Metal "puts the advanced capabilities of Apple‑designed GPUs at your fingertips" for graphics and compute workloads including machine learning.
* llama.cpp, https://github.com/ggml-org/llama.cpp, lists "Apple silicon is a first-class citizen - optimized via ARM NEON, Accelerate and Metal frameworks".

Verdict: matches.

## Splitting a model between graphics card and processor

Source: llama.cpp README, https://github.com/ggml-org/llama.cpp: "CPU+GPU hybrid inference to partially accelerate models larger than the total VRAM capacity", and "1.5-bit, 2-bit, 3-bit, 4-bit, 5-bit, 6-bit, and 8-bit integer quantization for faster inference and reduced memory use".

Verdict: supports the narration's description of split inference and quantization.

## NVIDIA CUDA

Source: https://developer.nvidia.com/cuda-zone: "CUDA is NVIDIA's platform for accelerated computing and the foundation for GPU computing." NVIDIA's comparison table lists CUDA Capability 12.0 for the RTX 50 series.

## ChatGPT Plus and API billing

Source: OpenAI Help Center, "What is ChatGPT Plus?", https://help.openai.com/en/articles/6950777-what-is-chatgpt-plus

* "ChatGPT Plus is a subscription plan that provides enhanced access to the ChatGPT web app for $20/month."
* Subscription Details: "Price: $20/month (billed monthly)." and "Not included: API usage is separate and billed independently. See API pricing."

OpenAI API pricing, https://openai.com/api/pricing/, bills models per million tokens of input and output.

Verdict: matches ($20 per month, API billed separately).

## Subscription arithmetic

* $20 × 12 = $240 (one year).
* $20 × 60 = $1,200 (five years).
* $20 × 120 = $2,400 (ten years).
* $1,999 ÷ $20 = 99.95 months, which is 8.33 years. "Almost 100 months" and "more than eight years" are correct for $1,999.

For the current U.S. entry Mac Studio at $2,499: $2,499 ÷ $20 = 124.95 months, or 10.4 years.

## Caveats

* Mac Studio configuration and price differ from Apple's current listing. Apple now sells the Mac Studio with M5 Max (36GB, $2,499) and M5 Ultra (up to 512GB, from $5,499). The M4 Max 36GB at $1,999 and the M3 Ultra up to 512GB are the previous generation and are not listed on apple.com today. The arithmetic built on $1,999 is internally correct, but the price is no longer Apple's current entry price.
* The RTX 5090 list price is $1,999 from NVIDIA. "Thousands of dollars" is accurate at roughly two thousand at list; any higher figure depends on retail pricing, which NVIDIA does not publish.
* The RTX 5090 power supply figure is NVIDIA's "Required System Power" for a system with a Ryzen 9 9950X, not a general recommendation for every build.
* The electricity figure uses the card's 575 W rating held for four hours a day over a 30 day month at $0.18 per kWh. It is an upper bound style illustration, not a measurement.
* The EIA rate of 18.31 cents is for July 2026, a summer month; the year to date average through July 2026 is 18.19 cents. Both round to 18 cents.
* AMD's 30 tokens per second figure is a single vendor test on an ASUS ROG Flow Z13 with LM Studio 0.3.21b4, llama.cpp runtime 1.44, Adrenalin 25.8.1 and one short prompt, sustained average of multiple runs.
* The Qwen 3.5 sizes are Ollama's default q4_K_M packages. Other packages of the same models range from 3.4GB to 9.3GB for 4B, 6.6GB to 19GB for 9B and 16GB to 56GB for 27B on the same page.
* ChatGPT plan pricing pages are localised by region; the $20 figure is from OpenAI's Help Center article, which states the price in U.S. dollars.
{% endraw %}

---
layout: default
title: "Deepseek 552B just ran on one mini PC. Here is how"
permalink: /deepseek-v4-1-one-dgx-spark/
date: 2026-09-19
---

# Deepseek 552B just ran on one mini PC. Here is how

{% raw %}
Every figure, name, command and benchmark this video puts on screen, chased to a primary
source. Checked 18 September 2026.

## The machine

**NVIDIA DGX Spark, US list $4,699.** NVIDIA raised the Founders Edition MSRP from $3,999
to $4,699 in February 2026, citing LPDDR5X memory supply constraints. The Founders Edition
ships with 128 GB of LPDDR5X unified memory, 4 TB of NVMe M.2 storage, the GB10 Grace
Blackwell Superchip and a ConnectX-7 NIC.
Source: NVIDIA DGX Spark product page; price change reported at
https://videocardz.com/newz/nvidia-officially-raises-dgx-spark-founders-edition-msrp-to-4699

**The memory is shared between CPU and GPU.** GB10 presents one unified LPDDR5X subsystem
rather than separate system and video memory, so the operating system and any other running
program draw from the same 128 GB the model does.
Source: NVIDIA DGX Spark specifications.

## The model

**DeepSeek V4.1 Flash: 552B parameter backbone.** A 552B-parameter mixture of experts, plus
roughly 196B parameters of Engram lookup tables. It activates about 8B parameters per prompt
token and about 16B per generated token.
Source: deepseek-ai/DeepSeek-V4.1-Flash model card, https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash

**Architecture.** A 40-layer causal encoder/decoder backbone: a 20-layer causal encoder
followed by a 20-layer decoder, with 384 routed experts, one shared expert and six selected
experts per token. Two trainable Engram tables at layers 1 and 14 provide tokenizer
dependent N-gram memory, as two tensors of roughly 384M rows by 256, about 94.6 GiB each.
Source: DeepSeek V4.1 Flash model card and the published architecture study at
https://deepseek-v3.ezyang.com/studies/dsv41-flash.html

## What the model scores

**deepSWE: 74.2 for V4.1 Flash, against 74.0 and 73.0.** DeepSeek's published comparison
puts V4.1 Flash at 74.2 per cent on DeepSWE v1.1, a software engineering benchmark, with
Claude Opus 5 at 74.0 and GPT 5.6 Sol at 73.0. Those three sit within one and a half points
of each other, which is why the video says the close scores do not establish an overall
winner rather than calling a win.
Source: DeepSeek's published comparison for V4.1 Flash, as reported at
https://venturebeat.com/technology/deepseek-v4-1-flash-debuts-with-0-003-1m-off-peak-cached-input-rate-and-benchmarks-eclipsing-gpt-5-6-sol-claude-opus-5
and https://officechai.com/ai/deepseek-v4-1-flash-benchmarks-pricing/

**These are the company's own numbers, and they are not measurements of the Q2 build.**
Every figure above is for the full precision model. The video says so in the narration and
draws the Q2 column on the chart empty, because nothing has published a score for the
compressed version running on a Spark.

**Running on a 128 GB Mac as well as a Spark.** ds4's README states that V4.1 Flash Q2
"runs with SSD streaming on one 128 GB Mac or Spark, or resident across two Macs or two
Sparks using RDMA", so the Mac route the video shows is documented rather than inferred.
Source: antirez/ds4, README.md


## The download

**341 GiB total, 189 GiB of it Engram tables, 152 GiB main weights.** ds4's DGX Spark guide
states the V4.1 Flash Q2 file "is 341 GiB, including 189 GiB of disk-only Engram tables",
and the installation docs give the main weights as 152 GiB. 341 GiB against 128 GB of
memory is the figure the video opens on.
Source: antirez/ds4, docs/DGX_SPARK.md and https://dwarfstar.sh/docs/installation/

**Q2 cannot be loaded resident on a 128 GB Spark.** ds4's own release QA record is explicit:
"Never load this Q2 model resident on a 128 GB Spark. Its 341 GiB file includes 189 GiB of
disk-only Engram; the remaining weights still exceed RAM."
Source: antirez/ds4, QA_BEFORE_RELEASES.md, CUDA SSD Streaming section

**Engram tables stay on disk in every mode.** "Engram tables remain on disk in every mode."
Source: antirez/ds4, README.md

## The software

**ds4, also called DwarfStar, by antirez.** A native, self-contained, open source (MIT)
inference engine for DeepSeek V4 Flash, DeepSeek V4.1 Flash, DeepSeek V4 PRO, GLM 5.2 and
5.3, GLM 5.3 Flash and Qwen3.8 Flash Next, on Metal, CUDA and ROCm.
Source: https://github.com/antirez/ds4

**Build and run on a Spark.** The documented target is `make cuda-spark`, which selects
`sm_121` and enables the Blackwell-specific kernels. The build needs `nvcc` and cuBLAS from
the CUDA development toolkit, and the guide says to check that `nvidia-smi` sees the GPU
before building. It also says to stop other inference services before loading a model so
they do not compete for memory.
Source: antirez/ds4, docs/DGX_SPARK.md

**The documented V4.1 Flash Q2 invocation.**
`./download_model.sh ds41f-q2`, then
`./ds4 --cuda -m gguf/DeepSeek-V4.1-Flash-Q2.gguf --ssd-streaming --ctx 32768`.
The same options apply to `ds4-agent` and `ds4-server`.
Source: antirez/ds4, docs/DGX_SPARK.md

**The expert cache is automatic.** "The expert cache is sized automatically; leave memory
for other programs and the context." Automatic sizing currently resolves to about 80 GiB on
an idle Spark, and the runtime can reduce a requested budget when memory is tight.
Source: antirez/ds4, docs/DGX_SPARK.md and QA_BEFORE_RELEASES.md

**Q2 is aggressive quantization of the expert weights.** ds4 runs DeepSeek V4 Flash locally
on 96 to 128 GB thanks to an asymmetric 2-bit quantization; other parts of the model are
kept at higher precision. Published benchmark scores for the full-precision model therefore
do not transfer to a Q2 local run.
Source: https://github.com/antirez/ds4 and https://www.noze.it/en/insights/dwarfstar-4/

## The speed

**About 9.3 generated tokens per second, on one Spark.** The release QA record states: "For
a roughly 3.2K `/read` prompt at 32K context, the automatic-cache reference is about 100 t/s
prefill and 9.3 t/s decode over 256 output tokens."
Source: antirez/ds4, QA_BEFORE_RELEASES.md, CUDA SSD Streaming section

**A thousand generated tokens at that rate is about 108 seconds.** 1000 / 9.3 = 107.5
seconds. This is generation time alone and excludes prompt reading and tool execution.
Derived from the figure above.

**Prefill plus reply fell from about 87 to 59 seconds after optimization.** The DGX Spark
guide records, for 13 to 14 September 2026 with automatic cache sizing: a 3,241-token
`/read README.md` prefill reached 93 to 96 t/s, up from 49 to 54 t/s, with 32K allocated
context, and "The automatic-cache 256-token reply test decoded about 5% slower, but prefill
plus the reply fell from about 87 to 59 seconds."
Source: antirez/ds4, docs/DGX_SPARK.md

## The alternatives

**Qwen3.8 Flash Next, Q2: 41.73 GiB resident.** "Q2 keeps 41.73 GiB of weights resident;
Q4 keeps 69.74 GiB. Both GGUFs also contain 95.37 GiB of BF16 n-grams, read directly from
the SSD." Vision, the native agent and server APIs all work on CUDA. Measured 15 September
2026 on one Spark: a 16K prefill reached 250 t/s and ordinary decode stayed around 17.3 t/s.
Source: antirez/ds4, docs/DGX_SPARK.md

**GLM 5.3 Flash, Q2: the resident target for one Spark.** Roughly 90 GiB, running resident
on a 128 GB Mac or one DGX Spark, with `--ctx 16384`. Q4 does not fit resident. GLM 5.3
Flash adds vision to the same text model through a separate encoder, and GLM vision works on
the CUDA backend.
Source: antirez/ds4, docs/DGX_SPARK.md and https://dwarfstar.sh/blog/glm-5-3-flash-lands-in-ds4/

**DeepSeek V4.1 on CUDA is text only.** "V4.1 CUDA vision and DSpark are not supported."
DeepSeek V4.1 Flash text and vision both run on Metal; on a DGX Spark only text runs. So the
larger model does not bring the vision feature with it.
Source: antirez/ds4, docs/DGX_SPARK.md and https://github.com/antirez/ds4

## Talking to it from an editor

**ds4-server plus a client configuration.** The server is started with `./ds4-server`, and
OpenCode is pointed at it by merging a provider into `~/.config/opencode/opencode.json` with
a `baseURL` of `http://127.0.0.1:8000/v1`. The guide warns: "Set the client's context limit
no higher than the server's. Output tokens also consume that context; a client limit does
not enlarge the server allocation."
Source: antirez/ds4, docs/CLIENTS.md

**The address is the part that catches people out.** "The examples use Flash and localhost.
Change the address for a trusted remote server." An editor running on a laptop resolves
`127.0.0.1` to the laptop, so reaching a server on the Spark needs the Spark's address or a
forwarded port.
Source: antirez/ds4, docs/CLIENTS.md

## Not checked

- The Engram table figure is quoted two ways by two primary sources: about 196B parameters
  on the model card, and 189 GiB on disk in ds4's Spark guide. Both are used here in their
  own terms, parameters and bytes, and neither is converted into the other.
- The 9.3 t/s decode reference is one workload at one context length on one machine, quoted
  by the project as a QA reference band rather than as a general throughput claim. Published
  figures for other configurations on the same hardware run higher.
- The 54.4 deepSWE score for the previous Flash is used as the script supplies it. The 74.2,
  74.0 and 73.0 figures were confirmed against reporting of DeepSeek's published comparison;
  the 54.4 baseline was not separately confirmed at a primary source.
- Every deepSWE figure in the video is DeepSeek's own published comparison rather than an
  independent evaluation, and none of them was measured on a DGX Spark or on the Q2 build.
- The sizes are labelled GB on screen and said as gigabytes, using the common shorthand.
  The underlying figures are the gibibyte values ds4's documentation publishes (341, 189,
  152 and 42), carried across unconverted so that the picture and the narration state the
  same number. This file keeps the GiB units of the sources above.
{% endraw %}

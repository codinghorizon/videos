---
layout: default
title: "Apple put a trillion parameter AI on just 4 macs"
permalink: /apple-four-macs-trillion-parameter-ai/
date: 2026-09-23
---

# Apple put a trillion parameter AI on just 4 macs

{% raw %}
Every figure, price, date, version and benchmark this video puts on screen, chased to a
primary source. Worked from the `TEXT:` lines in BEATS.md, so nothing drawn is unchecked.

The script was supplied finished and was recorded before any shot existed, so a claim that
turned out wrong could not be corrected in the narration. Nothing below is wrong; two
figures are stated more precisely on screen than in the words, and both are noted.

---

## The cluster, and what it ran

**Four Mac Studios, 1.5 TB of unified memory, just under $40,000.**
Two M3 Ultra Studios with 512 GB and two with 256 GB. Apple loaned the machines.
Per-unit configured prices: $11,699 for each 512 GB machine, $8,099 for each 256 GB one.
Source: Jeff Geerling, "1.5 TB of VRAM on Mac Studio: RDMA over Thunderbolt 5",
18 December 2025 — <https://www.jeffgeerling.com/blog/2025/15-tb-vram-on-mac-studio-rdma-over-thunderbolt-5/>

**Kimi K2 Thinking at around 30 tokens per second on that cluster, with Exo.**
Geerling's own wording is "around 30 tokens per second". The video says "roughly thirty"
and "around thirty", which is the source's own figure rather than a rounding of a more
precise one. Qwen3 235B on the same four machines measured 32 tokens/sec.
Same source.

**RDMA lowered memory access latency from 300 µs to under 50 µs; Thunderbolt 5 carries
50 to 60 Gbps of real-world throughput.** Exo 1.0, Apache 2.0, released the same day.
Same source. The 300 µs → under 50 µs figures are what beat 032 draws.

**Apple introduced RDMA over Thunderbolt 5 in macOS 26.2.**
Same source. The script says "version 26.2 of its mac operating system", which is that.

---

## Kimi K2 Thinking

Moonshot's own model card is the source for every number in chapters 1 to 3:
<https://huggingface.co/moonshotai/Kimi-K2-Thinking>

| Claim | Value |
|---|---|
| Total parameters | 1T |
| Activated parameters per token | 32B |
| Architecture | Mixture-of-Experts |
| Experts / selected per token | 384 / 8 |
| Context length | 256K |
| Released quantisation | Native INT4, via Quantization-Aware Training |

**Benchmarks, from the same card's own comparison table.** Every one of the six figures
the narration states matches exactly:

| Benchmark | K2 Thinking | GPT-5 (High) | Claude Sonnet 4.5 (Thinking) |
|---|---|---|---|
| BrowseComp (w/ tools) | 60.2 | 54.9 | 24.1 |
| SWE-bench Verified (w/ tools) | 71.3 | 74.9 | 77.2 |

**The evaluation conditions, which beat 026 puts on screen because the narration says the
tool setups are listed by Moonshot.** For agentic search the model "was equipped with
search, code-interpreter, and web-browsing tools" with "a limit was 300 steps with a
24 k-token reasoning budget per step". Coding scores were "produced with our in-house
evaluation harness" and "averaged over 5 independent runs". Same card.

**The 500 GB weights figure** in beat 007 is arithmetic stated as arithmetic: one trillion
values at four bits is 500 GB. The shot labels it as an idealised figure for weights only,
which is what the narration says. The released checkpoint is natively INT4, which is why
the four-bit figure is the right one to start from and why beats 014 and 015 exist.

---

## Kimi K3

<https://www.implicator.ai/moonshot-launches-kimi-k3-with-2-8-trillion-parameters-and-1m-context/>
and Moonshot's release. 2.8 trillion parameters, 104B active, native vision, 1M token
context, launched 16 July 2026, weights 27 July under the Kimi K3 License as a native
MXFP4 checkpoint. The three figures the narration states all check out.

---

## The cables, MLX and JACCL

**Apple documents the distributed stack through MLX and JACCL.**
Apple, "Explore distributed inference and training with MLX", WWDC26 session 233 —
<https://developer.apple.com/videos/play/wwdc2026/233/>
MLX distributes a model across Macs over Thunderbolt 5 using RDMA and Apple's open-source
JACCL communication library. JACCL is "Jack and Angelos' Collective Communication
Library", a pun on NVIDIA's NCCL.

**Four M3 Ultras running Qwen3.6-27B generated at nearly three times the single machine
rate.** Same WWDC26 session. The narration's "nearly three times" is the source's own
phrasing, so beat 040 draws a ghost outline at exactly 3× that the bar does not reach.

**Memory beside the chip against the link between machines.** M3 Ultra unified memory runs
at 819 GB/s; the Thunderbolt 5 link carries 50 to 60 Gbps. Sources: Exo's own post (819)
and Geerling (50 to 60). This is what beat 038 draws.

---

## Prefill, decode, and the Exo split

Exo's own benchmark post is the source for all of chapter 5's second half:
<https://blog.exolabs.net/nvidia-dgx-spark/>

Llama-3.1 8B at FP16, an 8,192 token prompt, generating 32 tokens:

| Configuration | Prefill | Generation | Total | Speedup |
|---|---|---|---|---|
| DGX Spark | 1.47s | 2.87s | 4.34s | 1.9× |
| M3 Ultra Mac Studio | 5.57s | 0.85s | 6.42s | 1.0× baseline |
| DGX Spark + M3 Ultra | 1.47s | 0.85s | **2.32s** | **2.8×** |

The narration's 2.32 and 6.42 are exact, and 2.8× is Exo's own figure. Their post also
gives the reason the video states: the Spark's prefill is 3.8× faster than the M3 Ultra's,
and the M3 Ultra's generation is 3.4× faster than the Spark's, because **prefill is
compute-bound and decode is memory-bound**. One DGX Spark and one Mac Studio, not two.

**Note for the capture framing.** That page's headline states a different multiple, 4×,
for a different configuration. Beat 048's crop is framed on the results table and
deliberately not on the headline, so the picture never states a figure the voice
contradicts.

---

## The M5 Ultra

Apple's own newsroom post is the source for all of chapter 6's Apple claims:
<https://www.apple.com/newsroom/2026/08/apple-introduces-new-mac-studio-with-m5-max-and-m5-ultra/>

| Claim | Value |
|---|---|
| Memory bandwidth | 1.2 TB/s, "50 percent higher than before" |
| Maximum unified memory | 512 GB |
| CPU / GPU | up to 36-core CPU, up to 80-core GPU |
| Neural Accelerators | brought "to the Ultra chip for the first time", up to 4.3× peak AI compute vs M3 Ultra |
| LLM prompt processing | "up to 4x faster than M3 Ultra" in LM Studio |
| Starting price | $5,499 |
| Availability | general 22 September 2026; **512 GB configuration "coming in late October"** |

The narration's "up to four times faster language model prompt processing in LM studio
compared with m3 ultra" is Apple's wording exactly, and "scheduled for late october" is
Apple's own date for that configuration.

**M3 Ultra at 0.8 TB/s**, drawn in beats 003 and 052, is derived from Apple's own "50
percent higher than before" rather than typed: 1.2 ÷ 1.5.

**4.8 TB/s across four machines** is arithmetic stated as arithmetic, and beat 053 exists
because the narration is explicit that the sum is not the speed of the cables.

**Independent test.** Tom's Hardware, "Apple Mac Studio (M5 Ultra) review" —
<https://www.tomshardware.com/desktops/mini-pcs/apple-mac-studio-m5-ultra-review>
Tested with Qwen3.8-27B-Q4_K_M, a four-bit dense model. The M5 Ultra's prompt processing
beat the DGX Spark's and its token generation was close to four times the Spark's. The
review is explicit that this is one dense model in one configuration, which is what beat
058 draws in amber.

---

## The other models

**Qwen3.8-27B** — native multimodal, a 27B language model with an integrated vision
encoder, 262K native context, Apache 2.0.
<https://github.com/AlibabaCloud-Official/Qwen3.8-27B>

**Qwen3-Coder-Next** — 80B total, 3B active, a coding specialist built on Qwen3-Next with
hybrid attention and MoE, 10 of 512 experts routed, 256K context, Apache 2.0, 70.6 on
SWE-bench Verified. <https://huggingface.co/Qwen/Qwen3-Coder-Next>

**DeepSeek V4.1-Flash** — released 10 September 2026, which is the narration's "september
release". 552B backbone, 8B active during prefill and 16B during decode, 1M context,
native image understanding through DeepSeek-ViT, MIT licensed.
<https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash>

Its context-cache claim, which is what beat 072 puts on screen, is specific and published:
a Causal Encoder-Decoder architecture where "the decoder's global KV cache is projected
from the final encoder hidden states"; SWA Bounded Replay reducing the persistent KV cache
footprint "to roughly 1/8 of that of DeepSeek-V4-Flash"; and Compressed Sparse Attention 2
with FP4 main KV caching reaching **890 bytes per token, roughly 1/4 of DeepSeek-V4-Flash**.
The 890 bytes figure is what the shot draws.

**NVIDIA DGX Spark** — 128 GB of unified memory per unit, CUDA, and dedicated high-speed
networking, which is what the narration claims and what beat 086 draws. Exo's own post
measures its coherent memory at 273 GB/s and its FP16 compute at about 100 TFLOPs, against
the M3 Ultra's 819 GB/s and about 26 TFLOPs — the numbers behind "one machine can win at
reading the request while another wins at writing the answer".

---

## The bill

**Just under $40,000** for the four tested M3 Ultra machines, storage upgrades included,
from Geerling's post. The narration is explicit that this is the reported price of that
tested setup rather than a current quote for four M5 machines, and beat 090 draws the
absent quote as an empty ghost row rather than inventing one.

**Forty months** is arithmetic on the narration's own deliberately simple example:
$40,000 against $1,000 a month. The shot carries the caveat line the narration states, and
beat 095 draws the two conditions that have to hold for the arithmetic to mean anything.

---

## Not checked

Nothing in the narration failed to chase to a primary source. Two items are weaker than
the rest and are listed for the upload sheet rather than hidden:

- **The 300 µs to under 50 µs RDMA latency figures** come from Geerling's write-up rather
  than from an Apple specification. They are his measurement of his own cluster.
- **Apple's "up to 4x" prompt processing claim** is Apple's own launch testing, not an
  independent result. The video says so in the narration and the shot labels it in amber.
{% endraw %}

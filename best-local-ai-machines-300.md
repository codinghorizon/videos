---
layout: default
title: "A $300 PC can run 27B AI, but there's a huge catch"
permalink: /best-local-ai-machines-300/
date: 2026-09-23
---

# A $300 PC can run 27B AI, but there's a huge catch

{% raw %}
Every figure, price, capacity and benchmark the picture puts on screen, chased to a
primary source. Checked 23 September 2026. US listings, prices before sales tax unless
stated.

Three claims could not be chased to a primary source and are listed under
**Not sourced** at the foot. Nothing in that section reaches the screen as a figure.

---

## The budget arithmetic

The video works to an example eight percent sales tax. Every figure it states is the
arithmetic on the listed price, and all of it holds:

| Stated | Arithmetic | Result |
|---|---|---|
| a $300 ceiling becomes about $277 before tax | 300 / 1.08 | $277.78 |
| $276.35 comes to $298.46 | 276.35 x 1.08 | $298.46 |
| the $330 machine becomes roughly $356 | 329.99 x 1.08 | $356.39 |
| $329.99 is $30 over budget | 329.99 - 300 | $29.99 |
| $275 before tax, as a ceiling for a strict $300 purchase | 275 x 1.08 | $297.00 |
| 32 GB is four times the 8 GB mini PC | 32 / 8 | 4 |
| 16 GB of RAM plus 6 GB of VRAM would be 22 GB | 16 + 6 | 22 |

The eight percent rate is the video's own worked example, not a rate that applies
anywhere in particular. Actual US sales tax is set by state and locality.

## The machines

**GMKtec G3S, Intel Alder Lake N95, $249.99.** The manufacturer's own US store lists
the G3S at $249.99. The N95 is a four core Alder Lake N part with integrated Intel UHD
graphics and no dedicated video memory.
<https://www.gmktec.com/collections/mini-pc>

**GMKtec G10, AMD Ryzen 5 3500U, advertised from $199.99.** The manufacturer's product
page lists the G10 from $199.99 and offers three configurations: *Barebone (No DDR & SSD
& OS)*, *16GB + 512GB SSD* and *16GB + 1TB SSD*. The page states outright that "The
Barebone model comes without DDR memory, SSD, and OS. You need to install your own
compatible DDR memory and SSD before powering on the device." The $199.99 headline is
therefore the barebones price, and the complete computer is a different SKU.
<https://www.gmktec.com/products/gmktec-g10-amd-ryzen-5-3500u-mini-pc>

The complete 16 GB / 512 GB configuration price is served by the store's variant
selector rather than as page text, so the exact $329.99 could not be read off a static
capture. See **Not sourced**.

**Dell OptiPlex 7060 small form factor: the upgrade limit is real.** Dell ships the SFF
chassis with a 200W power supply and a single **low profile** PCIe x16 slot. A full
height, dual slot GTX 1660 does not fit that slot and is not inside that power budget,
so it is not a drop in upgrade.
<https://www.dell.com/support/manuals/en-us/optiplex-7060-sff/opti_7060_sff_setup_specs_manual/power-supply>
<https://www.hardware-corner.net/desktop-models/Dell-OptiPlex-7060-SFF/>

The i5 8500 is a six core, six thread Coffee Lake desktop part, which is the "six core
desktop CPU" the video compares against the N95's four cores.

## The graphics cards

**GTX 1660 and 1660 Super carry 6 GB of GDDR6. The GTX 1650 Super carries 4 GB.** The
video's warning that similar names mean meaningfully different room for a model is the
50% capacity difference between those two parts.
<https://www.techpowerup.com/gpu-specs/geforce-gtx-1660-super.c3458>
<https://www.techpowerup.com/gpu-specs/geforce-gtx-1650-super.c3463>

**The 16 series has no tensor cores.** The GTX 16 family is built on Turing TU116 and
TU117, which are the Turing dies with the tensor and RT cores removed. They keep full
CUDA compute capability 7.5, so CUDA inference software still runs on them; what they do
not have is the tensor hardware the RTX cards use.

## The models

**Qwen 3.5 download sizes, from Ollama's own library page.** These are the figures the
video quotes and they are exact:

| Tag | Download |
|---|---|
| qwen3.5:2b | 2.7 GB |
| qwen3.5:4b | 3.4 GB |
| qwen3.5:9b | 6.6 GB |
| qwen3.5:latest | 6.6 GB, and it is the 9b |

<https://ollama.com/library/qwen3.5>

The last row is the video's point about default tags: `ollama run qwen3.5` with no tag
pulls the 9B, not the small model.

**Qwen 3.5 LiveCodeBench v6: 4B scores 55.8, 9B scores 65.6.** Both figures are from
Qwen's own published model card, in the row labelled `LiveCodeBench v6`. The separation
is 9.8 points, which is the "roughly ten points" the video states.
<https://huggingface.co/Qwen/Qwen3.5-9B>

**Gemma 4 memory requirements, from Google's own table.** The page is headed *Gemma 4
Inference Memory Requirements* and carries its own caveat that "These numbers may change
based on your specific inference tool and environment."

| Model | BF16 (16-bit) | SFP8 (8-bit) | **Q4_0 (4-bit)** |
|---|---|---|---|
| Gemma 4 E2B | 11.4 GB | 5.7 GB | **2.9 GB** |
| Gemma 4 E4B | 17.9 GB | 8.9 GB | **4.5 GB** |

<https://ai.google.dev/gemma/docs/core>

**The default Ollama gemma4 packages are much larger than the official four bit files.**
`gemma4:e2b` is 7.2 GB and `gemma4:e4b` is 9.6 GB, against the 2.9 GB and 4.5 GB above.
That gap is the video's point about matching the model, the quantization and the file
format together.
<https://ollama.com/library/gemma4>

**Ternary Bonsai 2 27B, from PrismML.** Every file size the video states is exact, and
comes from the repository's own file listing:

| File | Size |
|---|---|
| Language model, PTQ1_0 | 5.95 GB |
| Language model, PQ2_0 | 7.21 GB |
| Image projector, mmproj Q8_0 | 0.63 GB |
| F16 reference | 53.8 GB |

It is built on Qwen3.8 27B, is released under Apache 2.0, and **requires PrismML's own
llama.cpp fork**: the repository states that stock llama.cpp "rejects `PQ2_0` and
`PTQ1_0` as unknown types". CUDA, Metal and CPU backends are supported, and a separate
MLX build exists for Apple Silicon.
<https://huggingface.co/prism-ml/Ternary-Bonsai-2-27B-gguf>
<https://prismml.com/news/bonsai-2-27b>

The video's caution that a 5.95 GB file is not a promise it runs inside 6 GB of VRAM is
the ordinary difference between weights on disk and weights plus KV cache, activation
buffers and runtime overhead in memory. PrismML's own guidance is a 16 GB laptop or a
single 24 GB GPU.

## The marketplaces

**Jawa: a GTX 1660 system with 16 GB and a 512 GB SSD at $269.99, sold.** The listing is
"GTX 1660 | Intel i5 | 16GB DDR4 RAM | 512GB SSD | DVD Slot | Gaming PC" from the seller
Attack Computers, priced at $269.99 down from $299.99, published 23 November 2025 and
now **sold out**. That is exactly the shape of the video's claim: evidence of a past
price, not a checkout button.
<https://www.jawa.gg/product/90740/black-friday-gtx-1660-or-intel-i5-or-16gb-ddr4-ram-or-512gb-ssd-or-dvd-slot-or-gaming-pc>

**Swappa: $299 M1 Mac mini, 8 GB, 256 GB.** A Mac mini 2020 with Apple M1, 8 GB and
256 GB at $299 in mint condition is listed on Swappa. Live Swappa listings at this
configuration span roughly $265 to $478 depending on condition.
<https://swappa.com/listing/view/LYHH77291>

**The M1 Mac mini shares one pool of memory between CPU and GPU**, and local runtimes
reach its GPU through Apple's Metal API. The operating system draws on that same pool,
which is the video's point that an 8 GB machine does not hand a model eight empty
gigabytes. The memory is soldered, so 8 GB is a permanent ceiling on that unit.

**Activation Lock and remote management are real blockers on a used Mac.** A Mac still
signed in to a previous owner's Apple Account, or still enrolled in an organisation's
mobile device management, will ask for those credentials during setup and cannot be
cleared by the buyer.

## Not sourced

Three figures the narration states could not be chased to a primary source. None of
them is rendered as a figure on screen.

- **The eBay OptiPlex 7060 listing at $276.35 from the seller IT Supply Guy**, with free
  shipping and 30 day seller paid returns. eBay serves an error page to an automated
  request, so the listing could not be read or captured, and a marketplace listing is
  live inventory that changes hourly in any case. The seller exists and trades in this
  hardware; the specific price, configuration and returns terms are the script writer's
  own check and are stated as "when checked".
- **The GMKtec G10's complete 16 GB / 512 GB configuration at $329.99.** The
  configuration exists on the manufacturer's page and the $199.99 barebones base price
  is confirmed; the variant price is served by a selector that a static capture does not
  reach.
- **Whether the $299 Swappa Mac mini is a sold example or a live listing.** A $299 M1
  Mac mini at 8 GB and 256 GB on Swappa is confirmed; its sold status is not.

All three are marketplace prices, and all three carry the video's own caveat with them:
a sold listing is evidence of a past price rather than inventory anyone can order today.
{% endraw %}

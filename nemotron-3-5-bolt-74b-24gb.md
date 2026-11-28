---
layout: default
title: "NVIDIA's 74B Local AI Fits In 24GB (Nemotron 3.5 Bolt)"
permalink: /nemotron-3-5-bolt-74b-24gb/
date: 2026-11-28
---

# NVIDIA's 74B Local AI Fits In 24GB (Nemotron 3.5 Bolt)

{% raw %}
Every figure the video quotes, and where it comes from. Prices were read live on 28 November 2026
(the full price table, with each listing's exact configuration, is in PRICES.md). The script was
supplied finished; the red-team corrections made before recording are in CUT.md's header.

## The model and its size

- **NVIDIA Nemotron 3.5 Bolt technical report.** 74B total parameters, 9B active (74B-A9B);
  148GB in BF16; the 24GB release is a 22.1GB file with the experts at 2.0625 bits; NVIDIA's own
  memory table sums to 22.87GB with the context cache (21.3 GiB: weights 20.50, chat memory 0.58,
  work space 0.23); 40 of Bolt's layers are Mamba layers. 2-bit against BF16 Bolt: Terminal-Bench
  2.1 50.98 vs 53.93, AA-Omniscience accuracy 16.90 vs 21.80. NVIDIA's runs against Qwen 3.6
  35B-A3B (Bolt ahead on 11 of 14), BrowseComp, and the facts test (16.9 vs Qwen 19.47 and
  Gemma 4 22.17).
  https://research.nvidia.com/labs/nemotron/files/NVIDIA-Nemotron-3.5-Bolt-74B-A9B-24GB-Technical-Report.pdf
- **NVIDIA research page.** Launch summary for the 24GB release.
  https://research.nvidia.com/labs/nemotron/Nemotron-3.5-Bolt-24GB/
- **GGUF model card (recipes).** The two named llama.cpp recipes: the smaller "28GB recipe" asks
  for a 32GB card or bigger, with the helper (LiLiCorr drafter, 0.89 GiB) and the image part
  (vision encoder, 1.56 GiB) switched on; the bigger recipe asks for 48GB.
  https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Bolt-74B-A9B-24GB-GGUF
- **BF16 model card.** The full-size model the 2-bit file is compared with.
  https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Bolt-74B-A9B-BF16

## Measured speed and memory

- **llm-speed, 3 GPUs measured (llama.cpp).** RTX 4090: 107.3 tok/s with a 4K window, 105.7 with
  16K. RTX 3090: 87.8 tok/s at 4K, 80.3 with the window set to 8K. RTX 5090: 154.7 tok/s, 2.06x
  Qwen3.8 27B Q4_K_M on the same card. VRAM peaks of 21.3 to 21.5 GiB on the 3090 and 4090.
  https://llm-speed.com/blog/nemotron-3-5-bolt-74b-24gb-measured
  https://llm-speed.com/m/nemotron-3-5-bolt-74b-a9b
- **Elite Test Engineering, RTX 4090 run.** 108.6 tok/s on its own RTX 4090 run.
  https://elitetestengineering.substack.com/p/nemotron-35-bolt-74b-rtx-4090-iq2
- **Kingy, Ryzen AI Max+ 395 run.** Bolt on a 128GB Ryzen AI Max+ 395 mini PC, slower than every
  NVIDIA card here.
  https://kingy.ai/blog/nemotron-3-5-bolt-74b-at-home/
- **RX 7900 XTX.** No published Bolt run found on 28 November 2026 ("I couldn't find a single
  published run").

## Prices (28 November 2026, PRICES.md)

- Used RTX 3090 $1,921, used RTX 4090 $3,500, used RX 7900 XTX $1,455 (RigPrice typical eBay
  asking price): https://rigprice.com/gpu/rtx-3090/ https://rigprice.com/gpu/rtx-4090/
  https://rigprice.com/gpu/rx-7900-xtx/
- RTX 5090 $6,499.99 on Newegg's Black Friday deal:
  https://www.newegg.com/p/pl?d=rtx+5090+graphics+card&N=100007709%204131&Order=1
- GMKtec EVO-X2 (Ryzen AI Max+ 395, 128GB) $3,499.99:
  https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc?variant=48746069262490

## Our own arithmetic

- Dollars per tok/s: $1,921 / 87.8 = $21.88 (3090), $3,500 / 107.3 = $32.62 (4090),
  $6,499.99 / 154.7 = $42.02 (5090). 5090 against the used 3090 per tok/s: 1.92x.
- GB to GiB: NVIDIA's 22.87GB = 21.30 GiB (20.50 + 0.58 + 0.23); add the helper (0.89) and the
  image part (1.56) as NVIDIA's slabs and the column reaches 23.75 GiB of 24.

## Strata

- Strata releases (for 12GB cards): https://github.com/niko1221/strata/releases
{% endraw %}

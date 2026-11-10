---
layout: default
title: "The Best Local AI Image Generator For Every GPU"
permalink: /best-local-ai-image-generator-every-gpu/
date: 2026-11-10
---

# The Best Local AI Image Generator For Every GPU

{% raw %}
Every figure in the video comes from a published page below, read on 9 November 2026. We ran
no tests of our own. Every image on screen was made by the model it is labelled with, taken
from that model's maker or from a published same-prompt test, and is credited on screen.

## The models (makers' own pages)

**Z-Image Turbo** (Alibaba Tongyi), released 26 November 2025, Apache 2.0, 6B parameters,
8 steps, Qwen3-4B text encoder.
- Model card: https://huggingface.co/Tongyi-MAI/Z-Image-Turbo ("fits comfortably within 16G VRAM consumer devices")
- Repo and release date: https://github.com/Tongyi-MAI/Z-Image
- Blog and sample images: https://tongyi-mai.github.io/Z-Image-blog/
- Paper: https://arxiv.org/abs/2511.22699
- Repackaged files (bf16 transformer 12.31 GB, text encoder 8.04 GB): https://huggingface.co/Comfy-Org/Z-Image-Turbo

**FLUX.2 [klein] 4B and 9B** (Black Forest Labs), released 15 January 2026. 4B is Apache 2.0;
9B is under the FLUX Non-Commercial License.
- 4B card ("fits in ~13GB VRAM"): https://huggingface.co/black-forest-labs/FLUX.2-klein-4B
- 9B card ("fits in ~29GB VRAM", RTX 4090 and above): https://huggingface.co/black-forest-labs/FLUX.2-klein-9B
- Model page (VRAM 4B 8.4 GB, 9B 19.6 GB; RTX 5090 times ~1.2 s and ~2 s): https://bfl.ai/models/flux-2-klein
- Launch post and Elo chart: https://bfl.ai/blog/flux2-klein-towards-interactive-visual-intelligence
- Repo and sample images: https://github.com/black-forest-labs/flux2
- ComfyUI's measurements on an RTX 5090: https://blog.comfy.org/p/flux2-klein-4b-fast-local-image-editing

**FLUX.1 [schnell]** (Black Forest Labs), released 1 August 2024, Apache 2.0, 12B parameters,
1 to 4 steps, bf16 file 23.78 GB.
- Model card: https://huggingface.co/black-forest-labs/FLUX.1-schnell
- Launch post: https://bfl.ai/announcements/24-08-01-bfl
- Repo and sample grid: https://github.com/black-forest-labs/flux
- GGUF sizes: https://huggingface.co/city96/FLUX.1-schnell-gguf

**SDXL 1.0** (Stability AI), released 26 July 2023, CreativeML Open RAIL++-M.
- Model card (6.94 GB checkpoint; "does not achieve perfect photorealism", "cannot render legible text"): https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0
- Announcement ("should work effectively on consumer GPUs with 8GB VRAM"): https://stability.ai/news/stable-diffusion-sdxl-1-announcement
- Release date: https://github.com/Stability-AI/generative-models

## How good each looks

- Artificial Analysis, open-weights text-to-image board (human blind votes, read 9 Nov 2026):
  Z-Image Turbo 936, FLUX.2 [klein] 9B 932, klein 4B 840, FLUX.1 [schnell] 741; SDXL not listed.
  https://artificialanalysis.ai/image/leaderboard/text-to-image/open-weights
- Stable Diffusion Art, Z-Image Turbo against FLUX.1 dev, same prompts: https://stable-diffusion-art.com/z-image/
- Stable Diffusion Art, SDXL against FLUX.1 dev, same prompts: https://stable-diffusion-art.com/sdxl-vs-flux/
- getimg.ai, FLUX.1 schnell against SDXL, same prompts: https://getimg.ai/blog/flux-1-vs-stable-diffusion-ai-text-to-image-models-comparison
- Reddit, six models, same prompt and seed: https://www.reddit.com/r/StableDiffusion/comments/1rv7gwh/
- Reddit, Z-Image Base vs Turbo vs klein (skin detail, hands): https://reddit.com/r/StableDiffusion/comments/1rboeta/
- Wiro, klein Base 4B against Base 9B, five prompts: https://wiro.ai/blog/flux-2-klein-base-4b-vs-9b-5-prompt-image-test/
- Diffusion Doodles, klein 9B against Z-Image Turbo on an RTX 4060 Ti 16GB: https://diffusiondoodles.substack.com/p/flux2-klein-shrinking-flux2-dev

## How fast, and what fits

- ASCII.jp, Z-Image Turbo on an RTX 4070 12GB: about 18 s per 1024x1024 image; 2048x2048 sometimes out of memory: https://weekly.ascii.jp/elem/000/004/358/4358055/3/
- ComfyUI Wiki, Z-Image Turbo on an RTX 4090: 2.3 s per image: https://comfyui-wiki.com/en/news/2025-11-27-alibaba-z-image-turbo-release
- Reddit, klein 9B on 16GB and 24GB cards (edit times, an RTX 3090 owner): https://reddit.com/r/StableDiffusion/comments/1rrw4lx/ and https://reddit.com/r/StableDiffusion/comments/1roaiwk/
- Michael Dishmon, FLUX.1 schnell against Z-Image Turbo (schnell fp8 about 12 GB, a Q4 GGUF fits 8 GB): https://michaeldishmon-com.vercel.app/writing/flux-schnell-vs-z-image-turbo-quality
- Stable Diffusion Art, SDXL 13 s against FLUX.1 dev (NF4) 57 s for four 1024x1024 images on an RTX 4090 in Forge: https://stable-diffusion-art.com/sdxl-vs-flux/

## Something newer

- FLUX 3 Image Klein (Black Forest Labs, on Hugging Face October 2026): model card lists 25 to 31 GB peak memory on a data center card: https://huggingface.co/black-forest-labs/flux-3-image-klein
- Its Artificial Analysis open-weights score, 1,043 (second on the board): https://artificialanalysis.ai/image/leaderboard/text-to-image/open-weights

## Our arithmetic

- "Nearly 8 times faster" and "200 against more than 1,500 pictures an hour" are our arithmetic from the two times above (3600/18 and 3600/2.3).
- A viewer's comment under our best-and-worst GPUs video (https://youtu.be/wpCGpkUCCTs): "the 5070 ti is 8x faster than the 3060 12gb even if the model fits in memory".

## Prices (checked 9 November 2026)

- RTX 5060 8GB, $469.99 new: https://www.newegg.com/gigabyte-gv-n5060eagle-oc-8gd-geforce-rtx-5060-8gb-graphics-card-double-fans/p/N82E16814932803
- RTX 4060 8GB, $676.09 new: https://www.newegg.com/gigabyte-windforce-gv-n4060wf2oc-8gd-geforce-rtx-4060-8gb-graphics-card-double-fans/p/N82E16814932630
- RTX 3060 12GB, $459.97 new: https://www.newegg.com/gigabyte-windforce-oc-gv-n3060wf2oc-12gd-rev2-0-geforce-rtx-3060-12gb-graphics-card-double-fans/p/N82E16814932658
- RTX 3060 12GB used, about $400: https://rigprice.com/gpu/rtx-3060-12gb/
- RTX 5060 Ti 16GB, $799.99 new: https://www.newegg.com/msi-rtx-5060-ti-16g-ventus-3x-oc-geforce-rtx-5060-ti-16gb-graphics-card-triple-fans/p/N82E16814137957
- RTX 5060 Ti 16GB used, about $830: https://rigprice.com/gpu/rtx-5060-ti-16gb/
- RTX 4060 Ti 16GB, $1,037.97 new: https://www.newegg.com/p/N82E16814932659
- RTX 3090 24GB used, about $1,800: https://rigprice.com/gpu/rtx-3090/
- RTX 3090 24GB new old stock, $2,789.00: https://www.newegg.com/p/N82E16814932366
- RTX 4090 24GB used, about $3,650: https://rigprice.com/gpu/rtx-4090/
- Dollars per GB and upgrade costs are our arithmetic from these prices.

## Photos

- RTX 3060: Colorful iGame RTX 3060 12G, 极客湾Geekerwan, CC BY 3.0, Wikimedia Commons
- RTX 3090: Gigabyte GeForce RTX 3090 Eagle OC, PantheraLeo1359531, CC BY 4.0, Wikimedia Commons
- RTX 5060: PNY GeForce RTX 5060 at Computex 2025, 4300streetcar, CC BY 4.0, Wikimedia Commons
- RTX 5060 Ti: GeForce RTX 5060 Ti 16GB, PNY, FreeMediaKid!, CC BY-SA 4.0, Wikimedia Commons
{% endraw %}

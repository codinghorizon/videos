---
layout: default
title: "The Best Uncensored Local AI For Every VRAM Size"
permalink: /best-uncensored-local-ai-every-vram/
date: 2026-11-16
---

# The Best Uncensored Local AI For Every VRAM Size

{% raw %}
What every figure on screen rests on. Checked 2026-11-15 (claims verified before the script was
finalised; prices in PRICES.md). Captures and photos: qa/captures.md.

| on screen (beats) | figure | source |
|---|---|---|
| Harmless prompts refused (012-017) | XSTest: 250 safe prompts; Llama 2 70B chat, original safety prompt, fully refuses 38% | https://arxiv.org/abs/2308.01263 (captures xstest, xstest38) |
| Willingness 0-10, natural intelligence, thinking length (018-021, 082-083, 118-137) | UGI Leaderboard columns; GPT OSS 20B stock 0.5/10; Qwen3.5 9B ~16,000 characters of thinking | https://huggingface.co/spaces/DontPlanToEnd/UGI-Leaderboard |
| "0/465 refusals" (025-027) | uncensored Qwen 3.8 27B card; ~1.7M downloads in 30 days | https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF (capture hh27) |
| "zero capability loss" (028-031) | uncensored Qwen 3.5 9B card, no benchmark published | https://huggingface.co/HauhauCS/Qwen3.5-9B-Uncensored-HauhauCS-Aggressive (capture hh9) |
| 12/100 vs 98/100 (032-033) | careful uploader's held-out refusals | https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF (capture jc27) |
| 15 minutes, 45 minutes in a loop (035-038) | "Thinks way too much" discussion | https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF/discussions/15 (captures yap, yap45) |
| stock Qwen3 32B: full thinking, empty answer (043-044) | ollama-python issue 597 | https://github.com/ollama/ollama-python/issues/597 |
| abliteration, 2024, one refusal direction, 128 harmful/harmless prompts (047-053) | Arditi et al. 2024; mlabonne's write-up | https://arxiv.org/abs/2406.11717, https://huggingface.co/blog/mlabonne/abliteration |
| Heretic, KL 1.04 vs 0.16 at 3/100 refusals, Gemma 3 12B (058-065) | Heretic README, earlier commit | https://github.com/p-e-w/heretic/blob/662e4ba27e/README.md (capture heretic) |
| 23 versions, HarmBench 400, 8,000 tokens; best 95.5% vs 31%; 87 to 66; 24 empty + 39 cut off; "most broken is most downloaded" (067-079, 131-132) | DreamFast Gemma 4 E4B comparison | https://huggingface.co/DreamFast/Gemma4-e4b-abliterlitics (captures dfast, dfast2, dfast3) |
| 4K default under 24GB, 64K for agents (085-089, 101-102) | Ollama context-length docs | https://docs.ollama.com/context-length (capture ollama) |
| 64 KB per token, 32K = 2 GB (095-098) | our maths from the Qwen 3.8 27B config | https://huggingface.co/Qwen/Qwen3.8-27B/raw/main/config.json; https://sebastianraschka.com/llm-architecture-gallery/kv-cache-calculations/ |
| presence penalty (103-104) | Qwen 3.8 27B card | https://huggingface.co/Qwen/Qwen3.8-27B |
| NI 18.7 / 8.2 / 15.7 (Gemma 3 12B); 31 vs 6.3 (Qwen3.5 9B); 946K vs 20K downloads, 8.4 vs 18.7 (133-137) | UGI Leaderboard; OBLITERATUS and heretic cards | UGI as above; https://huggingface.co/OBLITERATUS/gemma-4-E4B-it-OBLITERATED (capture oblit); https://huggingface.co/coder3101/gemma-4-E4B-it-heretic |
| "Qwen3.8-9B" built on Qwen3.5-9B (148-152) | the repo's own card | https://huggingface.co/empero-ai/Qwen3.8-9B-Distill-GGUF (capture empero) |
| ~244K downloads in under 18 hours, malware (153-157) | HiddenLayer research | https://www.hiddenlayer.com/research/malware-found-in-trending-hugging-face-repository-open-oss-privacy-filter (capture hidden) |
| 8GB pick: Qwen3.5 9B heretic v2, 5.6GB, 6/100, NI 24 vs 20 (163-169) | model card, GGUF sizes, UGI | https://huggingface.co/trohrbaugh/Qwen3.5-9B-heretic-v2 |
| 12GB pick: Gemma 4 12B heretic, 9.8GB, MMLU 73 vs 76 (170-173) | model card | https://huggingface.co/llmfan46/gemma-4-12B-it-uncensored-heretic |
| 16GB pick: GPT OSS 20B heresy, 12.3GB, willingness 10; reasoning effort low/medium/high (174-181) | model card; OpenAI card | https://huggingface.co/MuXodious/gpt-oss-20b-RichardErkhov-heresy; https://huggingface.co/openai/gpt-oss-20b |
| 24/32GB pick: Gemma 4 31B heretic, 18.7GB Q4 / 25.2GB Q6, NI 36.5 vs 38.9 (182-198) | model card (capture g31), GGUF sizes, UGI | https://huggingface.co/coder3101/gemma-4-31B-it-heretic |
| $1,900 used 3090, $7,250 5090, $227 and $79 per GB (191-202) | PRICES.md | https://rigprice.com/gpu/rtx-3090/, https://rigprice.com/gpu/rtx-5090/ |
{% endraw %}

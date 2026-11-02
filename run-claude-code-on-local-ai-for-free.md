---
layout: default
title: "Run Claude Code On Local AI For Free"
permalink: /run-claude-code-on-local-ai-for-free/
date: 2026-11-02
---

# Run Claude Code On Local AI For Free

{% raw %}
The sources the script cites, as listed with it, checked on 2026-11-01. Nothing here was tested by us; every figure is someone else's published number.

- Claude Code setup (install commands, account requirement): https://code.claude.com/docs/en/setup
- Claude Code LLM gateway (Anthropic does not support routing Claude Code to non-Claude models): https://code.claude.com/docs/en/llm-gateway
- Claude Code gateway connection (ANTHROPIC_AUTH_TOKEN takes precedence, WebFetch domain check calls api.anthropic.com, Remote Control and voice dictation unavailable, CLAUDE_CODE_DISABLE_EXPERIMENTAL_BETAS): https://code.claude.com/docs/en/llm-gateway-connect
- Claude Code gateway protocol (/v1/messages, count_tokens optional with character-based fallback, thinking retries): https://code.claude.com/docs/en/llm-gateway-protocol
- Claude Code environment variables (ANTHROPIC_BASE_URL, ANTHROPIC_AUTH_TOKEN, ANTHROPIC_DEFAULT_HAIKU_MODEL used for background functionality): https://code.claude.com/docs/en/env-vars
- Claude Code model configuration (unknown models assumed 200K context; CLAUDE_CODE_MAX_CONTEXT_TOKENS, compaction at the declared window): https://code.claude.com/docs/en/model-config
- Claude Code tools reference (WebSearch availability): https://code.claude.com/docs/en/tools-reference
- Claude Code /context breakdown, system prompt 2.6K and system tools 17.6K tokens (Mukesh Murugan): https://codewithmukesh.com/blog/anatomy-claude-code-session/
- Claude Code first-request overhead of about 32,800 tokens on 2.1.207 (Gigazine, July 2026): https://gigazine.net/gsc_news/en/20260713-claude-code-consuming-token
- Claude plans (Pro $20, Max $100, Ultra $200 a month): https://claude.com/pricing
- Ollama Anthropic API compatibility for Claude Code, v0.14.0 (January 16, 2026): https://ollama.com/blog/claude
- ollama launch, v0.15 (January 23, 2026): https://ollama.com/blog/launch
- Ollama Claude Code integration (ANTHROPIC_AUTH_TOKEN=ollama, ANTHROPIC_API_KEY="", base URL localhost:11434, 64K+ context, hosted WebSearch not fully supported, Ollama web search API): https://docs.ollama.com/integrations/claude-code
- Ollama context length defaults (4K under 24 GiB VRAM; coding tools at least 64000): https://docs.ollama.com/context-length
- Ollama Anthropic compatibility limits (no count_tokens, cache_control, PDFs, URL images): https://docs.ollama.com/api/anthropic-compatibility
- llama.cpp Anthropic Messages API (January 19, 2026): https://huggingface.co/blog/ggml-org/anthropic-messages-api-in-llamacpp
- LM Studio API changelog (Anthropic-compatible /v1/messages in 0.4.1): https://lmstudio.ai/docs/developer/api-changelog
- LM Studio Claude Code guide (more than ~25K context): https://lmstudio.ai/docs/integrations/claude-code
- Qwen3.6 35B-A3B model card (35B total, 3B active, SWE-bench Verified 73.4): https://huggingface.co/Qwen/Qwen3.6-35B-A3B
- Ollama qwen3.6 (35B-A3B, 23GB): https://ollama.com/library/qwen3.6
- RTX 3050 6GB with 24GB RAM, Qwen3.6 35B-A3B Q4_K_M at 30 tok/s, about 22 at full 64K (llamaperf report): https://llamaperf.com/report/7b5b9eac-fc77-47b1-a24a-55d370ff99a3
- RTX 3090, Qwen3.6 35B-A3B UD-Q4_K_XL in llama.cpp at 65K context, 101.7 / 80.9 tok/s, 24.2GB, q8_0 KV cache (Amine Raji): https://aminrj.com/posts/llamacpp-qwen36-35b/
- Claude Sonnet 4.6 SWE-bench Verified 79.6 (Anthropic system card, February 2026): https://www.anthropic.com/claude-sonnet-4-6-system-card
- Claude Sonnet 5.5 (current model, Terminal-Bench 4.0 figures instead of SWE-bench Verified): https://www.anthropic.com/claude-sonnet-5-5
- gpt-oss-20b and gpt-oss-120b model card (SWE-bench Verified 60.7 and 62.4): https://arxiv.org/html/2508.10925
- Ollama gpt-oss (20b 14GB, 120b 65GB): https://ollama.com/library/gpt-oss
- RTX 5060 Ti 16GB, gpt-oss 20B MXFP4: 58.1 tok/s at 64K, 2,753.3 tok/s prompt processing at 16K (Hardware Corner): https://www.hardware-corner.net/gpu-llm-benchmarks/rtx-5060-ti-16gb/
- RTX 5060 Ti 16GB, $799.99 new, cheapest on Newegg: https://www.newegg.com/p/pl?d=rtx+5060+ti+16gb&N=4131&Order=1
- Used RTX 3090 asking prices, median $1,796 (RigPrice): https://rigprice.com/gpu/rtx-3090/
- Qwen 3.8 27B Q4_K_S on RTX 3090, 33.95 tok/s at 64K (Hardware Corner): https://www.hardware-corner.net/qwen3-8-27b-hardware-tests/
- Qwen 3.8 27B model card (dense 27B, no SWE-bench Verified figure): https://huggingface.co/Qwen/Qwen3.8-27B
- Qwen3-Coder-Next model card (80B total, 3B active, SWE-bench Verified 70.6): https://huggingface.co/Qwen/Qwen3-Coder-Next
- Ollama qwen3-coder-next (52GB q4_K_M): https://ollama.com/library/qwen3-coder-next
- Qwen3-Coder-Next 4-bit MLX on M4 Max 128GB, 84.4 tok/s, 43GB peak (oMLX): https://omlx.ai/benchmarks/16o42k14
- GMKtec EVO-X2, Ryzen AI Max+ 395, 128GB, $3,499.99: https://www.gmktec.com/products/amd-ryzen%E2%84%A2-ai-max-395-evo-x2-ai-mini-pc
- gpt-oss-120b MXFP4 on a GMKtec EVO-X2 128GB, Vulkan llama.cpp, 52.6 tok/s at depth 0 and 36.2 at 32K (Framework community): https://community.frame.work/t/dgx-spark-vs-strix-halo-initial-impressions/77055
- Qwen 3.8 Flash-Next 4-bit needs 96-114GB (Unsloth): https://unsloth.ai/docs/models/qwen3.8-next
- Qwen 3.8 Flash-Next model card (license, no SWE-bench Verified figure): https://huggingface.co/Qwen/Qwen3.8-Flash-Next
- Strata v0.1.16 (Coder option, 91% of full SWE-bench Verified claimed): https://github.com/Niko1221/Strata/releases/tag/v0.1.16

## Derived figures (our arithmetic on the numbers above)

- Claude Code's opening context: 2.6K system prompt + 17.6K tools = about 20K tokens before the first message.
- GPT-OSS 20B on the 5060 Ti reads those ~20K tokens in about 7.3 s at 2,753 tok/s prefill.
- A used RTX 3090 at about $1,800 = 90 months of Pro ($20), 18 months of Max ($100), 9 months of the $200 plan, before power.
- gpt-oss-120b (62.4) on a 128GB box scores below Qwen3.6 35B-A3B (73.4), which fits a 24GB card.
{% endraw %}

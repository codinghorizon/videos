---
layout: default
title: "Your Local AI Leaks More Than You Think (7 Ways)"
permalink: /your-local-ai-leaks-more-than-you-think/
date: 2026-10-31
---

# Your Local AI Leaks More Than You Think (7 Ways)

{% raw %}
Every figure in the video, and where it comes from. All pages opened on 2026-10-30. We did not test any of this ourselves.

## Exposed Ollama servers
- 175,108 unique exposed Ollama hosts in 130 countries, over 48% advertise tool calling (SentinelOne SentinelLABS and Censys, January 2026): https://www.sentinelone.com/labs/silent-brothers-ollama-hosts-form-anonymous-ai-network-beyond-platform-guardrails
- Coverage of the same study (The Hacker News): https://thehackernews.com/2026/01/researchers-find-175000-publicly.html
- 1,139 exposed Ollama servers, 214 serving models (Cisco Talos, September 2025): https://blogs.cisco.com/security/detecting-exposed-llm-servers-shodan-case-study-on-ollama
- Ollama FAQ: binds 127.0.0.1 port 11434 by default, OLLAMA_HOST=0.0.0.0 exposes it, local only mode by disabling cloud features: https://docs.ollama.com/faq

## Docker
- Published ports bind to all host addresses by default, and to 127.0.0.1 when given (Docker docs): https://docs.docker.com/engine/network/port-publishing/
- Published ports bypass ufw rules (Docker docs): https://docs.docker.com/engine/network/packet-filtering-firewalls/
- The Ollama image and its run command with -p 11434:11434: https://hub.docker.com/r/ollama/ollama

## Cloud models inside local apps
- Ollama cloud models and web search: https://docs.ollama.com/cloud
- LM Studio app privacy policy: https://lmstudio.ai/app-privacy

## Telemetry in editor plugins
- Continue's telemetry page (PostHog, the "Allow Anonymous Telemetry" toggle, what is and is not collected), Continue docs on GitHub as published until March 2026. The page was removed from the live docs on 2026-03-24: https://github.com/continuedev/continue/blob/bd36638ee0cf9fb90c314647bab2f1c6897aa6fe/docs/customize/telemetry.mdx

## Chats on disk, and Recall
- LM Studio keeps conversations as JSON files in ~/.lmstudio/conversations: https://lmstudio.ai/docs/app/basics/chat
- Windows Recall is opt in, with snapshots encrypted and kept on the device (Microsoft): https://support.microsoft.com/en-us/windows/privacy-and-control-over-your-recall-experience-d404f672-7647-41e5-886c-a3c59680af15

## Poisoned model files, and Probllama
- About 100 malicious models on Hugging Face, one payload opening a reverse shell (JFrog): https://jfrog.com/blog/data-scientists-targeted-by-malicious-hugging-face-ml-models-with-silent-backdoor/
- Coverage of the JFrog findings (Dark Reading): https://www.darkreading.com/application-security/hugging-face-ai-platform-100-malicious-code-execution-models
- Probllama, CVE-2024-37032, fixed in Ollama 0.1.34, over 1,000 exposed instances (Wiz): https://www.wiz.io/blog/probllama-ollama-vulnerability-cve-2024-37032
- Coverage of Probllama (The Hacker News): https://thehackernews.com/2024/06/critical-rce-vulnerability-discovered.html

## Agents and prompt injection
- Data exfiltration through markdown image rendering, fixed in Continue (VerSprite): https://versprite.com/blog/data-exfiltration-via-image-rendering-fixed-in-continue/
- A one pixel image can leak your data in HuggingChat (PromptArmor): https://www.promptarmor.com/resources/a-one-pixel-image-can-leak-your-data-in-huggingchat

## Firewalls
- LuLu, the free open source macOS firewall (Objective-See): https://github.com/objective-see/LuLu
- Portmaster, free application firewall for Windows and Linux (Safing): https://safing.io/
- Little Snitch, Single License €59, a three hour demo mode, macOS Sonoma or newer (Objective Development): https://www.obdev.at/products/littlesnitch/download.html

## Prices (checked 2026-10-30)
- Mac mini M6, 16GB / 256GB, $899 at the Apple store: https://www.apple.com/shop/buy-mac/mac-mini
- Mac mini M6 memory bandwidth, 153GB/s: https://www.apple.com/mac-mini/specs/
- A monthly chatbot plan, $20 a month (ChatGPT Plus): https://openai.com/chatgpt/pricing/
- Derived: $899 / 16GB = about $56 per GB; $899 / $20 = about 45 months; €59 / 36 months = about €1.64 a month.
{% endraw %}

---
layout: default
title: "The Best Offline Local AI For When The Internet Dies"
permalink: /offline-local-ai-when-the-internet-dies/
date: 2026-11-02
---

# The Best Offline Local AI For When The Internet Dies

{% raw %}
The sources the script cites, as listed with it, plus the sums the video does with them.
Prices were checked on 2026-11-02; several are sale or pre-order prices on the maker's own
store, and PRICES.md has every one with its formula.

## Sources
- Raspberry Pi 5 8GB, $175.00 (PiShop.us): https://www.pishop.us/product/raspberry-pi-5-8gb/
- Raspberry Pi 5 16GB, "available now for $305" (Raspberry Pi): https://www.raspberrypi.com/products/raspberry-pi-5/
- Raspberry Pi 5 power supply and USB current limits (600mA on a 3A supply, USB boot disabled by default): https://www.raspberrypi.com/documentation/computers/raspberry-pi.html
- Raspberry Pi 5 off-state draw of about 1 to 1.4W, 0.01W with POWER_OFF_ON_HALT=1 (Raspberry Pi documentation): https://www.raspberrypi.com/documentation/computers/raspberry-pi.html
- The same setting in the documentation's source, as shown on screen: https://github.com/raspberrypi/documentation/blob/master/documentation/asciidoc/computers/raspberry-pi/rtc.adoc
- Pi 5 8GB 3.2W idle (Jeff Geerling): https://www.jeffgeerling.com/blog/2024/new-2gb-pi-5-has-33-smaller-die-30-idle-power-savings/
- Ollama benchmarks with peak power: Pi 5 8GB llama3.2:3b 4.61 tok/s at 13.9W, Pi 5 16GB 4.88 tok/s, GMKtec G3 Plus N150 llama3.2:3b 9.06 tok/s at 26.4W and DeepSeek R1 14B 2.13 tok/s, RTX 3060 desktop 224W on DeepSeek R1 14B (Jeff Geerling): https://github.com/geerlingguy/ollama-benchmark
- Pi 5 Ollama speeds at Q4_K_M, gemma3:1b 11.53 tok/s (Stratosphere Lab): https://stratospherelinuxips.readthedocs.io/en/develop/immune/research_rpi_llm_performance.html
- Anker 737 Power Bank (PowerCore 24K), 24,000mAh, $109.99 on sale: https://www.anker.com/products/a1289
- Beelink EQ14 N150 16GB/500GB, $385 pre-order (usually $429), 12V/4A adapter: https://us.bee-link.com/products/beelink-eq14-n150
- EcoFlow RIVER 3 Plus, 286Wh LiFePO4, $279 on sale (usually $299): https://us.ecoflow.com/products/ecoflow-river-3-plus-portable-power-station-flash-sale
- GMKtec K8 Plus Ryzen 7 8845HS 32GB/1TB, $919.99 on sale (usually $1,099.99): https://www.gmktec.com/products/gmktec-nucbox-k8-plus-mini-pc-amd-ryzen%E2%84%A2-7-8845hs
- Beelink SER8 (Ryzen 7 8845HS, the same chip as the K8 Plus) 7-10W idle, 77-79W under stress-ng (ServeTheHome): https://www.servethehome.com/beelink-ser8-review-amd-ryzen-7-8845hs-powered-mini-pc/3/
- llama.cpp Vulkan scoreboard, Llama 2 7B Q4_0 tg128, AMD Ryzen 8000 Series 19.81 tok/s: https://github.com/ggml-org/llama.cpp/discussions/10879
- EcoFlow DELTA 3, 1,024Wh, $579 on sale (usually $699): https://us.ecoflow.com/products/delta-3-portable-power-station
- RTX 3060 12GB, Llama 3.1 8B Q4_K_M at 51.3 tok/s (LocalScore): https://www.localscore.ai/model/1
- Jackery runtime formula, capacity x 0.85 / watts: https://www.jackery.com/blogs/buying-advice/what-can-jackery-300-plus-run
- Jackery SolarSaga 100 Prime, $199 on sale (usually $249): https://www.jackery.com/products/jackery-solarsaga-100-prime-solar-panel
- PVGIS solar calculator (European Commission JRC), 100W fixed panel at the optimal angle, 14% loss: London about 120Wh a day in December and 400Wh in June, Seattle about 150Wh and Phoenix about 420Wh in December: https://re.jrc.ec.europa.eu/pvg_tools/en/
- Kiwix Wikipedia files as Kiwix lists them: wikipedia_en_all_maxi_2026-08 119G, nopic 49G, mini 13G, WikiMed 1.7G: https://download.kiwix.org/zim/wikipedia/
- Kiwix iFixit 3.3GB: https://download.kiwix.org/zim/ifixit/
- Kiwix Stack Exchange, diy.stackexchange.com 1.9GB: https://download.kiwix.org/zim/stack_exchange/
- Kiwix Project Gutenberg, gutenberg_en_all 206GB: https://download.kiwix.org/zim/gutenberg/
- Kiwix reader platforms, free: https://get.kiwix.org/en/solutions/applications/kiwix-reader/
- kiwix-serve, runs on Raspberry Pi Zero: https://get.kiwix.org/en/solutions/applications/kiwix-server/
- Organic Maps, free, 100% of features offline: https://organicmaps.app/
- Organic Maps map file sizes (our sums from countries.json, data version 260714): https://raw.githubusercontent.com/organicmaps/organicmaps/master/data/countries.json
- Ollama runs locally; OLLAMA_HOST for network access: https://docs.ollama.com/faq
- Ollama model sizes: https://ollama.com/library/llama3.2, https://ollama.com/library/gemma3, https://ollama.com/library/qwen3
- Project N.O.M.A.D. (Kiwix, Ollama, Kolibri, ProtoMaps; 4GB RAM minimum without AI, 32GB and a Ryzen 7 or Core i7 recommended with AI): https://github.com/Crosstalk-Solutions/project-nomad
- Internet-in-a-Box, free and open source: https://internet-in-a-box.org/
- PrepperDisk Premium 512GB $297.00, software on SD card $165.00: https://prepperdisk.com/products.json

## Our sums
Every runtime uses Jackery's formula: usable watt hours = capacity x 0.85, hours = usable / watts.
- Anker 737: 24,000mAh x 3.6V = 86.4Wh; x 0.85 = 73.4Wh usable.
- Pi 5 nonstop at 13.9W: 73.4 / 13.9 = 5.3 hours. Answering a tenth of the time: 0.1 x 13.9 + 0.9 x 3.2 = 4.27W, 73.4 / 4.27 = 17.2 hours. Idle at 3.2W: 73.4 / 3.2 = 22.9 hours.
- RIVER 3 Plus: 286 x 0.85 = 243Wh usable.
- DELTA 3: 1,024 x 0.85 = 870Wh usable. K8 Plus at 79W: 11 hours; at 10W idle: 87 hours (three and a half days). Desktop with RTX 3060 at 224W: 3.9 hours.
- Price per watt hour: Anker $109.99 / 86.4 = $1.27; RIVER 3 Plus $279 / 286 = $0.98; DELTA 3 $579 / 1,024 = $0.57.
- Full Wikipedia download: 119GiB = 127.4GB = 1,019 gigabits; at 100Mbps that is 10,190 seconds, about 2 hours 50 minutes.
- Solar Pi: a mostly idle Pi at about 3.75W uses about 90Wh a day, under London's December 120Wh.

## Not checked
- Runtimes are worked from published peak and idle draws, not measured on our own kit; a different model, screen or USB drive changes them.
- The Ryzen box's draw is ServeTheHome's figure for a Beelink SER8 with the same chip, not the K8 Plus itself.
- The N150 speeds are Geerling's GMKtec G3 Plus, not the Beelink EQ14.
- The gaming PC figure is one desktop with an RTX 3060; other PCs will differ.
{% endraw %}

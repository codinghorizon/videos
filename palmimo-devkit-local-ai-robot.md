---
layout: default
title: "This $4,000 Robot Exposes The Local AI Trap Now"
permalink: /palmimo-devkit-local-ai-robot/
date: 2026-09-09
---

# This $4,000 Robot Exposes The Local AI Trap Now

{% raw %}
Every figure this video puts on screen, chased to a primary source. Verified 2026-09-08.

## Palmimo DevKit

Primary sources: the Jizai product site [palmimo.dev/en](https://palmimo.dev/en), the Jizai
press release on [PR TIMES, 3 September 2026](https://prtimes.jp/main/html/rd/p/000000021.000145251.html),
and the Apache-2.0 SDK at [github.com/Jizai-inc/palmimo-devkit](https://github.com/Jizai-inc/palmimo-devkit).

| Figure | Value | Source |
| --- | --- | --- |
| Maker | Jizai, Japan | [palmimo.dev/en](https://palmimo.dev/en) |
| Dimensions | 400 x 300 x 300 mm | [Specs, palmimo.dev/en](https://palmimo.dev/en#specs) |
| Weight | approx. 2 kg | [Specs, palmimo.dev/en](https://palmimo.dev/en#specs) |
| Legs | six | [github.com/Jizai-inc/palmimo-devkit](https://github.com/Jizai-inc/palmimo-devkit) |
| Degrees of freedom | 21 axes, legs 3 x 6 = 18 plus neck 3 | [Specs, palmimo.dev/en](https://palmimo.dev/en#specs) |
| Actuators | DYNAMIXEL XC330-M288-T x 21, 5 V | [Specs, palmimo.dev/en](https://palmimo.dev/en#specs) |
| Compute | Raspberry Pi 5, 16 GB, plus a servo interface board over USB to serial at 1 Mbps | [Specs, palmimo.dev/en](https://palmimo.dev/en#specs) |
| Camera | 5 MP USB camera | [Specs, palmimo.dev/en](https://palmimo.dev/en#specs) |
| Audio | ReSpeaker mic array, 3 W stereo speakers | [Specs, palmimo.dev/en](https://palmimo.dev/en#specs) |
| Display | 2.8 inch round touch display, 480 x 480, RP2350 | [Specs, palmimo.dev/en](https://palmimo.dev/en#specs) |
| Connectivity | Wi-Fi 802.11, Bluetooth 5.0, USB | [Specs, palmimo.dev/en](https://palmimo.dev/en#specs) |
| Power | DC 5 V adapter plus 27 W USB PD | [Specs, palmimo.dev/en](https://palmimo.dev/en#specs) |
| Operating system | Raspberry Pi OS 64-bit | [Specs, palmimo.dev/en](https://palmimo.dev/en#specs) |
| Language | Python 3.12 or newer, with a Python SDK | [Specs](https://palmimo.dev/en#specs), [README Quickstart](https://github.com/Jizai-inc/palmimo-devkit) |
| Price | 598,000 yen excluding tax, which Jizai gives as approximately 3,980 US dollars | [Specs, palmimo.dev/en](https://palmimo.dev/en#specs) |

The price is explicitly an early one. Jizai lists it as "Early price / For Early Builders /
Early Partners" and footnotes it: "Prices exclude tax and are unit prices for companies and
research institutions. USD figures are approximate. The offering above applies to the
initial lot; terms may change for later lots." The press release calls it an early access
price with no monthly fees and a 30 day initial warranty.

### The MCP tool surface

Palmimo serves its robot actions over the Model Context Protocol through
`palmimo_sdk.mcp`, over stdio or streamable HTTP, with optional bearer token auth. The
[MCP server guide](https://docs.palmimo.dev/guides/mcp-server/) says any MCP speaking
client can "list and call them directly".

The complete registry is 24 tools, declared in
[`agent/tools.py`](https://github.com/Jizai-inc/palmimo-devkit/blob/main/packages/palmimo_sdk/palmimo_sdk/agent/tools.py):

`forward` `backward` `turn` `strafe` `creep` `dance` `body_tilt` `pushup` `wave`
`wave_both` `clap` `bow` `stretch` `nod` `head_shake` `sleep` `wake_up` `look`
`look_center` `set_face` `show_emoji` `say` `capture` `stop`

### Dry run

Jizai's own term. The product site says "In dry-run mode, you can try every motion API
before the robot even arrives", and the README says "every motion computes in dry-run,
with no hardware attached, before it ever reaches a servo".

### What is open

From the README section "What's open, and what ships":

- Open now, Apache-2.0: the `palmimo_sdk` Python SDK and drivers, the agent layer and MCP
  server, the example agents, the LeRobot plugins, the diagnostics and the docs.
- Opening progressively: more of the development stack, starting with the robot model for
  simulation and environments for robot learning.
- Not published: the manufacturing design of the hardware. The licence section adds
  "Hardware design files are not included at this time".

## MicroDuck

Primary sources: [pollen-robotics.com/microduck](https://pollen-robotics.com/microduck/)
and [github.com/pollen-robotics/microduck](https://github.com/pollen-robotics/microduck).
Pollen Robotics is part of Hugging Face.

| Figure | Value | Source |
| --- | --- | --- |
| Height | 25 cm | [pollen-robotics.com/microduck](https://pollen-robotics.com/microduck/) |
| Motors | 15 | [pollen-robotics.com/microduck](https://pollen-robotics.com/microduck/) |
| Sensing | camera, LiDAR, two IMUs | [pollen-robotics.com/microduck](https://pollen-robotics.com/microduck/) |
| Onboard policy loop | 50 Hz | [pollen-robotics.com/microduck](https://pollen-robotics.com/microduck/) |
| Compute | Rockchip RK3566 | [github.com/pollen-robotics/microduck](https://github.com/pollen-robotics/microduck) |
| Price | 399 US dollars, introductory, before taxes and shipping | [pollen-robotics.com/microduck](https://pollen-robotics.com/microduck/) |

The reinforcement learning stack is public: MuJoCo for physics, PPO for training, a
sim to real recipe and an ONNX export, in
[microduck_rl](https://github.com/pollen-robotics/microduck_rl). Pollen publishes seven
policies, one per shipped move, and describes the loop as train in simulation, deploy on
the robot, refine the simulation, publish the policy.

## NVIDIA Jetson Orin Nano Super Developer Kit

| Figure | Value | Source |
| --- | --- | --- |
| AI performance | 67 INT8 TOPS, sparse. The dense figure is 33 TOPS | [nvidia.com](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-orin/nano-super-developer-kit/), [nvidia.com/en-gb](https://www.nvidia.com/en-gb/autonomous-machines/embedded-systems/jetson-orin/) |
| GPU | 1024 core NVIDIA Ampere architecture GPU with 32 Tensor Cores | [nvidia.com](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-orin/nano-super-developer-kit/) |
| Memory | 8 GB 128 bit LPDDR5 | [nvidia.com](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-orin/nano-super-developer-kit/) |
| Memory bandwidth | 102 GB/s | [nvidia.com](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-orin/nano-super-developer-kit/) |
| CPU | 6 core Arm Cortex-A78AE, 1.7 GHz | [nvidia.com](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-orin/nano-super-developer-kit/) |
| Power | 7 W to 25 W | [nvidia.com](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-orin/nano-super-developer-kit/) |
| Price | 399 US dollars | [NVIDIA Jetson FAQ](https://developer.nvidia.com/embedded/faq) |

The widely repeated 249 dollar figure was the December 2024 launch price and is stale:
NVIDIA raised Jetson pricing in July 2026.

## Raspberry Pi AI HAT+ and Raspberry Pi 5

| Figure | Value | Source |
| --- | --- | --- |
| AI HAT+ top variant | Hailo-8, 26 TOPS | [raspberrypi.com/products/ai-hat](https://www.raspberrypi.com/products/ai-hat/) |
| AI HAT+ lower variant | Hailo-8L, 13 TOPS | [Raspberry Pi documentation](https://www.raspberrypi.com/documentation/accessories/ai-hat-plus.html) |
| What it is for | object detection, image segmentation, pose estimation, camera post processing, robotics | [raspberrypi.com/products/ai-hat](https://www.raspberrypi.com/products/ai-hat/) |
| AI HAT+ launch prices | 70 dollars for 13 TOPS, 110 dollars for 26 TOPS | [Raspberry Pi announcement](https://www.raspberrypi.com/news/raspberry-pi-ai-hat/) |
| Raspberry Pi 5, 16 GB | 305 US dollars | [raspberrypi.com/products/raspberry-pi-5](https://www.raspberrypi.com/products/raspberry-pi-5/) |

The 120 dollar figure for a 16 GB Pi 5 was its launch price and is stale. Raspberry Pi has
run several memory driven price rises, citing "an unprecedented rise in the cost of LPDDR4
memory, thanks to competition for memory fab capacity from the AI infrastructure roll-out".

## Caveats

- **MicroDuck's weight.** Pollen states approximately 800 g, on both the product page and
  the README. No primary source says "under" 800 g, so the weight is not shown on screen.
- **MicroDuck's depth sensing.** Pollen's product page says LiDAR; Pollen's own repository
  calls the same part a ToF depth sensor. Both are primary and they disagree. The screen
  follows the product page.
- **The Jetson's 67 TOPS is sparse INT8.** The dense figure is 33 TOPS. The screen states
  the precision rather than the bare number.
- **26 TOPS is the top of the AI HAT+, but no longer Raspberry Pi's fastest accelerator.**
  The later AI HAT+ 2 carries a Hailo-10H at 40 TOPS INT4 with 8 GB of its own memory, and
  Raspberry Pi's documentation says only that board has the memory to run language models.
- **The AI HAT+ 26 TOPS current price.** 110 dollars is confirmed as the launch price from
  Raspberry Pi's own announcement. The product page now renders prices client side and
  exposes only "from $70", so the current price of the 26 TOPS variant is not confirmed and
  is not shown on screen.
- **Ten MicroDucks.** At the 399 dollar introductory price, ten come to 3,990 dollars
  against Palmimo's approximately 3,980, so the comparison is a rounding rather than exact.
- **No US storefront for Palmimo.** The 3,980 dollar figure is Jizai's own approximation
  beside the yen price; purchase is through a request form, not a dollar checkout.
- **Everything here is pre release.** The Palmimo repository carries a pre-release badge and
  the spec table is footnoted "Specifications may change without notice".
{% endraw %}

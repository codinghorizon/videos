---
layout: default
title: "Hugging Face Just Made AI Physical For Only $399"
permalink: /hugging-face-microduck-programmable-ai-robot/
date: 2026-08-29
---

# Hugging Face Just Made AI Physical For Only $399

{% raw %}
Every figure, name and claim the finished picture puts on screen, chased to a primary
source. Ordered by where it appears.

## The product

**Price: $399, introductory, before taxes and shipping.**
Pre-orders opened 27 August 2026.
Source: Pollen Robotics store listing, https://store.pollen-robotics.com/products/microduck
Source: Pollen Robotics press kit, https://pollen-robotics.com/microduck/press-kit/

**First deliveries targeted before Christmas 2026.**
The store lists availability at launch in the US, Canada, the EU, the UK, Norway,
Switzerland, Japan and South Korea. The UK is listed separately from the EU, which is why
the narration names it separately.
Source: https://store.pollen-robotics.com/products/microduck

**Made by Pollen Robotics with Hugging Face.** Pollen Robotics is Hugging Face's robotics
company.
Source: https://pollen-robotics.com/microduck/

**25 cm tall, 14 cm wide, under 800 g.** The press kit gives the mass as 780 g.
Source: https://pollen-robotics.com/microduck/press-kit/

**15 motors.** Fifteen degrees of freedom across the legs, head and neck.
Source: https://pollen-robotics.com/microduck/press-kit/

**Sensors: a front facing camera, a compact 8x8 time of flight matrix, and two IMUs**, one
in the body and one in the head. The narration calls the time of flight matrix lidar,
which is what the product page calls it.
Source: https://pollen-robotics.com/microduck/press-kit/

**An articulated grasping beak** that picks up objects.
Source: https://pollen-robotics.com/microduck/

**Compute: a Rockchip RK3566 with an AI accelerator, 1 GB RAM, 32 GB storage, Wi-Fi and
Bluetooth.** A removable NP-F550 battery, about an hour of runtime.
Source: https://pollen-robotics.com/microduck/press-kit/

**A gamepad is included.**
Source: https://store.pollen-robotics.com/products/microduck

**Behaviours in the box: walking, sitting, crouching, roller skating, object grasping and
fall recovery.** The press kit states seven trained moves; the narration lists eight verbs
because it counts standing separately. The picture performs the behaviours and does not
print a count.
Source: https://pollen-robotics.com/microduck/press-kit/

## What is open

**The robot runtime, the SDK, the simulation and the reinforcement learning training stack
are public on GitHub, under Apache 2.0.**
Source: https://github.com/pollen-robotics/microduck
Source: https://github.com/pollen-robotics/microduck_rl

**The runtime: a Rockchip RK3566 running a 50 Hz control loop, driving fifteen servos from
neural policies exported to ONNX.** Written in Rust as a set of daemons that talk over
JSON RPC on Unix sockets: `robotd` owns the control loop and the motor bus, `updaterd`
handles signed releases and rollback, `configd` Wi-Fi and identity, `btd` Bluetooth,
`padd` gamepad input, `mediad` camera streaming over WebRTC, `tofd` the depth sensor.
Those are the service names the picture draws.
Source: https://github.com/pollen-robotics/microduck

**Training: MuJoCo Warp through mjlab, PPO, domain randomization, BAM actuator physics,
backlash simulation, and ONNX export.**
Source: https://github.com/pollen-robotics/microduck_rl

**A usable walking gait takes roughly one to two hours on a CUDA GPU at 4096 parallel
environments.** The quickstart states "uses your GPU; ~1-2 h for a usable gait at 4096
envs".
Source: https://github.com/pollen-robotics/microduck_rl

## Comparisons the script draws

**Raspberry Pi and Arduino** are named as developer hardware that mattered for being cheap
and approachable rather than for being the fastest or for replacing industrial equipment.
That is an argument rather than a measurement, and the picture states no figure for either.

**Tesla Optimus** is named once, as the thing Microduck is not. The picture draws the two
to scale and marks only Microduck's 25 cm, because Optimus's dimensions were not chased to
a primary source for this video and an unsourced figure is not put on screen.

## Not checked

- The narration says the robot ships with a USB C cable. The store listing confirms a
  gamepad and the removable NP-F550 battery; it does not itemise a cable. The picture draws
  the box contents without asserting a cable as a specification.
- The narration says "first deliveries targeted before Christmas twenty twenty six in North
  America, Europe, and the UK". The store lists a wider set of launch markets than those
  three. The narration is not wrong, it is narrower than the source.
- The narration lists eight out of the box behaviours; the press kit says seven trained
  moves. Nothing on screen prints a count.
- Line 105 of the supplied script ("But inspect a training run, adjust a reward, export a
  policy, and improve a physical result.") is a sentence fragment in the source and was
  recorded as supplied.
{% endraw %}

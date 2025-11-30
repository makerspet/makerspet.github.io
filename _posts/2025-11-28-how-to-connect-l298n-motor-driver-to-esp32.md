---
layout: post
title: "How to Connect L298N Motor Driver to ESP32"
author: iliao
categories: [ L298N, ESP32 ]
image: assets/images/webp/l298n.webp
# featured: true
# hidden: true
# comments: false
# tags: [red, yellow]
# rating: .5
---

L298N is a popular, low-cost motor driver board. Here is how you can connect L298N to ESP32 and drive a ROS2 (Kaia.ai-compatible) differential robot.

## Schematic

![ESP32, L298N and N20 Motors Schematic](/assets/images/webp/esp32_lm298n_n20motors_connections.webp 'ESP32, L298N and N20 Motors Schematic'){:class="zoom-image"}

## Wiring

Refer to these wiring example illustrations.

|![ESP32 to L298N Wiring](/assets/images/webp/esp32_to_l298n_wiring_b.webp 'ESP32 to L298N Wiring'){:class="zoom-image"}|![ESP32 to L298N Wiring](/assets/images/webp/esp32_to_l298n_wiring_a.webp 'ESP32 to L298N Wiring'){:class="zoom-image"}|

<p></p>

|![ESP32 to L298N and N20 Motor Wiring](/assets/images/webp/esp32_to_l298n_to_n20_motor_wiring_a.webp 'ESP32 to L298N and N20 Motor Wiring'){:class="zoom-image"}|![ESP32 to L298N Wiring](/assets/images/webp/esp32_to_l298n_wiring_c.webp 'ESP32 to L298N Wiring'){:class="zoom-image"}|

<p></p>

|![L298N to N20 Motor Wiring](/assets/images/webp/l298n_to_n20_motor_wiring_a.webp 'L298N to N20 Motor Wiring'){:class="zoom-image"}|![L298N Wiring](/assets/images/webp/l298n_wiring_a.webp 'L298N Wiring'){:class="zoom-image"}|

<p></p>

<div class="text-center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/V_50bZ3S7bE?si=vKl0UPY-jvC7vU5l&list=PLOSXKDW70aR-6j6sCWfK29ValtOl91iZ6" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>
<p></p>

## Firmware

Use the [default firmware](https://github.com/kaiaai/firmware) with no changes.

Use the [default config.yaml file](https://github.com/kaiaai/firmware/blob/iron/kaiaai-esp32/data/config.yaml) with no changes.

## Power supply

Make sure to power your L298N from a stable power supply.

For example, if your robot runs on batteries, powering your L298N directly from the battery can cause problems when the battery gets low on charge. Specifically, your robot's motors may not be able to achieve their maximum RPM when the battery voltage is low.

To work around this problem, you may want to put a DC-DC converter between your battery and L298N to stabilize the motor power.

## Bringup instructions

Follow [video instructions](https://m.youtube.com/watch?v=6GtjAB19GP8&list=PLOSXKDW70aR8uA1IFahSKVuk5ODDfjTZV) to build and bring-up your robot.

Happy robot building!
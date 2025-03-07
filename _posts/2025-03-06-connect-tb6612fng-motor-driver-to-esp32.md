---
layout: post
title: "How to Connect TB6612FNG Motor Driver to Your ESP32 DIY Robot"
author: iliao
categories: [ TB6612FNG, ESP32 ]
image: assets/images/webp/tb6612fng.webp
# featured: true
# hidden: true
# comments: false
# tags: [red, yellow]
# rating: .5
---

TB6612FNG is a low-cost driver IC for brushed DC motors - popular with DIY enthusiasts to build small wheeled robots. One TB6612FNG can drive two
motors with power supply voltage up to 15V, average output current up to 1.2A per motor and up to 3.2A peak current. I've used TB6612FNG it on many occasions to drive small, low-cost N20-size motors.

Here is how you can connect a [TB6612FNG motor driver IC](https://toshiba.semicon-storage.com/info/TB6612FNG_datasheet_en_20141001.pdf?did=10660&prodName=TB6612FNG) to ESP32 to drive a couple of small brushed DC motors.

Kaia.ai firmware aims works with all kinds of boards and drivers, so you can reuse your components.

Here is a schematic connecting TB6612FNG to ESP32 30-pin dev board.

![TB6612FNG motor driver IC connected to ESP32 schematic](/assets/images/webp/tb6612fng_connected_to_esp32_schematic.webp 'TB6612FNG motor driver IC connected to ESP32 schematic'){:class="zoom-image"}

In the schematic
- ESP32 GPIOs (configured as outputs) connect to TB6612FNG that drives two (left and right) DC brushed motors.
- ESP32 GPIOs (configured as inputs) also connect to (quadrature) motor encoders. Each quadrature motor encoder has 2 signals called A and B (or C1, C2 or something like that).
- resistors in series with GPIO inputs protect ESP32 from 5V encoder signal levels

The choice of GPIO numbers to connect TB6612FNG and encoders is up to you - subject to ESP32 GPIO own limitations. Read more about ESP32 GPIO limitations:
- [GPIO limitations in ESP32 modules](https://makerspet.com/blog/esp32-gpio-limitations/)
- [GPIO limitations in ESP32S3 modules](https://makerspet.com/blog/esp32-s3-gpio-limitations/)

Last, but not the least, Kaia.ai firmware has a special `config.yaml` [file](https://github.com/kaiaai/firmware/blob/iron/kaiaai-esp32/data/config.yaml)
where you can specify your GPIO assignments. Kaia.ai firmware loads this file at boot time.
Please see more `config.yaml` documentation [here](https://kaia.ai/blog/kaiaai-configuration-file/).
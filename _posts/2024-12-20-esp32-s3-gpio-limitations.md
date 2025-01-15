---
layout: post
title: ESP32-S3 GPIO Limitations
author: iliao
categories: [ ESP32, ESP32-S3 ]
image: assets/images/webp/ESP32_S3MINI_makerspet_mini_s3m.webp
# featured: true
# hidden: true
# comments: true
# tags: [red, yellow]
# rating: .5
---

[ESP32-S3](https://www.espressif.com/sites/default/files/documentation/esp32-s3_datasheet_en.pdf) comes with a number of GPIO limitations.

- Do not use GPIO26, GPIO27, GPIO28, GPIO29, GPIO30, GPIO31, GPIO32. These pins are connected to "in-package flash/PSRAM and NOT recommended for other uses". Configuring any of these pins for input or output typically crashes the firmware.
- Do not use GPIO33, GPIO34, GPIO35, GPIO36, GPIO37 when your ESP32-S3 or ESP-S3MINI module contains *octal* (8-bit data bus) in-package flash/PSRAM.
- GPIO0 and GPIO46 are boot strapping pins. Boot strapping pins should be pulled up/down externally to control the boot mode.
- GPIO45 is a strapping pin for VDD_SPI voltage
- GPIO46 straps pin for ROM message printing
- GPIO3 straps the JTAG signal source.
- GPIO39 goes HIGH after reset, as opposed to the majority of GPIOs going LOW
- GPIO42, GPIO47, GPIO21 transition low on reset slower than other GPIOs

Please refer to the [ESP32-S3](https://www.espressif.com/sites/default/files/documentation/esp32-s3_datasheet_en.pdf) for details.
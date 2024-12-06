---
layout: post
title: ESP32 GPIO Limitations
author: iliao
categories: [ ESP32 ]
image: assets/images/webp/ESP32_WROOM_32_Dev_Board_v1.webp
# featured: true
# hidden: true
# comments: true
# tags: [red, yellow]
# rating: .5
---

(ESP32)[https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_en.pdf] (and its DevKit boards) has a number of limitations with respect to its GPIOs. Here is a table of issues to keep in mind.

The took the list of ESP32 GPIO limitations from a [Randomnerd Tutorials post](https://randomnerdtutorials.com/esp32-pinout-reference-gpios/) and added a handful more limitations, unusual/undocumented behaviors, tips and tricks that we have noticed.

| GPIO    | Input | Output | Notes |
| -------- | ------- | ------- | ------- |
| 0 | Pulled up internally, Caution | Caution | Outputs a signal at boot. Must be LOW to enter flashing mode. Connected to BOOT button on Dev Kit boards. May be used as input, e.g. to read the BOOT button status: pinMode(0, OUTPUT); uint8_t boot = digitalRead(0); |
| 1 | TX pin, Caution | Caution | Outputs signal at boot. This pin is used for serial code upload. You may use this pin for other purposes after the code upload  (or if your code loads from flash), but doing so may break your serial communication. |
| 2 | OK | OK | Connected to on-board LED in ESP32 Dev Kits. Must be left floating or LOW to enter the flashing mode. |
| 3 | Caution | OK | RX pin, Caution | This pin is used for serial code upload. You may use this pin for other purposes after the code upload  (or if your code loads from flash), but doing so may break your serial communication. |
| 4 | OK | OK | |
| 5 | Pulled up internally, Caution | OK | Outputs a signal at boot. This is a strapping pin that sets the timing of the SDIO slave. |
| 6 | x | x | Connected to the integrated SPI flash. Leave unconnected. |
| 7 | x | x | Connected to the integrated SPI flash. Leave unconnected. |
| 8 | x | x | Connected to the integrated SPI flash. Leave unconnected. |
| 9 | x | x | Connected to the integrated SPI flash. Leave unconnected. |
| 10 | x | x | Connected to the integrated SPI flash. Leave unconnected. |
| 11 | x | x | Connected to the integrated SPI flash. Leave unconnected. |
| 12 | Caution | OK | Boot fails if pulled high. Don't pull this pin up or down externally. |
| 13 | OK | OK | |
| 14 | Caution | Caution | Outputs a signal at boot. Toggles while Arduino IDE is waiting for the user to press the BOOT button to upload firmware code. |
| 15 | Caution | Caution | Outputs a signal at boot. |
| 16 | OK | OK | GPIO16 should be pulled up and left unused in ESP32-WROOM-32E modules using QSPI RAM ESP32D0WDR2V3 IC |
| 17 | OK | OK | |
| 18 | OK | OK | |
| 19 | OK | OK | |
| 20 | OK | OK | |
| 21 | OK | OK | |
| 22 | OK | OK | |
| 23 | OK | OK | |
| 24 | OK | OK | |
| 25 | OK | OK | |
| 26 | OK | OK | |
| 27 | OK | OK | |
| 28 | OK | OK | |
| 29 | OK | OK | |
| 30 | OK | OK | |
| 31 | OK | OK | |
| 32 | OK | OK | |
| 33 | Caution | Caution | Sometimes goes high (instead of normal low) during reset (EN button pressed) |
| 34 | OK | x | Input only |
| 35 | OK | x | Input only |
| 36 | OK | x | Input only |
| 34 | OK | x | Input only |

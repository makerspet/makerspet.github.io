---
layout: post
title: Snoopy BoM Cost Breakdown
author: iliao
categories: [ Snoopy-pet-robot, 300mm, Robot-models, Electronics, ESP32 ]
image: assets/images/webp/PXL_20230916_012313227.webp
# featured: true
# hidden: true
# comments: true
# tags: [red, yellow]
# rating: .5
---
Snoopy's hardware [BoM](https://github.com/makerspet/makerspet_snoopy/tree/main/hardware/kicad/snoopy_bom_09_2023.pdf) (bill of materials) adds up to around $200. Here is the minimum BoM breakdown!

Let's add up part costs as of 09/2023. You can get these parts, for example, on Amazon or AliExpress.

<blockquote>{% include signup-form.html %}</blockquote>

{::options parse_block_html="true" /}
<style>
    table {
    width: 100%;
    background-color: whitesmoke;
    }
</style>

| Part | Quantity | Approx. Cost per Unit|
|:--------|:-------:|--------:|
| ESP32 ESP-WROOM-32 | 1 | $5 |
| Voltage regulator module | 1 | $5 |
| Battery with cable | 1 | $50 |
| Laser scanner YDLIDAR X4 with cable| 1 | $80 |
| Resistors 0603 | 4 | $0.10 |
| Connectors | 4 | $0.50 |
| Motor CHR-GM25-BLDC2418 with cable | 2  | $11 |
| 65mm tire with shaft adapter | 2  | $4 |
| Breakout PCB | 1 | $4 |
| PETG or PLA filament, 1Kg | 1  | $20 |
| Bring-your-own smartphone | 1  | $0 |
| Bring-your-own local PC | 1 | $0 |
| Bring-your-own 3D printer | 1 | $0 |
| | | |
| Parts and supplies total | | $199.60 |

<p></p>
Please note:
- The motors are BLDC (brushless), rated at 2.5W.
- Each motor includes a built-in encoder *and* a built-in BLDC
controller.
- Snoopy is designed to accomodate 5 cliff and 4 bumper *optional* sensors. These sensors cost around $1 each.

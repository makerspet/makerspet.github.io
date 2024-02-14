---
layout: post
title: Robot Assembly Bill of Materials
author: iliao
categories: [ Loki, Snoopy, Fido, LiDAR, LDS, ESP32, Motors ]
image: assets/images/webp/loki_parts.webp
# featured: true
# hidden: true
# comments: true
# tags: [red, yellow]
# rating: .5
# comments: false
---
Let's take a look at:
- the list of parts required for the robot assembly
- the part costs as of 02/2024
- where to get these parts

Please keep in mind that I'm going to launch an online store here, at makerspet.com, sometime in 2024, offering robot hardware kits. That said, you can always get all parts directly elsewhere.

I've upgraded the robot's Kaia.ai firmware to support a variety of motors and LiDAR/LDS laser distance scan sensors. Please read this [blog post](https://kaia.ai/blog/arduino-platform-firmware-avaiable/) with instructions on configuring your robot, including:
- selecting the motor model
- selecting the LiDAR/LDS laser distance scan sensor model
- selecting your robot model size
- connecting your robot to your WiFi network
- connecting your robot to your local PC

### Motors
Let's start with the robot's motors. The robot's [Arduino firmware](https://github.com/kaiaai/firmware) supports these motors:

- ChiHai Motor CHR-GM25-BL2418 200RPM. [AliExpress link.](https://www.aliexpress.us/item/2251832633601682.html) off AliExpress. The model you want is `24v 200rpm i45`.
- Far Along JGA25-BL2418 245RPM. [AliExpress link.](https://www.aliexpress.us/item/2255799833885046.html). The model you want is `Package A 24v 245rpm`.
- Recommended by default, ChiHai Motor CHR-GM25-BL2418 260RPM. [AliExpress link.](https://www.aliexpress.us/item/2251832633601682.html) off AliExpress. The model you want is `24v 260rpm i34`.
- Bringsmart JGA25-BL2418 408RPM. [AliExpress link.](https://www.aliexpress.us/item/2251832759774935.html). The model you want is `24v 408rpm`, although it seems to be out-of-stock.
- Far Along JGA25-BL2418 408RPM. [AliExpress link.](https://www.aliexpress.us/item/2255799833885046.html). The model you want is `Package A 24v 408rpm`.
- ChiHai Motor CHR-GM25-BL2418 450RPM 120PPR. [AliExpress link.](https://www.aliexpress.us/item/2251832633601682.html) The model you want is `24v 450rpm i20`.

![Supported 2418 BLDC motors and 65mm wheels](/assets/images/webp/motors-and-wheels.webp 'Supported 2418 BLDC motors and 65mm wheels'){:class="zoom-image"}

All of these motors are brushless (BLDC) with a built-in controller. All of them have the identical 2418 size, connector and same or similar BLDC "motor core". The difference between these motors is mainly in their gearbox gear ratio:
- use slower (but stronger) motors - those with a lower RPM - if you want your robot to be "strong". You need strong motors
  - to plow through a high carpet without getting stuck
  - to push or pull around some load
- use faster (but weaker) motors - those with a higher RPM - to maximize your robot's maximum speed

If you have a similar BLDC motor, but with a different gearbox ratio (maximum RPM), select `custom robot` in the [Kaia.ai robot configurator](https://github.com/kaiaai/firmware) and specify the motor's RPM (motor shaft rotation per minute) and PPR (encoder pulses per motor shaft rotation).

### LiDAR/LDS Laser Distance Scan Sensor
Next up, the robot's distance sensor. The robot's [Arduino firmware](https://github.com/kaiaai/firmware) supports these distance sensors out-of-the-box:
- YDLIDAR X4 (recommended by default). [Amazon search.](https://www.amazon.com/s?k=ydlidar+x4)
- YDLIDAR X3 and [X3 PRO](https://makerspet.com/blog/ydlidar-x3-pro-lidar-support/). [Amazon search.](https://www.amazon.com/s?k=ydlidar+x3)
- YDLIDAR X2/X2L. [Amazon search.](https://www.amazon.com/s?k=ydlidar+x2l)
- 3irobotix Delta-2A, Delta-2G. Some of these cost <$20. [AliExpress search.](https://www.aliexpress.us/w/wholesale-delta-lidar-lds.html)
- Neato X11. [eBay search](https://www.ebay.com/sch/i.html?_from=R40&_nkw=neato+xv+laser+sensor)
- Xiaomi Mi Roborock 1st gen [LDS02RR](https://makerspet.com/blog/xiaomi-lds02rr-lidar-support/). Some of these cost <$20. [AliExpress search.](https://www.aliexpress.us/w/wholesale-lds02rr.html)
- SLAMTEC RPLIDAR A1. [Amazon search.](https://www.amazon.com/s?k=rplidar+a1)
- (TODO) Hitachi-LG HLS-LFCD2 and HLS-LFCD3. [Google search.](https://www.google.com/search?q=buy+hls-lfcd2)
- (TODO) LDROBOT LD14P, etc. [Amazon search.](https://www.amazon.com/s?k=ld14p)
- (TODO) Xiaomi LDS01RR. [AliExpress search.](https://www.aliexpress.us/w/wholesale-lds01rr.html)
- (TODO) 3irobotix Delta-2C PRO
- (TODO) RPLIDAR C1. [Amazon search.](https://www.amazon.com/s?k=rplidar+c1)

There are many LiDAR/LDS sensors out there and many of those look alike. This [blog post](https://kaia.ai/blog/arduino-lidar-library/) can help you identifying the sensor model.

Here is the complete and up-to-date [list of supported laser distance sensors](https://github.com/kaiaai/LDS).

WARNING: although, to the best of my knowledge, all these LiDAR/LDS sensors appear to be safe, as claimed by sellers or manufacturer datasheets or manufacturer user manuals that I've personally seen, whichever LiDAR/LDS model you end up purchasing
- NEVER look into the LiDAR/LDS laser
- keep other humans (including children) from looking into the laser
- keep animals/pets from looking into the laser
- REMEMBER that the laser ray can bounce off reflective surfaces, especially mirrors. Therefore, avoid having reflective surfaces around.

You may ask, why the extra caution even if the seller/manufacturer claims its LiDAR/LDS is safe? This is because - even if you trust the seller/manufacturer with your vision health - a LiDAR/LDS sensor can get damaged, dropped and therefore, potentially, become unsafe to your vision.

### The Boards

Here is the robot's [main board](https://github.com/makerspet/pcb/tree/main/esp32_breakout), its [schematic](https://github.com/makerspet/pcb/blob/main/esp32_breakout/output/esp32_breakout_schematic.pdf) and [bill of materials](https://github.com/makerspet/pcb/blob/main/esp32_breakout/output/esp32_breakout_bom.csv). Briefly, the main board contains these components:
- ESP32 and its header connectors
- connectors for the robot's battery, motors, LiDAR/LDS
- connectors for optional extension board modules (you can ignore these for now)
- a power on/off switch
- an LM2596 DC-DC 24V-to-5V voltage regulator
- a few resistors, diodes and a safety fuse

![ESP32 main board in enclosure - top](/assets/images/webp/esp32_board_top.webp 'ESP32 main board in enclosure - top'){:class="zoom-image"}

![ESP32 main board in enclosure - bottom](/assets/images/webp/esp32_board_bottom.webp 'ESP32 main board in enclosure - bottom'){:class="zoom-image"}

The LiDAR/LDS sensors connect to the robot's [ESP32 breakout board](https://github.com/makerspet/pcb/tree/main/esp32_breakout) using a custom cable. Some LiDAR/LDS models lack a built-in motor control and, therefore, requires an additional adapter board to be connected.
- Xiaomi LDS02RR, LDS01RR require [this adapter board](https://github.com/makerspet/pcb/tree/main/lds02rr_adapter).
- Neato XV11 and 3irobotix Delta-2A, Delta-2G require [this adapter board](https://github.com/makerspet/pcb/tree/main/neato_delta_adapter).
- Hitachi-LG HLS-LFCD2 does have built-in motor control, but still requires [this adapter board](https://github.com/makerspet/pcb/tree/main/hls_adapter) because this LiDAR model lacks a connector socket.

![LDS02RR adapter board connected to ESP32 main board](/assets/images/webp/lds02rr_adapter_board.webp 'LDS02RR adapter board connected to ESP32 main board'){:class="zoom-image"}

![Delta2A adapter board connected to ESP32 main board](/assets/images/webp/delta2a_adapter_board.webp 'Delta2A adapter board connected to ESP32 main board'){:class="zoom-image"}

Here are the most-up-to-date [instructions (TODO)](https://github.com/makerspet/pcb) on connecting each LiDAR/LDS model to the robot's ESP32 breakout board.

I will be offering all these adapter boards and cables in the makerspet.com online store - once the store opens up. In the meantime, you might need to build those boards yourself using a breadboard PCB, a soldering iron and a few parts from, say, DigiKey.com. Here are all [board schematics, BoM and Gerber files](https://github.com/makerspet/pcb).

### Miscellaneous Parts

Other parts include
- two 65mm wheels with shaft adapters, [Google search](https://www.google.com/search?q=65mm+rubber+wheel+with+hex+coupling)
- a battery cable with an [XT30 plug](https://www.amazon.com/s?k=xt30). Here are battery choices:
  - You can use 3x 9V batteries connected in series. In my experience, the robot can actively run around for around 3 hours before these batteries run out.
  - Or, you can use 16 AA or AAA batteries in series. This battery pack will last your robot much longer.
  - Or, you can use a 6S1P rechargeable battery. I plan to offer these in the makerspet.com online store at a later time.
- 3D printed robot body - 0.5Kg of PLA or PETG should be enough for 200mm Loki

### Parts Cost

Here is my total estimate as of 02/14/2024. Tax, shipping and handling will be extra.

<blockquote>{% include signup-form.html %}</blockquote>

{::options parse_block_html="true" /}
<style>
    table {
    width: 100%;
    background-color: whitesmoke;
    }
</style>

| Part | Quantity | Approx. Cost|
|:--------|:-------:|--------:|
| ESP32 ESP-WROOM-32 | 1 | $5 |
| ESP32 main board | 1 | ~$10 |
| 3x 9V alkaline batteries with cable | 1 | ~$3 |
| Laser scanner LDS02RR with cable| 1 | ~$18 |
| Laser scanner adapter board | 1 | ~$5 |
| Motor CHR-GM25-BLDC2418 with cable | 2  | $11 |
| 65mm tire with shaft adapter | 2  | $4 |
| PETG or PLA filament, 0.5Kg (Loki) | 1  | $10 |
| Bring-your-own smartphone | 1  | $0 |
| Bring-your-own local PC | 1 | $0 |
| Bring-your-own 3D printer | 1 | $0 |
| | | |
| Parts and supplies total | | $66.00 |
---
layout: post
title: "How to Connect Delta-2G LiDAR to ESP32 and Maker's Pet Boards"
author: iliao
categories: [ Delta-2G, ESP32 ]
image: assets/images/webp/delta-2g_with_bdc-30p_marked_up.webp
# featured: true
# hidden: true
# comments: false
# tags: [red, yellow]
# rating: .5
---

3irobotix Delta-2G is a low-cost 2D LiDAR 360-degree distance sensor used in smart vacuum cleaners for navigation. Here are instructions to connect Delta-2G to the LiDAR port on Maker's Pet [BDC-30P](https://makerspet.com/store#!/Driver-Board-for-ESP32-DOIT-DevKit-V1-Brushed-DC-Motors-and-LiDAR/p/724227009), [BDC-38P](https://makerspet.com/store#!/Driver-Board-for-ESP32-DevKitC-V4-Brushed-DC-Motors-and-LiDAR/p/724216505) boards.

## Hardware Wiring

Delta-2G uses a JST PH 2.0mm 5-pin connector. The photo below shows the connector pinout (+5V/MOT+, MOT-, +5V, GND, TX) and connections to Maker's Pet [BDC-30P](https://makerspet.com/store#!/Driver-Board-for-ESP32-DOIT-DevKit-V1-Brushed-DC-Motors-and-LiDAR/p/724227009) board with a 30-pin ESP32 dev kit.

- connect Delta-2G TX to BDC-30P LiDAR TX
- connect Delta-2G GND to BDC-30P LiDAR GND
- connect Delta-2G MOT- to BDC-30P LiDAR M-
- connect Delta-2G +5V to BDC-30P LiDAR +5V
- connect Delta-2G +5V/MOT+ to BDC-30P LiDAR +5V

Idential wiring applies to the Maker's Pet [BDC-38P](https://makerspet.com/store#!/Driver-Board-for-ESP32-DevKitC-V4-Brushed-DC-Motors-and-LiDAR/p/724216505) board with a 38-pin ESP32 dev kit as well.

![3irobotix Delta-2G LiDAR connected to Maker's Pet BDC-30P ESP32 Board](/assets/images/webp/delta-2g_with_bdc-30p_marked_up.webp '3irobotix Delta-2G LiDAR connected to Makers Pet BDC-30P ESP32 Board'){:class="zoom-image"}

Optionally, put a resistor in series with TX (anything 100 Ohm to 10k, because Delta-2G TX outputs 5V signal, not 3.3V).

Here are more high-resolution photos of the wiring.

![3irobotix Delta-2G LiDAR connected to Maker's Pet BDC-30P ESP32 Board](/assets/images/webp/Delta-2G-connected-to-BDC-30P.webp '3irobotix Delta-2G LiDAR connected to Makers Pet BDC-30P ESP32 Board'){:class="zoom-image"}

![3irobotix Delta-2G LiDAR connected to Maker's Pet BDC-30P ESP32 Board](/assets/images/webp/Delta-2G-connected-to-BDC-30P-3.webp '3irobotix Delta-2G LiDAR connected to Makers Pet BDC-30P ESP32 Board'){:class="zoom-image"}

![3irobotix Delta-2G LiDAR connected to Maker's Pet BDC-30P ESP32 Board](/assets/images/webp/Delta-2G-connected-to-BDC-30P-2.webp '3irobotix Delta-2G LiDAR connected to Makers Pet BDC-30P ESP32 Board'){:class="zoom-image"}


## Firmware Configuration

Edit your Kaia.ai firmware `config.yaml` configuration file. In the `lidar` section comment out everything except your LiDAR model `3IROBOTIX DELTA-2G`.

Upload this edited configuration file to ESP32 as sketch data, see [video](https://www.youtube.com/watch?v=tKfVU1n5TjA&list=PLOSXKDW70aR8uA1IFahSKVuk5ODDfjTZV&index=4).

Here is [reference documentation](https://kaia.ai/blog/kaiaai-configuration-file/) for `config.yaml`.

```
lidar:
# model: LDROBOT LD14P
# model: NEATO XV11
# model: SLAMTEC RPLIDAR A1
# model: XIAOMI LDS02RR
# model: YDLIDAR SCL
# model: YDLIDAR X2
# model: YDLIDAR X2L
# model: YDLIDAR X3
# model: YDLIDAR X3 PRO
  model: 3IROBOTIX DELTA-2G
# model: 3IROBOTIX DELTA-2A 115200
# model: 3IROBOTIX DELTA-2A
# model: 3IROBOTIX DELTA-2B
# model: YDLIDAR X4 PRO
# model: YDLIDAR X4
```

Boot your firmware and check the Arduino Serial Monitor. The firmware should print `LIDAR model 3IROBOTIX DELTA-2G`.

```
ets Jul 29 2019 12:21:46

rst:0x1 (POWERON_RESET),boot:0x13 (SPI_FAST_FLASH_BOOT)
configsip: 0, SPIWP:0xee
clk_drv:0x00,q_drv:0x00,d_drv:0x00,cs0_drv:0x00,hd_drv:0x00,wp_drv:0x00
mode:DIO, clock div:1
load:0x3fff0030,len:1344
load:0x40078000,len:13964
load:0x40080400,len:3600
entry 0x400805f0

Kaia.ai firmware version 0.8.0-iron
ESP IDF version v4.4.7-dirty
SPIFFS mounted successfully
/network.yaml found; loaded OK
/config.yaml found; loaded OK
To enter web config push-and-release EN, then push-and-hold BOOT within 1 sec
Board model MINI-BDC30P-BODY with BDC-30P, version v1.1.1, manufacturer makerspet.com
LIDAR model 3IROBOTIX DELTA-2G
LIDAR RX buffer size 1024, baud rate 115200
Battery ADC attenuation 7.00, voltage 2.68V
Motor driver type IN1_IN2; motor encoder type AB_QUAD
Motor Max RPM 180.00; encoder PPR 1035.00 TPR 4140.00

Connecting to WiFi NETGEAR48 ... 
```

## ROS2 Software Configuration

When you get to running the Kaia.ai Docker image, edit `telem.yaml` file and change `lidar_model` to `"3IROBOTIX-DELTA-2G"`

```
pico /ros_ws/src/makerspet_mini/config/telem.yaml
```

Keep in mind that changes to this file will get lost when the `kaiaai/kaiaai` container shuts down, so you would have to edit this file again next time you launch the `kaiaai` Docker image. However, future Kaia.ai releases are going to implement automatic ROS2 LiDAR configuration, so you will not have to edit the `telem.yaml` file.

When you get to connecting your ESP32 to your local PC, your local PC should print something like this, including `LDS model 3IROBOTIX-DELTA-2G`.

Your Delta-2G LiDAR should be powered on and spinning.

![3irobotix Delta-2G LiDAR connected to Maker's Pet BDC-30P ESP32 Board ROS2 Bash Terminal Output](/assets/images/powershell_delta-2g_connected.png '3irobotix Delta-2G LiDAR connected to Makers Pet BDC-30P ESP32 Board ROS2 Bash Terminal Output'){:class="zoom-image"}

In the meantime, you should see your ESP32 firmware printing out `LiDAR RPM` around 4.75 or 5. This means your Lidar is spinning at 4.75 rotations per second.

```
connected, IP 192.168.1.153
Connecting to Micro-ROS agent 192.168.1.113 ... 

Telem avg 46 max 52ms, LiDAR RPM 4.75, wheels RPM 0.00 0.00, battery 8.00V, RSSI -60dBm
Telem avg 46 max 52ms, LiDAR RPM 4.75, wheels RPM 0.00 0.00, battery 8.00V, RSSI -59dBm
Telem avg 46 max 52ms, LiDAR RPM 4.75, wheels RPM 0.00 0.00, battery 8.00V, RSSI -61dBm
Telem avg 46 max 52ms, LiDAR RPM 4.75, wheels RPM 0.00 0.00, battery 8.00V, RSSI -62dBm
```

Run the `ros2 launch kaiaai_bringup monitor_robot.launch.py` command in Docker to check your Lidar output. It should be something like this.

<div class="text-center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/K2i_wee3JU8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

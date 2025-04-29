---
layout: post
title: "How to Connect Delta-2A, 2B and 2G LiDAR to Maker's Pet ESP32 Boards"
author: iliao
categories: [ Delta-2G, ESP32 ]
image: assets/images/webp/3irobotix_delta_2g_1200px.webp
# featured: true
# hidden: true
# comments: false
# tags: [red, yellow]
# rating: .5
---

3irobotix Delta-2A, 2B and 2G are a low-cost 2D LiDAR 360-degree distance sensor used in smart vacuum cleaners for navigation. Here are instructions to connect Delta-2G to the LiDAR port on Maker's Pet [BDC-30P](https://makerspet.com/store#!/Driver-Board-for-ESP32-DOIT-DevKit-V1-Brushed-DC-Motors-and-LiDAR/p/724227009) and [BDC-38P](https://makerspet.com/store#!/Driver-Board-for-ESP32-DevKitC-V4-Brushed-DC-Motors-and-LiDAR/p/724216505) motor driver and ESP32 carrier boards.

## Hardware Wiring

Maker's Pet BDC-30P and BDC-38C4 motor driver and ESP32 carrier boards have an 8-pin LiDAR header connector. The LiDAR header can be connected to a large variety of 2D LiDARs. The LiDAR header pins include:
- LiDAR TX
- LiDAR RX
- +5V power for LiDAR
- GND ground for LiDAR
- M- LiDAR's motor negative terminal
- M+ LiDAR's motor positive terminal (connected to +5V power)
- PWM for LiDAR motor speed control
- EN for LiDAR enable/disable (used by YDLIDAR X4 only)

Some LiDARs, including 3irobotix Delta-2G, do not have a built-in LiDAR motor control. Maker's Pet BDC-30 and BDC-38C4 have a special on-board circuit that drives the LiDAR motor directly. Kaia.ai Arduino ESP32 firmware controls that special circuit to perform real-time LiDAR motor speed control.

3irobotix Delta-2A, 2B and 2G use a JST PH 2.0mm 5-pin connector. The photo below shows the Delta-2G connector pinout and connections to Maker's Pet [BDC-30P](https://makerspet.com/store#!/Driver-Board-for-ESP32-DOIT-DevKit-V1-Brushed-DC-Motors-and-LiDAR/p/724227009) board with a 30-pin ESP32 dev kit.

- connect Delta LiDAR TX to BDC-30P LiDAR TX
- connect Delta LiDAR GND to BDC-30P LiDAR GND
- connect Delta LiDAR MOT- to BDC-30P LiDAR M-
- connect Delta LiDAR +5V to BDC-30P LiDAR +5V
- connect Delta LiDAR +5V/MOT+ to BDC-30P LiDAR +5V

Idential wiring applies to the Maker's Pet [BDC-38P](https://makerspet.com/store#!/Driver-Board-for-ESP32-DevKitC-V4-Brushed-DC-Motors-and-LiDAR/p/724216505) board with a 38-pin ESP32 dev kit as well.

![3irobotix Delta-2G LiDAR connected to Maker's Pet BDC-30P ESP32 Board](/assets/images/webp/delta-2g_with_bdc-30p_marked_up.webp '3irobotix Delta-2G LiDAR connected to Makers Pet BDC-30P ESP32 Board'){:class="zoom-image"}

Optionally, put a resistor in series with TX because Delta-2G TX outputs 5V signal, not 3.3V. A 100 Ohm to 10k resistor should work.

For easy connection, Maker's Pet sells a [breakout cable for 3irobotix Delta-2A and 2G](https://makerspet.com/store#!/Breakout-Cable-for-YDLIDAR-X2-X2L-X3-X3-PRO-SCL/p/746225737) with 2.54mm female DuPont connectors.

![breakout cable for 3irobotix Delta-2A and 2G](/assets/images/webp/delta_2g_breakout_cable_1_cropped.webp 'breakout cable for 3irobotix Delta-2A and 2G'){:class="zoom-image"}

Here are more high-resolution photos of the wiring.

![3irobotix Delta-2G LiDAR connected to Maker's Pet BDC-30P ESP32 Board](/assets/images/webp/Delta-2G-connected-to-BDC-30P.webp '3irobotix Delta-2G LiDAR connected to Makers Pet BDC-30P ESP32 Board'){:class="zoom-image"}

![3irobotix Delta-2G LiDAR connected to Maker's Pet BDC-30P ESP32 Board](/assets/images/webp/Delta-2G-connected-to-BDC-30P-3.webp '3irobotix Delta-2G LiDAR connected to Makers Pet BDC-30P ESP32 Board'){:class="zoom-image"}

![3irobotix Delta-2G LiDAR connected to Maker's Pet BDC-30P ESP32 Board](/assets/images/webp/Delta-2G-connected-to-BDC-30P-2.webp '3irobotix Delta-2G LiDAR connected to Makers Pet BDC-30P ESP32 Board'){:class="zoom-image"}


## Firmware Configuration

Edit your Kaia.ai firmware `config.yaml` configuration file. In the `lidar` section comment out everything except your LiDAR model:
- `3IROBOTIX DELTA-2A` for Delta-2A
- `3IROBOTIX DELTA-2A` for Delta-2A that runs at 115200 baud (I'm not 100% sure of this LiDAR model name)
- `3IROBOTIX DELTA-2B` for Delta-2B
- `3IROBOTIX DELTA-2G` for Delta-2G

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

Your board's `config.yaml` already contains ESP32 GPIO pin mapping to the board's LiDAR connector, including LiDAR TX, RX, PWM and EN:
- [BDC-30P config.yaml](https://github.com/makerspet/store/blob/main/BDC-30P/v1.1.1/config.yaml)
- [BDC-38C4 config.yaml](https://github.com/makerspet/store/blob/main/BDC-38C4/v1.2.0/config.yaml)

For illustration purposes, here is the ESP32 GPIO pin assignment LiDAR from the [BDC-30P config.yaml](https://github.com/makerspet/store/blob/main/BDC-30P/v1.1.1/config.yaml).

```
lidar:
  gpio:
    tx: 35
    rx: 27
    pwm: 13
    en: 32
```

Upload your edited configuration file to ESP32 as Arduino sketch data, see [video](https://www.youtube.com/watch?v=tKfVU1n5TjA&list=PLOSXKDW70aR8uA1IFahSKVuk5ODDfjTZV&index=4).

Next, boot your firmware and check the Arduino Serial Monitor. The firmware should print `LIDAR model 3IROBOTIX DELTA-2G`.

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

Follow this step if you are using Kaia.ai ROS2 PC software for robot mapping, navigation, SLAM and visualization. Otherwise you can skip this step.

Override the default LiDAR model when you launch your robot using the `lidar_model` argument, see [more details](https://github.com/kaiaai/kaiaai#overriding-default-robot-and-lidar-models-per-launch):

Set the `lidar_model` argument as follows:
- `3IROBOTIX-DELTA-2A` for 3irobotix Delta-2A and the 115200 baud Delta-2A
- `3IROBOTIX-DELTA-2B` for 3irobotix Delta-2B
- `3IROBOTIX-DELTA-2G` for 3irobotix Delta-2G

```
ros2 launch kaiaai_bringup physical.launch.py robot_model:=makerspet_loki lidar_model:=YDLIDAR-X3-PRO
```

The full list of supported `lidar_model` arguments is [here](https://github.com/kaiaai/kaiaai#list-of-supported-lidars).

When your robot's ESP32 connects to your local ROS2 PC, your local PC should print your LiDAR model `LDS model 3IROBOTIX-DELTA-2G`.

Your Delta LiDAR should be powered on and spinning.

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

<div class="text-center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/K2i_wee3JU8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

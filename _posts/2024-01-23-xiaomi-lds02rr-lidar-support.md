---
layout: post
title: "$15 LiDAR sensor is now supported!"
author: iliao
categories: [ LiDAR, LDS, LDS02RR, ROS, Arduino ]
image: assets/images/webp/Loki-LDS02RR-LiDAR-cropped.webp
# featured: true
# hidden: true
# comments: false
# tags: [red, yellow]
# rating: .5
---
A brief development update - Maker's Pet robots now work with Xiaomi 1st gen LDS02RR laser distance scan sensors.

This is a big deal for me because you can purchase LDS02RR off AliExpress for just $15~$17, including shipping. Compare that, say, to YDLIDAR X4 that costs around $80.

This means that the total cost of parts for Maker's Pet robot kits has dropped to under $100! Compare that to, say, a ROS robot kit like Turtlebot3 Burger, with a price tag (as of today) of $659.30.

I'd like to emphasize that I want Maker's Pet Arduino/ROS2 robot kits to be affordable for everyone.

 Why Xiaomi LDS02RR is so inexpensive? As far as I understand, this is because AliExpress sellers take used Xiaomi 1st gen Roborock vacuum cleaners (that users throw away when they, say, upgrade to a newer model), take the discarded robots apart and sell the (used) laser sensor.

The video below shows LDS02RR streaming the distance data live to ROS2 Rviz viewer using Maker's Pet Arduino ESP32 breakout board and Micro-ROS.

<div class="text-center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/STbCVhdgLSw?list=PLOSXKDW70aR8123OC3843DO4hrjXEa4Tm" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

In order to connect LDS02RR to Arduino, I had to design a tiny PCB board that plugs into Xiaomi LDS02RR LiDAR/LDS to connect the LiDAR to Arduino/ESP32 (and ROS2). This PCB has components that regulate the laser sensor's motor RPM.

You can download the PCB design files are [here](https://github.com/makerspet/pcb) under the lds02rr_adapter folder.

The video below shows the LDS02RR adapter PCB I had to design.

<div class="text-center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/Wes9GYomUdE?list=PLOSXKDW70aR8123OC3843DO4hrjXEa4Tm" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

This Xiaomi LiDAR does not have a built-in control for its motor. So, I also had to write firmware that controls the Xiaomi LiDAR motor and keeps the motor RPM stable and accurate. Since Maker's Pet robots now support multiple LiDAR/LDS models (currently YDLIDAR X4 and LDS02RR), I've written and published an Arduino library that wraps LiDAR/LDS internals into a simple API. Now it is (relatively) easy to add other LiDAR/LDS models - without changing the robot firmware.

You can find this LDS Arduino library source code [here](https://github.com/kaiaai/LDS).

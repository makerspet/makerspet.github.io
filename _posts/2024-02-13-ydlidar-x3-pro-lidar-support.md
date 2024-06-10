---
layout: post
title: "YDLIDAR X3 PRO LDS sensor is now supported"
author: iliao
categories: [ LiDAR, LDS, YDLIDAR, ROS, ROS2, Arduino ]
image: assets/images/webp/Loki-YDLIDAR-X3-PRO.webp
# featured: true
# hidden: true
# comments: false
# tags: [red, yellow]
# rating: .5
---
A brief development update - Maker's Pet robots now work with YDLIDAR X3 PRO laser distance scan sensors.

The video below shows YDLIDAR X3 PRO streaming the distance data live to ROS2 Rviz viewer using Maker's Pet Arduino [ESP32 breakout board](https://github.com/makerspet/pcb/) and [Kaia.ai fork](https://github.com/kaiaai/micro_ros_arduino_kaiaai) of Micro-ROS for Arduino.

<div class="text-center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/_VuRCiO55gA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

YDLIDAR X3 PRO connects to the [ESP32 breakout board](https://github.com/makerspet/pcb/) directly using a cable, without any adapter board.

Last but not the lease - the LDS support firmware. Please find the LDS Arduino library [source code here](https://github.com/kaiaai/LDS). You can install this library using the Arduino IDE Library Manager.
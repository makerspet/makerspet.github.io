---
layout: post
title: "How-to: Connect Xiaomi $15 LDS02RR LiDAR to ESP32, Arduino"
author: iliao
categories: [ LiDAR, LDS, LDS02RR, ROS, Arduino, ESP32 ]
image: assets/images/webp/LDS02RR_Lidar_with_adapter2.webp
# featured: true
# hidden: true
# comments: false
# tags: [red, yellow]
# rating: .5
---

Here is a DIY project I'd like to share. I've designed an [adapter PCB](https://makerspet.com/store#!/Adapter-v0-3-for-LDS02RR-LiDAR/p/715312353) to connect my LDS02RR Lidar to ESP32. I also wrote Arduino [firmware](https://github.com/kaiaai/LDS) to stream distance data live from LDS02RR - as well as many other low-cost 2D Lidar models. Lastly, I've had the adapter PCB manufactured and made it available at my [online DIY robotics store](https://makerspet.com/store).

![Maker's Pet LDS02RR Adapter v0.3 - rear](/assets/images/webp/LDS02RR_adapter_rear.webp 'Maker''s Pet LDS02RR Adapter v0.3 - rear'){:class="zoom-image"}

Both the adapter and firmware are open source.

![Maker's Pet LDS02RR Adapter v0.3 schematic](/assets/images/webp/LDS02RR_adapter_v03_schematic.webp 'Maker''s Pet LDS02RR Adapter v0.3 schematic'){:class="zoom-image"}

Here is how you can connect a LDS02RR Lidar to a 30-pin ESP32 development board using the v0.3 adapter.

![Schematic of LDS02RR Lidar connections to a 30-pin ESP32 development board using the v0.3 adapter](/assets/images/webp/LDS02RR_to_ESP32_example_connection.webp 'Schematic of LDS02RR Lidar connections to a 30-pin ESP32 development board using the v0.3 adapter'){:class="zoom-image"}

Why design and manufacture an adapter - and write firmware - for a LDS02RR Lidar? The reason is that LDS02RR is very inexpensive. I purchased my LDS02RR off AliExpress for around $15 including shipping to California.

Why LDS02RR is so inexpensive? I believe this is because LDS02RR is taken from used Xiaomi vacuum cleaners, "for parts". That said, if you choose to buy a used Lidar for yourself, make sure your LiDAR unit is not defective and safe to operate.

Here are step-by-step instructions to make LDS02RR stream the distance data live using Arduino and ESP32.

<div class="text-center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/hQKBI_xcKxQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

Besides displaying live distance data in Arduino IDE, I have also forwarded the distance data to ROS/ROS2 for visualization, SLAM, mapping and automatic navigation (Nav2) using [Kaia.ai ROS2-compatible software](https://github.com/kaiaai/install) and [Kaia.ai Arduino-compatible firmware](https://github.com/kaiaai/firmware).

Here is a demo of LDS02RR streaming distance data live to ROS2 Rviz viewer using an older version of the adapter PCB and Kaia.ai ROS2/Arduino software suite.

<div class="text-center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/STbCVhdgLSw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

Happy DIY robotics!
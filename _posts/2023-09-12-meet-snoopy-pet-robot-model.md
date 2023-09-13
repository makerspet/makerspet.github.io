---
layout: post
title: Meet Snoopy the pet robot!
author: iliao
categories: [ Snoopy-pet-robot, Robot-models ]
image: assets/images/webp/screenshot1-1024x576.webp
featured: true
hidden: true
comments: false
# tags: [red, yellow]
# rating: .5
comments: false
---
Meet Snoopy, an open-source pet robot! Snoopy is a 300mm, round-base, mid-size DIY 3D-printable indoor pet robot compatible with [Kaia.ai](https://kaia.ai) software platform.

Snoopy was designed in Fusion 360 in 05/2023 and printed using a Voron 2.4r2 350mm.

Please keep in mind that we are still in product development phase - please sign up for the mailing list below to be notified about product launch. You are also welcome to join our [Facebook group]({{ site.facebook_group_url }}).

<blockquote>{% include signup-form.html %}</blockquote>

## Features
- A 300mm round base.
- 3D-printable and moddable:
  - Requires a 300x300mm or larger build volume.
- 2 bumpers, 4 bumper sensors, 5 cliff sensors.
- A smartphone or a 7" tablet acts as as a head display.
- ESP32 micro-controller.
- Arduino [firmware](https://github.com/makerspet/kaiaai_snoopy/tree/main/firmware)
- Room mapping using a 360-degree laser distance sensor (ROS2-based).
- Fully autonomous indoor navigation (ROS2-based).
- Kaia.ai software platform compatible:
  - Off-the-shelf character and skills (work-in-progress)
  - Design-and-code a custom character (work-in-progress)
  - Design-and-code custom skills (work-in-progress)

|![Maker''s Pet Snoopy 3D-printed and assembled without bumpers](/assets/images/webp/PXL_20230530_031143988-768x1024.webp 'Maker''s Pet Snoopy 3D-printed and assembled without bumpers'){:class="zoom-image"}|![Maker''s Pet Snoopy 3D-printed and assembled with bumpers](/assets/images/webp/PXL_20230609_174802983-771x1024.webp 'Maker''s Pet Snoopy 3D-printed and assembled with bumpers'){:class="zoom-image"}|

<p></p>

## DIY Hardware Build
- 3D printing:
 - Instructions [here](https://github.com/makerspet/kaiaai_snoopy/tree/main/hardware/)
 - STL files [here](https://github.com/makerspet/kaiaai_snoopy/tree/main/hardware/stl/)
 - 3MF files [here](https://github.com/makerspet/kaiaai_snoopy/tree/main/hardware/3mf/)
 - Fusion 360 source files [here](https://github.com/makerspet/kaiaai_snoopy/tree/main/hardware/fusion360)

## Software Setup
- PC setup for [end users](https://github.com/kaiaai/docker/tree/main/kaia-ros)
- Firmware [here](https://github.com/makerspet/kaiaai_snoopy/tree/main/firmware/)
- Kaia.ai TODO

|![Maker''s Pet Snoopy's head being 3D-printed on a Voron 2.4 350mm](/assets/images/webp/PXL_20230529_041408418-771x1024.webp 'Maker''s Pet Snoopy's head being 3D-printed on a Voron 2.4 350mm'){:class="zoom-image"}|![Maker''s Pet Snoopy's head completed 3D-print](/assets/images/webp/PXL_20230530_021024946-771x1024.webp 'Maker''s Pet Snoopy's head completed 3D-print'){:class="zoom-image"}|

<p></p>

## Develop and Mod
- PC setup for [developers](https://github.com/kaiaai/docker/tree/main/kaia-ros-dev)
- ROS2 robot description package
  - config [here](https://github.com/makerspet/kaiaai_snoopy/tree/main/config)
  - instructions and robot model [here](https://github.com/makerspet/kaiaai_snoopy/tree/main/urdf)
- Firmware mod instructions [here](https://github.com/makerspet/kaiaai_snoopy/tree/main/firmware/)
- Kaia.ai TODO

|![Maker''s Pet Snoopy robot in Fusion 360](/assets/images/webp/screenshot2-1024x576.webp 'Maker''s Pet Snoopy robot in Fusion 360'){:class="zoom-image"}|![Maker''s Pet Snoopy robot in Fusion 360 - bottom view](/assets/images/webp/screenshot3-1024x576.webp 'Maker''s Pet Snoopy robot in Fusion 360 - bottom view'){:class="zoom-image"}|

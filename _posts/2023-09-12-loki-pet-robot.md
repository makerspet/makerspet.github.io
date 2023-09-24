---
layout: post
title: 200mm pet robot in the works!
author: iliao
categories: [ Loki-pet-robot, 200mm ]
image: assets/images/webp/Loki2.webp
featured: true
hidden: true
# comments: false
# tags: [red, yellow]
# rating: .5
# comments: false
---
Just a heads-up - I'm designing a 200mm (and a 250mm) pet robot right now.
Loki, the 200mm robot, will be small enough to fit the widely used 210x250mm
3D print volumes, so you don't have to invest in a bigger 3D printer.

Loki's Arduino firmware and software (ROS2) are ready - you can download the
files [here](https://github.com/makerspet/makerspet_loki).
Loki's Fusion 360, STL and 3MF files are in the works.

I'm designing Loki
- to be easily scalable to different sizes, including 250mm.
- to be modular - similar to Snoopy, but simplified
  - the side body will be segmented and modular, unlike Snoopy's.
  so you can add body sensors - including ultrasonic, optical proximity,
  collision, touch, laser pointer, optical distance - without reprinting
  the entire Loki's body. I would also venture a guess that - for now -
  Roomba-like bumper collision sensors may not be necessary for a pet
  robot.
  - the assembly becomes simplified because, unlike Snoopy, by default,
  Loki doesn't have a bumper (to sense collisions), yet you can add
  a bumper and collision sensors later if you wish so.
  - the CAD design becomes simpler (including myself)
- to be sturdier than Snoopy. The side walls now support upper plates.

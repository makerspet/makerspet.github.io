---
layout: post
title: Loki 200mm, Fido pet robot build, bring-up instructions
author: iliao
categories: [ Loki-pet-robot, 200mm, Fido-pet-robot, 250mm ]
image: assets/images/webp/Loki-v200.webp
# featured: true
# hidden: true
# comments: false
# tags: [red, yellow]
# rating: .5
# comments: false
---
Here is Loki, a 200mm pet robot.
Loki's dimensions is small enough to fit the widely used 210x250mm and 220x220mm
3D print volumes, so you don't have to invest in a bigger 3D printer.

Loki comes with his bigger brother Fido, 250mm. Both robots are basically identical, except for the size.

Snoopy, a 300mm robot, is the oldest and the biggest brother in the family.

Once the software is finished, Loki will act as a pet - look cute, play ball, hide-and-seek and chase,
demand its owners' attention and greet its owners happily at the door.
To get a feel of what Maker's Pet robots will do, watch Loki's big (300mm) brother
Snoopy (in a simulation)
- [play ball and hide ](https://kaia.ai/blog/snoopy-hides-plays-ball-in-simulation/)
under a table
- [self-drive, map and navigate](https://kaia.ai/blog/gazebo-mapping-navigation-demo/) a living room, all automatically.

Utility functions will include patrolling the house.

You can download design files here:
- Loki 200mm on [GitHub](https://github.com/makerspet/makerspet_loki)
- Fido 250mm on [GitHub](https://github.com/makerspet/makerspet_fido)

Each design repository includes:
- Fusion 360 3D CAD design files
- 3MF, STL files for 3D printing
- Arduino firmware source code
- ROS2 robot description package, configuraiton files and a Gazebo simulation model
- KiCad electronics schematics, BoM; PCB layout is in the works
- Assembly documentation is in the works, including assembly and bringup videos

## Step-by-step assembly instructions.
<div class="text-center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/WPB2B1DPf_s?si=vKl0UPY-jvC7vU5l&list=PLOSXKDW70aR8SA16wTB0ou9ClKhv7micy" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>
<p></p>

## One-time robot and PC setup instructions.
<div class="text-center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/XOc5kCE3MC0?si=Ea7-jGM7AQ_eJeUj&list=PLOSXKDW70aR8SA16wTB0ou9ClKhv7micy" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>
<p></p>

## Robot bring-up instructions video
<div class="text-center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/L_XbkA4pwRc?si=xbA206g8rESLKRwt&list=PLOSXKDW70aR8SA16wTB0ou9ClKhv7micy" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>
<p></p>

## Robot 3D printing instructions
<div class="text-center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/4k6W1QyJMMw?si=GYVRPQU3Z1ohQ-Zg&list=PLOSXKDW70aR8SA16wTB0ou9ClKhv7micy" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>
<p></p>

## Robot's Arduino ESP32 breakout board setup instructions
<div class="text-center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/zizGI8MjANU?si=I52Exhl3NUy_7eSQ&list=PLOSXKDW70aR8SA16wTB0ou9ClKhv7micy" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>
<p></p>

## CAD design animation (Fusion 360).
<div class="text-center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/_hDMFZ_Ny5s?si=CyJjd7Vz9T6qbCYG&list=PLOSXKDW70aR8SA16wTB0ou9ClKhv7micy" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>
<p></p>

## Loki's head 3D printed 

Loki's head gets 3D printed using a silk red PLA on a Prusa MK3.5S.

<div class="text-center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/MUxyDBdmDjE?si=3Ntay33aPRWOy4wE&list=PLOSXKDW70aR8SA16wTB0ou9ClKhv7micy" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>
<p></p>

## Loki design notes

Loki is designed
- to be easily scalable to different sizes, including 250mm.
- to be modular - similar to Snoopy, but simplified
  - the side body will be segmented and modular, unlike Snoopy's,
  so you can add body sensors - including ultrasonic, optical proximity,
  collision, touch, laser pointer, optical distance - without reprinting
  the entire Loki's body. I would also venture a guess that - for now -
  Roomba-like bumper collision sensors may not be necessary for a pet
  robot.
  - the assembly becomes simplified because, unlike Snoopy, by default,
  Loki doesn't have a bumper (to sense collisions), yet you can add
  a bumper and collision sensors later if you wish so.
  - the CAD design becomes simpler (including for myself)
- to be sturdier than Snoopy. The side walls now support upper plates.

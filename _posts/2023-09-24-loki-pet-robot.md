---
layout: post
title: A 200mm pet robot in the works!
author: iliao
categories: [ Loki-pet-robot, 200mm ]
image: assets/images/webp/Loki-v200.webp
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

Once finished, Loki will act as a pet - look cute, play ball, hide-and-seek and chase,
demand its owners' attention and greet its owners happily at the door.
To get a feel of what Maker's Pet robots will do, watch Loki's big (300mm) brother
Snoopy (in a simulation)
- [play ball and hide ](https://kaia.ai/blog/snoopy-hides-plays-ball-in-simulation/)
under a table
- [self-drive, map and navigate](https://kaia.ai/blog/gazebo-mapping-navigation-demo/) a living room, all automatically.

The 200mm Loki - and 250mm Fido - designs are about half done by now.
I'm making both designs simple to 3D print, assemble and mod.
The designs are also (nearly) identical except for sizing.

Here is CAD design animation (Fusion 360).

<div class="text-center">
<iframe width="473" height="840" src="https://www.youtube.com/embed/cdvADZQeDnA" title="Designing my home robot in CAD Fusion 360 - Arduino, ESP32, ROS, 3D printed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>
<p></p>

Utility functions will include patrolling the house.

Please follow our project on [Facebook]({{ site.facebook_group_url }})
[Reddit]({{ site.reddit_group_url }}), [Twitter]({{ site.twitter_url }}) 
or [YouTube]({{ site.youtube_url }}) where I post regular updates and tutorials.

Loki's Arduino firmware and software (ROS2) are ready - you can download the
files [here](https://github.com/makerspet/makerspet_loki).
Loki's Fusion 360, STL and 3MF files are in the works.

I'm designing Loki
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

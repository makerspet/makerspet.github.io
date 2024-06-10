---
layout: post
title: The Network Architecture
author: iliao
categories: [ Software ]
image: assets/images/webp/network_architecture.webp
# featured: true
# hidden: true
# comments: true
# tags: [red, yellow]
# rating: .5
---
Here is the current network connections architecture for Kaia.ai platform.

- The home robot's ESP32 micro-controller talks over WiFi to the Local PC.
- The home robot's smartphone talks over WiFi to the local PC.
  - Currently the ESP32 and the smartphone do not talk directly to each other.
- The cloud talks to all three local devices - the ESP32, the smartphone and the Local PC

Here are the functions assigned to each device:

- The local PC runs (in a Docker container):
  - ROS2 mapping, localization and navigation.
  - Micro-ROS that communicates with the ESP32.
  - Various non-ROS2 computation including image recognition of the smartphone camera feed
- The EPS32 runs:
  - Motor control
  - Laser scanner control
  - Micro-ROS for Arduino that communicates with the Local PC, including sending the laser scan data
- The cloud runs:
  - user authentication
  - some key functionality that I will describe at a later time
- The smartphone runs a browser that:
  - displays the robot face animations
  - forward the camera feed and microphone sound to the Local PC
  - plays audio

The PC can run any OS that supports Docker, including Windows OS and Linux.
The minimum local PC requirement should be 4GB of RAM, enough to run Docker.
The more powerful the local PC is - the more responsive the robot should be.

<blockquote>{% include signup-form.html %}</blockquote>

Just about any 2-3 years old smartphone should suffice as long as it can run a browser that
allows camera and sound capture.

Sometime later, I will continue this article to explain the order in which connections are established,
the authentication and how the various ways the user can communicate with the robot.
---
layout: post
title: ESP32, ESP32-S3 GPIO Limitations
author: iliao
categories: [ ESP32 ]
image: assets/images/webp/ESP32_WROOM_32_DevKit_v1.webp
# featured: true
# hidden: true
# comments: true
# tags: [red, yellow]
# rating: .5
---

[ESP32](https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_en.pdf) (and its DevKit boards) has a number of limitations with respect to its GPIOs. Here is a table of issues to keep in mind.

The took the list of ESP32 GPIO limitations from a [Randomnerd Tutorials post](https://randomnerdtutorials.com/esp32-pinout-reference-gpios/) and added a handful more limitations, unusual/undocumented behaviors, tips and tricks that we have noticed.

<style>
th, td {
  border: 1px solid black;
  padding: 2px;
}
</style>

<table style="border: 1px solid gray;">
<thead>
<tr class="header" style="background-color: #E5E4E2;">
<th>GPIO</th>
<th>Input</th>
<th>Output</th>
<th>Notes</th>
</tr>
</thead>

<tbody>

<tr>
<td markdown="span">0</td>
<td markdown="span">Pulled up internally, Caution</td>
<td markdown="span">Caution</td>
<td markdown="span">Outputs a signal at boot. Must be LOW to enter flashing mode. Connected to BOOT button on Dev Kit boards. May be used as input, e.g. to read the BOOT button status: pinMode(0, OUTPUT); uint8_t boot = digitalRead(0);</td>
</tr>

<tr>
<td markdown="span">1</td>
<td markdown="span">TX pin, Caution</td>
<td markdown="span">Caution</td>
<td markdown="span">Outputs signal at boot. This pin is used for serial code upload. You may use this pin for other purposes after the code upload  (or if your code loads from flash), but doing so may break your serial communication.</td>
</tr>

<tr>
<td markdown="span">2</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span">Connected to on-board LED in ESP32 Dev Kits. Must be left floating or LOW to enter the flashing mode.</td>
</tr>

<tr>
<td markdown="span">3</td>
<td markdown="span">Caution</td>
<td markdown="span">RX pin, Caution</td>
<td markdown="span">This pin is used for serial code upload. You may use this pin for other purposes after the code upload  (or if your code loads from flash), but doing so may break your serial communication.</td>
</tr>

<tr>
<td markdown="span">4</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">5</td>
<td markdown="span">Pulled up internally, Caution</td>
<td markdown="span">Caution</td>
<td markdown="span">Outputs a signal at boot. This is a strapping pin that sets the timing of the SDIO slave.</td>
</tr>

<tr>
<td markdown="span">6</td>
<td markdown="span">x</td>
<td markdown="span">x</td>
<td markdown="span">Connected to the integrated SPI flash. Leave unconnected.</td>
</tr>

<tr>
<td markdown="span">7</td>
<td markdown="span">x</td>
<td markdown="span">x</td>
<td markdown="span">Connected to the integrated SPI flash. Leave unconnected.</td>
</tr>

<tr>
<td markdown="span">8</td>
<td markdown="span">x</td>
<td markdown="span">x</td>
<td markdown="span">Connected to the integrated SPI flash. Leave unconnected.</td>
</tr>

<tr>
<td markdown="span">9</td>
<td markdown="span">x</td>
<td markdown="span">x</td>
<td markdown="span">Connected to the integrated SPI flash. Leave unconnected.</td>
</tr>

<tr>
<td markdown="span">10</td>
<td markdown="span">x</td>
<td markdown="span">x</td>
<td markdown="span">Connected to the integrated SPI flash. Leave unconnected.</td>
</tr>

<tr>
<td markdown="span">11</td>
<td markdown="span">x</td>
<td markdown="span">x</td>
<td markdown="span">Connected to the integrated SPI flash. Leave unconnected.</td>
</tr>

<tr>
<td markdown="span">12</td>
<td markdown="span">Caution</td>
<td markdown="span">OK</td>
<td markdown="span">Boot fails if pulled high. Don't pull this pin up or down externally.</td>
</tr>

<tr>
<td markdown="span">13</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">14</td>
<td markdown="span">Caution</td>
<td markdown="span">Caution</td>
<td markdown="span">Outputs a signal at boot. Toggles while Arduino IDE is waiting for the user to press the BOOT button to upload firmware code.</td>
</tr>

<tr>
<td markdown="span">15</td>
<td markdown="span">Caution</td>
<td markdown="span">Caution</td>
<td markdown="span">Outputs a signal at boot.</td>
</tr>

<tr>
<td markdown="span">16</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span">GPIO16 should be pulled up and left unused in ESP32-WROOM-32E modules using QSPI RAM ESP32D0WDR2V3 IC</td>
</tr>

<tr>
<td markdown="span">17</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">18</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">19</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">20</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">21</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">22</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">23</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">24</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">25</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">26</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">27</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">28</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">29</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">30</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">31</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">32</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">33</td>
<td markdown="span">Caution</td>
<td markdown="span">Caution</td>
<td markdown="span">Sometimes goes high (instead of normal low) during reset (EN button pressed).</td>
</tr>

<tr>
<td markdown="span">34</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">35</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">36</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

<tr>
<td markdown="span">39</td>
<td markdown="span">OK</td>
<td markdown="span">OK</td>
<td markdown="span"></td>
</tr>

</tbody>
</table>
<p></p>

## ESP32-S3 GPIO limitations

ESP32-S3 seems to have less GPIO limitations compared to ESP32. That said, there still have been surprises.

- `pinMode(26, INPUT);` in Arduino `setup()` function usually crashes my code built with Espressif Arduino compiler/SDK v2.0.17. Usually - not always.

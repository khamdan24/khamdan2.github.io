---
title: Module's Block Diagram
tags:
- tag1
- tag2
---

## Overview
Block diagram for the locomotion control system, includes power distribution, sensing, control, and actuation. The motor driver is powered by a 12 V power source, which is then stepped down to 3.3 V to power the PIC18F47K42 microcontroller, sensors, and display.The controller gets wheel speed feedback from a Hall effect sensor, and then the data status appears on an OLED screen. The left and right gear motors are driven by the motor driver, which receives control signals from the microcontroller after processing sensor data.


To get some initial formatting help, one can view ["here"](https://embedded-systems-design.github.io/EGR304DataSheetTemplate/Appendix/basic-markdown-examples/) some basic techniques.


## Block Diagram 
![Example of Indivial Block diagram ](BD.drawio.png)

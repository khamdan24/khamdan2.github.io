---
title: Welcome
tags:
- tag1
- tag2
---
<center>
<font size= "6">Khalid Hamdan Datasheet</font><br>
as part of<br>
<font size= "8"> Project Name</font><br>
for<br>
<font size= "5"> Team 303 </font><br>

**Submission: March, 6, 2026**
</center>

## Introduction

The Locomotion Control datasheet for Team 303's search and rescue robot documents the design and performance of the locomotion subsystem, which handles all movement-related functions—from rough terrain navigation to speed regulation and system integration. The module is built around an ESP32 microcontroller, which processes wheel speed data from a Hall effect sensor to control left and right gear motors via an IFX9201SG motor driver. Power is supplied at 12V and stepped down to 3.3V for the ESP32 and sensors. Communication with other subsystems is handled through SPI (to control the motor driver) and UART (to receive commands from the wireless module).

### Project Summary

Team 303 is developing a search and rescue robot capable of traversing uneven terrain and supporting both autonomous and manual operation. My contribution is the Locomotion Control Module, which ensures the robot can move smoothly over rough ground, maintain stability, and accurately control wheel speed while integrating with the broader system.

* Context for our team project [team report.](https://egr314-s-2026-303.github.io)

### My Contribution

* The Locomotion Control Module enables the robot to move reliably over rough terrain while maintaining stability and speed control. My work focused on:

* Motor Control: Using an ESP32 microcontroller and IFX9201SG motor driver to independently control left and right gear motors based on real-time feedback and external commands.

* Speed Sensing: Integrating a Hall effect sensor to measure wheel speed and adjust motor output accordingly.

* Power Distribution: Designing the 12V to 3.3V regulation to power the ESP32 and sensors.

* System Communication: Implementing SPI to command the motor driver and UART to receive wireless motor commands from another team member (Matthew Sanderson).

* Command Handling: Parsing incoming messages (message types 0x10, 0x11, 0x12) to execute forward, reverse, turn, and stop actions.

* Requirement Implementation: Meeting both threshold and target performance levels for rough terrain mobility, stability, and speed accuracy.

To review the details listed of the material used to construct the subsection, you can review it in the ["BOM"](https://embedded-systems-design.github.io/EGR314DataSheetTemplate/04-BOM/BOM/) section of the datasheet.

>Continue for all the remaining/missing sections.

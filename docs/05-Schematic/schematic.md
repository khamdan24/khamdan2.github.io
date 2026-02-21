---
title: Module Schematic
---

## Overview
The locomotion control module distributes 12V power to the motor driver and converts it to 3.3V to run the PIC18F47K42 and sensor so that the microcontroller reads the data wheel speed from a Hall effect sensor and uses this feedback to control the left and right gear motors through the IFX9201SG, allowing the the car/RC to move smoothly, maintain stability, and hopfully regulate speed on rough terrain. Power and communication are shared between modules through thr headers to enable coordinated movement and accurate distance control.


![schematic](Screenshot.png){style width:"350" height:"300;"}
**Figure ##:** Showing a example schematic.


## Resouces

The schematic as a PDF download is available [*here*](ExampleSchematic.pdf), and the Zip folder of the project [*here*](dummyZip.zip).

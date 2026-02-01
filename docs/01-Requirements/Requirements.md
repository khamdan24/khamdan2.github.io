---
title: Module's Requirements
---

## Module Requirements
The following sections document the requirements that the this module need to fulfills to .....

| **Requirement Description** | **Measure of<br> Threshold** | **Target<br>Measure** |**Stretch<br>Requirement<br>(Y-N)**|
|-----------------------------| ----------------- | ----------------- | :-----: |
| Surface mounted, 3.3V switching power regulatore | 3.2 Volts | 3.3 Volts | No |
| Drone must move over rough/rocky ground | Can consistently drive 5 mph over dirt and gravel | Can drive 10 mph over dirt and large (5x5x5 in. average) smooth rocks | Yes |
| Stable while moving | MoT of #2 without flipping ove | MoT of #1 without flipping over | No |
| Human Design Interface; Respond manually with buttons | Small OLED screen with pushbuttons that permits a user to view all sensor data in text; directly control the actuator; modify setpoints on all the system boards; toggle GPIO debug pins on ALL subsystems | All the content in MoT and ability to tune sensors and actuators with controls on exterior of device | No |
| I2C or SPI | Control peripheral devices such as sensors, microphones, and camera | Same as MoT | No |
| Daisy chain UART | Daisy chain UART connection between all subsystems | Separate UART loops for high speed communication through certain subsystems | No |
| Distance controlled wheel speed | The robot can control wheel speed and can display its speed within +-10 cm/s error, and can drive backwards. | MoT and robot uses sensors to determine speed, maneuver around obstacles by turning, and knows speed within +- 1 cm/s error | Yes |

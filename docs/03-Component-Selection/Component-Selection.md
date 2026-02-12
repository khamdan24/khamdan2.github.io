---
title: Module's Selected Major Components
---

## Module's Selected Major Components

### Actuator: 12V DC Gear Motor with Feedback
Requirement: 12V operation, integrated speed feedback, capable of driving robot over rough/rocky ground at 5-10 mph, surface-mount encoder interface preferred.


For more details, review the ["Appendix - Component Selection Process - Actuator"](https://embedded-systems-design.github.io/EGR314DataSheetTemplate/Appendix/01-Componet-Selection/Component-Selection-Process/#actuator) selection.

-----------

1. HG37-060-AB-00

    ![](motorONE.png)

    * $28.83/each
    * [link to product](https://www.digikey.com/short/p8jjb8t3)

    | Pros                                      | Cons                                                             |
    | ----------------------------------------- | ---------------------------------------------------------------- |
    | Lower cost – $28.83                       | Needs 24V, but we have 12V      |
    | durable, efficient                        | too slow for 5 mph   |
    |  good torque                              | 12 weeks to arrive |
    | Industrial grade	                        | Might need extra parts to work |
    | 37mm diameter |



2. Pololu 24V 37D

    ![](motorTWO.png)

    * $44.95/each
    * [link to product](https://www.pololu.com/product/4747)

    | Pros                                      | Cons                                                             |
    | ----------------------------------------- | ---------------------------------------------------------------- |
    | Strong build   | Needs 24V |
    | has Quiet gears      | expensive then the others |
    | 64 CPR encoder | Needs extra chip for 3.3V |
    | Low current draw | Power supply can be harder to design |


3. DIA42B 10W

    ![](motorTHREE.png)

    * $34.24/each
    * [link to product](https://www.digikey.com/short/2r033qnc)

    | Pros                                      | Cons                                                             |
    | ----------------------------------------- | ---------------------------------------------------------------- |
    | Runs on 12V  | No encoder |
    | Compact size | Only 6W power |
    | Good for daylight work | Speed isnt listed |
    | 14 week lead time | Cant handle heaviness |
    | RoHS compliant | No gearbox – need external gears |

4. FIT0441

    ![](motorFOUR.png)

    * $19.90/each
    * [link to product](https://www.digikey.com/short/2d2cdrnw)

    | Pros                                      | Cons                                                             |
    | ----------------------------------------- | ---------------------------------------------------------------- |
    | Runs on 12V | Lower torque than 24V motor |
    | Has encoder | 159 RPM |
    | Brushless | Smaller shaft size |
    | Low cost | Isn't an industrial grade |
    | 9 week lead time | less durable |
    | Integrated controller |  

Final Choice: option 4 – FIT0441

**Rationale:**  I chose option 4 because it runs on 12V, so no boost converter needed. It also has an encoder for speed control, which meets my requirement for parts. It's also cheaper and has a shorter lead time than the Nidec motor. Even though it may need extra gearing to reach 5 mph, it is easier to use and fits the project timeline better.

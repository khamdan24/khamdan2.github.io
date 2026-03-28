# Message Compliance
My part of the project is the locomotion control. I control the movement of our project using the PIC18F27Q43 nano board to function the two control motors (IFX9201SGAUMA1) making it move by using two motors when receiving messages from the Wireless by Matthew Sanderson, who is in charge of sending commands and receiving from others. Once it receives the commond it will start reading the code and message to move.

How it goes:
- Go straight - Both motors forward
- Go backward - Both motors reverse
- Turn left - Left motor reverse while the Right motor goes forword
- Turn right - Right motor reverse while the Left motor goes forword
- Stop - Both motors stop

## Pin PIC
| **Motor** | **CS** | **SCK** | **SI** |**SO** |
|:----------|:-------|:--------|:-------|:------|
|Left Motor |RC1|RC0|RC2|RC3|
|Right Motor|RC5|RC4|RC6|RC7|

## Message Type 0x10 - Left Motor
| **Field** | **Byte 1** | **Byte 2** | **Byte 3** |
|:----------|:-----------|:-----------|:-----------|
|Variable Name|message_type|motor_id  |motor_speed |
|Variable Type|uint8_t|uint8_t|int8_t|
|Min Value|0x10|0x01|-100|
|Max Value|0x10|0x01|100|
|Examlpe|0x10|0x01|75|

## Message Type 0x11 - Right Motor
| **Field** | **Byte 1** | **Byte 2** | **Byte 3** |
|:----------|:-----------|:-----------|:-----------|
|Variable Name|message_type|motor_id  |motor_speed |
|Variable Type|uint8_t|uint8_t|int8_t|
|Min Value|0x11|0x01|-100|
|Max Value|0x11|0x01|100|
|Examlpe|0x11|0x01|-50|

## Message Type 0x12 - Motor stop and go
| **Field** | **Byte 1** | **Byte 2** | **Byte 3** |
|:----------|:-----------|:-----------|:-----------|
|Variable Name|message_type|motor_id  |motor_speed |
|Variable Type|uint8_t|uint8_t|int8_t|
|Min Value|0x12|0x03|0.00|
|Max Value|0x12|0x03|0.01|
|Examlpe|0x12|0x03|0.01|

# Message Compliance
My part of the project is the locomotion control. I control the movement of our project using the ESP32 to drive the two control motors (IFX9201SGAUMA1), making the system move by using two motors when receiving messages from the Wireless module managed by Matthew Sanderson, who is in charge of sending commands and receiving data from other modules. Once the ESP32 receives a command, it reads and processes the message to execute the appropriate movement.

## How it goes:
- Go straight - Both motors forward
- Go backward - Both motors reverse
- Turn left - Left motor reverse while the Right motor goes forword
- Turn right - Right motor reverse while the Left motor goes forword
- Stop - Both motors stop

## ESP32
| **Motor** | **CS** | **SCK** | **SI** |**SO** |
|:----------|:-------|:--------|:-------|:------|
|Left Motor |5|18|21|17|
|Right Motor|4|18|21|17|

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
|Min Value|0x12|0x03|0|
|Max Value|0x12|0x03|1|
|Examlpe|0x12|0x03|1|

Note: For message type 0x12, motor_speed acts as a boolean where 0 = stop and 1 = go.

# In the Project 
The locomotion control module exposes the following command interface over UART (9600 baud, 8N1). All messages follow the format: `AZ[ID][CMD]YB`

| Command Byte | Action | Description |
|--------------|--------|-------------|
| `F` or `f`   | Forward  | Drives motor forward via SPI command 0xEF |
| `R` or `r`   | Reverse | Drives motor reverse via SPI command 0xED |
| `S` or `s`   | Stop | Stops motor via SPI command 0xE3 |

**UART Configuration:**
- Baud Rate: 9600
- TX Pin: GPIO 17
- RX Pin: GPIO 16
- Data Bits: 8
- Parity: None
- Stop Bits: 1

**SPI Configuration (to IFX9201):**
- Bus: SPI2
- Baud Rate: 1 MHz
- Polarity: 0, Phase: 1
- CS Pin: GPIO 5
- SCK: GPIO 18, MOSI: GPIO 23, MISO: GPIO 19

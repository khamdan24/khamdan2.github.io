# Resources

## Final Code
- **ESP32:** [Link to your final ESP32 code .zip file]
- **Main code:** `main.py` - Contains UART message parsing, SPI motor control, and main event loop
```python
from machine import Pin, SPI, UART
import time
import uasyncio as asyncio

# IFX9201 SPI commands
CMD_FORWARD = 0xEF
CMD_REVERSE = 0xED
CMD_STOP    = 0xE3

# Pin definitions
CS_PIN  = 5
DIR_PIN = 4
DIS_PIN = 2
LED_PIN = 15

# SPI pins (ESP32 default SPI2)
SCK_PIN  = 18
MOSI_PIN = 23
MISO_PIN = 19

# UART settings (matching Matt's setup)
UART_BAUD = 9600
UART_TX_PIN = 17
UART_RX_PIN = 16

# Team IDs (matching Matt's protocol)
team = [b'A', b'M', b'L', b'V', b'K', b'C']
my_id = b'M'  # This is Matt
broadcast = b'X'
MAX_MESSAGE_LEN = 64


def spi_send_command(spi, cs_pin, command):
    """Send SPI command to IFX9201"""
    cs_pin.value(0)          # Select device (active low)
    time.sleep_us(10)
    spi.write(bytes([command]))
    time.sleep_us(10)
    cs_pin.value(1)          # Deselect device


def motor_forward():
    """Move motor forward"""
    global led
    led.value(1)
    spi_send_command(spi, cs, CMD_FORWARD)
    print("Motor: Forward")


def motor_reverse():
    """Move motor in reverse"""
    global led
    spi_send_command(spi, cs, CMD_STOP)
    time.sleep_ms(500)  # safety delay
    led.value(1)
    spi_send_command(spi, cs, CMD_REVERSE)
    print("Motor: Reverse")


def motor_stop():
    """Stop motor"""
    global led
    led.value(0)
    spi_send_command(spi, cs, CMD_STOP)
    print("Motor: Stop")


def process_uart_message(message):
    """Process incoming UART message from Matt"""
    try:
        # Message format: b'AZ[ID][command]...YB'
        # Where first byte is 'A', second is 'Z', third is sender ID, fourth is command
        if len(message) >= 4:
            # Check if message starts with 'AZ' and ends with 'YB'
            if message[0:2] == b'AZ' and message[-2:] == b'YB':
                # Extract sender ID (3rd byte) and command (4th byte)
                sender_id = message[2:3]
                command_byte = message[3:4]
                
                # Check if sender is Matt (M)
                if sender_id == my_id:
                    print(f"Received command from Matt (M): {command_byte}")
                    
                    # Process motor commands
                    if command_byte == b'F' or command_byte == b'f':
                        motor_forward()
                    elif command_byte == b'R' or command_byte == b'r':
                        motor_reverse()
                    elif command_byte == b'S' or command_byte == b's':
                        motor_stop()
                    else:
                        print(f"Unknown command: {command_byte}")
                else:
                    print(f"Message from {sender_id} (ignoring)")
            else:
                print("Invalid message format")
        else:
            print(f"Message too short: {len(message)} bytes")
            
    except Exception as e:
        print(f"Error processing message: {e}")


def read_uart():
    """Read and parse UART messages"""
    if uart.any():
        # Read available bytes
        data = uart.read()
        if data:
            print(f"Raw UART: {data}")
            process_uart_message(data)


# Initialize global objects
spi = None
cs = None
direction = None
disable = None
led = None
uart = None


def setup():
    """Initialize all hardware"""
    global spi, cs, direction, disable, led, uart
    
    # Initialize pins
    cs = Pin(CS_PIN, Pin.OUT, value=1)
    direction = Pin(DIR_PIN, Pin.OUT, value=0)
    disable = Pin(DIS_PIN, Pin.OUT, value=0)
    led = Pin(LED_PIN, Pin.OUT, value=0)
    
    # Initialize SPI
    spi = SPI(
        2,
        baudrate=1000000,
        polarity=0,
        phase=1,
        bits=8,
        firstbit=SPI.MSB,
        sck=Pin(SCK_PIN),
        mosi=Pin(MOSI_PIN),
        miso=Pin(MISO_PIN)
    )
    
    # Initialize UART for receiving from Matt
    uart = UART(2, baudrate=UART_BAUD, tx=UART_TX_PIN, rx=UART_RX_PIN)
    uart.init(UART_BAUD, bits=8, parity=None, stop=1)
    
    time.sleep_ms(100)
    print("=" * 40)
    print("Motor Control with UART Receiver")
    print(f"My ID: {my_id}")
    print("Waiting for commands from Matt (M)...")
    print("Commands: F (Forward), R (Reverse), S (Stop)")
    print("=" * 40)


def main():
    setup()
    
    # Main loop - checks for UART messages
    while True:
        read_uart()
        time.sleep_ms(50)  # Small delay to prevent CPU hogging


# Run program
if __name__ == "__main__":
    try:
        main()
    except KeyboardInterrupt:
        print("\n\nProgram stopped")
        # Clean shutdown - stop motor
        if spi and cs:
            motor_stop()
            cs.value(1)
```

## Documentation
- [Final Schematic]
- [Final PCB Gerber Files]

## Demonstration Video
[Motor video part](https://youtu.be/VkRqs9AWPHQ?si=H0qLijxY4l5cSQjT)

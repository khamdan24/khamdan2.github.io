# Reflection

## Review of Module's Success

| Requirement | Meet |Status |
|-------------|--------|--------|
|Goes at 5 mph|Y|Manged to move when powerd and told to|
|Buttons for control|N|Only remote control|
|SPI communication|Y|ESP32 sends command to motor drive|
|UART module|Y|Receives commands from team|

Success: UART messages come in correctly. SPI sends the right commands (Forward(F), Reverse(R), Stop(S)). The motor runs on between 5V and 12V.

## Startup Tips
Things I wish I knew before starting:

- Keeping it simple – Get one thing working (like UART) before adding another (like SPI). I tried to do everything at once and wasted time.

- Analyzer – A cheap $10 tool shows you if your SPI or UART is actually sending data.

- Always stop the motor first – My code sends a stop command before reversing. Without that delay, you can break the motor driver.

## Lessons Learned 

- Message format – Use the AZ[ID][CMD]YB before writing any code. Without that code, it wont't work together with your team.

- Check your power budget early – My motor draws 2A at full power. My power supply only gave 1.5A. Simple math would have saved me.

- Test each piece individually – Test SPI with just the motor driver first. Test UART with just the wireless module first. After everthing is tested put them together and see how it goes.

- Write your pin numbers – I used CS_PIN = 5, LED_PIN = 27, so you can find and change yours pins easy.

- Vibration breaks things – My motor connection got loose when it starts moving on command. Adding some tape or a built in holder.

- Ordering parts – I bent the motor shaft during testing and had no replacement. Order two of anything that moves.

- Start simple – Get the motor to spin forward first. Worry about speed control and sensors later. I tried to do everything at once and got stuck for days.

- Add an LED – I put an LED that turns on when a command is active. This helped me know the code was running even when the motor was not moving.

- Always stop before going – Going straight from forward to reverse can break the motor driver. Add a small delay and a stop command in between, or make it go forward, stop, and then reverse.

- Print on console – Use print() to show what your UART is receiving. If you cannot see the data, you cannot debug it.

## Recommendations 

- Get an analyzer before the class – It is the most useful tool for debugging communication problems. Learn how to use it early.

- Order extra parts – If some of your item's break all of the sudden, you might have to order and wait for new ones to arrive. Always order at least two of your part.

- Start your PCB early – My 5-day PCB order took 12 days.

- Test as you build – Write a tiny script to blink an LED. Then one to send SPI. Then one to read UART. Put them together at the end. This makes the debugging part easy.

Get your message format approved before coding – The teaching team made me change my protocol twice. Get sign-off first so you do not have to rewrite code.

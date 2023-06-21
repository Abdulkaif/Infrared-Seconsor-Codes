# MicroPython LCD and IR Sensor Code

This is a MicroPython code snippet that demonstrates the usage of an LCD and an IR sensor. The code utilizes the utime, machine, and gpio_lcd modules.

### Dependencies
- utime
- machine
- gpio_lcd

### Code

```
import utime
from machine import Pin, PWM, ADC
from gpio_lcd import GpioLcd

# LCD PART:

pwm = PWM(Pin(7))
pwm.freq(50)
pwm.duty_ns(1500000)

# Create the LCD object
lcd = GpioLcd(rs_pin=Pin(8),
              enable_pin=Pin(9),
              d4_pin=Pin(10),
              d5_pin=Pin(11),
              d6_pin=Pin(12),
              d7_pin=Pin(13),
              num_lines=2, num_columns=16)

led = Pin(4, Pin.OUT)

ir_sensor = Pin(28, Pin.IN)

while True:
    lcd.clear()
    if ir_sensor.value() == 0:
        lcd.putstr("Detected")
    else:
        lcd.putstr("Not detected")
        
    utime.sleep(0.2)
```

### Description

The code performs the following actions:

- Initializes the PWM (Pulse Width Modulation) with a frequency of 50 and a duty cycle of 1.5 ms.
- Creates an LCD object using the specified GPIO pins for the RS, Enable, and data lines. It configures the LCD to have 2 lines and 16 columns.
- Sets up a pin (led) as an output pin.
- Sets up a pin (ir_sensor) as an input pin.
- Enters an infinite loop:
- Clears the LCD screen.
- Checks the value of the IR sensor pin:
- If the value is 0, displays "Detected" on the LCD.
- If the value is not 0, displays "Not detected" on the LCD.
- Sleeps for 0.2 seconds before repeating the loop.


### Usage

To use this code:

- Make sure you have the required dependencies installed on your MicroPython board.
- Connect the LCD and IR sensor to the appropriate GPIO pins as defined in the code.
- Upload and run the code on your MicroPython board.
- Observe the LCD display for the "Detected" or "Not detected" message depending on the state of





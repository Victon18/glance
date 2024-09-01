- USB Type-C power in
- DSI display port
- Wireless / Bluetooth
- Micro-HDMI 0
- Micro-HDMI 1
- System-on-chip
---
This includes the central processing unit (CPU) and the graphics processing unit (GPU)

- GPIO
-----
(general-purpose input output) pins and the GPIO Pinout is an interactive reference to these GPIO pins.

Voltages
there are two 5V pins and two 3V3 pins on the board. It also has several ground pins (0V). All these pins are unconfigurable.

Outputs
A GPIO pin can be designated as an output pin. The pin set as output pin can be set to 3V3(high) or 0V(low).

Inputs
A GPIO pin can be designated as an input pin.
The pin set as input pin can be read as 3V3(high) or 0V(low). You can use internal pull-up or pull-down resistors

PWM: Pulse-width modulation
Software PWM are available on all the pins whereas Hardware PWM are available on GPIO12, GPIO13, GPIO18, and GPIO19.

SPI: Serial Peripheral Interface
The SPI are available on the following −
SPI0: MOSI (GPIO10); MISO (GPIO9); SCLK (GPIO11); CE0 (GPIO8), CE1 (GPIO7)
SPI1: MOSI (GPIO20); MISO (GPIO19); SCLK (GPIO21); CE0 (GPIO18); CE1 (GPIO17); CE2 (GPIO16)

I2C: Inter-integrated Circuit
The I2C are available on the following −
Data: (GPIO2); Clock (GPIO3)
EEPROM Data: (GPIO0); EEPROM Clock (GPIO1)

Serial
The serial function is available at the following −
TX(GPIO14)
RX(GPIO15)

- RAM
----
Together, these components form Raspberry Pi’s volatile and non-volatile memories:
the volatile RAM loses its contents whenever Raspberry Pi is powered off, while the non-volatile microSD card keeps its contents.

- CSI camera port
- 3.5mm AV
- PoE
- USB 2.0
- USB 3.0
-  Ethernet port

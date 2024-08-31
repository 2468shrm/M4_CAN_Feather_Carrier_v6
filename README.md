# M4_CAN_Feather_Carrier_v6

## Board Intent
The carrier board is a platform to utilize the [Adafruit M4 Feather CAN
Express](https://www.adafruit.com/product/4759) in FRC robotic applications.
It was developed primarily for students of FRC teams 2468 ("Team Appreciate"),
2687 ("Team Apprentice"), and 2689 ("Team Alpha"). Alone, the M4 Feather CAN
Express board doesn't easily interface to an FRC robot. However, when connected
to a carrier board the feather board has great application potential due to the
integrated CAN port, the M4-processor's native single-precision floating-point
support, etc. FRC robots use CAN as a communication network for its control
system.

The promise of the platform isn't that one can hook a single sensor to the platform
and send the sendor value over CAN. There are many examples of awesome dedicated circuits
that perform functions like these that would result in a smaller solution
(e.g. [Grapple Robotics LaserCAN](https://www.thethriftybot.com/products/pre-order-grapple-robotics-lasercan)
is a CAN-connected Time-of-Flight sensor). Rather, the platform enables creative
combination of sensors and application-specific processing in an off-roboRIO
accelerator. Moreover, the platform provides a great opportunity to start an embedded
journey.

The platform leverages the use of CircuitPython and easy connect to breakout circuits
from [SparkFun](https://sparkfun.com) and [Adafruit](https://adafruit.com). As
experience is gained with the platform prototype sensor solutions can be developed very rapidly. The platform also provides RIO-like interfacing.

## Board Block Diagram and Features

The following a a simplified block diagram of the carrier board. 

![alt text](https://github.com/2468shrm/M4_CAN_Feather_Carrier_v6/blob/main/Images/Block%20Diagram.png?raw=true)

The carrier board provies the following features to simplify integration onto an FRC robot:

- Socket for M4 Feather CAN Express board (4).
  - M4 Feather CAN Express board suitable for [CircuitPython](https://circuitpython.org/) use.
  - Jumper (U) allows carrier board 5V supply to feed back on USB-C VBUS.
  - For connecting to and powering USB-C devices when M4 board is acting as USB host.
  - Uses Wago 2601-3102 latching terminal block for wire attachment. 16-24 AWG.

- Socket for [Adafruit Ethernet FeatherWing](https://www.adafruit.com/product/3201) (N).
  - Provides ability to use an alternate networking interface; when CAN isn't appropriate.
  - Socket inapproriate for other FeatherWing due to SPI chip select use.

- Battery-friendly power input (P).
  - Wago 2601-3102 wire to board connection (D).
  - Convert 12V to 5V.
  - Output 5V @ 2.5A.
  - 12V and 5V indicator LEDs, D102 and D102, respectively.

- 4 digital input/outputs (DIOs) (IO and L).
  - A 4x3 header pin block (J3) provides roboRIO similar digital interface.
  - Signal, Power, and Ground for each digital I/O.
  - Jumper (J5) provides selectable power to DIO header ppwer pins.
  - I/Os use level shifter.
  - Each I/O has an LED indicating logical value (high = LED on, low = LED off).

- 4 analog inputs (AI).
  - Input range is 0V-3.3V.
  - Buffered through rail-to-rail operational amplifier in unity gain configuration.
  - A 4x3 header pin block () provides roboRIO similar analog interface.

- 3 Qwiic / STEMMA QT compatible interfaces (X1, X2, and X4).
  - X1 is 3.3V only.
  - X2 and X4 use a slide switch to provide either 3.3V or 5V on the connector power pins and also includes a level shifter.
  - X2 and X4 are intended to connect to the TFMini-S or LiDAR Lite.

- MicroSD card socket (M)
  - Uses SPI mode/interfacing.

- A Neopixel interface (E).
  - Intended use is to provide visual communication of processed results.
  - Uses Wago 2601-3103 latching terminal block for wire attachment. 16-24 AWG.

The interfaces described above are shown in the following annotated board render.

![alt text](https://github.com/2468shrm/M4_CAN_Feather_Carrier_v6/blob/main/Images/Interface%20Detail.png?raw=true)

The following diagram provides more detail to the pins for some of the board's connectors.

The 4x3 and 4x2 pin headers are shown to indicate their function. Ground pins have a
green box, power pins have a red box, and signal pins have a white box. These header
follows the RIO organization (modeled on the servo interface).

For the Analog In signals, the power is 3.3V (sourced from the M4 Feather CAN Express
board).

For the DIOs, the power is controlled by a 2 position jumper (J5) adjacent to the DIO header.
The diagram shows the jumper position for the applied voltage.
- 3.3V is selected by jumpering the middle pin to the inner pin.
- 5V is selected by jumpering the middle pin to the outer pin.

The DIO signals connect to the M4 microcontroller through a level shifter. The level
shifter VCCB supply is powered from the same voltage as the middle pin.

The DIOs are also accompanied by a 4x2 pin header that provides the same power and ground
as the 4x3. The intent for this arrangement is to be able to connect 4 [beam break
emitter/detactor pairs](https://www.adafruit.com/product/2168) to the DIOs. 

Connectors X2 and X4 are modified Qwiic connectors. The switches adjacent to X2 and X4
allow the power provided to their respective connector to be either 3.3V or 5V.
- 3.3V is selected by sliding the switch to the left.
- 5V is selected by sliding the switch to the right.

Both of these Qwiic / STEMMA QT connections include a level shifter between connector
and the M4 microcontroller. This flexibility on X2 and X4 is intended to allow the
connection of 5V I2C sensors such as the Garmin LiDAR Lite (v3 and v4) and the
TFMini-S sensor. 

Connector X1 is a regular Qwiic connector that uses 3.3V for supplying power to the
breakout board.

The Neopixel is a 3 pin interface. To facilitate a connection to an LED string with
soldered on wires, a Wago 2601-3103 connector is provided for wire to board. This
allows the use of stripped wire (or with crimped ferrules) instead of needing a PWM
style connector.

The battery connection is made through a Wago 2601-3102.

![alt text](https://github.com/2468shrm/M4_CAN_Feather_Carrier_v6/blob/main/Images/Signal%20Detail.png?raw=true)

The sockets for the Feather and FeatherWing boards are shown in the following diagram.
These are not interchangable. Nor is the FeatherWing socket capable of working with
a FeatherWing other than the Ethernet FeatherWing.

![alt text](https://github.com/2468shrm/M4_CAN_Feather_Carrier_v6/blob/main/Images/Feather%20Sockets.png?raw=true)

The power circuit for the carrier board is shown in the following diagram.

![alt text](https://github.com/2468shrm/M4_CAN_Feather_Carrier_v6/blob/main/Images/Power%20Supply.png?raw=true)

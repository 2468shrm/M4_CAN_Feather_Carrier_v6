# M4_CAN_Feather_Carrier_v6

## Board Intent
The carrier board is a platform to utilize the [Adafruit M4 Feather CAN Express](https://www.adafruit.com/product/4759) in robotic applications, primarily for students of FRC teams 2468 ("Team Appreciate"), 2687 ("Team Apprentice"), and 2689 ("Team Alpha"). Alone, the M4 Feather CAN Express board doesn't easily interface to an FRC robot. However the feather board has great application potential due to the integrated CAN port. FRC robots use CAN as a communication network for its control system.


## Board Block Diagram and Features

![alt text](https://github.com/2468shrm/M4_CAN_Feather_Carrier_v6/blob/main/Images/Block%20Diagram.png?raw=true)

The carrier board provies the following features to simplify integration to an FRC robot:

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

![alt text](https://github.com/2468shrm/M4_CAN_Feather_Carrier_v6/blob/main/Images/Signal%20Detail.png?raw=true)

![alt text](https://github.com/2468shrm/M4_CAN_Feather_Carrier_v6/blob/main/Images/Feather%20Sockets.png?raw=true)

![alt text](https://github.com/2468shrm/M4_CAN_Feather_Carrier_v6/blob/main/Images/Power%20Supply.png?raw=true)

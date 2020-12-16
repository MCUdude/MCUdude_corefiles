# Arduino core files for MCUdude's cores
[![Build Status](https://travis-ci.org/MCUdude/MCUdude_corefiles.svg?branch=master)](https://travis-ci.org/MCUdude/MCUdude_corefiles)

This repo contains the Arduino corefiles used with [MightyCore](https://github.com/MCUdude/MightyCore), [MegaCore](https://github.com/MCUdude/MegaCore), [MiniCore](https://github.com/MCUdude/MiniCore) and [MajorCore](https://github.com/MCUdude/MightyCore).

## Supported devices

* ATmega640, ATmega1280, ATmega2560
* ATmega64, ATmega128, ATmega1281, ATmega2561
* AT90CAN32, AT90CAN64, AT90CAN128
* ATmega8535, ATmega16, ATmega32, ATmega164A/P, ATmega324A/P/PA/PB, ATmega644/P, ATmega1284/P
* ATmega8515, ATmega162
* ATmega8, ATmega48/P/PA/PB, ATmega88/P/PA/PB, ATmega168/P/PA/PB, ATmega328/P/PA/PB

## Supported clock frequencies
By supported I mean clocks that accurate timing is implemented for (millis,
micros, delay, delayMicroseconds).

* 32 MHz
* 24 MHz
* 20 MHz
* 18.432 MHz
* 16 MHz
* 14.7456 MHz
* 12 MHz
* 11.0592 MHz
* 8 MHz
* 7.3728 MHz
* 4 MHz
* 3.6864 MHz
* 2 MHz
* 1.8432 MHz
* 1 MHz

### Accuracy of `micros()` and `delay()`

The `micros()` function has zero drift for power-of-two clock frequencies.
After that, the following frequencies have the lowest drift error:

* 20 MHz has a drift of 1 in 65536 (~15 ppm)
* 18.432 Mhz has a drift of  1 in 64000 (~16 ppm)
* 14.7456 MHz has a drift of 1 in 10000 (100 ppm)
* 24 MHz has a drift of 1 in 4000 (250 ppm)
* 18 MHz has a drift of 1 in 4000
* 12 MHz has a drift of 1 in 4000
* 22.1184 MHz has a drift of 1 in 2850 (350ppm)
* 11.0592 MHz has a drift of 1 in 2850

The remaining frequencies have drifts around 1 percent or better.

The `delay()` function uses `micros()` internally and inherits its accuracy.

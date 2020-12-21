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
* 22.1184 MHz
* 20 MHz
* 18.432 MHz
* 18 MHz
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

The remaining frequencies are sorted by finite drift accuracy:

* 20 MHz has a drift of 1 in 65536 (~15 ppm)
* 18.432 Mhz has a drift of 1 in 64000 (~16 ppm)
* 14.7456 MHz has a drift of 1 in 10000 (100 ppm)
*  7.3728 MHz has a drift of 1 in 10000
*  3.6864 MHz has a drift of 1 in 10000
*  1.8432 MHz has a drift of 1 in 10000
* 24 MHz has a drift of 1 in 4096 (244 ppm)
* 18 MHz has a drift of 1 in 4096
* 12 MHz has a drift of 1 in 4096
* 22.1184 MHz has a drift of 1 in 2857 (350ppm)
* 11.0592 MHz has a drift of 1 in 2857

The `delay()` function uses `micros()` internally and inherits its accuracy.

### Exactness of `millis()`

For the clock speeds listed above, `millis()` is corrected to zero drift.
Even for very long run times, the `millis()` function will precisely follow the
oscillator used.
We do not register the rollover of the `unsigned long` millis counter that
occurs every day or two; such would have to be done in the user's program.
Often this is not necessary:  Expressions like

    (int) (millis() - millis_old)

are correct even when rolling over provided `millis_old` is of type `unsigned long`
and old and new time are no more than 16 seconds apart.

For clock speeds of 16 MHz and below, the return value of `millis()`
occasionally jumps up by more than one (notwithstanding zero long-time drift).
Thus, when relying on consecutive returns, run at 18 MHz or above.


![spiral icon](https://i.imgur.com/8JeVKCG.png)

[![Build Status](https://travis-ci.com/akilhylton/spiral.svg?token=Mhdf3XXByqN3Nb1swBdo&branch=master)](https://travis-ci.com/akilhylton/spiral)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
## What is spiral?
spiral is a model rocket flight firmware that is built to runs on the HELIX Flight Computer. \
The firmware features libaries that supports control for servos, USART, SPI and the on-board hardware. 

## Directory Structure
* board -- Code that runs on the ATmega328P
* boardesp -- Code that runs on the ESP32
------
    board
        ├── servo # Library used for servo control
        ├── usart # Library used for USART communication
        ├── spi # Library used for SPI communication
        ├── hardware # Library used to control on-board hardware 

## spiral hardware uses Bluetooth Low Energy
Data is sent from an AVR microcontroller via UART and received by Silicon Lab's BGX13P BLE module. \
This exchage is biodirectional so data can also be sent out from the BLE module to AVR microcontroller.

![Imgur](https://i.imgur.com/SPr4X3p.png)
## Servo library usage example
```
#include "drivers/servo.h"

int main(void) {
  servoInit(); // Configures 16 bit registers for 50Hz PWM signal.
  servoAttach(Y_SERVO); 
  servoAttach(Z_SERVO);
  while(1) {
    servoWriteY(0); // Write angle 0 to servo controlling Y axis
    servoWwriteZ(0); // Write angle 0 to servo controlling Z axis
  }
  return 0;
}
```

Prerequisites
- AVR-GCC
- AVRDUDE


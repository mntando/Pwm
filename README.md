# PWM with Variable Duty Cycle and Frequency on Arduino

PWM on arduino with variable duty cycle (0 - 100) and frequency (any value in MHz).

## Table of Contents
- [Features](#features)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Acknowledgements](#acknowledgements)

## Features
- Variable duty cycle and frequency.
- Read duty cycle and frequency from variable resistors

## Getting Started
Get the Pwm.zip and install to Arduino IDE to be able to use ``` #include Pwm.h``` and its functions.
The variable resistors are connected to A0 and A1 to vary the duty cycle and frequency respectively. [How to install](https://docs.arduino.cc/software/ide-v1/tutorials/installing-libraries/)

```cpp
#include <Pwm.h>

const int ledPin = 9;              // PWM pin connected to the LED
const int dutyCyclePin = A0;       // Potentiometer for duty cycle
const int frequencyPin = A1;       // Potentiometer for frequency

int prevFrequency = 0;             // Stores previous frequency to avoid unnecessary updates

void setup() {
  // Initialize all timers except for Timer0
  InitTimersSafe();

  pinMode(ledPin, OUTPUT);
  pinMode(dutyCyclePin, INPUT);
  pinMode(frequencyPin, INPUT);
}

void loop() {
  // Read analog values
  int dutyCycleValue = analogRead(dutyCyclePin);
  int frequencyValue = analogRead(frequencyPin);

  // Map analog values
  int dutyCycle = map(dutyCycleValue, 0, 1023, 0, 255);      // 0% to 100%
  int frequency = map(frequencyValue, 0, 1023, 1, 400);       // 1 Hz to 400 Hz

  // Only update frequency if it changes (avoids flicker and instability)
  if (frequency != prevFrequency) {
    bool success = SetPinFrequencySafe(ledPin, frequency);
    if (success) {
      prevFrequency = frequency;
    }
  }

  // Apply PWM signal
  pwmWrite(ledPin, dutyCycle);

  delay(30);  // small delay to stabilize changes
}

```

### Prerequisites
- Arduino IDE installed.
- Pwm installed to arduino.

### Installation
- Install Pwm to your Arduino IDE.
- Get the provided code.

## Contributing
1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Commit your changes.
4. Submit a pull request.


## Acknowledgements
- [Original library](https://code.google.com/archive/p/arduino-pwm-frequency-library/downloads)

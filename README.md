# PWM with Variable Duty Cycle and Frequency

[PWM on arduino with variable duty cycle (0 - 100) and frequency (any value in MHz).]

## Table of Contents
- [Features](#features)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Acknowledgements](#acknowledgements)

## Features
- [Variable duty cycle and frequency.]
- [Read duty cycle and frequency from variable resistors]

## Getting Started
Get the Pwm.zip and install to Arduino IDE to be able to use ``` #include Pwm.h``` and its functions.
The variable resistors are connected to A0 and A1 to vary the duty cycle and frequency respectively.

```cpp
const int dutyCyclePin = A0; // Analog pin for duty cycle control
const int frequencyPin = A1; // Analog pin for frequency control
...
// Read values from variable resistors
  int dutyCycleValue = analogRead(dutyCyclePin);
  int frequencyValue = analogRead(frequencyPin);

  // Map the analog values to the required range
  int dutyCycle = map(dutyCycleValue, 0, 1023, 0, 255);
  int frequency = map(frequencyValue, 0, 1023, 1, 400);
```

### Prerequisites
- Arduino IDE installed.
- Pwm.

### Installation
[Install Pwm to your Arduino IDE.]
[Get the provided code.]

## Contributing
1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Commit your changes.
4. Submit a pull request.


## Acknowledgements
- Original library: [https://code.google.com/archive/p/arduino-pwm-frequency-library/downloads]

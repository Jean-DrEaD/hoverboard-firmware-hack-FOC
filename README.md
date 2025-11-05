# Hoverboard Driver FOC Motor Control with Encoder and Brake Resistor Support
[![Build](https://github.com/SiMachines/hoverboard-firmware-hack-FOC/actions/workflows/build_on_commit.yml/badge.svg)](https://github.com/SiMachines/hoverboard-firmware-hack-FOC/actions/workflows/build_on_commit.yml)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

This is a fork of the [hoverboard-firmware-hack-FOC](https://github.com/EFeru/hoverboard-firmware-hack-FOC) project that adds AB encoder support and brake resistor functionality for precision motor control applications. 

For this fork instructions please check comments in config.h when modifyng and check [wiki](https://github.com/SiMachines/hoverboard-firmware-hack-FOC/wiki/Connections)

For general setup instructions, hardware information, and base firmware features, please refer to the [original repository](https://github.com/EFeru/hoverboard-firmware-hack-FOC).


---

## Key Improvements Over Original Repository

1. **Smooth Torque Output at Zero RPM**

Encoder feedback enables true zero-speed torque control with no cogging or vibration. Perfect for FFB devices like direct drive wheel base, ffb joystick, seatbelts.

2. **PSU Support**

Integrated brake resistor support allows safe operation from bench power supplies. The brake resistor dissipates regenerative energy that would otherwise cause voltage spikes and damage PSUs or trip overvoltage protection.

3. **High-Quality Input Control Performance**

Enhanced PWM input processing (both hardware and software implementations) provides:
- low latency 1000hz polling
- Noise-free
- High Resolution

For information on all improvments see [Pull Request #3](https://github.com/SiMachines/hoverboard-firmware-hack-FOC/pull/3#issue-3584417632).

---

## New Configurations

- **ONE_AXIS_VARIANT**: Single motor control with AB encoder, hardware pwm input and internal left driver brake resistor support
- **TWO_AXIS_VARIANT**: Dual motor control with AB encoders, software pwm input and external brake resistor support
---

## Quick Start Guide

### 1. Select Your Variant

In `platformio.ini`, uncomment your desired configuration:

```ini
default_envs = ONE_AXIS_VARIANT    ; Single motor with encoder
;default_envs = TWO_AXIS_VARIANT   ; Dual motors with encoders
```

### 2. Essential Configuration

Edit `Inc/config.h` with your specific parameters:

#### Battery Configuration
```c
#define BAT_CELLS               10      // Your battery cell count:
                                        // 6s  = 24V (22.2V - 25.2V)
                                        // 10s = 36V (37V - 42V)
                                        // 13s = 48V (48.1V - 54.6V)
```

#### Motor Configuration
```c
#define N_POLE_PAIRS            15      // Standard hoverboard motors: 15
                                        // Check your motor specs if different
```
---

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

---

## License

This project inherits the GPLv3 license from the original [hoverboard-firmware-hack-FOC](https://github.com/EFeru/hoverboard-firmware-hack-FOC) repository.

---

## Support

For issues specific to encoder and brake resistor functionality, please open an issue in this repository.

For general hoverboard firmware questions, refer to the [original repository](https://github.com/EFeru/hoverboard-firmware-hack-FOC) and its wiki.

---

- Original FOC firmware: [EFeru/hoverboard-firmware-hack-FOC](https://github.com/EFeru/hoverboard-firmware-hack-FOC)

---

## Recent Changes (This Fork)

- Added AB quadrature encoder support for precise motor control
- Implemented internal and external brake resistor functionality
- Enhanced PWM input processing (hardware and software)
- Added ADC watchdog handling
- Performance, safety and reliability improvements

For more changes, see [Pull Request #3](https://github.com/SiMachines/hoverboard-firmware-hack-FOC/pull/3#issue-3584417632).

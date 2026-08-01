# RP2040

This directory contains the RP2040 subsystem used in the Electronic Nose hardware.

## Overview

The RP2040 is employed as a dedicated co-processor to generate high-frequency PWM signals for independent control of the MEMS gas sensor heaters. Offloading PWM generation to a separate microcontroller reduces the computational load on the ESP32-S3 and enables precise heater control.

## Main Responsibilities

- High-frequency PWM generation
- Independent heater control
- Communication with the ESP32-S3 through UART
- Control of the heater driver

## Heater Control

Each MEMS gas sensor contains an integrated micro-heater. The RP2040 generates PWM signals that regulate the heater power, allowing accurate control of the sensor operating temperature.

## Interfaces

| Interface | Connected Device |
|-----------|------------------|
| UART | ESP32-S3 |
| GPIO | Heater Driver |
| PWM | MEMS Sensor Heaters |

## Features

- Dual-core ARM Cortex-M0+
- High-resolution PWM peripherals
- Precise timing control
- Low-power operation

## Design Rationale

The RP2040 was selected because it provides multiple hardware PWM channels with accurate timing, making it well suited for controlling the MEMS sensor heaters. Separating heater control from the primary processing tasks improves system performance and simplifies firmware development.

## Folder Contents

This folder will contain:

- RP2040 schematic
- UART interface
- PWM architecture
- PCB layout
- Design notes

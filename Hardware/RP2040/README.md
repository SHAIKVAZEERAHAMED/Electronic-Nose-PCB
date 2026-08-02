# RP2040

This directory contains the RP2040 subsystem used in the Electronic Nose hardware.

## Overview

The RP2040 serves as a dedicated co-processor responsible for generating high-frequency PWM signals for independent control of the MEMS gas sensor heaters. Offloading PWM generation from the ESP32-S3 reduces computational overhead while providing precise timing and accurate heater control. The generated PWM signals are applied to a DMOS driver, which supplies the required current to the sensor heaters.

## Main Responsibilities

- High-frequency PWM generation
- Independent heater control
- Communication with the ESP32-S3 through UART
- Control of the TBD62083AFNG DMOS driver

## Heater Control

Each MEMS gas sensor incorporates an integrated micro-heater that requires controlled power to achieve the desired operating temperature. The RP2040 generates configurable PWM signals, which are routed to the **TBD62083AFNG DMOS driver**. The DMOS driver provides the necessary current-driving capability to switch the heater supply, enabling reliable and efficient heater operation.

## Interfaces

| Interface | Connected Device |
|-----------|------------------|
| UART & SPI | ESP32-S3 |
| GPIO | TBD62083AFNG DMOS Driver |
| PWM | MEMS Sensor Heaters (via DMOS Driver) |

## Features

- Dual-core ARM Cortex-M0+ processor
- Hardware PWM peripherals
- Precise timing generation
- Low-power operation
- Independent heater control

## Design Rationale

The RP2040 was selected because it provides multiple hardware PWM channels with accurate timing, making it well suited for controlling the MEMS sensor heaters. Since the RP2040 GPIOs cannot directly drive the heater load, the PWM outputs (10 KHz frequency) are interfaced with the **TBD62083AFNG DMOS driver**, which provides the required current-driving capability for the heater circuits. Separating heater control from the primary processing tasks improves overall system performance and allows the ESP32-S3 to focus on sensor acquisition, communication, and system management.

## Signal Flow

```text
ESP32-S3
     │
   UART
     │
     ▼
RP2040
     │
   PWM Outputs
     │
     ▼
TBD62083AFNG
DMOS Driver
     │
     ▼
MEMS Sensor Heaters
```

## Components

| Component | Description |
|-----------|-------------|
| RP2040 | PWM co-processor |
| TBD62083AFNG | 8-channel DMOS sink driver |
| UART | Communication with ESP32-S3 |
| PWM Outputs | Heater control signals |

## Folder Contents

This folder contains:

- RP2040 schematic
- UART interface
- PWM generation circuit
- DMOS driver interface


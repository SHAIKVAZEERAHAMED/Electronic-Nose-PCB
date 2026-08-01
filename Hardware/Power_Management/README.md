# Power Management

This directory contains the power management circuitry of the Electronic Nose hardware.

## Overview

The power management subsystem supplies regulated voltages to the analog, digital, and sensor heater circuits. It is designed to support battery-powered operation while providing stable and efficient power distribution across the entire system.

## Main Functions

- Battery charging
- Battery voltage monitoring
- Fuel gauging
- Voltage regulation
- Power distribution

## Power Architecture

The system operates from a rechargeable lithium-ion battery. Dedicated power management circuits generate multiple regulated voltage rails required by the different subsystems.

| Voltage Rail | Purpose |
|--------------|---------|
| 3.3 V | ESP32-S3, RP2040, BME680, analog circuitry |
| 2.5 V | MEMS sensor heaters |
| 1.8 V | MEMS sensor heaters |

## Main Components

| Component | Function |
|-----------|----------|
| Battery Charger IC | Battery charging |
| Fuel Gauge IC | Battery monitoring |
| Buck Converter | 2.5 V supply |
| Buck Converter | 1.8 V supply |
| LDO / Regulator | 3.3 V supply |

## Design Considerations

- Independent power rails for digital and heater circuits
- Stable voltage supply for analog measurements
- Efficient battery-powered operation
- Low-noise power distribution
- Proper decoupling capacitors near integrated circuits

## Folder Contents

This folder will contain:

- Power management schematic
- Battery charger circuit
- Fuel gauge circuit
- Buck converter circuits
- Power tree diagram
- PCB layout images

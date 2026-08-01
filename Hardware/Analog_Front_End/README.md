# Analog Front End

This directory contains the analog signal acquisition circuit used to interface the MEMS gas sensors with the ESP32-S3 analog-to-digital converter (ADC).

## Overview

Each MEMS gas sensor produces an analog voltage proportional to the detected gas concentration. Before acquisition by the ESP32-S3, the sensor output passes through an analog front-end designed to improve signal quality and provide configurable amplification.

The analog front-end consists of:

- RC low-pass filter
- TLV9152 rail-to-rail operational amplifier
- Configurable gain selection using solder jumpers
- ADC interface to the ESP32-S3

## Low-Pass Filter

A first-order RC low-pass filter with a cutoff frequency of approximately **7 kHz** is used to suppress high-frequency noise before amplification and digitization.

## Operational Amplifier

The TLV9152 operational amplifier is configured to support two operating modes:

- **Voltage Follower**
  - Unity gain
  - High input impedance
  - Low output impedance

- **Non-Inverting Amplifier**
  - Gain selectable through solder jumpers
  - Used for low-level sensor signals

The low output impedance of the amplifier also minimizes signal degradation caused by long PCB traces between the sensor array and the ADC.

## Interface

Signal Flow:

MEMS Sensor
↓
RC Low-Pass Filter
↓
TLV9152 Operational Amplifier
↓
Gain Selection Jumpers
↓
ESP32-S3 ADC

## Components

| Component | Description |
|-----------|-------------|
| TLV9152 | Rail-to-rail operational amplifier |
| RC Network | 7 kHz low-pass filter |
| Solder Jumpers | Gain configuration |
| ESP32-S3 ADC | Analog signal acquisition |

## Folder Contents

This folder will contain:

- Analog front-end schematic
- RC filter calculations
- Gain calculations
- PCB layout images
- Circuit simulation (if available)

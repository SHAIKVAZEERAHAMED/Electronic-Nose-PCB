# Analog Front End

This directory contains the analog front-end circuitry used to interface the MEMS gas sensors with the data acquisition system of the Electronic Nose.

## Overview

Each MEMS gas sensor produces an analog voltage proportional to the detected gas concentration. Before digitization, the sensor output passes through an analog front-end designed to improve signal quality, provide configurable amplification, and ensure accurate analog-to-digital conversion.

The analog front-end consists of:

- RC low-pass filter
- TLV9152 rail-to-rail operational amplifier
- Configurable gain selection using solder jumpers
- ADS131M08 multi-channel Analog-to-Digital Converter (ADC)
- SPI interface to the ESP32-S3

## Low-Pass Filter

A first-order RC low-pass filter with a cutoff frequency of approximately **7 kHz** is used to suppress high-frequency noise before amplification and digitization.

## Operational Amplifier

The TLV9152 operational amplifier supports two operating modes:

### Voltage Follower

- Unity gain
- High input impedance
- Low output impedance

### Non-Inverting Amplifier

- Gain selectable using solder jumpers
- Suitable for low-level sensor signals

The low output impedance of the amplifier minimizes signal degradation caused by long PCB traces and provides a stable input to the ADC.

## Analog-to-Digital Conversion

The conditioned analog outputs from the gas sensors are sampled using the **ADS131M08**, an eight-channel, high-resolution analog-to-digital converter. The external ADC provides improved measurement accuracy and lower noise compared with the ESP32-S3 internal ADC. Digitized sensor data are transferred to the ESP32-S3 through the SPI interface for further processing.

## Signal Flow

```text
MEMS Gas Sensor
        │
        ▼
RC Low-Pass Filter (7 kHz)
        │
        ▼
TLV9152 Operational Amplifier
        │
        ▼
Gain Selection Jumpers
        │
        ▼
ADS131M08 ADC
        │
      SPI Bus
        │
        ▼
ESP32-S3
```

## Components

| Component | Description |
|-----------|-------------|
| TLV9152 | Rail-to-rail operational amplifier |
| RC Network | 7 kHz low-pass filter |
| Solder Jumpers | Gain configuration |
| ADS131M08 | 24-bit multi-channel ADC |
| SPI Interface | Communication between ADC and ESP32-S3 |

## Folder Contents

This folder contains:

- Analog front-end schematics
- ADC interface circuit
- RC filter calculations
- Gain calculations
- PCB layout images
- Design notes

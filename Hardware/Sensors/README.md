# MEMS Gas Sensors

This directory contains the MEMS gas sensor array used in the Electronic Nose system.

## Overview

The Electronic Nose employs a fourteen-channel MEMS-based gas sensor array to detect a broad range of volatile organic compounds (VOCs) and hazardous gases. The sensors were selected to provide diverse sensing characteristics, enabling improved gas discrimination through pattern recognition techniques.


## Sensor Inventory and Rail Assignments

All 14 sensors, their heater voltages, maximum heater power, and assigned rails are listed below.

| Sensor | Manufacturer | Target gas | V_H | P_H (max) | Rail |
|--------|-------------|-----------|-----|-----------|------|
| GM-102B | Winsen | NO₂ | 1.8 V ±0.1 V | ≤ 40 mW | 1.8 V |
| SMD1001 | IDM/Huiwen | Formaldehyde | 1.8 V ±0.05 V | ≤ 36 mW | 1.8 V |
| SMD1002 | IDM/Huiwen | Ammonia (NH₃) | 1.8 V ±0.05 V | ≤ 36 mW | 1.8 V |
| SMD1007 | IDM/Huiwen | Hydrogen sulfide (H₂S) | 1.8 V ±0.05 V | ≤ 36 mW | 1.8 V |
| SMD1008 | IDM/Huiwen | Methane (CH₄) | 1.8 V ±0.05 V | ≤ 30 mW | 1.8 V |
| SMD1011 | IDM/Huiwen | Propane (C₃H₈) | 1.8 V ±0.05 V | ≤ 30 mW | 1.8 V |
| SMD1013B | IDM/Huiwen | TVOC | 1.8 V ±0.1 V | ≤ 43 mW | 1.8 V |
| SMD1015 | IDM/Huiwen | Acetone | 1.8 V ±0.1 V | ≤ 30 mW | 1.8 V |
| GM-602B | Winsen | H₂S & benzene | 1.9 V ±0.1 V | ≤ 40 mW | 1.8 V† |
| GM-202B | Winsen | Smoke/alcohol | 2.5 V ±0.1 V | ≤ 50 mW | 2.5 V |
| GM-302B | Winsen | Ethanol | 2.5 V ±0.1 V | ≤ 50 mW | 2.5 V |
| GM-502B | Winsen | VOC | 2.5 V ±0.1 V | ≤ 50 mW | 2.5 V |
| GM-512B | Winsen | H₂S/alcohol/acetone | 2.5 V ±0.1 V | ≤ 50 mW | 2.5 V |
| GMV-2021B | Winsen | Hydrogen (H₂) | 2.5 V ±0.1 V | ≤ 50 mW | 2.5 V |

**†** The GM-602B is rated 1.9 V ±0.1 V, giving an operating range of 1.8 V to 2.0 V. Running it at 1.8 V places it at the lower bound of its specified tolerance. Heater power will be slightly less than at the 1.9 V nominal (by a factor of (1.8/1.9)² ≈ 90%), which is conservative and within the ≤ 40 mW limit. Sensitivity curves in the GM-602B datasheet are characterised at 1.9 V; response function will be marginally different at 1.8 V but the sensor is not damaged or out-of-spec. This grouping avoids the need for a dedicated third rail.

## Features

- Fourteen MEMS gas sensors
- Two independent heater voltage rails (1.8 V and 2.5 V)
- Individual analog output for each sensor
- PWM-based heater control through the RP2040

## Folder Contents

This folder will contain:

- Sensor schematics
- Sensor placement diagrams
- PCB images
- Sensor documentation

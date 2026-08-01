# MEMS Gas Sensors

This directory contains the MEMS gas sensor array used in the Electronic Nose system.

## Overview

The Electronic Nose employs a fourteen-channel MEMS-based gas sensor array to detect a broad range of volatile organic compounds (VOCs) and hazardous gases. The sensors were selected to provide diverse sensing characteristics, enabling improved gas discrimination through pattern recognition techniques.

## Sensor Array

The following MEMS gas sensors are used in the design:

| Sensor | Target Gas | Heater Voltage |
|---------|------------|---------------|
| SMD1001 | VOC | 1.8 V |
| SMD1002 | Carbon Monoxide (CO) | 1.8 V |
| SMD1007 | Alcohol | 1.8 V |
| SMD1008 | Combustible Gases (CH₄) | 1.8 V |
| SMD1011 | Propane | 1.8 V |
| SMD1013B | TVOC | 2.5 V |
| SMD1015 | Acetone | 2.5 V |
| GM-102B | Carbon Monoxide (CO) | 2.5 V |
| GM-202B | Smoke | 2.5 V |
| GM-302B | VOC / Alcohol | 2.5 V |
| GM-402B | VOC / Combustible Gases | 2.5 V |
| GM-502B | VOC | 2.5 V |
| GM-512B | Breath Odor | 2.5 V |
| GM-602B | Hydrogen Sulfide (H₂S) | 2.5 V |

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

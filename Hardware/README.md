# Hardware

This directory contains the complete hardware design of the Electronic Nose PCB.

The hardware is organized into functional subsystems to simplify design, development, testing, and future maintenance.

## Hardware Organization

| Folder | Description |
|---------|-------------|
| Sensors | MEMS gas sensor array and sensor interface |
| Analog_Front_End | Signal conditioning circuits including RC filters and operational amplifiers |
| ESP32-S3 | Main controller responsible for sensor acquisition and communication |
| RP2040 | Dedicated PWM controller for MEMS heater control |
| Power_Management | Battery charger, fuel gauge, voltage regulators, and power distribution |
| PCB | PCB layouts, fabrication outputs, and 3D models |
| KiCad_Project | Complete KiCad project files |

## Design Software

- KiCad 9.0.7

## Hardware Overview

The Electronic Nose PCB integrates a fourteen-channel MEMS gas sensor array, analog front-end circuits, dual microcontrollers (ESP32-S3 and RP2040), and a dedicated power management subsystem into a compact modular platform.

Each subsystem is documented separately within its respective directory.

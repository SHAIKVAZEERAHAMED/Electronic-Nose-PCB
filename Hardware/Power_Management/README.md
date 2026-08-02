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
| Buck Boost Converter | 3.3 V supply |

### Per-rail power summary

| Rail | Sensors | Peak current (all on) | Max heater power |
|------|---------|----------------------|-----------------|
| 1.8 V | 9 | ~179 mA | ≤ 321 mW |
| 2.5 V | 5 | ~100 mA | ≤ 250 mW |
| **Total** | **14** | | **≤ 571 mW** |

Peak current and power figures are calculated from the rated maximum heater power at the rail voltage (I = P_max / V_rail). Actual in-use power will be lower, as not all sensors will be active simultaneously during temperature modulation sequences, and most sensors draw less than their rated maximum.

---

## Why Two Voltage Rails Are Required

All sensors in this array are MEMS resistive hot-plate sensors. Their heater elements are calibrated at a specific voltage which sets the hot-plate operating temperature, and therefore the sensitivity profile of the sensing material. Running a sensor at the wrong heater voltage shifts its operating temperature, degrading both sensitivity and cross-selectivity characteristics.

### Why not run all sensors from a single rail with PWM?

A common simplification is to power all sensors from the higher 2.5 V rail and use PWM with a lower duty cycle to reduce the effective drive for the 1.8 V sensors. This does not work correctly for resistive heaters, for the following reason.

A resistive heater responds to **average power**, not average voltage. Average power is proportional to V²:

```
P = V_rms² / R
```

With PWM at duty cycle D from a 2.5 V source:

```
V_avg = 2.5 × D
V_rms = 2.5 × √D
P_avg = (2.5)² × D / R
```

To set `V_avg = 1.8 V`, you need `D = 1.8 / 2.5 = 72%`. But this gives:

```
V_rms = 2.5 × √0.72 = 2.12 V
P_avg ∝ (2.12)² = 4.49   (vs 1.8² = 3.24 for true 1.8 V DC)
```

The heater would receive **38% more power** than intended, running significantly hotter than specified. To match the power of a 1.8 V DC supply, the duty cycle must be set to:

```
D = (1.8 / 2.5)² = 51.8%
```

— which gives a mean voltage of only ~1.3 V, not 1.8 V. The "average voltage = rated voltage" shortcut is incorrect for resistive loads.

Additionally, sensors in both groups prohibit exceeding 120 mW heater dissipation. With heater resistance tolerance of 60–100 Ω and 2.5 V applied during PWM ON-phases, instantaneous power can approach 104 mW — uncomfortably close to the limit with no margin for component variation.

Two separate regulated voltage rails eliminate this ambiguity and ensure each sensor operates within its characterised, calibrated conditions.

---

## Why Buck Converters at This Scale

### The efficiency argument is significant across ~570 mW of heater load

With a total heater load of ~571 mW, LDO losses from a 3.3 V input rail would be substantial:

| Rail | LDO efficiency (from 3.3 V) | Wasted power |
|------|---------------------------|--------------|
| 1.8 V (321 mW load) | 55% | ~262 mW wasted |
| 2.5 V (250 mW load) | 76% | ~79 mW wasted |

Total LDO waste would be ~341 mW — more than half the useful heater power, dissipated as heat on the PCB. Buck converters operating at 85–90% efficiency reduce total waste to roughly **60–85 mW**, a saving of ~260 mW.

### Thermal contamination of measurements

The wasted regulator power does not simply reduce battery runtime — it heats the PCB. All sensors in this array show strong temperature dependence: the Winsen GM-series datasheets show Rs/Rs₀ varying by factors of 2–3 across -20 °C to +50 °C. Heat dissipated by voltage regulators near the sensor array introduces a temperature offset and drift into all measurements. Buck converters, being far more efficient, dissipate far less heat locally.

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

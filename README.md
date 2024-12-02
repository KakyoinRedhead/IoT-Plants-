# Raspberry Pi Soil Moisture Monitoring System

## Project Overview
This project automates irrigation using Raspberry Pi 4, 10 capacitive soil moisture sensors, and 10 water pumps controlled via relay modules. It's designed for gardening or smart irrigation systems.

---

## Table of Contents
1. [Requirements](#requirements)
2. [Hardware Setup](#hardware-setup)
3. [Software Configuration](#software-configuration)
4. [Calibration and Testing](#calibration-and-testing)
5. [Running the System](#running-the-system)

---

## Requirements

### Hardware:
- **Raspberry Pi 4** with Raspberry Pi OS.
- **10 capacitive soil moisture sensors**.
- **10 water pumps** (e.g., 5V/12V DC pumps).
- **10-channel relay module** (or two 8-channel relay modules).
- **Power supply** for pumps (e.g., 12V with sufficient current).
- **ADC (e.g., ADS1115 or MCP3008)** for analog-to-digital conversion.
- Jumper wires, breadboard, and connectors.
- Power cables for pumps.

### Software:
- Python 3 with the following libraries:
  - `RPi.GPIO`
  - `adafruit-circuitpython-ads1x15`

---

## Hardware Setup

### 1. Soil Moisture Sensors:
- Connect **VCC** and **GND** of all sensors to Raspberry Pi's 3.3V and GND pins.
- Connect the **OUT** of each sensor to the ADC module (e.g., ADS1115):
  - Use I²C to connect ADC to Raspberry Pi:
    - **SDA** → GPIO Pin 3
    - **SCL** → GPIO Pin 5
    - **VCC** and **GND** to Raspberry Pi.

### 2. Relay and Pumps:
- Connect relay module **VCC** and **GND** to Raspberry Pi.
- Attach **IN1-IN10** on the relay module to GPIO pins on Raspberry Pi.
- Connect each pump's power wires to the relay:
  - **NO (Normally Open)** → Pump positive lead.
  - **COM (Common)** → Pump power source positive.
  - GND of the pump power source should connect to Raspberry Pi's GND.

### 3. Power Supply:
- Ensure the pump's power supply provides sufficient current.
- Connect all grounds (GND) together to avoid floating grounds.

---

## Software Configuration

### 1. Enable I²C:
Run the following command to enable I²C:
```bash
sudo raspi-config

# ESP32 IoT – Environmental Monitoring System

<p align="center">
  <strong>An IoT environmental monitoring project built with ESP32 and MicroPython.</strong>
  <br>
  Sensor integration, OLED interface, joystick navigation and future network communication.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-ESP32-blue?logo=espressif" alt="ESP32">
  <img src="https://img.shields.io/badge/Language-MicroPython-green" alt="MicroPython">
  <img src="https://img.shields.io/badge/Status-In%20Development-orange" alt="In Development">
</p>

---

## 1. Overview

This project focuses on developing an **IoT Environmental Monitoring System** using an ESP32 microcontroller programmed with MicroPython.

The system collects environmental measurements using digital sensors and displays the information on an OLED screen. A joystick provides a simple interactive interface to navigate through different sections of the device.

The project is being developed progressively, starting with sensor integration and local user interaction, with the goal of implementing Wi-Fi communication and an IEEE 1451-inspired STIM/NCAP architecture.

### Main objectives

- Acquire environmental data from multiple sensors.
- Display real-time measurements on an OLED screen.
- Develop an interactive menu controlled by a joystick.
- Monitor ESP32 system resources.
- Implement Wi-Fi and TCP/IP communication.
- Explore the IEEE 1451 smart transducer architecture, including TEDS.

---

## 2. Hardware

The current prototype is based on the following components:

| Component | Description |
|---|---|
| ESP32-WROOM-32D | Main microcontroller |
| BME280 | Temperature, humidity and pressure sensor |
| BH1750 | Digital ambient light sensor |
| DFR0507 | OLED display and joystick interface |
| OLED 128 × 64 | Monochrome display |
| Joystick | Menu navigation and selection |

### Hardware connections

The sensors and OLED display share the same I²C bus.

| Signal | ESP32 GPIO |
|---|---:|
| I²C SDA | GPIO 21 |
| I²C SCL | GPIO 22 |
| Joystick ADC | GPIO 34 |
| Button A | GPIO 4 |
| Button B | GPIO 0 |

### I²C device addresses

| Device | I²C address |
|---|---|
| BH1750 | `0x23` |
| OLED display | `0x3C` |
| BME280 | `0x77` |

The joystick uses an analog resistor-ladder interface connected to GPIO 34. Different joystick positions produce different ADC values.

---

## 3. Current Features

### Environmental Monitoring

The system currently reads four environmental measurements:

- Temperature (°C)
- Relative humidity (%)
- Atmospheric pressure (hPa)
- Ambient light intensity (lux)

**Sensors used:**
- BME280: temperature, humidity and pressure.
- BH1750: ambient light intensity.

Measurements are periodically refreshed and can be displayed through the OLED interface or printed to the serial console.

### OLED User Interface

The OLED display provides a welcome screen and a navigable main menu.

The welcome screen displays:

```text
ESP32 IoT

Hello there!

Welcome to my IoT project

by Bethany Q.
```

After the welcome screen, the main menu becomes available.

### Main Menu

The interface currently contains four sections:

| Section | Current functionality |
|---|---|
| Environment | Displays live environmental measurements |
| Games | Placeholder for the Snake game |
| System Monitor | Placeholder for system information |
| Settings | Placeholder for device configuration |

### Joystick Navigation

The joystick allows the user to:

- Move up and down through menu options.
- Select a section using the joystick's central press.
- Return to the main menu using another central press.

### Standalone Programs

Two independent programs are currently available:

- `main.py`: Environmental monitoring with serial output and OLED display.
- `menu.py`: Welcome screen, interactive menu and environmental data submenu.

Both programs use the same sensor drivers and hardware configuration.

---

## 4. Software and Development Tools

| Tool / Technology | Purpose |
|---|---|
| MicroPython | Firmware and programming language |
| uPyCraft V1.1 | MicroPython IDE |
| Git | Version control |
| GitHub | Source code repository |
| I²C | Communication with environmental sensors and OLED |
| ADC | Reading joystick positions |
| SSD1306 driver | OLED display control |

### Python modules

- `BME280.py`: BME280 sensor driver.
- `BH1750.py`: BH1750 sensor driver.
- `ssd1306.py`: OLED display driver.

---

## 5. Project Structure

```text
iot_esp32/
│
├── README.md
│
├── docs/
│   ├── AmI Documentacio Practiques ESP32(2019).pdf
│   ├── Ejemplo Transferencias TCP micropython.pdf
│   ├── TEDS_Domotica.pdf
│   └── Transferencia_Domotica_v2.pdf
│
└── workSpace/
    │
    ├── main.py
    ├── menu.py
    │
    ├── test_bme280.py
    ├── test_bh1750.py
    └── test_joystick.py
    │
    ├── BME280.py
    ├── BH1750.py
    └── ssd1306.py
```

The `workSpace` directory contains the original MicroPython source files developed for the project. These files are maintained on the computer and uploaded to the ESP32 when required.

The ESP32 filesystem (`device`) is used for deployment and execution, rather than as the main location for source code development.

---

## 6. Getting Started

### Requirements

- ESP32 development board.
- MicroPython firmware installed on the ESP32.
- uPyCraft IDE or another MicroPython-compatible editor.
- BME280 sensor.
- BH1750 sensor.
- OLED display and joystick interface.
- USB cable and appropriate USB-to-UART driver.

### Installation

1. Clone or download this repository:

```bash
git clone <YOUR_REPOSITORY_URL>
```

2. Connect the ESP32 to your computer.

3. Open the project using uPyCraft.

4. Upload the required Python files and sensor drivers to the ESP32.

5. Make sure the hardware connections and I²C addresses match your setup.

### Running the programs

To run the environmental monitoring program:

```python
exec(open('main.py').read(), globals())
```

To run the interactive menu:

```python
exec(open('menu.py').read(), globals())
```

The two programs are independent. Run only one at a time.

---

## 7. Development Roadmap

The project is being developed in several stages.

- [x] ESP32 and MicroPython environment setup.
- [x] BME280 sensor integration.
- [x] BH1750 sensor integration.
- [x] I²C communication and device detection.
- [x] OLED display integration.
- [x] Joystick analog reading and direction detection.
- [x] Interactive main menu.
- [x] Welcome screen.
- [x] Environmental data submenu with live measurements.
- [ ] Custom pixel-art icons for the OLED interface.
- [ ] Snake game implementation.
- [ ] System monitor implementation.
- [ ] Settings menu.
- [ ] Wi-Fi connectivity.
- [ ] TCP/IP communication between ESP32 and a PC.
- [ ] STIM/NCAP architecture.
- [ ] IEEE 1451-inspired TEDS implementation.

---

## 8. Future Architecture: STIM and NCAP

One of the main goals is to extend the project towards an IoT architecture inspired by **IEEE 1451**.

The planned architecture consists of:

- **STIM (Smart Transducer Interface Module):** the ESP32, responsible for collecting sensor data and providing access to its transducer channels.
- **NCAP (Network Capable Application Processor):** a PC application that communicates with the ESP32 over a network.

The communication layer is planned to use Wi-Fi and TCP sockets.

The project will also explore the implementation of:

- Meta-TEDS.
- Channel-TEDS.
- Sensor channel identification.
- Data read and write commands.
- Trigger-related commands.

These features are planned development objectives and are not yet implemented.

---

## 9. Repository

This repository documents the development of the ESP32 IoT project, including source code, hardware tests and technical documentation.

**Project status:** Active development.

---

*Developed by Bethany Quintero*  
*Electronics and Telecommunications Engineering*




\*Developed as an Electronics and Telecommunications Engineering project at the University of Barcelona.\*


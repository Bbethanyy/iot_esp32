# ESP32 IoT Environmental Monitoring System



An IoT environmental monitoring system developed using an \*\*ESP32 microcontroller and MicroPython\*\*. The project combines environmental sensors, local data visualization and wireless communication, with the aim of implementing a simplified smart transducer architecture inspired by the IEEE 1451 standard.



## 1. Project Overview



The goal of this project is to develop an embedded environmental monitoring system capable of collecting, processing and communicating real-world measurements.



The ESP32 acts as the main controller and interfaces with environmental sensors to measure:



- **Temperature**

- **Relative humidity**

- **Atmospheric pressure**

- **Ambient light intensity**



The collected measurements will be displayed locally and made available to an external client through wireless communication.



The project also explores the concepts of \*\*Smart Transducer Interface Modules (STIM)\*\*, \*\*Network Capable Application Processors (NCAP)\*\* and \*\*Transducer Electronic Data Sheets (TEDS)\*\*, following the architecture introduced in the project documentation.



## 2. Objectives



The main objectives are:



1\. \*\*Sensor integration:\*\* Connect and communicate with multiple environmental sensors using the I2C protocol.

2\. \*\*Data acquisition:\*\* Read and process temperature, humidity, pressure and light measurements.

3\. \*\*Local interface:\*\* Use the display and physical controls to visualize measurements and interact with the system.

4\. \*\*Wireless connectivity:\*\* Establish Wi-Fi communication between the ESP32 and an external computer.

5\. \*\*TCP communication:\*\* Implement a client-server communication system for exchanging sensor data and commands.

6\. \*\*TEDS implementation:\*\* Explore and implement Meta-TEDS and Channel-TEDS structures to describe the connected transducers.

7\. \*\*STIM/NCAP architecture:\*\* Develop a simplified implementation of the smart transducer communication model.



## 3. Hardware Components



| Component | Description |

|---|---|

| ESP32-WROOM-32D | Main microcontroller and processing unit |

| UB-Domòtica CPU Board | Development board hosting the ESP32 and onboard BH1750 sensor |

| BME280 | External sensor for temperature, relative humidity and atmospheric pressure |

| BH1750 | Ambient light intensity sensor |

| DFR0507 Display Board | Display and physical controls (joystick and buttons) |



### Communication interfaces



- \*\*I2C:\*\* Used to communicate with the BME280 and BH1750 sensors.

- \*\*Wi-Fi:\*\* Planned wireless communication interface.

- \*\*TCP/IP:\*\* Planned data exchange between the ESP32 and an external computer.



### I2C Pin Configuration



| Signal | ESP32 GPIO |

|---|---|

| SDA | GPIO 21 |

| SCL | GPIO 22 |



Both environmental sensors are intended to share the same I2C bus.



## 4. Software and Development Tools



- \*\*MicroPython:\*\* Programming language and firmware environment.

- \*\*uPyCraft IDE:\*\* Development, execution and debugging of MicroPython programs.

- \*\*Git:\*\* Version control.

- \*\*GitHub:\*\* Source code hosting and project documentation.



## 5. System Architecture



The project follows a simplified STIM/NCAP architecture inspired by IEEE 1451.



### STIM – Smart Transducer Interface Module



The ESP32 acts as the STIM. Its responsibilities include:



- Acquiring measurements from connected sensors.

- Managing sensor data.

- Providing a local user interface.

- Responding to external requests.

- Providing transducer information through TEDS structures.


### NCAP – Network Capable Application Processor



An external computer is planned to act as the NCAP client. It will communicate with the ESP32 over Wi-Fi and TCP/IP to request measurements and exchange commands.



This approach allows the NCAP functionality to be developed in software without requiring a second physical ESP32 board.



## 6. Project Structure



```text

iot\\\_esp32/

│

├── experiments/

│   ├── 01\\\_bme280/

│   │   ├── test\\\_bme280.py

│   │   └── README.md

│   │

│   └── 02\\\_bh1750/

│       ├── test\\\_bh1750.py

│       └── README.md

│

├── src/

│   ├── main.py

│   ├── sensors/

│   ├── communication/

│   ├── teds/

│   └── interface/

│

├── tests/

│

├── README.md

└── .gitignore

```



The `experiments/` directory contains individual hardware tests and prototypes. The `src/` directory is intended for the integrated application and its modules.



## 7. Development Progress



### Completed



- \[x] ESP32 development environment configured.

- \[x] MicroPython development using uPyCraft.

- \[x] Git repository initialized.

- \[x] BH1750 sensor successfully tested.

- \[x] BME280 sensor successfully tested.

- \[x] I2C communication configured using GPIO 21 (SDA) and GPIO 22 (SCL).

- \[ ] Integrated application reading both sensors simultaneously.



### Planned



- \[ ] Integrate all sensor measurements into `main.py`.

- \[ ] Integrate the display and physical controls.

- \[ ] Establish Wi-Fi connectivity.

- \[ ] Implement TCP server on the ESP32.

- \[ ] Develop the external NCAP client..

- \[ ] Implement Meta-TEDS and Channel-TEDS.

- \[ ] Implement the required communication commands.

- \[ ] Perform system integration and validation.



## 8. Development Roadmap



The project will be developed incrementally:



1\. \*\*Hardware validation:\*\* Test each sensor independently and verify communication.

2\. \*\*Sensor integration:\*\* Combine sensor readings into a single application.

3\. \*\*Local interface:\*\* Display measurements and implement physical interaction.

4\. \*\*Wireless communication:\*\* Configure Wi-Fi and establish TCP connections.

5\. \*\*TEDS implementation:\*\* Define and manage transducer identification and configuration data.

6\. \*\*STIM/NCAP communication:\*\* Implement the communication protocol and exchange data with the external client.

7\. \*\*Testing and documentation:\*\* Validate the complete system and document the results.



## 9. Project Status



*\*Current stage:\*\* Hardware validation and sensor integration.



The BH1750 and BME280 have been individually tested and successfully communicate with the ESP32 using I2C and MicroPython. The next step is to integrate both sensors into the main application.



---



\*Developed as an Electronics and Telecommunications Engineering project at the University of Barcelona.\*


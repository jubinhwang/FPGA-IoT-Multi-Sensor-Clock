# FPGA-IoT-Multi-Sensor-Clock
A Verilog-based multi-function digital clock on a Basys3 FPGA, featuring real-time data from DHT11 (temperature/humidity) and Ultrasonic (distance) sensors, with UART command interface for PC control and monitoring.

# Digital Clock Design with Various Functions on FPGA

[![Made with Verilog](https://img.shields.io/badge/Made%20with-Verilog-1f425f.svg)](https://verilog.org/)
[![Board-Basys3](https://img.shields.io/badge/FPGA%20Board-Basys3-blue.svg)](https://digilent.com/reference/programmable-logic/basys-3/start)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[cite_start]This is the final project for the "Semicon_Academi 2nd Term," a multi-function digital clock implemented on a Xilinx Artix-7 Basys3 FPGA board using Verilog HDL[cite: 4, 5].

[cite_start]The primary goal of this project was to design an IoT system foundation by collecting various environmental data through sensors and ensuring stable data communication with a PC[cite: 6, 46, 47, 48].


## ✨ Key Features

* [cite_start]**Multi-Function Clock**: Provides standard clock, stopwatch, and timer functionalities[cite: 42].
* **Environmental Sensing**:
    * [cite_start]Measures real-time temperature and humidity using a **DHT11 sensor**[cite: 8, 9].
    * [cite_start]Measures distance using an **HC-SR04 Ultrasonic sensor**[cite: 10].
* [cite_start]**PC Interface**: Enables robust, bidirectional communication with a PC via **UART** for real-time monitoring and control[cite: 43].
* [cite_start]**Stable Data Transmission**: Utilizes a **FIFO buffer** to ensure reliable data handling between the processing core and the UART module[cite: 88, 108].
* [cite_start]**On-board I/O**: Displays information on the 7-segment display and uses on-board buttons and switches for direct user interaction[cite: 51, 52, 54].

## 🛠️ System Architecture

[cite_start]The system is designed with three main sections: an input section for data acquisition, a central processing unit on the FPGA, and an output/transmission section for displaying and sending data[cite: 70].

1.  [cite_start]**Input Section**: Gathers data from the DHT11 and Ultrasonic sensors, as well as user inputs from the on-board buttons and switches or commands from the PC via UART[cite: 76].
2.  **Processing Section (FPGA)**: The core of the system processes all incoming data. [cite_start]It runs the clock logic, calculates sensor values, and manages the overall state of the device[cite: 80, 81, 87].
3.  [cite_start]**Output & Transmission Section**: Displays the current mode's information on the 7-segment display and transmits formatted data strings to the PC through the UART interface[cite: 82, 83].

![System Block Diagram](https://i.imgur.com/your-image-url.png) 
*추신: 발표자료의 시스템 구성도 이미지를 캡처하여 업로드한 후 위 링크를 교체하세요.*

## 💻 UART Command Interface

The device can be controlled and monitored using a standard serial terminal (e.g., Tera Term, PuTTY) with a **9600 Baud Rate**. The following commands are supported:

| Command | Description |
| :--- | :--- |
| `C` | [cite_start]Enters **Clock Mode**[cite: 120]. |
| `W` | [cite_start]Enters **Stopwatch Mode**[cite: 121]. |
| `T` | [cite_start]Enters **Timer Mode**[cite: 122]. |
| `U` | [cite_start]Enters **Ultrasonic Sensor Mode**[cite: 123]. |
| `D` | [cite_start]Enters **DHT11 Sensor Mode**[cite: 124]. |
| `X` | [cite_start]Requests the current data value for the selected mode (e.g., time, distance)[cite: 125]. |
| `S` | [cite_start]Toggles the setting state (On/Off) for Clock or Timer modes[cite: 129, 149]. |
| `M` | [cite_start]In Clock setting mode, toggles between Hour/Min and Sec adjustment[cite: 130]. |
| `u`, `d`, `l`, `r` | [cite_start]Adjusts values (Up, Down, Left, Right) in setting modes or controls functions (e.g., `r` for Run/Stop in Stopwatch/Timer)[cite: 131, 135]. |
| `c` | [cite_start]Clears the stopwatch[cite: 136]. |

## 🚀 Getting Started

1.  Clone this repository to your local machine.
2.  Open the project in Xilinx Vivado.
3.  Synthesize the design and upload the bitstream to a Basys3 board.
4.  Connect the DHT11 and Ultrasonic sensors to the Pmod connectors as specified in the constraints file.
5.  Connect the Basys3 board to your PC via USB.
6.  Open a serial terminal, connect to the correct COM port, and set the Baud Rate to 9600.
7.  Use the on-board switches/buttons or the UART commands listed above to interact with the device.

## 📈 Future Improvements

* [cite_start]Implement additional features using the ultrasonic sensor, such as an object detection alarm[cite: 417].
* [cite_start]Expand the UART command set to allow all device functions to be controlled solely from a PC for a more streamlined user experience[cite: 418].

---

[cite_start]**Author:** J주는ubee Hwang (황주빈) [cite: 5]

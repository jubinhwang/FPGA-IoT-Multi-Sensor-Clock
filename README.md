# FPGA-IoT-Multi-Sensor-Clock
A Verilog-based multi-function digital clock on a Basys3 FPGA, featuring real-time data from DHT11 (temperature/humidity) and Ultrasonic (distance) sensors, with UART command interface for PC control and monitoring.

# FPGA를 이용한 다기능 디지털 시계 설계

[![Made with Verilog](https://img.shields.io/badge/Made%20with-Verilog-1f425f.svg)](https://verilog.org/)
[![Board-Basys3](https://img.shields.io/badge/FPGA%20Board-Basys3-blue.svg)](https://digilent.com/reference/programmable-logic/basys-3/start)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

'Semicon_Academi 2기' 최종 프로젝트로, Verilog HDL을 사용하여 Xilinx Artix-7 Basys3 FPGA 보드에 구현한 다기능 디지털 시계입니다.

본 프로젝트는 다양한 센서로 환경 데이터를 수집하고 PC와의 안정적인 데이터 통신을 구현하여, 스마트 IoT 시스템의 기반을 설계하는 것을 목표로 합니다.

![Basys3 보드와 센서가 연결된 사진](https://i.imgur.com/your-image-url.png) 
*추신: 발표자료의 동작 사진 등을 캡처하여 업로드한 후 위 링크를 교체하세요.*

## ✨ 주요 기능

* **다기능 시계**: 일반 시계, 스톱워치, 타이머 기능을 제공합니다.
* **환경 데이터 측정**:
    * **DHT11 센서**를 이용해 실시간 온도와 습도를 측정합니다.
    * **HC-SR04 초음파 센서**를 이용해 거리를 측정합니다.
* **PC 인터페이스**: **UART** 통신을 통해 PC와 양방향으로 데이터를 주고받으며, 실시간 모니터링 및 제어가 가능합니다.
* **안정적인 데이터 전송**: **FIFO 버퍼**를 사용하여 처리 코어와 UART 모듈 간의 데이터를 안정적으로 처리합니다.
* **온보드 입출력**: 7-세그먼트 표시 장치에 정보를 출력하고, 보드의 버튼과 스위치를 통해 직접적인 사용자 상호작용이 가능합니다.

## 🛠️ 시스템 아키텍처

시스템은 데이터 수집을 위한 입력부, FPGA 기반의 중앙 처리부, 그리고 데이터 출력 및 전송을 담당하는 출력부, 세 부분으로 구성됩니다.

1.  **입력부**: DHT11, 초음파 센서로부터 데이터를 수집하고, 보드의 버튼/스위치 입력 또는 PC로부터의 UART 명령을 받습니다.
2.  **중앙 처리부 (FPGA)**: 시스템의 핵심으로, 모든 입력 데이터를 처리합니다. 시계 로직을 실행하고, 센서 값을 계산하며, 전체 시스템의 상태를 관리합니다.
3.  **출력 및 전송부**: 현재 모드의 정보를 7-세그먼트에 표시하고, 형식화된 데이터 문자열을 UART를 통해 PC로 전송합니다.

![시스템 구성도](https://i.imgur.com/your-image-url-2.png) 
*추신: 발표자료의 시스템 구성도 이미지를 캡처하여 업로드한 후 위 링크를 교체하세요.*

## 💻 UART 명령어 인터페이스

PC의 시리얼 터미널 프로그램(예: Tera Term, PuTTY)을 이용해 **9600 Baud Rate**로 장치를 제어하고 모니터링할 수 있습니다. 지원되는 명령어는 다음과 같습니다:

| 명령어 | 설명 |
| :--- | :--- |
| `C` | **시계 모드**로 진입합니다. |
| `W` | **스톱워치 모드**로 진입합니다. |
| `T` | **타이머 모드**로 진입합니다. |
| `U` | **초음파 센서 모드**로 진입합니다. |
| `D` | **DHT11 센서 모드**로 진입합니다. |
| `X` | 선택된 모드의 현재 데이터 값(시간, 거리 등)을 요청합니다. |
| `S` | 시계 또는 타이머 모드에서 설정 상태(On/Off)를 전환합니다. |
| `M` | 시계 설정 모드에서 시/분 조정과 초 조정을 전환합니다. |
| `u`, `d`, `l`, `r` | 설정 모드에서 값을 조정(Up/Down/Left/Right)하거나, 스톱워치/타이머를 실행/정지(`r`)합니다. |
| `c` | 스톱워치를 초기화(Clear)합니다. |

## 🚀 시작하기

1.  이 저장소를 로컬 컴퓨터에 복제(Clone)합니다.
2.  Xilinx Vivado에서 프로젝트를 엽니다.
3.  디자인을 합성(Synthesize)하고 Basys3 보드에 비트스트림을 업로드합니다.
4.  제약 파일(constraints file)에 명시된 대로 DHT11 및 초음파 센서를 Pmod 커넥터에 연결합니다.
5.  Basys3 보드를 USB를 통해 PC에 연결합니다.
6.  시리얼 터미널을 열고, 올바른 COM 포트에 연결한 후 Baud Rate를 9600으로 설정합니다.
7.  보드의 스위치/버튼 또는 위에 명시된 UART 명령어를 사용하여 장치와 상호작용합니다.

## 📈 개선 및 보완점

* 초음파 센서를 활용한 객체 감지 알람 등 추가 기능 구현
* 모든 동작을 PC 명령어로 제어할 수 있도록 UART 명령어 세트를 확장하여 사용자 경험을 간소화

---

**개발자**: 황주빈 (Jubin Hwang)

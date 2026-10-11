# 🔌 CH9344 Industrial USB-to-Quad-UART

<div align="center">

![IC](https://img.shields.io/badge/IC-WCH%20CH9344-blue?style=for-the-badge&logo=microchip)
![Channels](https://img.shields.io/badge/Channels-4x%20High--Speed%20UART-green?style=for-the-badge)
![EDA](https://img.shields.io/badge/EDA-Altium%20Designer-orange?style=for-the-badge&logo=altiumdesigner)
![Kernel](https://img.shields.io/badge/Platform-Linux%20Kernel%20Driver-lightgrey?style=for-the-badge&logo=linux)

<p align="center">
  <b>Complete industrial hardware integration for the WCH CH9344 controller: Custom Altium Designer schematic/footprint libraries, layout guidelines, and Linux kernel driver with automated build automation.</b>
</p>

---

</div>

## 📌 Overview

The **WCH CH9344** is a USB 2.0 High-Speed to quad-UART bridge controller providing 4 independent full-duplex asynchronous serial ports with hardware automatic flow control (CTS/RTS) and baud rates up to **12 Mbps**. 

Because official footprints and out-of-the-box build tooling are often fragmented or missing, this repository provides:
1. **Altium Designer Libraries:** Custom-engineered Schematic Component (`.SchLib`) and PCB Footprint (`.PcbLib`) with IPC-compliant dimensions.
2. **Linux Kernel Driver:** Patched kernel module source code with a clean, standalone `Makefile` for zero-friction compilation across modern Linux kernels.
3. **Datasheets & Reference:** Official documentation and pinout reference for embedded industrial gateway and multi-modem designs.

---

## ✨ Key Features

* **Quad Serial Interfaces:** 4x independent high-speed UART ports (`/dev/ttyCH9344USB0` through `/dev/ttyCH9344USB3`).
* **High Baud Rates:** Supports baud rates from 1200 bps up to **12 Mbps** with integrated FIFO buffers.
* **Hardware Flow Control:** Full hardware handshaking signals (RTS, CTS, DTR, DSR, DCD, RI) supported on all channels.
* **Complete EDA Suite:** Ready-to-import Altium Designer schematic symbols and tight PCB footprint libraries.
* **Modern Driver Build:** Standalone Linux kernel build integration tested on modern Ubuntu/Debian x86_64 and MIPS/ARM cross-compilation environments.

---

## 🛠 Hardware Specifications

| Specification | Details |
| :--- | :--- |
| **USB Interface** | USB 2.0 High-Speed (480 Mbps), compatible with Full-Speed |
| **Number of UARTs** | 4 Full-Duplex Serial Ports |
| **Baud Rate Range** | 1200 bps to 12 Mbps |
| **I/O Voltage Domain** | 3.3V (5V tolerant with external level shifting) |
| **Modem Signals** | CTS, RTS, DTR, DSR, DCD, RI on all 4 channels |
| **Package** | LQFP-48 (0.5mm pitch) |

---

## 🚀 Linux Driver Installation

### 1. Prerequisites
Ensure you have the Linux kernel development headers and build essentials installed:
```bash
sudo apt update
sudo apt install build-essential linux-headers-$(uname -r)
```

### 2. Compile the Driver
Navigate into the driver directory and compile:
```bash
cd CH9344/Driver/driver
make
```

### 3. Load Kernel Module
Insert the newly built module into the running kernel:
```bash
sudo insmod ch9344.ko
```

Verify that the 4 serial interfaces have enumerated:
```bash
dmesg | grep -i ch9344
ls -l /dev/ttyCH9344USB*
```

---

## 📂 Repository Layout

```text
├── Altium/               # Custom Altium Designer design assets
│   ├── CH9344.SchLib     # Schematic component symbol
│   ├── CH9344.PcbLib     # Accurate LQFP-48 PCB footprint
│   └── example.png       # Schematic implementation preview
├── Datasheet/            # Official technical documentation
│   └── CH9344.pdf        # Complete chip datasheet and register maps
├── Driver/               # Linux kernel driver implementation
│   ├── driver/           # Kernel module source code and Makefile
│   └── lib/              # Dynamic library and user-space helpers
├── about-CH9344.md       # Hardware integration summary
└── README.md             # Project documentation
```

---

## 🔍 Keywords & Topics

```text
Keywords: CH9344, WCH, USB to Quad Serial, Multi-UART, Altium Designer, PCB Design, Linux Kernel Driver, ttyCH9344, Hardware Engineering, Shayan Shirazi, شایان شیرازی.
```

---

## 📄 License

The hardware design assets and custom Makefile wrapper are released under the **MIT License**. The underlying kernel driver implementation is subject to the respective licensing terms of Nanjing Qinheng Microelectronics (WCH).

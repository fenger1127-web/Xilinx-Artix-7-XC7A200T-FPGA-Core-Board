# Xilinx Artix-7 XC7A200T FPGA Core Board

![License](https://img.shields.io/badge/License-CERN_OHL_W_v2-blue.svg)
![Hardware](https://img.shields.io/badge/Hardware-FPGA-orange.svg)
![Status](https://img.shields.io/badge/Status-Verified-success.svg)
![EDA](https://img.shields.io/badge/EDA-EasyEDA%2FKiCad-green)

<div align="center">
  <img src="Images/Board_Topview.png" alt="Board_Topview" width="600"/>
  <img src="Images/Board_BottomView.png" alt="Board_BottomView" width="600"/>
  <br>
</div>

## 📖 Overview

This project is an open-source hardware design of a high-performance **FPGA Core Board** based on the **Xilinx Artix-7 XC7A200T**. 

Originally developed as the verification platform for a **Satellite-borne Optical Remote Sensing Object Detection System (YOLOv10 implementation)** during my Master's Thesis, this board is engineered to handle computationally intensive tasks such as CNN acceleration and high-speed image processing.

Designed with modularity in mind, this Core Board decouples the central processing unit from peripherals, exposing high-speed I/Os through **Board-to-Board (BTB)** connectors for flexible carrier board integration.

## 🚀 Key Features

### 🧠 FPGA Core
* **Device:** Xilinx Artix-7 `XC7A200T-2FBG484I` (Industrial Grade)
* **Logic Resources:** 215,360 Logic Cells
* **DSP Capability:** 740 DSP48E1 Slices (Optimized for Neural Network MAC operations)
* **Block RAM:** 13,140 Kb

### 💾 High-Speed Memory
* **DDR3 SDRAM:** Micron `MT41K256M16TW-107:P`
* **Capacity:** 4Gb (512MB)
* **Bus Width:** 16-bit
* **Bandwidth:** Up to 1066 MT/s (533 MHz Clock)

### ⚡ Robust Power System (PDN)
Designed to handle high transient currents required by deep learning inference logic.

| Voltage Rail | Source Chip | Max Current | Description |
| :--- | :--- | :--- | :--- |
| **VCCINT (1.0V)** | **TI LMZ31710** | **10A** | Integrated Inductor Power Module. Ultra-low ripple for core logic. |
| **VCCAUX (1.8V)** | TI TPS54627 | 6A | Auxiliary voltage & Ethernet IO. |
| **VCC_DDR (1.5V)** | TI TPS54627 | 6A | DDR3 Power & Banks 34/35. |
| **VCCIO (3.3V)** | TI TPS54627 | 6A | System IO (Banks 0/13/14), Flash, Clock. |

### 🔌 Connectivity
* **Interface:** High-density **Board-to-Board (BTB)** connectors.
* **Signals:** Supports Gigabit Ethernet (RGMII), HDMI, UART, JTAG, and SDIO routing.

## 🛠️ PCB Design & Signal Integrity

This board utilizes an **8-Layer High-Density Interconnect (HDI)** stack-up to ensure signal integrity for the 533MHz DDR3 interface and stable power delivery.

* **Stack-up Process:** JLC081611-3313
* **Impedance Control:**
  * 50Ω Single-ended (DDR3 Address/Control)
  * 100Ω Differential (DDR3 Clock / DQS)
* **Power Integrity:** Dedicated split power planes and ground references for noise minimization.

## 📂 Repository Structure

```text
.
├── Hardware
│   ├── Schematic           # Circuit design files (PDF / Source)
│   ├── PCB                 # Layout files
│   └── BOM                 # Bill of Materials
├── Datasheets              # Component datasheets (FPGA, DDR3, Power ICs)
├── Learning_Materials      # Related papers and study notes on FPGA
├── Reference               # Design references
└── Images                  # Board photos and renders

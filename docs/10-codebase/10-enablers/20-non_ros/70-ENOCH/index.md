---
title: ENOCH
pagination_label: ENOCH
description: Document transceiver design for ENOCH paper @ PerCom 2025
---

# ENOCH

**Description**: ENOCH: ENabling On-body Network Contention Handling.  

* **Primary Functionality**: Document transceiver design for ENOCH paper @ PerCom 2025.
* **Target**: Transceiver front end
* **Task**: T2.1
* **Responsible**: Mengyao Liu

<Button label="🔗 openswarm-eu/ENOCH repository" link="https://github.com/openswarm-eu/ENOCH" block /><br />
> Mengyao Liu, Jonathan Oostvogels, Bingwu Fang, Sam Michiels, Haoxiang Ma, Yang Yang, and Danny Hughes In Proceedings of the IEEE International Conference on Pervasive Computing and Communications (PerCom),  Washington, DC, USA, March 17–21, 2025. IEEE, 2025.

## Overview
ENOCH is a low-latency, capacitively coupled on-body communication system optimized for ultra-low-power operation. It employs off-the-shelf components and is programmed on an **Arduino Due**, making it accessible for researchers and developers interested in **body area networks (BANs)**.

This repository contains all necessary files to **replicate and extend** our implementation, including:
- Hardware schematics and PCB design files
- Arduino source code and API documentation
- Experimental setups and results

## 🛠 Hardware Setup
### Component Specifications
- **Greinacher Voltage Multiplier:** A capacitive charge-pump circuit optimized for RF signal rectification.
- **Comparator with RC Low-Pass Filter:** Dynamically adjusts thresholds to enhance noise immunity.
- **RF Switches:** ADG918 (TX/RX switching) and ADG902 (OOK modulation).
- **Arduino Due:** Serves as the processing unit for signal transmission and reception.

### PCB Design
The **hardware folder** contains:
- **Schematics** (`.sch`) and **PCB layout files** (`.pcbdoc`)
- **Gerber files** for manufacturing
- **Altium Designer project files**

Manufacturing can be done via [PCBWay](https://www.pcbway.com/). We recommend using the **evaluation board** before transitioning to the miniaturized version.

## 💻 Software Setup
### Requirements
1. Install the [Arduino IDE](https://www.arduino.cc/en/software)
2. Download this repository
3. Connect **Arduino Due** via USB

### Compiling & Uploading
1. Open `Arduino IDE`
2. Select **Arduino Due (Programming Port)** under `Tools → Board`
3. Open `enochtx.ino` or `enochrx.ino`
4. Click `Verify (✔)` and then `Upload (⬆)`
5. Open `Serial Monitor` to view output

## 📡 ENOCH API
To use ENOCH with an **Arduino Due**, define the following pins:
```cpp
#define ENOCHTxCarrier 7     // Tx carrier frequency pin
#define ENOCHOOKSW 2         // Modulation (OOK) Switch pin
#define ENOCHRxGPIO 6        // Rx GPIO pin
#define ENOCHTxRxSwitch 8    // Switch for Tx/Rx mode
```
### Available Functions
```cpp
void Send_preamble(int cycles); // Transmit preamble
void Send_bytes(byte bytex[]);  // Send data bytes
void Read_bytes(byte load[]);   // Read received bytes
boolean checkRxStatus();        // Check channel availability
```

## ⚡ Experiments 
![ENOCH Transceiver](img/demo.png)
### 1️⃣ Single Transmitter & Receiver
- One **ENOCH board** transmits, the other receives.
- The receiver outputs data via `Serial Monitor`.
- **Evaluate packet delivery reliability** by testing different body placements (wrist, arm, ankle).

### 2️⃣ Multi-Node Contention
- Multiple nodes attempt to transmit simultaneously.
- A **hardware trigger button** ensures synchronized transmission.
- Transmission priority is determined by `Send_preamble(int cycles)`.

## 📂 Repository Structure
```
ENOCH/
├── Hardware/       # PCB schematics, Gerber files, and Altium projects
├── Software/       # Arduino source code for Tx and Rx
├── Docs/           # Additional documentation and experiments
├── README.md       # This file
```

## 📬 Contact & Contribution
Feel free to **open an issue** for questions or contributions. We welcome pull requests to improve the ENOCH project!

📧 Contact: [mengyao.liu@kuleuven.be](mailto:mengyao.liu@kuleuven.be)

## 🔗 Links
- 🔬 **Paper:** [PerCom 2025](https://www.percom.org/)
- 📖 **GitHub Repo:** [ENOCH Project](https://github.com/KULeuvenNESLFradio/ENOCH)
- 🏭 **PCB Manufacturing:** [PCBWay](https://www.pcbway.com/)

---
🚀 *Bringing robust on-body network contention handling to ultra-low-power systems!*

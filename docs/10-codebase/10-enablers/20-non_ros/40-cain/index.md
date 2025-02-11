---
title: CaIN
pagination_label: CaIN
description: Document transceiver design for CaIN paper @ EWSN 2024
---

# CaIN

**Description**: CaIN introduces a novel near-field mesh networking system that combines ultra-low power with low-latency performance. 

* **Primary Functionality**: Document transceiver design for CaIN paper @ EWSN 2024.
* **Target**: Transceiver front end
* **Task**: T2.1
* **Responsible**: Mengyao Liu

<Button label="🔗 openswarm-eu/CaIN repository" link="https://github.com/openswarm-eu/CaIN" block /><br />

> Mengyao Liu, Bingwu Fang, Jonathan Oostvogels, Sam Michiels, Andrei Belogaev, Xinlei Liu, Jeroen Famaey, Danny Hughes,"*CaIN: Low Power and Low Latency VHF Mesh Networking*", the 21st International Conference on Embedded Wireless Systems and Networks, EWSN '24: Abu Dhabi, UAE, December 10-13, 2024

## Overview
1. [Abstract](#abstract)
2. [Project Structure](#project-structure)
   - [Hardware](#hardware)
   - [Software](#software)

## Abstract
Low-power wireless mesh networks provide a solution for the seamless wireless coverage of complex physical environments due to their ability to route around physical obstructions and sources of interference. For example, networks such as SmartMesh-IP, WirelessHART and 6TiSCH deliver industry-grade reliability with low routing power consumption. However, conventional low power mesh networks suffer from high latency. The root of this problem is the need to reduce receiver power consumption by duty cycling the radio receiver using time-synchronized wake-ups or preamble sampling. We tackle this problem by introducing **CaIN**, **a near field mesh network that transmits information using strong Capacitive and INductive effects** that can be detected by a passive receiver front end, thereby side-stepping the need for intermittent receiver usage. Given that near field effects are limited to a few wavelengths, we implement our proof-of-principle transceiver in the **VHF frequency band at 40 MHz**, achieving a unique performance profile including: **20 kbps link layer throughput**, **sub-𝜇W receiver power consumption**, **sub-ms wireless wake-up and 17 m per-hop range**. Building upon these properties, we realize a novel mesh network with a worst-case latency of under 40 ms for a 3 hop network. To promote replication and further work, we have made the hardware and software of our reference implementation open source.

## Project Structure
This repository is divided into multiple folders, each containing specific materials needed to replicate or extend the CaIN transceiver.

### Hardware
In the `Hardware` folder, you will find:
1. **Schematic Designs** – Includes the schematic for each iteration of the CaIN transceiver hardware.  
2. **PCB Project Files** – The original project files used to design the PCB.  
3. **Gerber Files** – Ready-to-submit files for PCB manufacturing.

#### Hardware Version
The hardware version used in the article is **CaIN v2.2**, featuring a pin header compatible with the Arduino Due.

#### Microcontroller & Evaluation Board
All software code was written using the **Arduino IDE**, and the evaluation board used for testing is the 
[Arduino Due](https://store.arduino.cc/products/arduino-due), based on the Atmel SAM3X8E ARM Cortex-M3 CPU.

#### Main Components on the CaIN Transceiver
| **CAIN Prototype Components** | **Part Number**  | **Purchase Link**                                              |
|------------------------------:|:----------------:|:--------------------------------------------------------------:|
| Rectifying Diodes                | SMS7630-005LF     | [Digi-Key](https://www.digikey.com/en/products/detail/???/???) |
| RF SPDT Switche                      | ADG918            | [Mouser](https://www.mouser.com/ProductDetail/???/???)         |
| RF SPST Switche                       | ADG902            | [Mouser](https://www.mouser.com/ProductDetail/???/???)         |
| Analog Comparator                      | TLV7031           | [Mouser](https://www.mouser.com/ProductDetail/???/???)         |
| VCO                      | LTC6905           | [Digi-Key](https://www.digikey.com/en/products/detail/???/???) |
| RF Amplifier                     | TRF37D73          | [Mouser](https://www.mouser.com/ProductDetail/???/???)         |
| Antenna Connector                 | SMA-EDGE-S        | [Mouser](https://www.mouser.com/ProductDetail/???/???)         |

---
### Software
In the `Software` folder, you will find:

1. **CaIN_20131016Worked**  
   - This version does not use a front-end amplifier.  
   - The receiver is connected to the USB serial port of a laptop to continuously print the received data.

2. **CaINamp**  
   - This code configures the MCU to send and receive data as a transceiver for CaIN.  
   - After initialization, the MCU uses the RF switch to connect the antenna to the receiver front end, putting the transceiver into **receive mode**.  
   - In receive mode, the MCU attaches an interrupt handler to the RX pin and then goes into sleep mode. It wakes up upon receiving a CaIN message.  
   - When acting as a transmitter, the MCU drives the RF switch via a GPIO pin to connect the antenna to the transmitter front end, enabling **transmit mode**.

---


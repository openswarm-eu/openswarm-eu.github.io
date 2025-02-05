---
title: SmartMesh Network Stack
pagination_label: SmartMesh Network Stack
description: SmartMesh Network Stack.
---

# SmartMesh Network Stack

**Description**: SmartMesh Network Stack.

* **Primary Functionality**: SmartMesh Network Stack.
* **Target**: MAX32655
* **Task**: T2.1
* **Responsible**: Luiz Sampaio

SmartMesh IP, developed by Analog Devices, is a sophisticated wireless networking solution designed for industrial
Internet of Things (IoT) applications. It consists of highly scalable, self-forming multi-hop mesh networks of wireless
nodes, known as motes, which collect and relay data. These motes work in conjunction with a network manager that
monitors and manages network performance and security, ensuring seamless data exchange with a host application.
SmartMesh IP is built on the 6LoWPAN and IEEE 802.15.4e standards, which enable low power consumption and exceptional
data reliability, even in challenging and dynamically changing RF environments.

One of the standout features of SmartMesh IP is its ability to achieve over 99.999% data reliability, making it ideal
for critical industrial applications where data integrity is paramount1. The network supports an ultra-low power roaming
node feature called Blink Mode, which further enhances its efficiency. By leveraging SmartMesh IP, users can deploy
large-scale, secure, and reliable wireless sensor networks without the need for extensive network stack development.
This makes SmartMesh IP a versatile and robust solution for modern industrial automation and IoT deployments.

More information can be found in the
[SmartMesh IP Product Description](https://www.analog.com/en/product-category/smartmesh-ip.html).

In OpenSwarm, the SmartMesh technology is ported to the MAX32655, an ultra-low power, dual-core microcontroller,
providing a more affordable and streamlined option to develop on top of. The RISC-V core can run the SmartMesh network
stack and drive the low-power wireless radio, and the ARM Cortex-M4 is fully available to the user application.

# Published Paper

The port of SmartMesh to the MAX32655 was presented at IECON 2024 ([link to paper](https://inria.hal.science/hal-04828853/document)).

>**Running SmartMesh on the MAX32655 with MicroPython**\
>Luiz Sampaio, Kate O’Riordan, Brian Coffey, Lance Doherty, Thomas Watteyne.
>*In IECON 2024 Annual Conference of the IEEE Industrial Electronics Society (IECON), 2024*

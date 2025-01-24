---
title: Capbot-Swarm-BLE-Server
pagination_label: Capbot-Swarm-BLE-Server
description: DK-Board firmware for multi-robot communication using BLE.
---

# Capbot-Swarm-BLE-Server

**Description**: Implements CapBots that can communicate with other CapBots via a central server (server side).

* **Primary Functionality**: DK-Board firmware for multi-robot communication using BLE.
* **Target**: nRF52840
* **Task**: T4.1
* **Responsible**: Genki Miyauchi

<Button label="🔗 jessicajayakumar/DK-Board-Central repository" link="https://github.com/jessicajayakumar/DK-Board-Central" block /><br />

# Overview

This repository contains the server side code for a CapBot (previously known as FreeBot) to communicate with other CapBots using BLE. The code The client side code can be found [here](../90-capbot-swarm-ble-client/index.md).

Also refer to [Capbot Swarm Swarmhack](../../../../20-noncodebase/10-enablers/20-non_ros/70-capbot-swarm-swarmhack/index.md) for more information.

>**NOTE**: The working example can currently be found in the ```work-and-charge``` branch. Make sure to ```git checkout work-and-charge``` when using the BLE-client.
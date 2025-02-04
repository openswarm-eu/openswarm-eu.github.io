---
title: Freebot Examples
pagination_label: Freebot Examples
description: Provide example code for CapBot SW.
---

# CapBot Examples

**Description**: Showcases how to use the CapBot Hardware/Software from a developer's point of view.

* **Primary Functionality**: Provide example code for CapBot SW.
* **Target**: nRF52840
* **Task**: T4.1
* **Responsible**: Mengyao Liu

<Button label="🔗 KULeuven-CapBot/example-blink repository" link="https://github.com/KULeuven-CapBot/example-blink" block /><br />
<Button label="🔗 KULeuven-CapBot/example-log-vcap repository" link="https://github.com/KULeuven-CapBot/example-log-vcap" block /><br />
<Button label="🔗 openswarm-eu/example-drive repository" link="https://github.com/openswarm-eu/freebot-example" block /><br />

## Overview

There are three basic examples on how to use the CapBot:

- **Blink**:
  This example makes the on-board LEDs blink.
  It's a good point to get started and verify the local toolchain instalation.
- **Log VCap**:
  The robot is powered by a supercapacitor which has a more limitied energy storage compared to a traditional battery.
  Therefore, software should make sure that it can be recharge before it's completely drained.
  This example demonstrates how to read the robot's capacitor voltage and logs it over a UART connection.
- **Drive**:
  This example demonstrates how to make CapBot's wheels spin.

## Build process

Currently, the easiest way to build a Zephyr project for CapBot is probably through nordic's toolchain docker images.
For example, the following command starts a container with the nRF Connect v2.7.0 toolchain:

```console
docker run --rm -it -v .:/firmware ghcr.io/nrfconnect/sdk-nrf-toolchain:v2.7.0
```

With the example project's directory mounted to `/firmware` in the container, the dependencies can be pulled in by running:
```console
cd /firmware/app
west init --local
west update
```

Finaly, the example can be build for a CapBot target. This should result in an ELF-file at `/firmware/app/build/zephyr/zephyr.hex`.
```console
west build --no-sysbuild --board capbot
```

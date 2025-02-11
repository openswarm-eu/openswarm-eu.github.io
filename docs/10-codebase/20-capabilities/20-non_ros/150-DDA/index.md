---
title: DDA
pagination_label: DDA
description: Data Distribution Agent (DDA).
---

# DDA

**Description**: Coaty evolution for constrained environments.

* **Primary Functionality**:  Enables unified and universal data-centric communication and collaboration in distributed and decentralized applications.
* **Target**: Various
* **Task**: T2.4
* **Responsible**: Markus Sauer

<Button label="🔗 openswarm-eu/dda repository" link="https://github.com/openswarm-eu/dda" block /><br />

# Overview

This project realizes the Data Distribution Agent (DDA), a loosely coupled multi-agent system that enables unified and universal data-centric communication and collaboration in distributed and decentralized applications. Its main goal is to remove the inherent complexity in developing communication technologies for distributed systems by exposing Data-centric Communication as a Service to application developers in the form of a middleware without requiring in-depth knowledge of messaging protocols and communication networks. DDA is designed for universal data exchange, enabling human-to-human, machine-to-machine, or hybrid communication.

A DDA exposes a collection of application-level peripheral services that _abstract_ commonly used functionality in decentralized applications:

* data-centric communication over interchangeable messaging protocols
* distributed state synchronization based on consensus algorithms that guarantee strong consistency
* local persistent key-value storage

Application components that do not embed the DDA library directly can consume these services through modern open-standard APIs.

In addition, a DDA supports observability, i.e. the ability to measure and infer its internal state by analyzing [OpenTelemetry](https://opentelemetry.io) traces, logs, and metrics that it generates and exports.

# Installation

Quick start guide can be found in [openswarm-eu/dda repository](https://github.com/openswarm-eu/dda).


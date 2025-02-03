---
title: Flocking
pagination_label: Flocking
description: Flocking formation.
---

# Flocking

**Description**: Python implementation of the flocking controller for a swarm of robots with range and bearing to its neighboring robots.

* **Primary Functionality**: Flocking formation.
* **Target**: Python-based robot
* **Task**: T5.1
* **Responsible**: Genki Miyauchi

<Button label="🔗 openswarm-eu/flocking repository" link="https://github.com/openswarm-eu/flocking" block /><br />

# Overview

This repository contains a Python implementation of a flocking controller for a swarm of robots that has range and bearing access to its neighboring robots.

It is based on the [Mie potential](https://en.wikipedia.org/wiki/Mie_potential), which involves attractive and repulsive forces. Each robot calculates virtual forces with its neighbors, which results in an overall flocking behavior.
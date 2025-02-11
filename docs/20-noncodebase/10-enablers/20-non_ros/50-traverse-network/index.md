---
title: Traverse Network
pagination_label: Traverse Network
description: Navigation along an ad-hoc network of robots.
---

# Traverse Network

**Description**: Python implementatoon of the navigation controller for a robot to traverse along an established ad-hoc network formed by robots.

* **Primary Functionality**: Navigation along an ad-hoc network of robots.
* **Target**: Python-based robot
* **Task**: T5.1
* **Responsible**: Genki Miyauchi

<Button label="🔗 openswarm-eu/traverse-network repository" link="https://github.com/openswarm-eu/traverse-network" block /><br />

# Overview

This repository contains a Python implementation of the navigation controller for a robot to traverse an established ad hoc network formed by robots.

The ad hoc network formed by the robot are assumed to be aware of their hop counts to the leaf nodes in the network and is broadcasting this information to any robot that are within their communication range. The robot traversing the network experiences attractive forces towards a robot forming the network with the smallest hop count to the target leaf node. Given the communication range of the robot traversing the network and the robot forming the ad hoc network are identical, the traversing robot is able to detect the next node along the network once it moves close enough to the current node. It also experiences repulsive forces to prevent collisions between robots.

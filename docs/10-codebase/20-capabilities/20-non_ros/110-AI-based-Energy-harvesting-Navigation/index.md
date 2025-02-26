---
title: AI-based-Energy-harvesting-Navigation
pagination_label: AI-based-Energy-harvesting-Navigation
description: Energy aware path planning.
---


# AI-based Energy Harvesting Navigation

## Description
AI solution for energy harvesting aware path planning in a swarm of robots.

- **Primary Functionality**: Energy-aware path planning.
- **Target**: Server / PC / Robot
- **Task**: T3.4
- **Responsible**: Mohmmadsadegh Mokhtari

[🔗 OpenSwarm-EU AI-based-Energy-harvesting-Navigation Repository](https://github.com/openswarm-eu/AI-based-Energy-harvesting-Navigation)

## Overview
This repository contains the Energy Harvesting Aware Path Planning Python codes. It uses **PPO and Q-learning** methods to find the best path inside the environment while balancing distance and energy harvesting opportunities.

<img src="https://github.com/user-attachments/assets/000d7206-1b00-43b5-995e-6200625afddd" width="50%" />

**Figure 1**: Visualization of the technical workflow for setting up the environment.

This research leverages **OpenAI Gymnasium** to simulate the environment and PPO learning. Traditional **Q-learning** is also adapted to the problem. The simulation analyzes different scenarios, including:

- Grid size
- Light sources
- Harvesting range
- Multiple robots
- Reward weight impact on navigation performance

<img src="https://github.com/user-attachments/assets/5537d387-aa40-4a75-92dd-b17970c6a9bb" width="50%" />

**Figure 2**: Illustration of the learning process outcomes, highlighting efficient pathfinding while maximizing energy harvesting.

Comprehensive results are documented in **deliverable T3.4**.

## Installation Guide

### Step 1: Install Required Dependencies
Run the following command to install the necessary libraries:

```sh
pip install gymnasium 
pip install numpy
pip install pygame
```

### Step 2: Verify Installation
To confirm that everything is installed correctly, open Python and run:

```python
import gymnasium as gym
from gymnasium import spaces
import numpy as np
import pygame
```

If no errors appear, the installation was successful.

### Step 3: Running the Code
Execute the following test scripts to see results:

```sh
/AI-based-Energy-harvesting-Navigation-main/tests/gridsize_tests.py    
                                                  multi_robot_tests.py 
                                                  reward_weights_tests.py
                                                  lightsource_tests.py 
                                                  range_EH_tests.py  

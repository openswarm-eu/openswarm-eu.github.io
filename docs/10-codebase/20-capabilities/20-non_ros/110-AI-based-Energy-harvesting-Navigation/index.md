---
title: AI-based-Energy-harvesting-Navigation
pagination_label: AI-based-Energy-harvesting-Navigation
description: Energy aware path planning.
---

# AI-based-Energy-harvesting-Navigation

**Description**: AI solution for energy harvesting aware path planning in a swarm of robots.

* **Primary Functionality**: Energy aware path planning.
* **Target**: Server / PC / robot
* **Task**: T3.4
* **Responsible**: Mohmmadsadegh Mokhtari

<Button label="🔗 openswarm-eu/AI-based-Energy-harvesting-Navigation repository" link="https://github.com/openswarm-eu/AI-based-Energy-harvesting-Navigation" block /><br />

![Drawing 3 (3)](https://github.com/user-attachments/assets/000d7206-1b00-43b5-995e-6200625afddd)
Figure 1: The overview of the technical steps of preparing the environment.  

<img width="504" alt="path_example (1)" src="https://github.com/user-attachments/assets/5537d387-aa40-4a75-92dd-b17970c6a9bb" />
Figure 2: This figure shows the results reported by the learning process inside the environment.  It shows promising results in maximizing the energy harvesting (in our case light energy) while finding the closest optimal path.  


#Overview
This repository contains the Energy Harvesting Aware Path Planning Python codes. It uses PPO and Q-learning methods to find the best path inside the environment considering the tradeoff between distance and energy harvesting opportunities. Figure 1 shows the overview of the proposed approach. This research uses the Open-AI Gymnasium tool to simulate the environment and the learning process of PPO. Also, to adapt the Q-learning to the problem, the traditional Q-learning method is used. 

 The codes simulate different scenarios to evaluate the model’s performance. Figure 2 shows an example of the results. This analysis investigates the impact of grid size, light source, harvesting range, multiple robots, and reward weight on navigation performance. The comprehensive results are accessible in deliverable T3.4. 




Installation Guide
**Step 1**: Install Required Dependencies
Run the following command to install the necessary libraries:

pip install gymnasium 
pip install numpy
pip install pygame


**Step 2**: Verify Installation
To confirm that everything is installed correctly, open Python and try importing the modules:

import gymnasium as gym
from gymnasium import spaces
import numpy as np
import pygame

If no errors appear, the installation was successful.

**Step 3**: Running the Code
Now, execute the following codes to see the results:


/AI-based-Energy-harvesting-Navigation-main/tests/gridsize_tests.py    
                                                  multi_robot_tests.py 
                                                  reward_weights_tests.py
                                                  lightsource_tests.py 
                                                  range_EH_tests.py  

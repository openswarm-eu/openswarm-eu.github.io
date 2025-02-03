---
title: Kilobots Positioning and Navigation
pagination_label: Kilobots Positioning and Navigation
description: Kilobot navigation using ARK.
---

# Kilobots Positioning and Navigation

**Description**: The Augmented Reality for Kilobots (ARK) system is employed to provide the Kilobot robots (used in task 5.3 of the open swarm project) with global positioning.

* **Primary Functionality**: Kilobot navigation using ARK.
* **Target**: PC and Kilobots
* **Task**: T5.1
* **Responsible**: Mohamed S. Talamali

<Button label="🔗 mstalamali/Kilobots-Positioning-and-Navigation repository" link="https://github.com/mstalamali/Kilobots-Positioning-and-Navigation" block /><br />

# Overview

This example showcases how the Augmented Reality for Kilobots (ARK) System is used to provide the Kilobot robots with positioning information. The Kilobots use the positioning information received from ARK to navigate between two locations of interast

The repository provides:

1. The ARK experiment which uses ARK's tracking functionalities to create a grid-based positioning system and periodically send IR message to the Kilobots on the arena to provide positioning information.

2. The .c code that is compiled and uploaded on the Kilobot to parse the positioning information received from the ARK system and use it to navigate between to locations of interest.


# Prerequisites

To use the code provided in the repository, the user must be familiar with the Kilobot robots and their programming (see [paper](https://ieeexplore.ieee.org/abstract/document/6224638) and [guide](https://www.giovannireina.com/kilowiki/index.php?title=Getting_Started:_How_to_work_with_kilobots)) and the ARK system (see [paper](https://ieeexplore.ieee.org/document/7915692) & [guide](https://www.giovannireina.com/kilowiki/index.php?title=Getting_started_on_ARK))


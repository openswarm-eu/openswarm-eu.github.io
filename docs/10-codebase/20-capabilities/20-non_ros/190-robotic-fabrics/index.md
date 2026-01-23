---
title: Robotic Fabrics
pagination_label: Robotic Fabrics
description: A plug-and-play framework for producing scalable, deformable modular robot entities.
---

# Robotic Fabrics

**Description**: A plug-and-play framework for producing scalable, deformable modular robot entities.

* **Primary Functionality**: Software used to run navigate the Kilobot swarm robotic fabric.
* **Target**: Kilobot
* **Task**: T5.3
* **Responsible**: Genki Miyauchi

<Button label="🔗 openswarm-eu/robotic-fabrics repository" link="https://github.com/openswarm-eu/robotic-fabrics" block /><br />

# Overview

Robotic Fabrics is a plug-and-play framework for producing scalable, deformable modular robot entities. The software and hardware have been designed for a robotic fabric comprising up to 81 Kilobots that are connected using deformable links to move straight or turn left or right.

# Software

The Kilobot controller can be found in ```software/```.

* ```forward_open-loop.c``` : Open-loop controller to make a single Kilobot move forward.
* ```deformation-correcting.c``` : Straight motion controller proposed in Pratissoli et al. 2023 ([paper](https://doi.org/10.1038/s41467-023-39660-6), [code](https://github.com/ilpincy/argos3-kilobot/blob/softrobot/src/examples/behaviors/KBSR_rebuild.c)). Each Kilobot measures the distance to its neighbors to detect the deformation in the lattice-structure and corrects its motion accordingly to maintain the shape of the structure.
* ```turning_open-loop.c``` : Proposed turning controller executed on each Kilobot to make the robotic fabric follow a curved trajectory.

# Supplementary videos

Experiment videos can be found [here](https://doi.org/10.15131/shef.data.27021310).

# Citing Robotic Fabrics

If you use Robotic Fabrics ([paper](https://ieeexplore.ieee.org/document/10993294)) in your research, please use the following BibTeX entry:

```BibTex
@article{obilikpa2025scalable,
    title = {Scalable Plug-and-Play Robotic Fabrics Based on Kilobot Modules},
    author = {Obilikpa, Stanley C. and Talamali, Mohamed S. and Miyauchi, Genki and Oyekan, John and Gro{\ss}, Roderich},
    journal = {IEEE Robotics and Automation Letters (RA-L)},
    volume = {10},
    number = {7},
    pages = {6832--6839},
    year = {2025},
    publisher = {IEEE},
    doi = {https://doi.org/10.1109/LRA.2025.3568313},
}
```

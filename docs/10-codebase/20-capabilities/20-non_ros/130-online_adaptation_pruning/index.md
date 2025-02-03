---
title: Online Adaptation Pruning
pagination_label: Online Adaptation Pruning
description: Training framework for low-power model fine-tuning.
---

# Online Adaptation Pruning

**Description**: This is the code used to complete the experiments in the paper: Online Adaptation of Compressed Models by Pre-Training and Task-Relevant Pruning.

* **Primary Functionality**: Training framework for low-power model fine-tuning.
* **Target**: Server / PC / robot
* **Task**: T3.2
* **Responsible**: Matthias Hutsebaut-Buysse

<Button label="🔗 openswarm-eu/online_adaptation_pruning repository" link="https://github.com/openswarm-eu/online_adaptation_pruning" block /><br />

# Overview

Neural networks are increasingly deployed on edge devices, where they must adapt to new data in dynamic environments. Here, model compression techniques like pruning are essential. This involves removing redundant neurons, increasing efficiency at the cost of accuracy, and creating a conflict between efficiency and adaptability. We propose a novel method for training and compressing models that maintains and extends their ability to generalize to new data, improving online adaptation without reducing compression rates. By pre-training the model on additional knowledge and identifying the parts of the deep neural network that actually encode task-relevant knowledge, we can effectively prune the model by 80% and achieve 16% higher accuracies when adapting to new domains.

# Published Paper

Avé, Thomas, et al. "Online Adaptation of Compressed Models by Pre-Training and Task-Relevant Pruning." ESANN 2024 proceedings: European Symposium on Artificial Neural Networks, Computational Intelligence and Machine Learning, 9-11 October, 2024, Bruges, Belgium. 2024. https://www.esann.org/sites/default/files/proceedings/2024/ES2024-50.pdf
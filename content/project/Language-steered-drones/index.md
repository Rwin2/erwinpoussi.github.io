---
title: "Language-Steered Drones"
date: 2026-01-01
summary: "Reinforcement learning for language-guided drone navigation with instruction-conditioned, object-level goal identification."
tags: ["Reinforcement Learning", "Robotics", "Autonomous Navigation", "Vision-Language"]
---
Developing reinforcement learning algorithms for **language-guided drone navigation**, enabling **instruction-conditioned, object-level goal identification** and **autonomous closed-loop navigation**.

This project explores how natural-language instructions can be mapped to semantic, object-level navigation goals and executed by autonomous aerial agents.

### Technical stack
- Reinforcement Learning (policy gradients, actor–critic)
- Vision–Language models for instruction grounding
- Sampling-based planning (RRT) for low-level control
- Simulation-based training and evaluation
- Python, PyTorch, Gsplat

### Current status
This project is in an **early stage**. Below is a preliminary demonstration showing **vehicle motor rate control** using **RRT-based trajectory tracking** along a spiral path in 3D gaussian splat reconstructed environment.

## Demo
<iframe width="100%" height="420"
src="https://www.youtube.com/embed/tMEvtIlwTAw"
frameborder="0" allowfullscreen></iframe>

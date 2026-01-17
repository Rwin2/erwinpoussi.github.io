---
title: "Language-Steered Drones"
date: 2026-01-01
summary: "Reinforcement learning for language-guided drone navigation with instruction-conditioned, object-level goal identification."
tags:
  - Reinforcement Learning
  - Robotics
  - Autonomous Navigation
  - Vision-Language
---

This project focuses on **reinforcement learning for language-guided drone navigation**, enabling **instruction-conditioned, object-level goal identification** and **autonomous closed-loop control**.

The pipeline acquires real-world imagery of an environment, reconstructs a **3D Gaussian Splat (GSplat) representation**, and derives a **semantic scene abstraction**. Policies are trained in simulation and transferred to real-world experiments, enabling **language-driven navigation from perception to control**.

This research is conducted under **Prof. Mac Schwager**  
([Multi-Robot Systems Lab, Stanford](https://web.stanford.edu/~schwager/))  
and in collaboration with **PhD student Maximilian Adang**  
([MSL Stanford](https://msl.stanford.edu/people/maximilianadang)).

### Technical stack
- Reinforcement Learning (policy gradients, actor–critic)
- Vision–Language models for instruction grounding
- Sampling-based planning (RRT) for low-level control
- Simulation-based training and sim-to-real transfer
- Python, PyTorch, Gaussian Splatting (GSplat)

### Current status
This project is in an **early stage**. The demonstration below shows **low-level motor rate control** using **RRT-based trajectory tracking** along a spiral path in a **3D Gaussian Splat reconstructed environment**.

## Demo
<iframe
  width="100%"
  height="420"
  src="https://www.youtube.com/embed/tMEvtIlwTAw"
  frameborder="0"
  allowfullscreen>
</iframe>

---
title: "Language-Steered Drones"
date: 2026-01-01
summary: "End-to-end robot learning pipeline for language-guided drone navigation — from MPC expert demonstrations to sim-to-real deployment via behavioral cloning and DAgger."
tags:
  - Robotics
  - Deep Learning
  - Robot Learning
  - Imitation Learning
  - Sim-to-Real Transfer
  - Vision-Language
  - Autonomous Systems
---

## Drone navigating to a leaf blower
<iframe
  width="100%"
  height="420"
  src="https://www.youtube.com/embed/R6zd46fFNQ0"
  frameborder="0"
  allowfullscreen>
</iframe>

Developed a vision-language navigation (VLN) policy for autonomous drone flight in photorealistic 3D Gaussian Splatting environments. Given a natural language instruction like "go to the green leafblower," the drone autonomously identifies and navigates to the target — collision-free.

The video shows the drone's onboard view: RGB (left) and semantic similarity field (right) for the query "green and pink leafblower." In the right view, red indicates high similarity with the query and blue indicates low similarity — the drone navigates towards the high-similarity region while avoiding obstacles. The system first encodes the language instruction via CLIP embeddings, localizes the target using CLIPSeg semantic segmentation, and generates real-time control commands to navigate through a cluttered indoor environment.

The control policy is a lightweight neural network (SqueezeNet Commander MLP) trained via Behavioral Cloning from an ACADOS-based MPC expert. A key contribution is the design and implementation of a full DAgger (Dataset Aggregation) pipeline — including mixed-policy rollouts, expert annotation filtering, iterative retraining with best-model checkpointing, and automated benchmarking — to systematically correct for compounding errors under distribution shift. A second key contribution is the introduction of explicit geometric features — bearing and elevation — extracted from the CLIPSeg heatmap centroid, providing the policy with a direct spatial signal for goal-directed control. This replaces the previous approach where target localization had to be implicitly learned from visual embeddings alone.

**Results:** 90% navigation success rate (up from 52%), collision rate reduced from 20% to 8%, with generalization to unseen RRT-planned trajectories.

This research is conducted under **Prof. Mac Schwager**
([Multi-Robot Systems Lab, Stanford](https://web.stanford.edu/~schwager/))
in collaboration with **PhD student Maximilian Adang**
([MSL Stanford](https://msl.stanford.edu/people/maximilianadang)).

**[GitHub Repository](https://github.com/Rwin2/SINGER/tree/feature/centroid-v9)**

### Tech Stack
PyTorch · 3D Gaussian Splatting (gsplat) · CLIPSeg · ACADOS optimal control · CUDA

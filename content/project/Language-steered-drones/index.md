---
title: "Language-Steered Drones"
date: 2026-01-01
summary: "End-to-end robot learning pipeline for language-guided drone navigation — from MPC expert demonstrations to sim-to-real deployment via behavioral cloning and DAgger."
tags:
  - Robot Learning
  - Imitation Learning
  - Sim-to-Real Transfer
  - Vision-Language
  - Autonomous Systems
---

## Simulated Trajectory
<iframe
  width="100%"
  height="420"
  src="https://www.youtube.com/embed/tMEvtIlwTAw"
  frameborder="0"
  allowfullscreen>
</iframe>

**SINGER** (Stanford Intelligent Navigation with Generalist Embodied Robots) trains a neural drone pilot — *InstinctJester* — to navigate to language-described targets inside photorealistic **3D Gaussian Splat** environments.

The system follows a full Learning from Demonstration pipeline. An **MPC expert** (VehicleRateMPC via ACADOS optimal control) flies **RRT\*-planned trajectories** through the scene, generating ~8,800 perturbed short rollouts per object. Each rollout starts from a randomly offset state, forcing the expert to demonstrate recovery behavior — not just nominal flight. At each timestep, the pilot's **OODA loop** extracts what the neural network would observe (drone state, goal descriptor, CLIPSeg visual embeddings, 20-step motion history) paired with the expert's action `[thrust, ωx, ωy, ωz]`, yielding ~52,800 labeled training samples.

The **InstinctJester** architecture separates temporal reasoning from command generation: a **HistoryEncoder** compresses the rolling 20-step motion history into a feature vector, and a **Commander** network maps the full observation to motor commands. Both are trained via **behavioral cloning** (MSE loss, Adam, lr=1e-4) on expert demonstrations.

To correct distributional shift, **DAgger** iteratively refines the Commander: a mixed policy (β · expert + (1−β) · pilot) flies full trajectories, annotations are filtered by deviation and goal proximity, and the Commander is retrained on BC data plus the new corrections (lr=3e-5). A best-model restoration strategy with fixed evaluation seeds (seed=42) ensures each iteration makes genuine, reproducible progress.

Natural language goal specification uses **CLIPSeg** to ground object queries (e.g., *"green clock"*, *"yellow cordless drill on two boxes"*) to spatial targets in the reconstructed scene, enabling instruction-conditioned navigation without manual goal annotation.

This research is conducted under **Prof. Mac Schwager**  
([Multi-Robot Systems Lab, Stanford](https://web.stanford.edu/~schwager/))  
in collaboration with **PhD student Maximilian Adang**  
([MSL Stanford](https://msl.stanford.edu/people/maximilianadang)).

### Technical Stack
- Behavioral cloning + DAgger (dataset aggregation) for policy learning
- MPC expert (ACADOS) + RRT\* for demonstration generation
- CLIPSeg for language-conditioned object grounding
- 3D Gaussian Splatting (GSplat / FiGS) for photorealistic simulation
- Sim-to-real transfer with real-hardware evaluation
- Python · PyTorch · ACADOS · W&B
```


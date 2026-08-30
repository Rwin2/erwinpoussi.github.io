---
title: "GAIT: Graph-Memory Agent with Interrupt-Triggered Reasoning"
date: 2026-08-01
draft: false
summary: "Leverage online semantic scene graph construction to build a persistent memory for vision-language-action models, enabling open-vocabulary navigation."
tags:
  - Deep Learning
  - Robotics
  - Autonomous Navigation
  - Vision-Language
  - Robot Learning
---

## Demo
<video width="100%" height="420" autoplay loop muted playsinline>
  <source src="demo.mp4" type="video/mp4">
</video>

**GAIT** (Graph-memory Agent with Interrupt-Triggered reasoning) builds a persistent, structured memory for vision-language-action (VLA) models by constructing semantic scene graphs online during navigation. The agent incrementally builds a graph-based spatial memory from egocentric observations, encoding object identities, spatial relations, and semantic attributes as it explores. An interrupt-triggered reasoning mechanism allows the agent to re-plan on the fly when novel or task-relevant cues are detected — bridging reactive control with deliberative graph-based reasoning.

This enables **open-vocabulary navigation**: given a free-form language goal, the agent retrieves and reasons over its scene graph memory to localize targets it has previously observed, or to plan exploration strategies for unseen goals — without requiring a fixed object vocabulary or pre-built map.

**Status:** More to come soon!

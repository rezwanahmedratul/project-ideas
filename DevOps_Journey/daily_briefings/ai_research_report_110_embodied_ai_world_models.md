# AI Research Report #110 — Embodied AI: From LLMs to World Models

**Date:** 2026-09-09  
**Category:** AI Research

---

## Executive Summary

Embodied AI represents the convergence of large language models with physical interaction — giving AI systems the ability to perceive, reason about, and act in the real world. This report explores the latest advances in embodied AI, from vision-language-action models to world model architectures.

---

## What is Embodied AI?

Embodied AI refers to AI systems that:
1. **Perceive** their environment through sensors (cameras, microphones, etc.)
2. **Reason** about observations using learned models
3. **Act** upon the environment to achieve goals

Unlike traditional LLMs that process text, embodied AI systems operate in continuous, multimodal spaces.

---

## Key Architectural Approaches

### 1. Vision-Language-Action (VLA) Models

VLA models unify perception, language understanding, and motor control.

**Representative Systems:**
- **RT-2 (Google):** Translates visual inputs to robot actions via LLM fine-tuning
- **V-JEPA (Meta):** Joint Embedding Predictive Architecture for world modeling
- **PaLI-3 (Google):** Multimodal model with robotics capabilities

**Architecture:**
```
┌──────────┐    ┌──────────┐    ┌──────────┐
│  Image   │───▶│  Encoder │───▶│  Vision  │
│  Input   │    │          │    │  Module  │
└──────────┘    └──────────┘    └────┬─────┘
                                     │
                              ┌────────┴────────┐
                              │  Language Model │
                              │  (Joint embedding)│
                              └────────┬────────┘
                                       │
                              ┌────────┴────────┐
                              │  Action Decoder │
                              │  (Motor control)│
                              └─────────────────┘
```

### 2. World Models

World models learn to predict the consequences of actions, enabling planning without explicit simulation.

**Components:**
- **Encoder:** Compresses observations into latent states
- **Dynamics model:** Predicts next state given current state + action
- **Decoder:** Reconstructs observations from latent states

**Benefits:**
- Efficient planning in latent space
- Generalization to unseen scenarios
- Sample-efficient learning

---

## Recent Breakthroughs (2025)

### 1. LLM-Planner Integration
Research shows LLMs can serve as high-level planners for robotic systems:
- Decompose tasks into sub-goals
- Select appropriate skills/actions
- Handle errors and replan

### 2. Self-Reflection in Embodiment
Agents can now:
- Evaluate their own performance
- Learn from failures
- Adapt strategies autonomously

### 3. Generative World Models
Combining generative AI with robotics:
- Create synthetic training data
- Simulate diverse environments
- Accelerate learning

---

## Applications

### Robotics
- Household assistance
- Warehouse automation
- Surgical robots

### Autonomous Vehicles
- Perception and decision making
- Navigation in complex environments

### AR/VR
- Interactive virtual environments
- Digital twins

### Manufacturing
- Quality inspection
- Assembly automation

---

## Challenges

1. **Sim-to-real gap:** Models trained in simulation struggle in reality
2. **Sample efficiency:** Real-world learning is slow and expensive
3. **Safety:** Physical agents can cause real harm
4. **Generalization:** Handling novel situations

---

## References

1. [Embodied AI: From LLMs to World Models](https://arxiv.org/html/2509.20021v1) - Tsinghua University, Sep 2025
2. [RT-2: Vision-Language-Action Models](https://robotics-transformer2.github.io/)
3. [V-JEPA: Meta's World Model](https://ai.meta.com/research/v-jepa/)
4. [LLM-planner Research](https://mn.cs.tsinghua.edu.cn/xinwang/PDF/papers/2025_Embodied+AI+from+LLMs+to+World+Models.pdf)

---

*Generated: 2026-09-09 | Source: Overnight research engine*

---
layout: page
title: ICU Glucose Monitoring Optimization
description: Offline RL + decision-theoretic modeling to recommend when to measure blood glucose in the ICU under uncertainty.
img: assets/img/glucoseMonitor.jpg
importance: 1
category: AI/ML
---

## Problem

Critically ill ICU patients require frequent blood glucose monitoring, but measurements are costly in time, labor, and resources. Clinicians must decide when to measure glucose under uncertainty, balancing patient safety against operational constraints. This creates a challenging sequential decision-making problem with sparse, noisy observations and partial observability.

## Goal / Solution

I developed a data-driven decision framework that recommends when to perform blood glucose measurements in the ICU. We formulated glucose-monitoring allocation as a Markov Decision Process (MDP) and investigated whether offline reinforcement learning could recover clinically sensible monitoring strategies from historical ICU data.

## Methods

- **MDP formulation**: cost-sensitive decision process with actions: wait, finger-prick test, or lab analysis
- **Approximate partial observability**: compact belief-state representation (8 features) summarizing recent glucose history, trends, variability, and time since last measurement
- **Clinically informed reward**: measurement costs plus penalties for missed measurements prior to insulin interventions (used as proxies for hyperglycemic events)
- **Offline policy learning and baselines (MIMIC-III)**:
  - Heuristic baselines (always wait, fixed-interval monitoring, myopic value-of-information)
  - Deep Q-Learning (DQN) on historical trajectories
  - Behavioral cloning to imitate clinician measurement decisions
- **Evaluation**: measurement frequency and the ability to capture clinically relevant interventions

## Results & Conclusion

Learned policies produced clinically reasonable monitoring behaviors despite sparse observations and no online interaction. However, they only marginally outperformed simple heuristics, highlighting limitations of purely data-driven approaches under partial observability and limited clinical context. The results suggest compact state representations and offline RL are feasible for ICU monitoring tasks, but richer physiological dynamics and more clinically informed models are likely necessary to achieve meaningful performance gains.

## Takeaway

This project demonstrates how reinforcement learning and decision-theoretic modeling can be applied to real-world healthcare resource allocation problems, while also surfacing the practical challenges of offline RL, partial observability, and reward design in safety-critical clinical settings.

## Full paper

- **PDF**: [CS238 Project Final Paper](assets/pdf/CS238_Project_Final_Paper.pdf)

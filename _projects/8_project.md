---
layout: page
title: NMDA Receptor Binding for Pain Therapeutics
description: Investigated the molecular interactions between NMDA receptor antagonists and their binding sites
img: assets/img/NMDA_screenshot.png
importance: 8
category: Bioengineering
giscus_comments: false
---

## Overview

This project explores the structural basis of how NMDA receptor antagonists bind the human NMDA receptor, motivated by the role of NMDA signaling in central sensitization and chronic pain. NMDA antagonists can inhibit receptor activation, making them promising candidates for chronic pain therapeutics—yet the molecular details of binding are still not fully understood.

## Methods

I ran ligand–receptor docking simulations using SwissDock (AutoDock Vina). Ligand structures (from PubChem) and an NMDA receptor structure (from RCSB PDB) were docked with the search space centered around the ion channel opening, the binding site of interest. For each ligand, I filtered out poses that bound outside the target site and recorded the highest-affinity pose that bound correctly.

## Key results

Across the ligands tested, the best in-site binding affinities were:

- **S-ketamine**: \(-6.065\) kcal/mol
- **Dextromethorphan**: \(-7.144\) kcal/mol
- **Amantadine**: \(-5.442\) kcal/mol

In this dataset, dextromethorphan showed the strongest predicted binding to the NMDA receptor and emerged as the most promising candidate for follow-up evaluation.

## Next steps

Future work would expand the ligand set (literature-driven screening of additional NMDA antagonists), validate docking trends across alternative tools (e.g., AutoDock Tools, Chimera), and investigate safety/feasibility considerations for therapeutic translation.

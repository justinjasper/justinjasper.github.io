---
layout: page
title: Synthetic Biosensor for Salmonella Detection 
description: Developed a novel biosensor to detect waterborne Salmonella enterica using a SynNotch receptor system.
img: assets/img/synnotch_screenshot.png
importance: 7
category: Molecular Biology
related_publications: true
---

## Executive Summary

This project focused on the design, construction, and preliminary validation of a mammalian-cell–based biosensor capable of detecting *Salmonella* O-antigens using a SynNotch receptor system. HEK293 cells were engineered to express a surface SynNotch receptor containing an anti-O-antigen scFv and a Myc epitope tag, coupled to a downstream fluorescent reporter (mCherry). Through iterative plasmid preparation, transfection optimization, flow cytometry–based surface expression assays, and co-culture experiments with inactivated model *Salmonella*/*E. coli*, our team established proof-of-concept that receptor expression scales with plasmid dose and that reporter activation trends higher in the presence of bacterial antigen.

## Motivation and Objectives

Foodborne illness caused by *Salmonella enterica* remains a significant public health concern. Existing detection methods can be slow, equipment-intensive, or require specialized microbiological expertise. The objective of this project was to develop a modular, cell-based biosensor that translates the presence of *Salmonella* O-antigens into a fluorescent readout using synthetic biology principles.

Specific objectives included:

- Designing and preparing a SynNotch receptor plasmid targeting *Salmonella* O-antigens
- Validating surface expression of the receptor in mammalian cells using Myc-tag staining
- Optimizing receptor and reporter plasmid transfection ratios
- Developing a safe bacterial inactivation protocol suitable for mammalian co-culture
- Testing whether the biosensor produces increased reporter output in the presence of model *Salmonella* antigens

## System Design Overview

The engineered system consists of:

- **Chassis**: HEK293 mammalian cells
- **Sensor**: SynNotch receptor with an extracellular anti-*Salmonella* O-antigen scFv and an extracellular Myc tag (for surface detection)
- **Signal transduction**: ligand-induced SynNotch cleavage releasing an intracellular transcriptional activator (Gal4-VP16)
- **Output**: Gal4-driven transcription of a fluorescent reporter (mCherry) for quantitative single-cell readout

This design decouples antigen recognition from reporter expression and keeps the system modular (receptors and outputs can be swapped in future iterations).

## Experimental Workflow (High-Level)

### Plasmid preparation and handling

Plasmids were resuspended, transformed into *E. coli*, streaked for single colonies, expanded in selective media, and archived as glycerol stocks. Plasmids were isolated via miniprep and quantified using Nanodrop, with multiple colonies processed for redundancy.

### Transfection verification (Comet GFP)

To verify that our transfection workflow was functioning, we intentionally transfected a Comet GFP plasmid. Cells fluoresced following transfection, confirming successful delivery and expression of the Comet GFP construct.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/VerificationOfTransfection.png" title="Verification of transfection (Comet GFP)" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Verification of successful transfection using a Comet GFP plasmid.
</div>

### Myc-tag staining and flow cytometry (surface expression)

Two rounds of Myc-tag surface staining were performed to assess SynNotch receptor surface expression as a function of receptor plasmid dose:

- **First Myc stain**: Dose-dependent increases in Myc signal (40 ng → 400 ng), confirming surface expression but with low positive-cell fractions.
- **Second Myc stain**: Protocol optimizations (longer expression time, gentler harvesting, revised plasmid concentrations) improved data quality; 1500 ng receptor plasmid produced ~3× higher Myc-tag signal than 500 ng.

Flow cytometry was chosen for quantitative, single-cell–resolution assessment of heterogeneous expression across cell populations.

<div class="row justify-content-sm-center">
  <div class="col-sm-12 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/FlowCytometryResults.png" title="Flow cytometry results" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Flow cytometry results used to quantify SynNotch surface expression (Myc-tag staining) and guide plasmid-dose decisions.
</div>

### Reporter expression and leakiness analysis

Reporter-only and receptor+reporter conditions were compared to evaluate baseline leakiness. Positive controls using constitutive Gal4-VP16 showed strong mCherry expression, while negative controls showed minimal signal. Lower reporter plasmid doses reduced leakiness, and a 1:1 receptor-to-reporter ratio was selected as a practical compromise for downstream sensing experiments.

### Model bacteria culture, inactivation, and co-culture

A model *Salmonella*/*E. coli* strain was cultured and tested under multiple inactivation strategies (heat, cold, ethanol). After iterative evaluation of bacterial survival and mammalian cell safety, heat inactivation was selected for co-culture experiments. Optical density measurements were used to estimate bacterial concentration and choose bacteria-to-mammalian-cell ratios; a high excess of bacteria was used to maximize the likelihood of SynNotch activation.

HEK293 cells transfected with receptor and reporter plasmids were co-cultured with heat-inactivated model bacteria (triplicate wells with bacteria, triplicate wells without bacteria, plus positive/negative controls), then analyzed by fluorescence microscopy and flow cytometry.

## Results (Summary)

- **Receptor expression**: Myc-tag flow cytometry confirmed that receptor surface expression increases with receptor plasmid dose; protocol refinements significantly improved signal quality.
- **Cell viability and morphology**: Microscopy showed no major morphological differences between cells cultured with or without inactivated bacteria, indicating the bacterial treatment was effective and non-toxic under the tested conditions.
- **Reporter activation**: Positive controls exhibited strong reporter expression. Experimental groups showed modest but consistent trends, with higher reporter output in bacteria-exposed wells relative to matched no-bacteria controls across multiple replicates.

## Challenges and Limitations

- **Sourcing genetic parts**: scFv sequences and SynNotch backbones were difficult to locate due to intellectual property constraints.
- **Expression efficiency**: Early experiments produced low receptor-positive fractions, requiring protocol iteration and optimization.
- **Bacterial inactivation**: Multiple iterations were required to ensure safety without compromising antigen integrity.

## Future Work

- Increase replicate count and refine controls for co-culture experiments
- Systematically vary receptor-to-reporter ratios and bacterial concentrations
- Test isolated O-antigens instead of whole bacteria to improve specificity and safety
- Evaluate higher-affinity / better-characterized anti-*Salmonella* scFvs
- Add dynamic measurements (e.g., time-lapse imaging) to study activation kinetics

## Recombinant Plasmid Map

<div class="row justify-content-sm-center">
  <div class="col-sm-12 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/MyRecombinantPlasma.png" title="Recombinant plasmid map/diagram" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Map/diagram of the recombinant plasmid used in this project.
</div>

## Appendix

- **Plasmid sequence (PDF)**: [My recombinant plasmid sequence](assets/pdf/My-recombinant-plasmid-sequence.pdf)
- **Video presentation**: [Project presentation (YouTube)](https://youtu.be/WVyUvVSWCis)

---
layout: page
title: Dynamic Electronic Health Record Reconstruction
description: Ontology-first, VLM-driven pipeline that converts scanned medical record bundles into a structured, queryable patient chart with full provenance and deterministic retrieval.
img: assets/img/EHRX.png
importance: 2
category: AI/ML
---

## Abstract

Healthcare interoperability remains limited in practice despite legislative mandates and standardized data models such as  Fast Healthcare Interoperability Resources (FHIR) and  Observational Medical Outcomes
Partnership (OMOP). Most inter-institutional record transfers still occur via faxed or scanned PDFs, producing fragmented, non-queryable document bundles that impose significant cognitive and time burdens on clinicians.

EHRX is a proof-of-concept system that reconstructs an interactive, queryable Electronic Health Record (EHR) from unstructured transferred medical documents. The system leverages vision-language models (VLMs), a predefined clinical ontology, and deterministic retrieval to transform raw document scans into a structured, navigable patient chart while preserving full provenance to source documents. Experiments demonstrate accurate extraction of clinically critical information and reliable multi-document reasoning with **zero hallucinations**.

## Problem

Although modern EHR systems internally store structured data, cross-institutional data exchange remains largely unstructured. External patient records are typically received as scanned PDFs containing lab reports, pathology notes, operative reports, and discharge summaries with no consistent layout or machine-readable structure. This creates several critical issues:

- **High clinician burden**: providers manually search through hundreds of pages to find key details
- **Loss of computability**: PDF-based records cannot be queried or integrated into decision support systems
- **Fragmented patient narratives**: clinicians must reconstruct timelines and context, increasing the risk of missed findings and medical error

The motivating question:

**Can we reconstruct a usable, interactive EHR from the unstructured documents already being exchanged today?**

## Solution & Goals

EHRX proposes an ontology-first, VLM-driven pipeline that converts unstructured clinical documents into a structured, queryable EHR representation. The primary goals were to:

- Automatically extract clinically meaningful information from heterogeneous scanned medical documents
- Reconstruct an EHR-like structure (problems, medications, labs, notes, etc.) rather than flat text
- Enable deterministic, complete-recall querying over the reconstructed record to avoid hallucinations or missed facts
- Preserve full provenance and auditability, allowing each extracted fact to be traced to its source document and location

Rather than relying on probabilistic retrieval (e.g., embedding-based RAG), the system emphasizes determinism, completeness, and clinical safety.

## Methods

### System architecture

EHRX is composed of two phases:

- Offline extraction & structuring
- Online querying & reasoning

### 1) Vision-language model (VLM) extraction

- Each page of a scanned PDF is processed as an image by a lightweight VLM.
- The VLM performs joint OCR and semantic classification, extracting document elements with bounding boxes and confidence scores.
- Extraction is constrained to a predefined clinical ontology, turning open-ended parsing into a more reliable classification problem.

### 2) Ontology-guided structuring

- Extracted elements are assembled into a hierarchical JSON schema that mirrors modern EHR structure.
- Deterministic heuristics group elements into logical clinical sections using headers and keyword-based rules.
- Each element retains spatial coordinates and links to the original document for auditability.

### 3) Deterministic query pipeline

- A small LLM maps user queries to relevant semantic types.
- A deterministic ontology filter retrieves all matching elements (complete recall).
- A larger reasoning model synthesizes answers over the filtered context and returns conclusions with supporting evidence.

This filter-then-reason architecture replaces stochastic similarity search and eliminates hallucinations—critical for clinical use.

## Experimental Evaluation

Two targeted experiments evaluated performance on realistic clinical tasks:

- **Experiment 1: “Needle in the Haystack” extraction**
  - Identified a single critical datapoint buried in a large, noisy document bundle
  - All queries answered accurately with zero false positives / hallucinations
- **Experiment 2: Multi-fact clinical reasoning**
  - Cross-document reasoning across pathology, imaging, labs, operative reports, and consultations
  - Synthesized treatment plans, staging, prognosis, and chemotherapy eligibility
  - Achieved ~80% relevant datapoint inclusion with most responses rated high quality

Across all experiments, **no hallucinated clinical facts** were observed, validating the deterministic retrieval design.

## Conclusion

EHRX demonstrates that clinical documents are visually unstructured but semantically predictable, making them well-suited to ontology-driven reconstruction. By combining VLMs with predefined clinical ontologies and deterministic retrieval, EHRX transforms unstructured document bundles into interactive, queryable patient records.

While still a proof-of-concept, the approach suggests a feasible path to improve interoperability without waiting for universal standards adoption—reducing clinician burden, preserving provenance, and avoiding failure modes common in stochastic retrieval systems.



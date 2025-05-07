# PlantPhenotyping-Segmentation

# Plant Phenotyping via Deep Learning (PhenoBench + Probabilistic DLv3+ + EMNet)

This repository contains the complete implementation of a semantic segmentation pipeline for plant phenotyping, specifically distinguishing crops, weeds, and background from UAV images under real-world agricultural conditions.

## Summary

- **Baseline**: Probabilistic DeepLabV3+ (with MC Dropout) tested in zero-shot mode.
-  **Improvement 1**: CEI-based preprocessing + CutMix augmentation + composite loss (CE + Dice + Focal).
-  **Improvement 2**: Edge-Aware Mirror Network (EMNet) for sharper boundaries.
- Trained & validated on [PhenoBench](https://doi.org/10.1038/s41597-023-02213-3), using 5-channel CEI-enhanced input.

## Repository Structure


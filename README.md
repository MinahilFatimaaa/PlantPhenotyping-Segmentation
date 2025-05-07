# PlantPhenotyping-Segmentation

# Plant Phenotyping via Deep Learning (PhenoBench + Probabilistic DLv3+ + EMNet)

This repository contains the complete implementation of a semantic segmentation pipeline for plant phenotyping, specifically distinguishing crops, weeds, and background from UAV images under real-world agricultural conditions.

## Summary

- **Baseline**: Probabilistic DeepLabV3+ (with MC Dropout) tested in zero-shot mode.
-  **Improvement 1**: CEI-based preprocessing + CutMix augmentation + composite loss (CE + Dice + Focal).
-  **Improvement 2**: Edge-Aware Mirror Network (EMNet) for sharper boundaries.
- Trained & validated on [PhenoBench](https://doi.org/10.1038/s41597-023-02213-3), using 5-channel CEI-enhanced input.


## Experimental Setup

- Dataset: [PhenoBench](https://doi.org/10.1038/s41597-023-02213-3)
- Backbone: ResNet-50 with MC Dropout active during inference
- Input Channels: RGB + Excess Green (ExG) + Excess Red (ExR)
- Augmentation: Random flip, scale, rotation, Gaussian noise, CutMix
- Optimizer: AdamW
- Learning Rate Schedule: OneCycleLR with LR Finder
- Loss Function: Composite (Cross-Entropy with weights + Dice + Focal)
- Evaluation Metrics: Mean Intersection-over-Union (mIoU), Expected Calibration Error (ECE)

## Training Stages

| Stage                          | Dataset      | Trained On   | mIoU (%) | ECE     |
|--------------------------------|--------------|--------------|----------|---------|
| Zero-shot Prob. DLv3+          | Weedsgalore  | Weedsgalore  | ~29.0    | —       |
| Zero-shot Prob. DLv3+          | PhenoBench   | Weedsgalore  | ~29.0    | —       |
| Baseline + Improvement 1       | PhenoBench   | PhenoBench   | 56.52    | 0.0404  |
| Baseline + Improvement 2 (EMNet)| PhenoBench  | PhenoBench   | 77.01    | ~0.040  |





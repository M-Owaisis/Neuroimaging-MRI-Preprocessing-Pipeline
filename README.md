# Neuroimaging MRI Preprocessing Pipeline 🧠

A complete and robust automated preprocessing pipeline tailored for 3D Brain MRIs, specifically designed for dementia detection and neuro-imaging classification models.

## Overview
Raw MRI scans contain artifacts, intensity variations, and structural misalignments that severely impact the performance of deep learning models. This repository contains the standalone preprocessing pipeline developed to handle these issues by standardizing structural brain MRIs into a format ready for neural network classifiers.

## Key Features & Preprocessing Phases
The pipeline is split into distinct logical phases:

### Phase 1: Core Standardisation
- **N4 Bias Field Correction:** Removes low-frequency intensity non-uniformity (bias fields) caused by the MRI scanner.
- **Skull Stripping:** Isolates the brain tissue by removing the skull, dura, and non-brain matter from the scan.
- **Normalization:** Scales pixel intensities to standardize contrast across different patients and scanners.

### Phase 2: Spatial & Structural Processing
- **Co-registration / Spatial Normalization:** Aligns all MRIs to a standard stereotaxic space (such as MNI152) to ensure structural anatomical consistency across the dataset.
- **Resampling:** Uniformly resamples voxel spacing so every scan has the same physical scale.

## Usage
The central execution logic is routed through `preprocess.py`, which coordinates `phase1_preprocessing.py` and `phase2_preprocessing.py`.

```bash
# Example command to run the pipeline
python preprocess.py --input_dir /path/to/raw/mris --output_dir /path/to/processed/mris
```

## Repository Context
This code was extracted from the main pipeline to serve as a modular, standalone repository for Medical Image Processing researchers and machine learning engineers looking to standardise their own Brain MRI datasets before applying 3D CNNs or Vision Transformers.

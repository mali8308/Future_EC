# Future EC Prediction from DNA Methylation

## Overview

This repository contains the code, data, and analysis pipeline for a research project investigating the prediction of **Endometrial Cancer (EC)** using DNA methylation data. The primary focus is on developing models to:

- Diagnose existing EC
- Predict **Future EC risk** using peripheral blood samples
- Perform functional analysis of predictive CpG sites
- Explore integration with transcriptomics and epigenetic aging

## Goals

1. ✅ Compile accurate metadata (1,384 samples)
2. ✅ Predict EC (diagnosis) from Infinium HM450/850 arrays
3. ✅ Predict Future EC via survival analysis
4. ✅ Identify CpGs associated with EC and perform functional analysis

## Datasets Used

- **GSE89093**: Monozygotic twins, one healthy and one with EC
- **TCGA-UCEC**
- **GSE263434**: For transcriptomic analysis of candidate genes

## Diagnosis Prediction (Current EC)

- Focused on two key genes: `HAND2` and `ADCYAP1`
- Applied:
  - Random forest classifiers
  - Penalized logistic regression (elastic net)
- Ensemble feature selection methods
- AUC Performance on GSE89093:
  - `HAND2`: 0.81–0.83
  - `ADCYAP1`: 0.69–0.85
  - Both combined: 0.81 (Random Forest)

## Future EC Prediction (Survival Analysis)

- Models applied:
  - Penalized Cox Proportional Hazards
  - Random Survival Forests (RSF)
- Used both raw CpGs and `PhenoAge` clock probes
- Results:
  - `PhenoAge` CpGs correlated in GSE89093 but failed in TCGA
  - 146 CpGs significant for survival in GSE89093; 15 retained in final model
  - No consistent survival prediction across datasets

## Feature Engineering

- Created CpG × Gene interaction features using linear models
- Attempted pseudotime projection and PCA
- These features did **not** improve survival prediction

## Functional Analysis

- Used top 146 CpGs for pathway and ontology enrichment
- No Reactome or GO enrichment detected
- Protein–Protein Interaction network revealed involvement in:
  - Proteasome system
  - Cell cycle regulation
  - Mitophagy (Yao et al., 2022)
  - CDK2–CCNE1 axis (House et al., 2025)

## Key Findings

- Methylation of `HAND2` and `ADCYAP1` is lower in serous carcinoma compared to endometrioid
- Diagnosis prediction works better with **non-linear models**
- `PhenoAge` shows promise but lacks generalizability across tissue types

## Limitations

- Limited success in generalizing predictive CpG signatures
- Lack of train/test separation impacted statistical confidence in some analyses
- Multi-modal integration and EpiScore development were not completed

## Future Directions

- Develop self-supervised models to extract feature embeddings
- Explore transfer learning from published epigenetic clocks
- Integrate methylation with gene expression data for causal inference
- Focus on tissue-specific differences in methylation (e.g., tumor vs blood)

## References

- Yao et al. (2022). CDK9 inhibition and mitophagy in HCC. *Autophagy*.
- Multinu et al. (2020). DNA methylation in endometrial biopsies. *Gynecologic Oncology*.
- House et al. (2025). CDK2 inhibitors in ovarian and endometrial tumors. *Cancer Research*.
- Li et al. (2025). DNA methylation in EC risk and therapy. *Frontiers in Oncology*.

---

Thank you for checking out this project!  
Feel free to open an issue or contact me for questions or collaborations.

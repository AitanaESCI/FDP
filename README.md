# Evaluating ML-Based Continuous Predictors for Missense Variant Pathogenicity

A comprehensive evaluation of continuous pathogenicity scores versus established binary classifiers using experimental (DMS) and clinical (ClinVar/Humsavar) datasets.

## Repository structure

```bash
├── README.md
├── environment.yml
├── data/
│   └── ClinHum_ALL_preds_cleaned.csv
├── notebooks/
│   ├── quantitative_preds_remaining.ipynb
│   ├── preanalysis.ipynb
│   ├── block1_part1_analysis.ipynb
│   ├── block1_part2_analysis.ipynb
│   ├── block2_analysis.ipynb
│   └── block3_analysis.ipynb
├── results/
│   ├── figures/
│   └── tables/
└── supplement/
    └── Supplementary_Materials.pdf
```

## Overview

This project benchmarks five continuous predictors (CADD, MetaRNN, Envision, QAFI, EVE) against four binary classifiers (AlphaMissense, BayesDel, REVEL, VEST4). Analyses include:

- Correlation with DMS functional scores  
- ROC-based clinical discrimination on ∼47,000 ClinVar/Humsavar variants  
- Platt-scaling calibration and threshold optimization  
- Mapping to ACMG/AMP evidence categories ([Pejaver et al. (2022)](https://pmc.ncbi.nlm.nih.gov/articles/PMC9748256/) workflow)

## Data preprocessing

- **ClinVar and Humsavar cleaning**  
  Preprocessing notebooks and raw data are maintained in separate repositories:  
  - [ClinVar Data Cleaning repo](https://github.com/AitanaESCI/clinvar_data_cleaning)
  - [Humsavar Data Cleaning repo](https://github.com/AitanaESCI/humsavar_data_cleaning)
 
  Each contains detailed Zenodo links for the source datasets.  

- **Quantitative predictor merge**  
  Precomputed scores for tools not available via VEP are processed in `data/quantitative_preds_remaining/`.  

- **Merged clinical dataset**  
  `data/ClinHum_ALL_preds_cleaned.csv` contains all filtered variants with raw and calibrated scores.

- **DMS data**  
  Residue-level functional scores were extracted from [Beltran et al. (2025)](https://www.nature.com/articles/s41586-024-08370-4). See their publication for raw data access; processed inputs are not stored here.

## Environment setup

```bash
conda env create -f environment.yml && conda activate <env-name>
```

## Running the analysis

Execute the notebooks in order:

- `preanalysis.ipynb`
- `block1_part1_analysis.ipynb`
- `block1_part2_analysis.ipynb`
- `block2_analysis.ipynb`
- `block3_analysis.ipynb`

Each notebook reads from `data/ClinHum_ALL_preds_cleaned.csv` and outputs figures into `results/figures/` and tables into `results/tables/`.

## Results

Final figures and tables for the manuscript are stored under `results/figures/` and `results/tables/`. Supplementary materials (additional tables, KDE plots, Brier scores, etc.) are in the same folders, labeled with “S” prefixes.


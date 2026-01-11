# pd-scrna-seq-analysis

# Single-Cell RNA-seq Analysis for Parkinson's Disease Biomarker Discovery

## Project Overview

This repository showcases a computational biology workflow for discovering peripheral blood biomarkers in Parkinson's Disease (PD) using single-cell RNA sequencing (scRNA-seq) analysis. Rather than replicating published analyses, this project applies machine learning approaches to identify cell populations and gene signatures with diagnostic and prognostic potential.

## Biological Context

**Parkinson's Disease (PD)** is the second most common neurodegenerative disorder worldwide, affecting over 6 million people. While PD is characterized by motor symptoms resulting from dopaminergic neuron loss in the substantia nigra, peripheral immune dysregulation plays a crucial role in disease pathogenesis and progression.

**Key Challenge:** Current PD diagnosis relies primarily on clinical assessment of motor symptoms, which emerge only after ~60-80% of dopaminergic neurons are already lost. There is an urgent need for early-stage, accessible biomarkers.

**Why Peripheral Blood?** Unlike brain tissue, peripheral blood mononuclear cells (PBMCs) provide:
- Non-invasive, clinically accessible sampling
- Dynamic immune signatures reflecting disease state
- Potential for longitudinal monitoring and treatment response assessment

## Dataset

**Source:** [GSE223138](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE223138)  
**Publication:** [npj Parkinson's Disease (2024)](https://www.nature.com/articles/s41531-024-00790-3)

**Original Study Findings:**
- scRNA-seq profiling of PBMCs from PD-Early (HY stages I-II), PD-Late (HY stages III-IV), and healthy controls
- Identified NK cell depletion correlating with PD progression
- Discovered XCL2 as a potential severity biomarker
- Demonstrated peripheral-CNS communication through NK cell infiltration

**This Project's Focus:**
Rather than replicating the published analysis, this project extends the work by:
1. Systematically identifying cell populations with the most informative transcriptional signatures
2. Applying machine learning methods for feature selection and biomarker discovery
3. Building predictive models to distinguish PD stages based on cellular transcriptomes
4. Validating findings through multiple analytical approaches

## Repository Structure
```
├── notebooks/
│   ├── 01_quality_control_preprocessing.ipynb    # Data QC, filtering, normalization
│   ├── 02_dimensionality_reduction_clustering.ipynb  # Cell type identification
│   ├── 03_cell_type_annotation.ipynb             # Biological annotation & validation
│   └── 04_biomarker_discovery_ML.ipynb           # ML-based feature selection & modeling
├── figures/                                       # Output visualizations
├── data/                                          # Data directory (excluded from repo)
│   ├── raw/                                       # Raw count matrices
│   └── processed/                                 # Filtered/normalized objects
├── src/                                           # Helper functions (optional)
│   └── utils.py
├── environment.yml                                # Conda environment specification
├── requirements.txt                               # Python package dependencies
├── .gitignore
└── README.md
```

## Analysis Workflow

### Part 1: Quality Control & Preprocessing
- Raw data inspection and quality metric calculation
- Cell and gene filtering with biological justification
- Normalization and batch effect assessment
- Highly variable gene selection

![Alt text for the image](/figures/01_PreProcessing.png"Optional title for the image")

### Part 2: Dimensionality Reduction & Clustering
- PCA for noise reduction and computational efficiency
- UMAP visualization of cellular heterogeneity
- Graph-based clustering optimization
- Cluster stability and resolution assessment

### Part 3: Cell Type Annotation & Biological Interpretation
- Automated annotation using reference datasets (Celltypist)
- Manual curation using canonical marker genes
- Validation across multiple annotation methods
- Cell type-specific differential expression

### Part 4: Biomarker Discovery & Machine Learning
- Identification of disease-relevant cell populations
- Feature selection using multiple approaches (DEG, LASSO, Random Forest)
- Classification models for PD stage prediction
- Cross-validation and independent cohort validation (if available)
- Pathway enrichment and functional interpretation

## Technical Stack

**Core Analysis:**
- Python 3.9+
- scanpy (scRNA-seq analysis)
- scikit-learn (machine learning)
- pandas, numpy (data manipulation)

**Visualization:**
- matplotlib, seaborn
- plotly (interactive plots)

**Environment Management:**
- Conda/Mamba (recommended)
- Full environment specification in `environment.yml`

## Installation & Usage

### Data Access

The raw data from GSE223138 can be downloaded from GEO:
```bash
# Instructions for downloading from GEO
# Place downloaded files in data/raw/
```

### Running Analysis

Notebooks are designed to be executed sequentially:
```bash
jupyter lab
# Open and run notebooks in order: 01 → 02 → 03 → 04
```

## Key Objectives & Learning Outcomes

This project demonstrates proficiency in:

**Computational Biology:**
- Single-cell RNA-seq data processing and quality control
- Batch effect correction and data integration
- Cell type annotation and validation strategies
- Differential expression analysis

**Machine Learning:**
- Feature engineering for high-dimensional transcriptomic data
- Model selection and hyperparameter optimization
- Cross-validation strategies for limited sample sizes
- Interpretable ML for biological discovery

## References

1. [Insert GSE223138 publication citation]
2. [Insert relevant methodological papers you follow]

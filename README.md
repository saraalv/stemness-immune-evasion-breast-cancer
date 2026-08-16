# Stemness and Immune Evasion in Breast Cancer

## A machine learning and gene signature-based approach

This repository contains the computational analysis developed as part
of my Master's Thesis in Bioinformatics and Biostatistics.

The project investigates the interaction between **cancer stemness**
and **immune evasion** in breast cancer using bulk RNA-seq data,
gene signatures, co-expression network analysis and machine learning.

The analysis combines **WGCNA**, **Random Forest** and
**Gene Ontology enrichment** to identify molecular patterns and
genes associated with the interaction between these two biological
processes.

---

## Overview

Tumour progression and metastasis are associated with the acquisition
of biological properties that allow cancer cells to survive in new
environments and evade immune control.

Two important characteristics are:

- **Stemness** — the acquisition of stem-cell-like properties that
  can contribute to tumour progression, resistance and metastasis.
- **Immune evasion** — the ability of tumour cells to avoid or
  suppress anti-tumour immune responses.

Increasing evidence suggests that these processes may interact and
reinforce each other. However, their molecular relationship remains
insufficiently characterised.

This project investigates this interaction at the transcriptomic
level using publicly available breast cancer RNA-seq datasets.

---

## Research question

> **Can transcriptomic profiles be used to characterise the
> interaction between stemness and immune evasion in breast cancer?**

The analysis aims to identify co-expression patterns and genes that
are particularly informative about this interaction and to determine
whether these patterns are consistent across different breast cancer
datasets.

---

## Objectives

The main objectives of the project are:

- Characterise stemness and immune evasion gene signatures in breast
  cancer.
- Analyse the expression of these signatures across tumour samples.
- Identify modules of co-expressed genes using WGCNA.
- Investigate associations between co-expression modules and the
  biological signatures of interest.
- Identify genes that are informative of the interaction between
  stemness and immune evasion.
- Apply machine learning to evaluate the predictive capacity of the
  identified gene sets.
- Compare the results across independent breast cancer datasets.
- Perform functional enrichment analysis to interpret the biological
  relevance of the selected genes.

---

## Datasets

The project uses bulk RNA-seq data from two publicly available
resources:

### The Cancer Genome Atlas (TCGA)

TCGA provides large-scale molecular data from multiple cancer types and is used in this project as one of the main breast cancer transcriptomic datasets.

### AURORA US

AURORA US is a breast cancer research initiative focused on understanding tumour metastasis.

The project analyses:

- AURORA primary breast tumours
- AURORA metastatic breast tumours

Using multiple datasets allows the identified molecular patterns to be investigated across different tumour contexts.

---

## Gene signatures

The analysis uses previously published gene signatures to represent the biological processes of interest.

These signatures provide a way of quantifying the transcriptional state of individual samples with respect to:

- Stemness
- Immune evasion / immune-related activity

Gene expression scores are subsequently used to investigate their relationships with co-expression modules.

---

# Methodology

The analysis follows a multi-stage computational workflow.

```text
Public RNA-seq datasets
          │
          ▼
     Data filtering
          │
          ▼
 Gene expression analysis
          │
          ├── Stemness signature
          └── Immune evasion signature
          │
          ▼
      WGCNA analysis
          │
          ▼
 Co-expression modules
          │
          ▼
Module–signature associations
          │
          ▼
 Identification of relevant modules
          │
          ▼
      Random Forest
          │
          ▼
 Informative gene selection
          │
          ▼
    Model evaluation
          │
          ▼
 Gene Ontology enrichment
          │
          ▼
 Biological interpretation
```
---

## 1. Data preprocessing 
Before constructing the co-expression networks, the RNA-seq datasets are inspected and filtered.

The preprocessing workflow includes:

- Quality control.
- Detection of atypical samples.
- Hierarchical clustering.
- Principal Component Analysis.
- Removal of outlier samples.
- Selection of appropriate expression data for downstream analysis.

The filtering procedure is applied independently to the TCGA and AURORA datasets.

---

## 2. Gene expression signatures
Published gene signatures are used to quantify the biological
processes of interest.

For each sample, gene expression scores are calculated to represent
the activity of the corresponding signatures.

These scores are subsequently used to investigate associations
between biological processes and co-expression modules.

---

## 3. Weighted Gene Co-expression Network Analysis

**Weighted Gene Co-expression Network Analysis (WGCNA)** is used to
construct gene co-expression networks.

The objective is to identify groups of genes with similar expression
patterns across tumour samples.

The analysis includes:

- Selection of the soft-thresholding power.
- Network construction.
- Hierarchical clustering.
- Module identification.
- Module eigengene calculation.
- Module–trait relationships.

The resulting modules are evaluated according to their association
with the stemness and immune-related signatures.

---

## 4. Identification of relevant modules

The WGCNA results are used to identify modules associated with the
biological processes under study.

Particular attention is given to modules showing relevant
relationships with:

- Stemness.
- Immune evasion.
- The interaction between both processes.

The selected modules are subsequently characterised in greater
detail.

---

## 5. Machine learning

Machine learning is applied to identify the genes that contribute
most strongly to the classification of samples according to their
functional profiles.

**Random Forest** models are trained using genes from the selected
co-expression modules.

The models are evaluated according to their predictive performance
and used to identify the most informative genes.

This feature-selection step reduces the gene sets to a smaller
number of candidates with greater relevance for the biological
question.

---

## 6. Gene Ontology enrichment 

The genes identified as most informative by the Random Forest models
are analysed using **Gene Ontology (GO) enrichment**.

The objective is to determine which biological processes and
functional categories are over-represented among the selected genes.

The enrichment analysis identifies biological pathways related to
processes including:

- Immune signalling.
- Cell differentiation.
- Cellular regulation.
- Tumour-related biological processes.

---

## Results

The analysis identifies co-expression modules associated with the
biological signatures of interest.

The WGCNA analysis reveals modules showing relationships with
stemness and immune-related transcriptional profiles.

The machine learning analysis subsequently identifies genes that
are particularly informative for distinguishing samples according to
their functional profiles.

The selected genes show enrichment in biologically relevant
processes, particularly those associated with **immune signalling**
and **cell differentiation**.

The results provide evidence supporting the existence of a molecular
relationship between stemness and immune evasion in breast cancer.

---

## Visualisations

The project includes several visualisation approaches, including:

PCA plots for sample quality assessment.
Hierarchical clustering dendrograms.
WGCNA module dendrograms.
Module–signature relationship plots.
Gene Ontology enrichment plots.
Machine learning performance visualisations.

Example:
![WGCNA modules](figures/wgcna_modules.png)

---

## Technologies

### Programming

- **R**

### Transcriptomics

- Bulk RNA-seq
- Gene expression analysis
- Gene signatures

### Network analysis

- **WGCNA**
- Weighted gene co-expression networks

### Machine learning

- **Random Forest**
- Feature selection
- Classification
- Model evaluation

### Functional analysis
- Gene Ontology enrichment
- Biological pathway interpretation

### Data analysis
- Principal Component Analysis
- Hierarchical clustering
- Correlation analysis
- Data visualisation

---
## Repository structure

```text
stemness-immune-evasion-breast-cancer/
│
├── README.md
├── .gitattributes
│
├── Rawdata/
│   ├── tcga_rawdata1.RData
│   ├── tcga_data.RData
│   ├── GSE209998_AUR_129_raw_counts.txt
│   ├── clindata_aurora.csv
│   └── aurora_data.RData
│
├── firmas/
│   ├── firmasgenicas.csv
│   └── firmasgenicas_met.csv
│
├── Data/
│
├── codigo/
│   ├── Preparacion del dataset.R
│   ├── Normalizacion.R
│   ├── preparacion firmas.R
│   ├── Red de coexpresion TCGA.R
│   ├── Red de coexpresion AURORA.R
│   ├── RandomForest_TCGA.R
│   ├── RandomForest_AURORA.R
│   └── analisis enriquecimiento GO.R
│
└── figuras/
    ├── Preparacion_Data/
    ├── Redes_coexpresion/
    │   ├── AURORA_metastasis/
    │   │   └── modulos_interes/
    │   ├── AURORA_primarios/
    │   │   └── modulos_interes/
    │   └── tcga/
    │      └── modulos_interes/
    ├── modelos_random_forest/
    │   ├── AURORA_metastasis/
    │   ├── AURORA_primarios/
    │   └── tcga/
    └── analisis_enriquecimiento_GO/

```

---

## Reproducibility

The main analysis was developed in **R**.

The workflow is organised into several stages:

1. Data acquisition and preprocessing.
2. Sample quality control.
3. Gene signature calculation.
4. WGCNA network construction.
5. Module identification.
6. Module–signature association analysis.
7. Random Forest modelling.
8. Informative gene selection.
9. Gene Ontology enrichment.
10. Biological interpretation.

The complete workflow can be reproduced using the R scripts included in this repository.

---

## Skills demonstrated

### Bioinformatics
- Bulk RNA-seq analysis
- Gene expression analysis
- Gene signatures
- Co-expression networks
- WGCNA
- Functional enrichment
### Machine Learning
- Random Forest
- Feature selection
- Classification
- Model evaluation
### Data Science
- High-dimensional data analysis
- Dimensionality reduction
- Hierarchical clustering
- Network analysis
- Data visualisation
### Cancer research
- Breast cancer
- Cancer stemness
- Immune evasion
- Tumour heterogeneity
- Molecular profiling

---

## Academic context 

This project was developed as part of my **Master's Thesis** in the
**Master's Degree in Bioinformatics and Biostatistics**, within the
area of Omics Data Analysis.

**Title:**
> *Interaction between stemness and immune evasion in breast cancer:
> a machine learning and gene signature-based approach.*

**Author:** Sara Álvarez Estévez

**Supervisor:** Helena Brunel Montaner

**Year:** 2025

---

## Author

**Sara Álvarez Estévez**
- GitHub: https://github.com/saraalv
- LinkedIn: [www.linkedin.com/in/saraalvarezestevez]

---

## License

This project is licensed under a
Creative Commons Attribution-NonCommercial-NoDerivatives 3.0 Spain
license, in accordance with the original Master's Thesis.

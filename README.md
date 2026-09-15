# A Synthetic Dermatology miRNA Analysis

> This repository contains synthetic data only. Every record and result was generated from random distributions. Nothing here comes from a patient, hospital, thesis dataset, or clinical study.

This project is a public teaching version of a clinical qPCR workflow. It shows how I approach data validation, ΔCq analysis, reference stability, multiple testing, clinical subgroups, adjusted association models, ROC analysis, sensitivity checks, and reproducible reporting.

The numerical results have no medical or diagnostic meaning. The workflow is the project.

![Analysis workflow](assets/analysis-workflow.svg)

## What is included

- One detailed and fully executed Jupyter notebook
- A generated cohort of 320 synthetic records
- Fourteen analysis tables
- Ten blog-ready figures
- Fourteen rendered table images
- A machine-readable session record
- Five English blog drafts with placement notes and captions

## Start with the notebook

[Open the complete notebook](notebooks/synthetic_dermatology_mirna_case_study.ipynb)

The notebook generates the dataset from a fixed random seed. It then runs the full analysis from beginning to end.

## Analysis map

| Section | What it demonstrates |
|---|---|
| Synthetic cohort | Reproducible generation of demographic, dermatology, and qPCR variables |
| Validation | Required columns, unique IDs, expected missingness, and QC flags |
| Demographics | Continuous and categorical group summaries |
| Clinical profile | Descriptive summaries for synthetic acne records |
| Reference check | A stable reference and a deliberately unstable teaching example |
| Primary analysis | ΔCq comparisons, effect sizes, bootstrap intervals, and FDR control |
| Clinical relationships | Spearman correlations with severity and other clinical measures |
| Subgroups | Exploratory comparisons with family-wise FDR control |
| Adjusted models | Associations with case status after demographic adjustment |
| ROC analysis | Out-of-fold predictions from stratified five-fold cross-validation |
| Sensitivity | Full sample, QC-pass sample, and synthetic female-only sample |
| Co-expression | Group-specific Spearman coefficients and a direct bootstrap difference |
| Power planning | Prospective sample sizes under several assumed effect sizes |

## A synthetic result snapshot

The simulation was designed to contain a visible group signal. It is useful for checking that the workflow behaves as expected.

| Synthetic result | Estimate |
|---|---:|
| miR-25-3p cross-validated AUC | 0.72 |
| miR-143-3p cross-validated AUC | 0.77 |
| Two-miRNA cross-validated AUC | 0.77 |
| Direct difference in co-expression rho | 0.04 |
| Co-expression permutation p-value | 0.58 |

The deliberately unstable reference reverses the apparent direction of both target comparisons. This is intentional. It shows why reference stability should be checked before interpreting ΔCq.

## Selected figures

The full set is organized inside the five [blog post folders](blog-series/README.md).

### Synthetic cohort characteristics

![Synthetic cohort characteristics](figures/00_synthetic_demographic_balance.png)

### Primary synthetic comparison

![Synthetic primary expression comparison](figures/01_synthetic_primary_expression.png)

### Clinical correlations

![Synthetic clinical correlations](figures/02_synthetic_clinical_correlations.png)

### Subgroup estimates

![Synthetic subgroup forest plot](figures/03_synthetic_subgroup_forest.png)

### Cross-validated ROC curves

![Synthetic cross-validated ROC curves](figures/04_synthetic_cross_validated_roc.png)

### Within-group co-expression

![Synthetic within-group co-expression](figures/05_synthetic_coexpression.png)

## Run locally

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

Open `notebooks/synthetic_dermatology_mirna_case_study.ipynb` and run all cells.

All generated files are deterministic when the package versions and seed remain unchanged.

## Repository structure

```text
.
├── README.md
├── requirements.txt
├── assets/
│   └── analysis-workflow.svg
├── blog-series/
│   ├── asset-manifest.csv
│   ├── part-1/
│   ├── part-2/
│   ├── part-3/
│   ├── part-4/
│   └── part-5/
├── data/
│   ├── README.md
│   └── synthetic_mirna_cohort.csv
├── figures/
├── notebooks/
├── tables/
└── session.json
```

## Research and privacy note

This repository was designed so that it can be public without releasing protected study data. Synthetic IDs such as `SYN0001` do not refer to real people. The distributions are educational choices and should not be read as prevalence estimates.

The code is not a medical device. The results should not guide diagnosis, treatment, or research conclusions about acne vulgaris or miRNA biology.

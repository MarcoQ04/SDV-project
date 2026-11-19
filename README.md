# TCGA-BRCA: Gene Expression Analysis

This project explores breast cancer gene-expression profiles from the TCGA-BRCA PanCancer Atlas. It has two main parts: an exploratory analysis of immune-related expression patterns and a classification of molecular subtypes.

**Authors:** Alessia Tranquilli, Marco Quartu

## Dataset

The analysis uses the [Breast Invasive Carcinoma, TCGA PanCancer Atlas study on cBioPortal](https://www.cbioportal.org/study/summary?id=brca_tcga_pan_can_atlas_2018). It includes 1,082 samples with expression profiles, of which 981 have a known molecular subtype. After excluding rows with ambiguous gene identifiers, 20,481 gene features remain.

The analysis is organized in three notebooks:

## [01 — Data and preparation](notebooks/01_dati_e_preparazione.ipynb)

Introduces the dataset and checks how expression profiles, samples and patients are matched. It describes the cohort through subtype, age, pathological stage, recorded vital status and observation time.

The notebook also checks the expression matrix, removes ambiguous gene identifiers and applies the `log2(1 + RSEM)` transformation..

## [02 — ICR gene clustering](notebooks/02_clustering_icr.ipynb)

Looks for groups of samples with similar expression across 20 immune-related ICR genes. It compares K-means solutions using the elbow rule, then examines three groups with low, intermediate and high relative ICR expression.

The results are shown through a UMAP projection, gene-expression heatmap and comparisons with known molecular subtypes. Subtype labels are used for interpretation after clustering.

## [03 — Molecular subtype classification](notebooks/03_classificazione_sottotipi.ipynb)

Uses gene expression to predict five known molecular subtypes. The notebook compares different numbers of genes selected by ANOVA and different regularization settings for multiclass logistic regression. Selection and scaling are fitted within the training folds.

It presents training and validation loss, out-of-fold metrics, test results, model coefficients and predicted probabilities.

# Single-Cell RNA Sequencing Analysis of *Pleurodeles* 🧬

This repository contains a complete computational pipeline for analyzing single-cell RNA sequencing (scRNA-seq) data from *Pleurodeles*. The workflow covers everything from raw data quality control to the identification of distinct cellular populations and differential expression analysis.

## 🚀 Key Features
* **Quality Control (QC):** Implementation of Knee-plot algorithms to distinguish valid droplets from ambient RNA noise.
* **Dimensionality Reduction:** Comparative analysis using PCA, UMAP, and t-SNE to capture both global and local transcriptomic structures.
* **Cell Annotation:** Identification of 17 distinct clusters including GABAergic neurons, astrocytes, and microglia using a hybrid approach of prior biological knowledge and unbiased marker discovery.
* **Advanced Statistical Validation:** * **Bootstrap Clustering:** Evaluation of cluster stability using 1,000 iterations.
  * **Pseudobulk DE Analysis:** Differential expression testing between excitatory and inhibitory neurons using the **DESeq2** framework.

---

## 🛠 Analysis Workflow

### 1. Data Preprocessing & Filtering
* **Knee Plot:** Used to identify the inflection point of UMI counts to exclude low-quality cells.
* **Mitochondrial QC:** Filtered out cells with high mitochondrial read percentages (up to 60% in raw data) to ensure only healthy cells were analyzed.

### 2. Variable Feature Selection
Identified the top 2000 Highly Variable Genes (HVGs) to focus on biological signals over technical noise. Key variable genes found include:
* **Neurotransmission/Signaling:** *PTGDS*, *TAC1*, *CCK*, *NPY*, *SST*.
* **Structural/Immune:** *C1QB*, *PDGFRA*.

### 3. Clustering and Annotation
Cells were clustered at multiple resolutions (0.1 to 3.0). Major cell types identified at resolution 0.3 include:
| Cluster | Annotated Cell Type | Key Marker Gene |
| :--- | :--- | :--- |
| 0 | GABAergic Neurons | *SHISA8* |
| 2 | Astrocytes | *GJA1* |
| 3 | Excitatory Neurons | *TBR1* |
| 11 | Microglia | *CSF1R* |
| 14 | Oligodendrocytes | *NKX2-2* |

### 4. Transcriptomic Relationships
* **Spearman Correlation:** Generated on pseudobulk aggregated data to assess similarities between cell types.
* **Specificity Index:** Calculated to determine how uniquely genes are expressed within specific lineages.

---

## 💻 Tech Stack
* **Language:** R
* **Primary Framework:** [Seurat v5](https://satijalab.org/seurat/)
* **Differential Expression:** [DESeq2](https://bioconductor.org/packages/release/bioc/html/DESeq2.html)
* **Visualization:** `ggplot2`, `pheatmap`, `ggdendro`

## 📂 Repository Structure
* `Brandon_chua_Report.Rmd`: The main analysis script and report.
* `top_markers_per_cluster.csv`: Output table of identified cluster markers.
* `annotated_seurat_obj.rds`: The final processed and annotated Seurat object.

---
**Author:** Brandon Chua (4745778)  
**Date:** April 2025  
**Project:** Single-Cell Sequencing Report

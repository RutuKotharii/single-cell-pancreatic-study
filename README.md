# Single-Cell RNA-seq Analysis of Pancreatic Tissue (Seurat + Monocle3 + CellChat)

This repository contains a full single-cell RNA-seq (scRNA-seq) analysis pipeline implemented in R using [Seurat](https://satijalab.org/seurat/), [Monocle3](https://cole-trapnell-lab.github.io/monocle3/), and [CellChat](https://github.com/sqjin/CellChat). It processes publicly available scRNA-seq data to explore tumor microenvironment composition, cell type dynamics, and cell–cell communication.

## Contents

- `scRNAseq_analysis.Rmd` – RMarkdown script containing the full pipeline
- `scRNAseq_analysis.html` – Rendered HTML report with figures and discussion
- `README.md` – Project overview

## Dataset

Data used is from a published study:

> Chan-Seng-Yue, M., et al. (2020). *Transcriptional and epigenomic fidelity of primary human pancreatic cancer cell lines*. Nature Communications, 11, 4084.  
> [Link to Paper](https://www.nature.com/articles/s41467-023-40727-7)

- Format: 10X Genomics output
- Includes ≥ 4 samples across conditions: normal, primary tumor, metastasis

## Analysis Overview

### 1. **Preprocessing & QC**
- Sample-wise Seurat objects
- Mitochondrial content calculation
- Violin + scatter plots for QC
- Doublet removal using `scDblFinder`

### 2. **Normalization & Feature Selection**
- Log-normalization (`LogNormalize`)
- 2000 highly variable genes (VST method)

### 3. **Dimensionality Reduction & Clustering**
- PCA and ElbowPlot
- UMAP visualization
- Clustering (Louvain, resolution = 0.5)

### 4. **Integration**
- Canonical Correlation Analysis (CCA)
- Correction of batch effects between samples

### 5. **Cell Type Annotation**
- Automated: `SingleR` + Human Primary Cell Atlas
- Manual: Marker-based refinement using literature

### 6. **Downstream Analyses**
- Marker gene discovery
- Pseudotime inference using `Monocle3`
- Cell–cell communication with `CellChat`
- Condition-specific interaction network analysis
  
## Highlight Figures

- Integrated UMAP of annotated cell types
- Top marker genes per cluster (violin plots)
- Pseudotime trajectories across conditions
- CellChat heatmaps showing signaling changes from normal to tumor

## Reproducibility

All code is contained in the RMarkdown file. Software versions used are printed at the end via `sessionInfo()`.

### R version
Tested with:
- R 4.3.x
- Seurat ≥ 4.3
- Monocle3 ≥ 1.3.1
- CellChat ≥ 1.6.0


# Differential-gene-expression
Differential gene expression analysis in R using DESeq2  identifying significantly up/down regulated genes between control and treated samples from RNA-seq count data, with MA plot visualization.

#Differential Gene Expression Analysis using DESeq2

A complete RNA-seq differential gene expression (DGE) analysis pipeline built in R using the **DESeq2** package. This project identifies statistically significant differentially expressed genes (DEGs) between **control and treated** human samples using publicly available RNA-seq count data, and visualizes the results through an **MA Plot**.


##Background

Differential gene expression analysis is a fundamental step in understanding how genes respond to biological conditions such as drug treatments, disease states, or environmental changes. This pipeline uses **DESeq2**, one of the most widely used and statistically robust tools for RNA-seq count data analysis, based on a negative binomial distribution model.

The dataset used is **GSE60424**, a publicly available human RNA-seq dataset from the **NCBI GEO database**, aligned to the **GRCh38.p13** human reference genome.


## What It Does

- **Data Loading** — Reads raw RNA-seq count matrix from a `.tsv` file (`GSE60424_raw_counts_GRCh38.p13_NCBI.tsv`)
- **Data Filtering** — Removes low-expression genes with total counts ≤ 10 across all samples to reduce noise
- **Sample Grouping** — Assigns 6 samples into two groups: 3 control and 3 treated
- **DESeq2 Model Fitting** — Constructs a `DESeqDataSet` object and fits the negative binomial model using `~ condition` design
- **Differential Expression Testing** — Runs the DESeq2 statistical pipeline to compute:
  - Log2 Fold Change (LFC)
  - p-values and adjusted p-values (padj)
  - Base mean expression
- **Significance Filtering** — Flags genes as significant if `padj < 0.1`
- **MA Plot Visualization** — Plots mean expression vs log2 fold change, with significant DEGs highlighted in **red**


## Tools & Libraries Used
R Programming - Core scripting language 
DESeq2 - Differential expression statistical analysis 
ggplot2 - MA plot visualization 
tidyverse - Data manipulation and transformation q

## Input

| File | Format | Description |
|------|--------|-------------|
| `GSE60424_raw_counts_GRCh38.p13_NCBI.tsv` | TSV | Raw RNA-seq gene count matrix aligned to GRCh38.p13 |

- **Organism:** Homo sapiens (Human)
- **Reference Genome:** GRCh38.p13 (NCBI)
- **Samples Used:** 6 samples (columns 1–6)
- **Groups:** 3 Control | 3 Treated

---

## Installation

Install all required packages before running the script:

```r
install.packages("BiocManager")
BiocManager::install(c("DESeq2", "airway"))
install.packages(c("tidyverse", "ggplot2", "dplyr"))

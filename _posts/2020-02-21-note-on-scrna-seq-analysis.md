---
title: 'A Brief Note on Single-Cell RNA-Seq Analysis'
date: 2020-02-21
permalink: /blogs/2020/02/note-on-scrna-seq-analysis/
author_profile: false
tags:
  - transcriptomics
  - computational biology
---

A brief note highlighting the workflow of single-cell RNA-seq data analysis.


<p align="center">
    <img src="https://hzmaxwell.github.io/images/scrna-seq.jpg" width="600"/>
</p>


## Contents
- [1. Pre-Processing](#1-pre-processing)
  - [1.1 Quality Control](#11-quality-control)
  - [1.2 Normalization](#12-normalization)
  - [1.3 Data Correction](#13-data-correction)
  - [1.4 Dimensionality Reduction](#14-dimensionality-reduction)
- [2. Downstream Analysis](#2-downstream-analysis)
  - [2.1 Cluster Analysis](#21-cluster-analysis)
  - [2.2 Trajectory Analysis](#22-trajectory-analysis)
  - [2.3 Gene-Level Analysis](#23-gene-level-analysis)
- [References](#references)

## 1. Pre-Processing

**Goal**:
- To pre-process the scRNA-seq count matrices so as to obtain different levels of pre-processed data for different downstream analyses


### 1.1 Quality Control

**Goal**:
- To remove outlier barcode data produced by dying cells, broken cells, doublets, etc.

**Covariates used for thresholding**:
- the number of counts per barcode (count depth)
- the number of genes per barcode
- the fraction of counts from mitochondrial genes per barcode

**Notes**:
- Consider all covariates jointly
- Revisit QC if downstream analysis is not satisfactory
- Adjust QC thresholds for different samples if necessary

<div style="text-align: right">[<a href="#contents">back to top</a>]</div>

### 1.2 Normalization

**Goal**:
- To remove unwanted technical variation coming from count sampling

**Notes**:
- It's more common to normalize the count data by cells than by genes
- Normalized data should be `$\log(x+1)$`-transformed for downstream analysis that assumes data are normally distributed
- Quality-controlled or normalized data can also be used for statistical testing of gene expression

<div style="text-align: right">[<a href="#contents">back to top</a>]</div>

### 1.3 Data Correction

**Goal**:
- To further remove unwanted technical and biological variation

**Source of variation**:
- technical effects
  - count depth
  - batch
    - between cell groups in an experiment (solution: batch correction)
    - between experiments in a laboratory (solution: data integration)
    - between datasets from different laboratories (solution: data integration)
  - dropout (solution: imputation/denoising/expression recovery)
- biological effects
  - cell cycle
  - mitochondrial gene expression

**Notes**:
- Corrected data can also be used for visual comparison of gene expression 


<div style="text-align: right">[<a href="#contents">back to top</a>]</div>


### 1.4 Dimensionality Reduction

**Goal**:
- To summarize and visualize the data in order to make downstream analysis computationally easier and more intuitive

#### Notes:
- Typically 1,000 to 5,000 highly variable genes are firstly selected via feature selection
- The feature number is further reduced by dedicated dimensionality reduction algorithms
- Dimensionality reduction methods should be considered separately for summarization and visualization


<div style="text-align: right">[<a href="#contents">back to top</a>]</div>

## 2. Downstream Analysis

**Goal**:
- To extract biological insights and describe the underlying biological system

### 2.1 Cluster Analysis

**Goal**:
- To explain the heterogeneity in the data based on a categorization of cells into groups

**Methods**:
- **Clustering**: to organize cells into clusters
- **Compositional analysis**: to analyse clustered data in terms of the proportions of cells that fall into each cell-identity cluster
- **Cluster annotation**: to find marker genes to characterize each cluster and annotate it with a meaningful biological label


<div style="text-align: right">[<a href="#contents">back to top</a>]</div>


### 2.2 Trajectory Analysis 

**Goal**:
- To regard the data as a snapshot of a dynamic process and investigate this underlying process
- By representing the clusters as nodes and the in-between trajectories as edges, one can represent both the static and dynamic nature of the data

**Methods**:
- **Trajectory inference**: to capture transitions between cell identities, branching differentiation processes, or gradual, unsynchronized changes in biological function
- **Metastable states identification**: to investigate cellular densities along a trajectory, and find dense regions which may represent metastable transcriptomic states
- **Gene expression dynamics**: to model the genes that vary smoothly across pseudotime in order to characterize the trajectory and identify the underlying biological process


<div style="text-align: right">[<a href="#contents">back to top</a>]</div>


### 2.3 Gene-Level Analysis

**Goal**:
- Rather than describing the cellular heterogeneity, gene-level analysis uses this heterogeneity as context in which gene expression is to be understood

**Methods**:
- **Differential expression analysis**: to investigate whether any genes are differentially expressed under different experimental conditions
- **Gene-set (pathway) analysis**: to facilitate the interpretation of long candidate gene lists by grouping the genes into sets based on shared characteristics and testing whether these characteristics are overrepresented in the list
- **Gene regulatory network inference**: to uncover the regulatory interactions among different genes and small molecules


<div style="text-align: right">[<a href="#contents">back to top</a>]</div>





## References


1. Current best practices in single-cell RNA-seq analysis: a tutorial. MD Luecken, FJ Theis. *Molecular systems biology*, 2019
2. Computational Methods for Single-Cell Data Analysis. GC Yuan. *Springer*, 2019
3. Orchestrating single-cell analysis with Bioconductor. RA Amezquita, et al. *Nature methods*, 2019
4. Single-cell RNA sequencing technologies and bioinformatics pipelines. B Hwang, JH Lee, D Bang. *Experimental & molecular medicine*, 2018



<div style="text-align: right">[<a href="#contents">back to top</a>]</div>





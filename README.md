# 🧬 SysBio-DiseaseNetwork
### Comparative Systems Biology Analysis of Alzheimer's Disease, Type 2 Diabetes, and NAFLD

This project performs a comprehensive systems-level analysis to uncover shared and disease-specific protein-protein interaction (PPI) networks among **Alzheimer's Disease (AD)**, **Type 2 Diabetes (T2D)**, and **Non-Alcoholic Fatty Liver Disease (NAFLD)**. Leveraging disease-gene associations from **DisGeNET**, PPI data from **STRING**, and network analytics via **NetworkX**, the study identifies key hub-bottleneck genes and shared genetic mechanisms underlying neurodegeneration and metabolic dysfunction.

---

## 📑 Table of Contents
- [1. Project Summary](#1-project-summary)
- [2. Dataset Description](#2-dataset-description)
- [3. Methodology](#3-methodology)
- [4. Key Results](#4-key-results)
- [5. Repository Structure](#5-repository-structure)

---

## 1. Project Summary

Recent findings suggest that **AD**, **T2D**, and **NAFLD** share genetic and molecular pathways. This project explores these overlaps by:

- Extracting disease-specific gene sets from *DisGeNET* (GWAS evidence).
- Building disease-specific PPI networks via the *STRING* database.
- Performing network centrality analysis to detect key regulators.
- Identifying shared hub-bottleneck genes (e.g., **APOE**, **INS**, **LEP**) across conditions.

The goal is to highlight systems-level interactions that may drive comorbid disease progression.

---

## 2. Dataset Description

| Source       | Data Type                     | Description                                  |
|--------------|-------------------------------|----------------------------------------------|
| DisGeNET     | GWAS gene sets                | Curated disease-gene associations            |
| STRING API   | Protein interactions          | High-confidence (score > 0.7) PPI data       |
| Cytoscape/NetworkX | Network analysis         | Graph construction and centrality analysis   |

---

## 3. Methodology

### 🧩 Step 1: Data Acquisition
- Download GWAS-based gene lists from DisGeNET for each disease.
- Identify overlapping genes between diseases.

### 🔗 Step 2: Network Construction
- Query STRING API to retrieve PPIs for each gene set.
- Construct directed graphs using NetworkX.

### 🧠 Step 3: Topological Analysis
- Calculate **degree**, **betweenness**, and **closeness centralities**.
- Detect **hub** (top-degree) and **bottleneck** (high-betweenness) proteins.
- Evaluate clustering coefficients and connected components.

### 🔍 Step 4: Disease Intersection
- Perform Venn-style analysis of gene overlap.
- Analyze intersections: AD-T2D, AD-NAFLD, T2D-NAFLD, and all three.

---

## 4. Key Results

| Disease   | Top Hub-Bottleneck Genes      | Insights                                     |
|-----------|-------------------------------|----------------------------------------------|
| AD        | APOE, APP, SRC                | Neurodegeneration-related regulators         |
| T2D       | INS, APOE                     | Metabolic control and shared node (APOE)     |
| NAFLD     | LEP                           | Hormonal control of lipid/glucose metabolism |
| Shared    | APOE, LEP                     | Suggests convergent pathogenic mechanisms    |

> 🧠 **Conclusion:** APOE is a central multi-disease hub gene. NAFLD displayed fewer shared nodes due to its limited GWAS gene set.

---

## 5. Repository Structure

```bash
SysBio-DiseaseNetwork/
├── data/ # Gene lists and overlaps
│ ├── alz_genes.tsv
│ ├── t2d_genes.tsv
│ ├── nafld_genes.tsv
│ ├── shared_AD_T2D_NAFLD.tsv
│ ├── shared_AD_NAFLD.tsv
│ └── shared_T2D_NAFLD.tsv
├── notebooks/ # Interactive Jupyter Notebooks
│ ├── gwas_gene_extraction.ipynb
│ └── network_analysis.ipynb
├── scripts/ # Automation Scripts
│ └── string_network_pipeline.py
├── LICENSE
└── README.md


📬 Contact
Isarar Siddique
📧 isararsiddique@gmail.com
🌐 LinkedIn | ORCID

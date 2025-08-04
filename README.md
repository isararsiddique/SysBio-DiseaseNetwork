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
- [6. Installation & Requirements](#6-installation--requirements)
- [7. Usage Guide](#7-usage-guide)
- [8. Outputs](#8-outputs)
- [9. References](#9-references)
- [10. License](#10-license)

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


## 6. Installation & Requirements

### ✅ Requirements

Install dependencies with:

```bash
pip install pandas networkx matplotlib gseapy tqdm requests
Or use a virtual environment:

bash
Copy
Edit
python -m venv venv
source venv/bin/activate       # For Linux/macOS
venv\Scripts\activate          # For Windows
pip install -r requirements.txt
7. Usage Guide

⚙️ Run the Full Pipeline

python scripts/string_network_pipeline.py
Edit gene lists inside data/ or modify confidence thresholds in the script as needed.

📓 Run Interactive Notebooks
Launch:

bash
Copy
Edit
jupyter notebook notebooks/network_analysis.ipynb
These notebooks provide step-by-step visualization and centrality-based insights.

8. Outputs
📊 Network Graphs (via Matplotlib)

📄 Tabular Outputs

Top hub/bottleneck genes

Centrality metrics

Overlapping gene lists (TSV)

📈 Visualizations

Degree distributions

Betweenness centrality histograms

Network topology graphs

9. References
Piñero, J., et al. (2020). The DisGeNET knowledge platform for disease genomics: 2019 update. Nucleic Acids Research.

Szklarczyk, D., et al. (2021). STRING v11: protein–protein association networks with increased coverage. Nucleic Acids Research.

Sharma, S., et al. (2021). Systems biology study reveals shared pathways in AD, T2D, and NAFLD. Bioinformatics Reports.

10. License
This repository is licensed under the MIT License. See the LICENSE file for details.


### ✅ Notes:
- You can copy this directly into your `README.md` file.
- Make sure your actual `requirements.txt` file includes all necessary packages.
- Add links or DOIs to the references if you plan to publish or host it on GitHub for broader access.

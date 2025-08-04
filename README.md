# 🧬 SysBio-DiseaseNetwork
### Comparative Systems Biology Analysis of Alzheimer's Disease, Type 2 Diabetes, and NAFLD

This project performs a systems-level analysis to identify shared and unique protein-protein interaction (PPI) networks and hub-bottleneck genes associated with three chronic diseases: Alzheimer's Disease (AD), Type 2 Diabetes (T2D), and Non-Alcoholic Fatty Liver Disease (NAFLD). Using curated disease-gene associations from DisGeNET, STRING PPI data, and Cytoscape-style network analysis in Python, this work reveals key overlapping mechanisms among neurodegeneration and metabolic disorders.

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

Alzheimer’s Disease, T2D, and NAFLD have shown clinical and molecular correlations. Recent evidence suggests that shared genetic components and signaling pathways may underlie these conditions. This project:
- Extracts gene sets using DisGeNET (GWAS-specific evidence).
- Constructs disease-specific PPI networks using STRING (confidence > 0.7).
- Analyzes networks with NetworkX and identifies topological hub-bottlenecks.
- Highlights shared genes (e.g., **APOE**, **INS**, **LEP**) indicating multi-disease relevance.

---

## 2. Dataset Description

| Source       | Data                                  | Description                                   |
|--------------|---------------------------------------|-----------------------------------------------|
| DisGeNET     | `GWAS` filtered gene sets             | Disease-gene associations for AD, T2D, NAFLD  |
| STRING API   | PPI networks                          | High-confidence (>0.7) physical interactions  |
| Cytoscape    | Visual and centrality-based analysis  | Centrality scores, clustering coefficients    |

---

## 3. Methodology

1. **Data Acquisition**
   - Retrieve curated GWAS-based gene sets from DisGeNET for AD, T2D, and NAFLD.
   - Identify overlapping genes between diseases.

2. **Network Construction**
   - Use the STRING API to retrieve PPI data for each gene set.
   - Construct directed graphs using NetworkX.

3. **Topological Analysis**
   - Calculate centrality metrics: degree, betweenness, closeness.
   - Identify hub (top-degree) and bottleneck (high betweenness) proteins.
   - Compute clustering coefficients and connected components.

4. **Gene Set Overlap**
   - Venn-style intersection to identify shared genes across diseases.
   - Specific overlaps: AD-T2D, AD-NAFLD, T2D-NAFLD, AD-T2D-NAFLD.

---

## 4. Key Results

| Disease   | Top Hub-Bottleneck Genes              | Comments                                     |
|-----------|---------------------------------------|----------------------------------------------|
| AD        | APOE, APP, SRC                        | APOE and APP linked to neurodegeneration     |
| T2D       | INS, APOE                             | INS as metabolic regulator, APOE shared      |
| NAFLD     | LEP                                   | LEP regulates lipid and glucose metabolism   |
| Shared    | APOE (AD + T2D), LEP (T2D + NAFLD)     | Indicates common pathophysiological features |

> **Conclusion:** APOE emerged as a critical multi-disease hub gene. NAFLD showed fewer shared nodes due to limited GWAS-validated genes.

---

## 5. Repository Structure

SysBio-DiseaseNetwork/
├── data/ # Input gene sets and shared genes
│ ├── alz_genes.tsv
│ ├── t2d_genes.tsv
│ ├── nafld_genes.tsv
│ ├── shared_AD_T2D_NAFLD.tsv
│ ├── shared_AD_NAFLD.tsv
│ └── shared_T2D_NAFLD.tsv
├── notebooks/ # Interactive Jupyter notebooks
│ ├── network_analysis.ipynb
│ └── gwas_gene_extraction.ipynb
├── scripts/ # Python scripts for pipeline automation
│ └── string_network_pipeline.py
├── README.md # This file
└── LICENSE # MIT license

yaml
Copy
Edit

---

## 6. Installation & Requirements

### ✅ Requirements
Install dependencies using pip:
```bash
pip install pandas networkx matplotlib gseapy tqdm requests
Or create a virtual environment:

bash
Copy
Edit
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate (Windows)
pip install -r requirements.txt
7. Usage Guide
⚙️ Running the Full Pipeline
To run the PPI network analysis:

bash
Copy
Edit
python scripts/string_network_pipeline.py
You may customize the gene list inputs in the data/ folder or edit the script to adjust confidence thresholds.

📓 Interactive Analysis
Open Jupyter notebooks:

bash
Copy
Edit
jupyter notebook notebooks/network_analysis.ipynb
These notebooks allow visualization, annotation, and step-by-step execution.

8. Outputs
Network graphs plotted with matplotlib

Tabular data: hub genes, centrality scores

Gene overlaps across diseases (TSV)

Degree distributions and bottleneck gene lists

Plots include:

Node degree histograms

Betweenness centrality ranks

Network graphs (simplified layouts)

9. References
Piñero, J., et al. (2020). The DisGeNET knowledge platform for disease genomics: 2019 update. Nucleic Acids Research.

Szklarczyk, D., et al. (2021). STRING v11: protein–protein association networks. Nucleic Acids Research.

Sharma, S., et al. (2021). Systems biology study reveals shared pathways in AD, T2D, and NAFLD. Bioinformatics Reports.

10. License
This project is licensed under the MIT License - see the LICENSE file for details.
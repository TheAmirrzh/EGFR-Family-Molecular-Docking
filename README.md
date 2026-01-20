# EGFR Family Molecular Docking Pipeline

![Python](https://img.shields.io/badge/Python-3.14-blue)
![Bioinformatics](https://img.shields.io/badge/Bioinformatics-Molecular%20Docking-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📌 Project Overview
This repository contains a comprehensive bioinformatics pipeline developed to perform blind molecular docking against the kinase domains of the EGFR family. [cite_start]The project investigates the binding potential of natural bioactive compounds compared to established anti-cancer drugs[cite: 1, 4].

[cite_start]The pipeline integrates structural biology, AlphaFold modeling, and molecular docking to analyze binding affinities and interaction patterns [cite: 5-9].

### Biological Context
[cite_start]The EGFR family (ErbB1, ErbB2, ErbB3, ErbB4) plays a central role in cell growth and cancer development [cite: 11-18]. [cite_start]This project targets the kinase domains of these receptors to evaluate potential inhibitors[cite: 19].

## 🎯 Objectives
This automation achieves the specific goals outlined in Task 2 of the project documentation:
1.  [cite_start]**Protein Structure Preparation:** Retrieve experimental structures from PDB and model missing residues using AlphaFold[cite: 103, 134].
2.  [cite_start]**Ligand Preparation:** Prepare drug-like and natural compounds for docking[cite: 104].
3.  [cite_start]**Blind Docking:** Perform unbiased docking simulations to explore binding sites across the entire kinase domain[cite: 105, 173].
4.  [cite_start]**Comparative Analysis:** Evaluate selectivity and potency between natural compounds and FDA-approved drugs[cite: 106, 199].

## 🧪 Methodology

### 1. Structure Preparation
* [cite_start]**Proteins:** Experimental structures (EGFR, ErbB2, ErbB3, ErbB4) were retrieved from the RCSB PDB [cite: 111-116]. [cite_start]Missing structural regions were identified and completed by merging coordinates from AlphaFold predictions [cite: 136-138].
* [cite_start]**Ligands:** Structures for **Curcumin**, **Apigenin**, and **Osimertinib** were retrieved from PubChem[cite: 153]. [cite_start]Preparation included 3D conformation generation, MMFF94 energy minimization, and charge assignment [cite: 157-160].

### 2. Molecular Docking
* **Engine:** AutoDock Vina (v1.2+) via Command Line Interface.
* [cite_start]**Technique:** Blind docking using a grid box covering the full kinase domain with 10Å padding[cite: 175].
* **Conversions:** Automated PDB $\to$ PDBQT conversion using OpenBabel.

### 3. Analysis
* Calculation of binding affinity matrices.
* [cite_start]Evaluation of ligand selectivity scores[cite: 202].
* Generation of heatmaps and comparative bar plots.

## 🛠️ Installation & Prerequisites

This pipeline requires **Python 3.x** and specific bioinformatics system tools.

### System Dependencies (macOS/Linux)
You must install **AutoDock Vina** and **OpenBabel** command-line tools.
```bash
# macOS (via Homebrew)
brew tap brewsci/bio
brew install autodock-vina
brew install open-babel
```
### Python Dependencies
Install the required Python libraries:
```Bash 
pip install numpy pandas matplotlib seaborn biopython rdkit requests
```

### 🚀 Usage
1. Clone the repository:
```bash
git clone [https://github.com/your-username/egfr-docking-pipeline.git](https://github.com/your-username/egfr-docking-pipeline.git)
cd egfr-docking-pipeline
```

2. Run the pipeline:
The entire workflow (Data Retrieval $\to$ Docking $\to$ Analysis) is encapsulated in the main script.
```Bash 
python docking_pipeline.py
```

### 📂 Repository Structure
```Plaintext├── docking_pipeline.py       # Main execution script
├── docking_data/             # Generated output directory
│   ├── proteins/             # Cleaned PDB structures (PDB + PDBQT)
│   ├── ligands/              # Prepared ligand files (PDB + PDBQT)
│   ├── docking_results/      # Vina output logs and poses (.pdbqt)
│   └── analysis/             # Final reports and figures
│       ├── analysis_report.txt
│       ├── binding_heatmap.png
│       ├── binding_affinities.csv
│       └── selectivity_analysis.csv
└── README.md
```
### 📊 Key Results
The pipeline generates a comparative analysis of binding affinities. Below is a summary of the findings based on the simulation:
Ligand,Average Affinity (kcal/mol),Selectivity Profile
Osimertinib,-8.39,Selective (High preference for ErbB4/EGFR)
Apigenin,-8.72,Non-Selective (Strong promiscuous binder)
Curcumin,-7.82,Non-Selective (Moderate promiscuous binder)

Detailed interpretation is available indocking_data/analysis/analysis_report.txt.


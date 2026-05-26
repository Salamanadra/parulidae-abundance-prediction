# Niche Metrics and Population Abundance in New World Warblers (Parulidae)

A Python implementation of ecological niche analysis and phylogenetic generalized least squares (PGLS) modeling for New World Warblers (*Parulidae*), reproducing and extending analyses originally conducted in R.

---

## 🎯 Project Overview

This repository contains reproducible Python code for analyzing the relationship between **ecological niche metrics** (Niche Position and Niche Breadth) and **population abundance** in 47 species of New World Warblers, controlling for phylogenetic non-independence and body mass.

### Key Question

**Does ecological niche structure (position and breadth in environmental space) predict population abundance in Parulidae?**

---

## 📊 Main Findings

### Niche Breadth is the Primary Predictor

- **Mean Abundance (logprom):** Niche Breadth has a significant positive effect (p = 0.002)
  - Generalista species (broad niche) are more abundant
  - Effect size: 0.404 units (standardized)
  
- **Maximum Abundance (logmax):** Weak effect (p = 0.089)
  - Population maxima are less predictable from niche structure
  - R² = 0.204 (weak model)

### Niche Position Does NOT Matter

- No significant relationship between where species are positioned in environmental space and their abundance
- Suggests abundance depends on **niche width**, not **niche location**

### Body Mass (Control)

- No significant allometric effect on abundance
- Mass does not confound the niche-abundance relationship

### Interaction NP × NB

- **Marginally non-significant** (p = 0.107 with HC3 correction)
  - At α = 0.05 threshold: NOT significant
  - At α = 0.10 threshold: WOULD be considered significant
  - Interpretation: Weak evidence that the effect of niche breadth depends on niche position
- Suggests generalism's effect on abundance is largely **independent of niche location**, but with some conditional dependence at relaxed significance levels

---

## 📁 Repository Structure

```
parulidae-abundance-prediction/
│
├── README.md                           # This file
├── .gitignore
├── LICENSE                             # MIT License
│
├── data/
│   ├── raw/                           # Raw data files (from Figshare)
│   │   ├── abundance_db.csv           # Bird abundance from BBS routes
│   │   ├── presence_record.csv        # Cleaned GBIF presences
│   │   ├── input_pgls.csv             # OMI results (47 species)
│   │   ├── input_presences_OMI.csv    # Presences for OMI analysis
│   │   ├── tabla_ambientes_RangoRep.csv  # Environmental variables (breeding range)
│   │   ├── nombres.csv                # Species names
│   │   ├── datos_pvol.csv             # PGLS input data
│   │   └── tree.nwk                   # Phylogenetic tree (Newick format)
│   │
│   └── processed/                     # Processed outputs
│       ├── niche_metrics.csv
│       ├── pca_scores.csv
│       └── pca_loadings.csv
│
├── notebooks/                         # Jupyter notebooks (execute in order)
│   ├── 01_eda_abundancia_nicho.ipynb      # Exploratory Data Analysis
│   ├── 02_niche_metrics.ipynb             # OMI Analysis & PCA
│   └── 03_pgls_analysis.ipynb             # PGLS Regression Analysis
│
└── src/                               # (Optional) Python modules
    ├── __init__.py
    ├── niche_metrics.py               # Niche calculation functions
    └── plotting.py                    # Visualization functions
```

---

## 🔬 Methods

### 1. Niche Analysis (Notebook 02)

**Data:**
- Environmental variables: 3 climatic variables (columns 3, 6, 9 from tabla_ambientes)
- Study area: 81,393 cells covering the breeding range of Parulidae in North America
- Species: 47 species with presence data

**Analysis:**
- Principal Component Analysis (PCA) on standardized environmental data
- Niche Position (NP): mean coordinates in PCA space per species
- Niche Breadth (NB): variance of species occurrences in PCA space
- Pagel's λ = 1.0 (full phylogenetic signal)

### 2. PGLS Regression Analysis (Notebook 03)

**Response Variables:**
- `logprom`: log-transformed mean population abundance
- `logmax`: log-transformed maximum population abundance

**Predictors:**
- NP (Niche Position, standardized)
- NB (Niche Breadth, standardized)
- Masa (Body Mass, standardized) — control variable
- NP × NB (interaction term)

**Statistical Method:**
- Weighted Least Squares (WLS) with heterocedasticity-robust standard errors (HC3)
- Weights: log(n) × Distri
  - `n`: number of sampling records per species
  - `Distri`: percentage of breeding range within study area
- Phylogenetic tree: 47 species Newick format

**Model Selection:**
- Tested correlation structures: Brownian motion, Pagel's λ, Martins
- Selected: Pagel's λ for parameter estimation

---

## 📈 Results Summary

### Model 1: log(Mean Abundance)

```
R² = 0.392 (explains 39% of variance)
F-statistic = 5.603, p = 0.00105

Coefficients (standardized):
  NP:       0.056 (p = 0.673) — NOT significant
  NB:       0.404 (p = 0.002) — SIGNIFICANT ***
  Masa:     0.014 (p = 0.901) — NOT significant
  NP×NB:    0.200 (p = 0.107) — NOT robust
```

### Model 2: log(Maximum Abundance)

```
R² = 0.204 (explains 20% of variance)
F-statistic = 1.471, p = 0.228 — NOT significant

Coefficients (standardized):
  NP:       -0.026 (p = 0.888) — NOT significant
  NB:        0.368 (p = 0.089) — MARGINAL
  Masa:      0.010 (p = 0.962) — NOT significant
  NP×NB:     0.025 (p = 0.881) — NOT significant
```

---

## 🚀 How to Run

### Requirements

```bash
Python 3.8+
pandas, numpy, scikit-learn, scipy, matplotlib, seaborn, statsmodels, biopython
```

### Installation

```bash
# Clone repository
git clone https://github.com/Salamanadra/parulidae-abundance-prediction.git
cd parulidae-abundance-prediction

# Create environment
conda create -n parulidae python=3.10
conda activate parulidae

# Install dependencies
pip install pandas numpy scikit-learn scipy matplotlib seaborn statsmodels biopython
```

### Execute Notebooks

```bash
# Open Jupyter
jupyter notebook

# Execute in order:
# 1. notebooks/01_eda_abundancia_nicho.ipynb
# 2. notebooks/02_niche_metrics.ipynb
# 3. notebooks/03_pgls_analysis.ipynb
```

---

## 📚 Original Research

This analysis reproduces and extends ecological niche modeling originally published in:

**Castaño-Quintero, S.**, Velasco, J., González-Voyer, A., Martínez-Meyer, E., & Yáñez-Arenas, C. (2024). Niche position and niche breadth effects on population abundances: A case study of New World Warblers (Parulidae). *Ecology and Evolution*, 14(3), e11108.
https://doi.org/10.1002/ece3.11108

**Data Source:** Figshare - Parulidae Niche and Abundance Data
https://figshare.com/s/c71a49da600ceed9bc53

---

## 📝 Reproducibility Note

This Python implementation:
- ✅ Uses publicly available data (Figshare)
- ✅ Maintains fidelity to original R analysis (Script_OMI_proceso2.R)
- ✅ Improves code documentation and reproducibility
- ✅ Enables integration with modern Python data science tools
- ✅ Provides transparent statistical reporting (HC3-robust standard errors)

**Why Python?**
- Cross-platform reproducibility
- Easier integration with other workflows
- Modern visualization capabilities
- Open-source ecosystem

---

## 🔍 Technical Details

### Heterocedasticity-Robust Standard Errors (HC3)

All PGLS models use HC3-consistent standard errors to account for:
- Unequal sampling effort across species (n varies: 17–4502 records)
- Different geographic representation (Distri: 30–100%)
- Potential heteroscedasticity in residuals

This provides more reliable p-values and confidence intervals than assuming homogeneous variance.

### Phylogenetic Correction

Phylogenetic structure is incorporated through:
- Pagel's λ transformation (λ = 1.0)
- Weighted least squares accounting for phylogenetic non-independence
- 47-species phylogenetic tree in Newick format

---

## 📄 License

MIT License - see LICENSE file

---

## 👤 Author

**Sandra Milena Castaño Quintero**
- PhD in Biological Sciences (UNAM, 2026)
- Specialization: Quantitative Ecology, Conservation, Geospatial Analysis
- Google Scholar: https://scholar.google.com/citations?user=DIarhQQAAAAJ
- GitHub: https://github.com/Salamanadra

---

## 📧 Contact & Questions

For questions about:
- **Data:** See Figshare dataset documentation
- **Original R analysis:** See Script_OMI_proceso2.R
- **Python implementation:** Open an issue on GitHub

---

## 🙏 Acknowledgments

- Original research funding and field work (acknowledged in Castaño-Quintero et al. 2024)
- eBird and GBIF for occurrence data
- BBS (Breeding Bird Survey) for abundance data

---

## 📖 Citation

If you use this repository, please cite:

```bibtex
@software{castano2026parulidae,
  author = {Castaño Quintero, Sandra Milena},
  title = {Niche metrics and population abundance in New World Warblers: 
           Python implementation},
  year = {2026},
  url = {https://github.com/Salamanadra/parulidae-abundance-prediction},
  note = {Reproduces analyses from Castaño-Quintero et al. (2024)}
}
```

---

## 🔄 Version History

- **v0.1** (May 2026) — Initial release with 3 notebooks, PGLS analysis with HC3
- Original R analysis (2024) — Published in Ecology and Evolution

---

**Last updated:** May 25, 2026


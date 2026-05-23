# Niche Position and Niche Breadth Effects on Population Abundances: New World Warblers (Parulidae)

## 📄 Publication
**Castaño-Quintero, S.**, Velasco, J., González-Voyer, A., Martínez-Meyer, E., & Yáñez-Arenas, C. (2024).  
Niche position and niche breadth effects on population abundances: A case study of New World Warblers (Parulidae).  
*Ecology and Evolution*, 14(3), e11108.  
https://doi.org/10.1002/ece3.11108

---

## 🎯 Research Question

**How do niche position and niche breadth influence species population abundances?**

Traditional ecological theory suggests that species occupying broader environmental niches should maintain larger populations. However, the relationship between niche properties and abundance remains poorly understood at continental scales. This study examines whether niche characteristics (position and breadth) are predictive of species abundance patterns in New World Warblers.

---

## 📊 Dataset

**Public Data:** https://figshare.com/s/c71a49da600ceed9bc53

- **Observations:** 500K+ bird occurrence records (New World Warblers, family Parulidae)
- **Species:** Multiple warbler species across North America
- **Environmental Variables:** 50+ climatic and habitat features
  - Temperature (mean annual, seasonality)
  - Precipitation (annual, seasonality)
  - Elevation, habitat type, vegetation indices
- **Temporal Coverage:** Multiple years

---

## 🔬 Methodology

### 1. Niche Quantification
- **Niche Position:** Central location of species in environmental space (using species occurrence data)
- **Niche Breadth:** Range of environmental conditions occupied (variance in environmental space)
- **Tools:** Ecological niche modeling, multivariate analysis

### 2. Abundance Estimation
- Extract population abundance data from occurrence records
- Standardize abundance metrics across species
- Account for sampling effort and detection biases

### 3. Statistical Analysis
- Correlation analysis: niche properties ↔ abundance
- Multivariate regression models (GAM, Random Forest)
- Feature importance analysis to identify key predictors
- Cross-validation for model robustness

### 4. Visualization
- Niche space plots (PCA of environmental variables)
- Scatter plots: niche breadth vs. abundance
- Spatial distribution maps of species abundance

---

## 📈 Key Results

### Primary Findings:
1. **Niche breadth is a significant predictor of abundance**
   - Species with broader environmental tolerances tend to have higher population abundances
   - Effect size varies among species

2. **Niche position matters**
   - Position in environmental space influences abundance patterns
   - Some positions in environmental space support higher abundances

3. **Continental-scale patterns**
   - Results consistent across multiple warbler species
   - Supports predictive power for conservation planning

---

## 💻 Technologies & Tools

**Data Processing & Analysis:**
- Python (pandas, numpy)
- R (tidyverse, terra, sf) for geospatial analysis
- scikit-learn for machine learning models

**Ecological Niche Modeling:**
- Ecological niche quantification methods
- Multivariate statistical analysis

**Visualization:**
- matplotlib, seaborn (Python)
- ggplot2 (R)

---

## 📁 Repository Structure

parulidae-abundance-prediction/
├── README.md                          # This file
├── requirements.txt                   # Python dependencies
├── LICENSE                            # MIT License
├── .gitignore
│
├── notebooks/
│   ├── 01_data_loading_exploration.ipynb      # Load Figshare data, EDA
│   ├── 02_niche_quantification.ipynb          # Calculate niche position & breadth
│   ├── 03_abundance_estimation.ipynb          # Extract/standardize abundance
│   ├── 04_statistical_analysis.ipynb          # Correlation & regression
│   └── 05_visualization_results.ipynb         # Reproduce main figures
│
├── src/
│   ├── niche_metrics.py               # Functions for niche calculation
│   ├── abundance_processing.py        # Abundance data processing
│   └── plotting.py                    # Visualization functions
│
└── data/
└── raw/                           # Downloaded from Figshare
└── README_data.md             # Data download instructions

---

## 🚀 How to Reproduce

### 1. Download Data
Download the public dataset from: https://figshare.com/s/c71a49da600ceed9bc53

Place files in `data/raw/` directory.

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run Analysis
```bash
jupyter notebook notebooks/01_data_loading_exploration.ipynb
```

Run notebooks 1-5 in sequence.

---

## 📚 How to Cite

If you use this code or reproduce this analysis, please cite the original publication:

```bibtex
@article{Castano2024,
  author = {Castaño-Quintero, S. and Velasco, J. and González-Voyer, A. and Martínez-Meyer, E. and Yáñez-Arenas, C.},
  year = {2024},
  title = {Niche position and niche breadth effects on population abundances: {A} case study of {N}ew {W}orld {W}arblers ({P}arulidae)},
  journal = {Ecology and Evolution},
  volume = {14},
  number = {3},
  pages = {e11108},
  doi = {10.1002/ece3.11108}
}
```

---

## 👤 Author

**Sandra Milena Castaño Quintero**  
Data Scientist | PhD in Quantitative Ecology  
Specialization: Ecological niche modeling, species distribution, population ecology  

📧 sandramilenacq@gmail.com  
🔗 [Google Scholar](https://scholar.google.com/citations?user=DIarhQQAAAAJ)  
🔗 [GitHub](https://github.com/Salamanadra)

---

## 📄 License

MIT License - See LICENSE file for details

---

## 🔗 Related Publications

- Castaño-Quintero, S., Escobar-Luján, J., Villalobos, F., Ochoa-Ochoa, L. M., & Yáñez-Arenas, C. (2022). Amphibian Diversity of the Yucatan Peninsula: Representation in Protected Areas and Climate Change Impacts. *Diversity*, 14(10), 813.

---

## 💡 Key Insights for Data Scientists

This project demonstrates:
- ✅ Working with real, published research data
- ✅ Reproducing peer-reviewed findings with code
- ✅ Combining ecological domain expertise with machine learning
- ✅ Handling complex multivariate biological datasets
- ✅ Communicating scientific insights through visualization
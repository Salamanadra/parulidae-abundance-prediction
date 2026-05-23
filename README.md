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

**Public Data Repository:** https://figshare.com/s/c71a49da600ceed9bc53

- **Observations:** 500K+ bird occurrence records (New World Warblers, family Parulidae)
- **Species:** Multiple warbler species across North America
- **Environmental Variables:** 50+ climatic and habitat features
  - Temperature (mean annual, seasonality)
  - Precipitation (annual, seasonality)
  - Elevation, habitat type, vegetation indices
- **Temporal Coverage:** Multiple years

---

## 🔬 Methodology

### Niche Quantification
- **Niche Position:** Central location of species in environmental space
- **Niche Breadth:** Range of environmental conditions occupied
- **Tools:** Ecological niche modeling, multivariate analysis

### Abundance Estimation
- Extract population abundance data from occurrence records
- Standardize abundance metrics across species
- Account for sampling effort and detection biases

### Statistical Analysis
- Correlation analysis: niche properties vs. abundance
- Multivariate regression models (GAM, Random Forest)
- Feature importance analysis
- Cross-validation for model robustness

### Visualization
- Niche space plots (PCA of environmental variables)
- Scatter plots: niche breadth vs. abundance
- Spatial distribution maps

---

## 📈 Key Results

1. **Niche breadth is a significant predictor of abundance**
   - Species with broader environmental tolerances tend to have higher population abundances

2. **Niche position matters**
   - Position in environmental space influences abundance patterns

3. **Continental-scale patterns**
   - Results consistent across multiple warbler species

---

## 💻 Technologies

- **Python:** pandas, numpy, scikit-learn, matplotlib, seaborn
- **Jupyter:** Interactive notebooks
- **Machine Learning:** GAM, Random Forest, XGBoost

---

## 🚀 How to Reproduce

### 1. Get Data
Download from: https://figshare.com/s/c71a49da600ceed9bc53

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run Analysis
```bash
jupyter notebook notebooks/01_data_loading_exploration.ipynb
```

Run notebooks in sequence (01-05).

---

## 📚 Citation

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

📧 sandramilenacq@gmail.com  
🔗 [Google Scholar](https://scholar.google.com/citations?user=DIarhQQAAAAJ)  
🔗 [GitHub](https://github.com/Salamanadra)

---

## 📄 License

MIT License - See LICENSE file for details

# Corn Yield Prediction in Wisconsin (County-Level)

## Project Overview
This project investigates county-level corn yield prediction in Wisconsin using a combination of statistical, machine learning, and deep learning approaches. In addition to predictive performance, the project explicitly examines **spatial heterogeneity** in yield–climate relationships to assess whether model behavior and feature effects vary geographically.

The project is driven by three core research questions:
1. How well can historical climate and environmental variables explain inter-annual variability in corn yield?
2. Do temporal and spatiotemporal models outperform static or purely tabular approaches?
3. Is there evidence of **spatial non-stationarity** in yield–climate relationships across counties?

---

## Data Sources
- **Corn yield data**: USDA NASS county-level annual corn yield
- **Climate variables**: PRISM temperature and precipitation aggregates
- **Spatial boundaries**: Wisconsin county polygons

All datasets are harmonized to a county–year panel, with spatial geometry retained for spatial analysis.

---

## Feature Engineering
- Growing-season climate summaries
- Lagged yield and climate variables
- Standardization within training folds
- Spatial attributes retained for spatial diagnostics and regression

---

## Methods

### 1. Spatial Heterogeneity Analysis
Before fitting complex predictive models, the project evaluates spatial non-stationarity using:

- **Geographically Weighted Regression (GWR)**  
  GWR is applied to assess whether the relationship between corn yield and key climate predictors varies across space. Local parameter estimates are analyzed to:
  - Identify counties with distinct yield–climate sensitivities
  - Compare local vs. global regression performance
  - Inform whether spatially varying coefficients justify more complex spatial models

GWR results are treated as **diagnostic and exploratory**, not purely predictive.

---

### 2. Predictive Models
Models are trained on the same county–year dataset for performance comparison:

#### Baseline Models
- Linear Regression (global, non-spatial)
- Random Forest
- Gradient Boosting (optional)

#### Deep Learning Models
- Multilayer Perceptron (MLP)
- LSTM for temporal sequences
- Hybrid LSTM–MLP architecture

Model choice is interpreted in light of GWR findings on spatial heterogeneity.

---

## Evaluation Strategy
- Temporal splits by year to avoid leakage
- Metrics: RMSE, MAE, R²
- Comparison between:
  - Global linear models
  - Spatially varying (GWR) regression
  - Nonlinear ML/DL models

---

## Project Structure
cornyield/
│
├── data/
│ ├── raw/
│ ├── processed/
│
├── notebooks/
│ ├── 01_exploration.ipynb
│ ├── 02_gwr_analysis.ipynb
│ ├── 03_feature_engineering.ipynb
│ ├── 04_model_training.ipynb
│
├── src/
│ ├── data_utils.py
│ ├── spatial_utils.py
│ ├── models.py
│ ├── evaluation.py
│
├── results/
│ ├── gwr_outputs/
│ ├── metrics/
│ ├── figures/
│
├── README.md
└── requirements.txt


---

## Reproducibility
- Fixed random seeds
- Explicit spatial bandwidth selection for GWR
- Saved intermediate outputs for spatial diagnostics

---

## Current Status
- Data preprocessing: **Completed**
- GWR spatial heterogeneity analysis: **Completed**
- Baseline ML models: **Completed**
- Deep learning models: **In progress**

---

## Future Work
- Compare GWR findings with graph-based spatial models (e.g., GNNs)
- Examine consistency between local GWR coefficients and DL feature importance
- Extend spatial analysis to multi-state Midwest regions

---

## References
- USDA National Agricultural Statistics Service (NASS)
- PRISM Climate Group
- Brunsdon et al. (1996), Geographically Weighted Regression

---


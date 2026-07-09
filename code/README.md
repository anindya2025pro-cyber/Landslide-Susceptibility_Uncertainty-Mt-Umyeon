# Python Scripts

## Execution Sequence

This directory contains the complete Python pipeline for landslide susceptibility mapping.

### 1. Data Preprocessing
**File:** `01_Data_Preprocessing.py`
- Loads raw inventory data
- Removes invalid records
- Imputes missing values
- Standardizes features
- Output: Clean CSV for modeling

### 2. Model Benchmarking
**File:** `02_Baseline_22_Models_Evaluation.py`
- Tests 22 different classifiers
- Uses 5-fold cross-validation
- Calculates metrics: AUC, MCC, Accuracy, Precision, Recall, F1-score
- Output: Performance comparison table

### 3. Ensemble Optimization
**File:** `03_Genetic_Ensemble_Optimization.py`
- Combines LDA + SVM-RBF + XGBoost
- Uses Optuna for weight optimization (2000 trials)
- Tunes decision threshold
- Output: Optimal weights (0.118, 0.457, 0.425)

### 4. SHAP Explainability
**File:** `04_SHAP_XAI_Explainability.py`
- Calculates SHAP values
- Creates global importance plots
- Generates local waterfall explanations
- Output: Feature importance rankings

### 5. Spatial Mapping
**File:** `07_Geospatial_Susceptibility_Mapping.py`
- Projects predictions to spatial raster grid
- Creates bivariate uncertainty maps
- Exports GeoTIFF files
- Output: Landslide susceptibility maps

## How to Run

```bash
# Install dependencies
pip install scikit-learn xgboost optuna shap pandas numpy matplotlib seaborn rasterio geopandas

# Run in order
python 01_Data_Preprocessing.py
python 02_Baseline_22_Models_Evaluation.py
python 03_Genetic_Ensemble_Optimization.py
python 04_SHAP_XAI_Explainability.py
python 07_Geospatial_Susceptibility_Mapping.py

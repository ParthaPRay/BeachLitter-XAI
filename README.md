# BeachLitter-XAI

## Explainable Geospatial Machine Learning for Coastal Cleanliness Risk Prediction Using Marine Litter Watch Data

**BeachLitter-XAI** is a research-oriented Python/Colab notebook for predicting, mapping, and explaining coastal cleanliness risk using Marine Litter Watch beach-litter data. The framework combines Clean-Coast Index proxy construction, machine-learning regression, 3-class and 5-class coastal risk classification, geospatial mapping, SHAP-based explainability, statistical analysis, and publication-grade visual outputs.

Repository: [https://github.com/ParthaPRay/BeachLitter-XAI](https://github.com/ParthaPRay/BeachLitter-XAI)

---

## Overview

Marine litter is a major environmental concern for coastal ecosystems, tourism, public health, and marine biodiversity. This project develops an explainable geospatial machine-learning workflow to assess coastal cleanliness risk from beach-litter survey records.

The main notebook, **`BeachLitter-XAI.ipynb`**, performs the complete workflow from dataset loading to risk modelling, mapping, explainability, and result export.

The study uses Marine Litter Watch records containing beach metadata, event information, geospatial coordinates, and item-level litter-code columns. A plastic-litter-based Clean-Coast Index proxy is computed and used for regression and classification tasks.

---

## Main Objectives

The project aims to:

1. Construct a Clean-Coast Index proxy from marine litter records.
2. Predict CCI-proxy values using machine-learning regression models.
3. Classify coastal cleanliness risk into 3-class and 5-class categories.
4. Generate publication-grade geospatial maps of observed and predicted risk.
5. Explain model predictions using SHAP and permutation importance.
6. Perform statistical and risk-based interpretation of coastal litter patterns.
7. Export figures, tables, maps, and reports for manuscript preparation.

---

## Proposed Title

**BeachLitter-XAI: Explainable Geospatial Machine Learning for Coastal Cleanliness Risk Prediction Using Marine Litter Watch Data**

---

## Notebook File

The main executable notebook is:

```text
BeachLitter-XAI.ipynb
```

It is designed to run in **Google Colab CPU**.

---

## Dataset

The notebook uses the Marine Litter Watch dataset:

```text
MLW_Data.csv
```

The dataset contains:

* Beach-level survey records
* Event date and event type
* Country and regional sea metadata
* Beach location and beach type
* Beach length
* Geospatial coordinates
* Litter-code columns such as G1, G3, G4, G7, G21, G27, etc.

The litter codes are grouped into broader material and source categories, such as:

* Plastic
* Rubber
* Cloth/textile
* Paper/cardboard
* Processed/worked wood
* Metal
* Glass/ceramics
* Chemicals
* Sanitary/medical waste
* Fishing-related litter
* Smoking-related litter
* Packaging-related litter
* Plastic fragments

---

## Clean-Coast Index Proxy

A plastic-litter-based Clean-Coast Index proxy is calculated using:

```text
CCI_proxy = 20 × plastic_litter / surveyed_area_m2
```

where:

```text
surveyed_area_m2 = BeachLength_m × assumed beach width
```

The notebook uses an assumed beach width of 10 m.

A log-transformed target is also created:

```text
log_CCI_proxy = log1p(CCI_proxy)
```

---

## Classification Targets

Two classification schemes are used.

### 3-Class Coastal Risk

| CCI-proxy range | Class         |
| --------------- | ------------- |
| CCI ≤ 5         | Low risk      |
| 5 < CCI ≤ 20    | Moderate risk |
| CCI > 20        | High risk     |

### 5-Class Cleanliness Category

| CCI-proxy range | Class           |
| --------------- | --------------- |
| CCI ≤ 2         | Very clean      |
| 2 < CCI ≤ 5     | Clean           |
| 5 < CCI ≤ 10    | Moderate        |
| 10 < CCI ≤ 20   | Dirty           |
| CCI > 20        | Extremely dirty |

---

## Feature Engineering

The notebook creates temporal, geospatial, and litter-composition features.

### Temporal Features

* Year
* Month
* Day of year
* Season

### Geospatial Features

* Midpoint longitude
* Midpoint latitude

### Litter-Density Features

The following features are computed per 100 m of beach length:

* Single-use plastic per 100 m
* Fishing-related litter per 100 m
* Smoking-related litter per 100 m
* Sanitary/medical litter per 100 m
* Packaging litter per 100 m
* Plastic fragments per 100 m
* Rubber litter per 100 m
* Textile litter per 100 m
* Paper litter per 100 m
* Wood litter per 100 m
* Metal litter per 100 m
* Glass litter per 100 m

---

## Machine-Learning Models

The notebook evaluates multiple machine-learning models for regression and classification.

### Regression Models

* XGBoost Regressor
* Gradient Boosting Regressor
* LightGBM Regressor
* HistGradientBoosting Regressor
* Extra Trees Regressor
* Random Forest Regressor
* CatBoost Regressor
* K-Nearest Neighbours Regressor

### Classification Models

* XGBoost Classifier
* Gradient Boosting Classifier
* LightGBM Classifier
* HistGradientBoosting Classifier
* Extra Trees Classifier
* Random Forest Classifier
* CatBoost Classifier
* K-Nearest Neighbours Classifier

---

## Evaluation Metrics

### Regression Metrics

* MAE on log scale
* RMSE on log scale
* R² on log scale
* MAE on original scale
* RMSE on original scale
* R² on original scale

### Classification Metrics

* Accuracy
* Weighted precision
* Weighted recall
* Weighted F1-score
* Confusion matrix
* Classification report

---

## Explainable AI Analysis

The notebook includes model explainability using:

* SHAP global feature importance
* SHAP summary plots
* SHAP feature-importance bar plots
* Permutation importance
* SHAP vs permutation-importance comparison

These analyses help identify the major drivers of coastal cleanliness risk prediction.

---

## Geospatial Mapping

The project generates both static and interactive maps.

### Static Maps

* CCI-proxy spatial distribution map
* 3-class coastal risk map
* 5-class cleanliness map
* Model-predicted coastal risk map
* High-risk probability map
* Local Moran hotspot map

### Interactive Maps

* Folium-based interactive CCI risk map
* Folium heatmap of CCI-proxy intensity

---

## Statistical Analysis

The notebook includes additional statistical analyses, such as:

* Descriptive statistics of CCI-proxy by class
* Normality testing
* Kruskal-Wallis test
* Effect-size estimation
* Pairwise Mann-Whitney U tests
* Spearman correlation analysis
* Country-wise CCI risk summary
* Regional sea-wise risk summary
* Bootstrap confidence intervals
* Calibration analysis
* Prediction-confidence analysis
* Ordinal error analysis for the 5-class task
* Threshold sensitivity analysis

---

## Advanced Spatial and Multivariate Analysis

The extended workflow also supports:

* Global Moran’s I spatial autocorrelation
* Local Moran hotspot detection
* Seasonal risk analysis
* Year-wise CCI trend analysis
* PCA of litter-density profiles
* K-means clustering of beach litter profiles
* Litter-source contribution analysis

---

## Output Folders

The notebook creates several result folders, including:

```text
Observed_vs_Predicted_Individual_Models/
Confusion_Matrices_3Class_Individual_Models/
Confusion_Matrices_5Class_Individual_Models/
Publication_Maps/
Interactive_Maps/
SHAP_Explainability/
Risk_Analysis_Plots/
Statistical_Analysis/
Model_Reliability/
Advanced_Spatial_Analysis/
Temporal_Risk_Analysis/
Threshold_Sensitivity/
Ordinal_Error_Analysis/
Litter_Source_Analysis/
Multivariate_Analysis/
Final_Results/
```

---

## Main Outputs

The workflow produces:

* Regression result tables
* 3-class classification result tables
* 5-class classification result tables
* Confusion matrices
* Observed-vs-predicted plots
* Geospatial risk maps
* Interactive Folium maps
* SHAP plots
* Permutation-importance plots
* Statistical test tables
* Bootstrap confidence intervals
* Calibration curves
* Risk-profile tables
* PCA and clustering outputs
* Final Excel workbook of results
* ZIP file containing all generated outputs

---

## Installation

The notebook installs or uses the following major Python packages:

```python
pandas
numpy
matplotlib
seaborn
scikit-learn
xgboost
lightgbm
catboost
shap
geopandas
folium
imbalanced-learn
libpysal
esda
```

For Google Colab, the required packages can be installed using:

```python
!pip install xgboost lightgbm catboost shap geopandas folium imbalanced-learn -q
!pip install libpysal esda -q
```

---

## How to Run

1. Open `BeachLitter-XAI.ipynb` in Google Colab.
2. Upload the dataset file:

```text
MLW_Data.csv
```

3. Run the notebook cell by cell.
4. Review model outputs, maps, SHAP plots, and statistical tables.
5. Run the final ZIP-download cell to export all generated files.

---

## Recommended Runtime

The notebook is designed for:

```text
Google Colab CPU
```

A GPU is not required because the workflow mainly uses tabular machine learning, geospatial analysis, statistical testing, and explainability methods.

---

## Suggested Citation

If you use this repository or adapt the workflow, please cite it as:

```text
Ray, P. P. BeachLitter-XAI: Explainable Geospatial Machine Learning for Coastal Cleanliness Risk Prediction Using Marine Litter Watch Data. GitHub repository: https://github.com/ParthaPRay/BeachLitter-XAI
```

---

## Author

**Partha Pratim Ray**
Department of Computer Applications
Sikkim University, India

GitHub: [https://github.com/ParthaPRay](https://github.com/ParthaPRay)



---

## Disclaimer

This project uses a CCI-proxy derived from available litter and beach-length information. The results should be interpreted as computational and statistical risk indicators, not as official regulatory classifications. The analysis depends on the quality, completeness, and representativeness of the underlying Marine Litter Watch data.

# Predicting the Logistics Performance Index (LPI) with Tree-Based Machine Learning Methods
#### Author: Eric Torres

This repository presents a machine learning-based framework to predict the World Bank's  **Logistics Performance Index (LPI)**. The official 2023 LPI relies on Big Data, such as postal and container-level event records from systems like TradeLens, UPU, and Cargo iQ. As most of these data are not publicly available, this project leverages **open-access macroeconomic and trade datasets**, particularly from **UNCTAD**, to estimate the LPI using statistical and machine learning methods.

---

## 🎯 Project Objectives

1. Predict the World Bank’s LPI index using only open-access macro-level datasets.
2. Create a structured and interpretable ML pipeline for LPI approximation.
3. Assess model performance and interpretability across countries and income groups.
4. Predict the scores for more countries

---

## 🧪 Main Notebook

> **Notebook**: `LPI_Prediction_MLModels.ipynb`

This notebook implements the complete modeling pipeline:
- Data ingestion and merging
- Feature engineering and exploratory analysis
- Model training and tuning
- LPI prediction and error diagnostics
- Feature importance
- Predict the index for 13 new countries

---

## 🔁 Modeling Pipeline

| Stage | Description |
|-------|-------------|
| **1. Data Collection** | Aggregation of publicly available datasets from UNCTADstat, WDI, CEPII BACI, etc. |
| **2. Data Cleaning and Feature Engineering** | Select relevant variables within each dataset, include data from 2023 or the closest available year, and harmonize feature names. |
| **3. Key alignment (pre-merge)** | Align merge keys (e.g., fixing country names, year formats, duplicates) across datasets. |
| **4. Merging process** | Merge all the harmonized datasets into a single unified dataset. |
| **5. Handling Missing Data** | Identification of missing values across datasets. |
| **6. Model Training** | Perform Random Forest, Gradient Boosting, and other ML models via `scikit-learn` and evaluation with RMSE and R², Cross-validation (e.g., k-fold). |
| **7. Results** | Output table with predicted LPI scores for countries with no available LPI data. |

---

## 🗂️ Datasets Overview
#### From the following list of datasets, a total of 21 variables are extracted: the target variable (LPI index) and 20 explanatory features.

| Filename | Source | Contents |
|----------|--------|----------|
| `LPI_INDEX.csv` | World Bank | Official World Bank's LPI scores from the 2023 Big Data–based index |
| `IncomeREgions.csv` | World Bank | Export and import volume indices referenced to the base year 2015. These indices measure the physical volume of trade, excluding price effects. |
| `US_ConcentDiversIndices.csv` | UNCTADstat | Trade concentration and diversification: Measures how focused or diversified a country’s trade is across products, and how it differs from the global pattern. |
| `US_ContPortThroughput.csv` | UNCTADstat | Estimated number of containers handled per country, measured in 20-foot equivalent units. A 40-foot container equals two TEUs. |
| `US_FdiFlowsStock.csv` | UNCTADstat | Foreign direct investment (FDI) inward and outward flows and stocks, expressed in millions of US dollars. |
| `US_GDPTotal.csv` | UNCTADstat | gross domestic product (GDP) in millions of US dollars at constant 2015 prices. |
| `US_GoodsAndServTradeOpennessBpm6.csv` | UNCTADstat | Trade in Goods and Openness: Value of exported and imported goods (in USD) and their share of nominal GDP; excludes services. |
| `US_LSCI.csv` | UNCTAD based on MDS Transmodal  | Liner Shipping Connectivity Index (LSCI), which measures how well a country is integrated into global shipping networks. |
| `US_PCI.csv` | UNCTAD | The Productive Capacities Index (PCI), assesses a country’s ability to produce goods and services across eight dimensions. This pipeline includes only three: Transport, ICT, and the Overall score. |
| `US_Tariff_20230704020713.csv` | UNCTAD TRAINS / WITS | Effectively applied import tariff rates for major categories of non-agricultural and non-fuel products. |
| `US_TermsOfTrade.csv` | UNCTADstat | Export and import volume indices referenced to the base year 2015. These indices measure the physical volume of trade, excluding price effects. |



📝 All data is aggregated to the country level for the year 2023 (or closest available year aligned with LPI 2023).

---

## 📊 Model Output

- The best-performing models yield **R² ≈ 0.89** and **RMSE ≈ 0.195**
- Scatter plots show strong linearity between predicted and true LPI scores
- Residual analysis highlights over-/under-performing countries
- Model interpretation via feature importance and SHAP values
- Tables with predicted values

---

## 📈 Visualizations

Figures generated include:
- Missings by variable
- Correlation matrix
- Residuals by income group and region
- Feature importance (tree-based models)


📁 All plots are saved in the `figures` directory.

---





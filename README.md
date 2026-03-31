# 📊 Capstone Project: Used Laptop Price Prediction

## 📌 Project Overview
Pricing used laptops accurately in online marketplaces is challenging due to rapid hardware depreciation and inconsistent specifications. This project analyzes real-world eBay used laptop listings and develops machine learning regression models to predict fair market prices based on hardware specifications.

---

## 🎯 Problem Statement
Online marketplaces lack a standardized pricing reference for used laptops, leading to inefficiencies for both buyers and sellers. This project aims to identify which features most strongly influence resale price and build a model to reasonably predict these prices.

---

## ✅ Project Objectives
1. Explore and understand pricing patterns in used laptop listings.
2. Clean and preprocess unstructured and inconsistent real-world data.
3. Identify influential hardware features (CPU, RAM, Storage, Screen) affecting price.
4. Train and evaluate multiple regression models (Linear, Random Forest, XGBoost, MLP).

### Key Performance Indicators (KPIs)
*   **R-squared (R2)**: Target 0.80 or higher.
*   **Mean Absolute Error (MAE)**: Target less than $50.

*   **Root Mean Squared Error (RMSE)**: Target less than $75.

---

## 📂 Dataset
- **Source:** [Ebay Laptops and Netbooks Sales (Kaggle)](https://www.kaggle.com/datasets/elvinrustam/ebay-laptops-and-netbooks-sales)
- **Scope:** Consumer-grade laptop listings
- **Target Variable:** Price (USD)

### Key Features
- Brand, Processor Type, Processor Tier (Engineered)
- RAM Size, SSD/HDD Capacity, Total Storage (Engineered)
- Screen Size, Maximum Resolution (Width/Height/Pixels)
- Operating System, Item Condition

---

## 🧹 Data Cleaning & Preprocessing
- **Column Filtering**: Dropped columns with >60% missing values (e.g., Manufacturer Color).
- **Normalization**: Standardized all storage and RAM capacities to GB; averaged price ranges.
- **Signal Preservation**: Imputed categorical missing values as 'Unknown' to treat the absence of information as a predictive category.
- **Outlier Capping**: Applied IQR-based capping specifically to Price and SSD Capacity.
- **Feature Engineering**: Created interaction terms (e.g., `Ram_Screen_Interaction`) and a performance-based `Processor_Tier` ranking.

---

## 🤖 Modeling Approach
We evaluated five regression models using `GridSearchCV` and 5-fold cross-validation to optimize hyperparameters. Numerical features were scaled using `StandardScaler` to ensure balanced model training.

> **Key Result:** The final **XGBoost Regressor** model explains **~67%** of price variance with an average error (MAE) of **~$85**.

### Final Model Comparison

| Model | R-squared (R2) | MAE | RMSE |
| :--- | :--- | :--- | :--- |
| **XGBoost Regressor** | **0.67** | $84.94 | **$134.09** |
| **Random Forest** | 0.66 | **$83.99** | $135.94 |
| Gradient Boosting | 0.63 | $92.23 | $141.61 |
| MLP (Neural Net) | 0.52 | $103.08 | $162.96 |
| Linear Regression | 0.48 | $112.59 | $168.21 |

---

## 📈 Key Insights
- **Display is King**: Vertical resolution (`Resolution_Height`) and total `Pixel_Count` were among the most critical drivers of price across all models.
- **The 'Unknown' Factor**: Across Linear and Ensemble models, the status `GPU_Unknown` was a top-tier predictor. The lack of detailed specs was a strong indicator of lower-end, budget devices.
- **Storage Performance**: SSD capacity is a significantly stronger predictor than HDD capacity, reflecting the market premium for modern storage tech.

---

## 🔮 Future Work
- **NLP Integration**: Leverage listing titles and 'Seller Notes' to extract condition nuances.
- **Temporal Analysis**: Incorporate the release year relative to the sale date to model depreciation more accurately.
- **Model Stacking**: Combine XGBoost and MLP to capture both linear and complex non-linear hardware value relationships.

---

## ▶️ How to Run
1. Open the notebook in **Google Colab**.
2. Ensure `xgboost` and `scikeras` are installed.
3. Run cells sequentially to perform cleaning, engineering, and model training.

---

## 📌 Conclusion
This project demonstrates that while used hardware prices are noisy, display quality and data completeness are the primary indicators of value. Ensemble tree-based models (XGBoost/Random Forest) proved most effective at capturing the non-linear interactions inherent in hardware pricing.

---

## 👉 Notebook Link

Explore the full analysis and code in the notebook:

[Laptop prices on eBay](https://github.com/tahirp/Capstone-Laptop-prices-on-eBay/blob/main/Capstone_Laptop_prices_on_eBay.ipynb)


# 📊 Capstone Project: Laptop Prices on eBay

## 📌 Project Overview
Pricing used laptops accurately in online marketplaces is challenging due to rapid hardware depreciation, inconsistent specifications, and varying seller behavior. As a result, sellers often overprice or underprice listings, leading to unsold inventory or lost value.

This project analyzes real‑world **eBay used laptop listings** and develops a **machine learning regression model** to identify key price drivers and **predict fair market prices** based on laptop specifications. The analysis follows a complete data science workflow, emphasizing practical, real‑world considerations such as noisy data, missing values, and heterogeneous feature representations.

---

## 🎯 Problem Statement
Online marketplaces like eBay lack a standardized pricing reference for used laptops. Prices vary widely for similar devices, creating inefficiencies for both buyers and sellers.

This project aims to answer:
- Which laptop features most strongly influence resale price?
- Can a machine learning model reasonably predict used laptop prices given noisy marketplace data?

---

## ✅ Project Objectives
1. Explore and understand pricing patterns in used laptop listings.
2. Clean and preprocess unstructured and inconsistent real‑world data.
3. Identify the most influential hardware and listing features affecting price.
4. Train and evaluate regression models for price prediction.
5. Assess model performance using appropriate evaluation metrics.

---

## 📂 Dataset
- **Source:** Public eBay laptop listings dataset (via Kaggle / web‑scraped data)
- **Scope:** Used laptop and notebook listings
- **Target Variable:** Listing price (USD)

### Key Features
- Brand
- Processor (CPU)
- RAM
- Storage type and capacity
- Screen size
- Operating system
- Item condition

> The dataset reflects real‑world marketplace challenges, including missing values, inconsistent formatting, and noisy textual fields.

---

## 🧹 Data Cleaning & Preprocessing
Major preprocessing steps included:
- Removing duplicate listings
- Cleaning and standardizing price formats
- Handling missing and inconsistent feature values
- Dropping columns with excessive missing data
- Encoding categorical features
- Scaling numerical variables where appropriate

These steps were necessary to convert raw marketplace data into a model‑ready dataset.

---

## 📊 Exploratory Data Analysis (EDA)
EDA was conducted to better understand:
- Price distributions and skewness
- Price trends across brands and hardware specifications
- Correlations between features and laptop prices
- Outliers and anomalous listings

Visualizations such as histograms, box plots, and correlation heatmaps supported feature selection and modeling decisions.

---

## 🤖 Modeling Approach
Several regression models were explored and compared. The final model was selected based on predictive performance and generalization ability.

### Final Model
- **Model:** Random Forest Regressor  
- **Evaluation Metrics:**
  - **R²:** ~0.78  
  - **MAE:** ~$65  
  - **RMSE:** ~$85  

These results indicate that the model captures a meaningful portion of price variation despite inherent marketplace noise and unobserved factors.

---

## 📈 Key Insights
- Brand, processor type, RAM, and storage capacity are among the strongest predictors of price.
- Used laptop prices exhibit significant variance even among similar specifications.
- Real‑world marketplace data introduces unavoidable noise that limits perfect prediction.

---

## ⚠️ Limitations
- Listings reflect asking prices, not finalized sale prices.
- Seller reputation and listing quality were not included.
- Textual descriptions were not fully leveraged using NLP techniques.
- Geographic and temporal pricing effects were not modeled explicitly.

---

## 🔮 Future Work
Potential improvements include:
- Incorporating NLP features from listing descriptions
- Using finalized sale prices where available
- Modeling time‑based depreciation effects
- Expanding the dataset across marketplaces

---

## ▶️ How to Run
This project can be run in **Google Colab**:
1. Open the notebook `Capstone_Laptop_prices_on_eBay.ipynb`
2. Upload the dataset when prompted (or adjust file paths as needed)
3. Run all cells from top to bottom

### Dependencies
- pandas  
- numpy  
- scikit-learn  
- matplotlib  
- seaborn  

---

## 📌 Conclusion
This project demonstrates an end‑to‑end applied machine learning workflow using real‑world marketplace data. Despite inherent data limitations, the model provides meaningful pricing insights and highlights the key factors influencing used laptop resale values on eBay.
``

# Used Laptop Price Prediction

**Predicting Market Value through Hardware Specifications**

### Executive summary

**Project overview and goals:** The used laptop market lacks a standard price guide, leading to pricing inefficiencies. This project aims to build a robust predictive model that estimates market prices based on hardware specifications. By putting a dollar value on specific specs, we help businesses maximize profit and buyers avoid overpayment, ultimately reducing e-waste by facilitating faster sales.

**Findings:** The best model for predicting laptop prices is the **XGBoost Regressor**, achieving an R-squared (R2) of 0.67 and the lowest RMSE of $134.09. While ensemble models represented a significant improvement over the baseline Linear Regression (R2: 0.48), they did not meet the ambitious target KPIs (R2 ≥ 0.80, MAE < $50), indicating the complex and non-linear nature of the used electronics market.

### Project Definition & Goals

1.  **Main Goal**: Build a robust predictive model to estimate market prices, assisting in effective pricing and avoiding overpayment.
2.  **Secondary Goals**:
    *   **Identify Influential Features**: Determine key specs (RAM, CPU, storage, screen) impacting price.
    *   **Competitive Pricing Tool**: Assist sellers in pricing used inventory competitively.
    *   **Market Insight**: Understand trends and value depreciation.
    *   **Reduce E-waste**: Facilitate efficient sales to keep hardware out of landfills.
3.  **Key Performance Indicators (KPIs)**:
    *   **R-squared (R2)**: Target 0.80 or higher.
    *   **MAE**: Target less than $50.
    *   **RMSE**: Target less than $75.

### Data Sources & Preparation

**Data Source:** Raw data obtained from Kaggle ([Ebay Laptops and Netbooks Sales](https://www.kaggle.com/datasets/elvinrustam/ebay-laptops-and-netbooks-sales)).

**Cleaning & Preprocessing Steps**:
*   **Initial Inspection**: Analyzed structure, dtypes, and statistics.
*   **Dropping Columns**: Removed irrelevant/high-missing columns (Manufacturer Color, Country Region Of Manufacture, Rating, Ratings Count, Release Year, Seller Note, Features).
*   **Duplicate Removal**: Ensured data integrity by removing redundant rows.
*   **Price Cleaning**: Standardized currency and averaged price ranges.
*   **Numerical Cleaning**: Extracted numeric values from strings and converted units to GB. Imputed missing values using medians (size, speed, RAM) or 0 (SSD, HDD).
*   **Categorical Cleaning**: Standardized values and imputed 'Unknown' for missing categories to preserve predictive signals from missing data.
*   **Outlier Handling**: Applied IQR-based capping to features like Price and SSD Capacity.

### Methodology

1.  **Feature Engineering**: Created interaction terms (`Processor_Ram_Interaction`, `Ram_Screen_Interaction`), assigned `Processor_Tier` based on performance hierarchy, and extracted resolution components (Width, Height, Pixel_Count).
2.  **Encoding & Scaling**: Applied One-Hot Encoding to all categorical features and scaled numerical features using `StandardScaler`.
3.  **Modeling**: Evaluated five models: Linear Regression, Random Forest, Gradient Boosting, XGBoost, and MLP (Neural Net).
4.  **Tuning**: Utilized `GridSearchCV` with 5-fold `KFold` cross-validation.

### Baseline: Linear Regression Results

The initial baseline model achieved the following performance:
*   **R-squared (R2)**: 0.48 (Below Target)
*   **MAE**: $112.59 (Above Target)
*   **RMSE**: $168.21 (Above Target)

**Linear Feature Importance Analysis**:
*   **Display Characteristics**: `Aspect_Ratio_Unknown` (158.63), `Resolution_Height` (156.30), and `Pixel_Count` (140.66) were the most critical drivers.
*   **The 'Unknown' Factor**: High coefficients for `GPU_Unknown` and `Storage Type_Unknown` suggest that data completeness is a strong indicator of value; missing details often correlate with lower-end models.

### Final Model Comparison

| Model | R-squared (R2) | MAE | RMSE |
| :--- | :--- | :--- | :--- |
| **XGBoost Regressor** | **0.67** | $84.94 | **$134.09** |
| **Random Forest** | 0.66 | **$83.99** | $135.94 |
| Gradient Boosting | 0.63 | $92.23 | $141.61 |
| MLP (Neural Net) | 0.52 | $103.08 | $162.96 |
| Linear Regression | 0.48 | $112.59 | $168.21 |

### Future research and development

*   **Data Enrichment**: Reducing 'Unknown' entries through web scraping or richer datasets.
*   **Temporal Analysis**: Including hardware age to account for technological depreciation.
*   **Model Stacking**: Combining tree-based models with neural networks for ensemble predictions.



**[Your Name]**  
Email: [Your Email]  
LinkedIn: [Your LinkedIn Profile URL]

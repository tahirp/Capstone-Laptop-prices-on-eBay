# Used Laptop Price Prediction

**Predicting Market Value through Hardware Specifications**

### Executive summary

**Project overview and goals:** The used laptop market lacks a standard price guide, leading to pricing inefficiencies for both buyers and sellers. This project aims to build a robust predictive model that estimates market prices based on hardware specifications (CPU, RAM, Storage, etc.). By putting a dollar value on specific specs, we help businesses maximize profit and buyers avoid overpayment, ultimately reducing e-waste by facilitating faster sales.

**Findings:** The best model for predicting laptop prices is the **XGBoost Regressor**, achieving an R-squared (R2) of 0.67 and the lowest Root Mean Squared Error (RMSE) of $134.09. It is closely followed by the Random Forest Regressor, which provided the lowest Mean Absolute Error (MAE) of $83.99. While these models represent a significant improvement over the baseline Linear Regression (R2: 0.47), they did not meet the ambitious target KPIs (R2 ≥ 0.80, MAE < $50), indicating the complex and non-linear nature of the used electronics market.

**Results and conclusion:** Analysis of feature importance across all ensemble models revealed that **GPU status (specifically if unknown/integrated)**, **SSD Capacity**, and **Display Resolution** are the primary drivers of price. Notably, the 'Unknown' status of a GPU was the single most dominant predictor, suggesting that incomplete listings act as a strong signal for lower-valued, budget-tier devices. 

### Rationale

Without data-driven pricing, sellers often lose money through underpricing or miss sales through overpricing. This project quantifies the value of hardware upgrades (like extra RAM or SSD space), providing transparency in a messy market and preventing functional hardware from ending up as e-waste due to poor pricing strategies.

### Research Question

What is the most accurate regression model for estimating the price of a used laptop based on its technical specifications, and which specific features contribute most to its market value?

### Data Sources

**Dataset:** Sourced from Kaggle ([Ebay Laptops and Netbooks Sales](https://www.kaggle.com/datasets/elvinrustam/ebay-laptops-and-netbooks-sales)). The raw data contained 6,620 entries with 23 features, including Brand, Price, Condition, Processor, and Storage details.

**Cleaning and preparation:** 
*   Dropped irrelevant columns with >60% missing values.
*   Standardized numerical values (RAM, SSD, HDD) to Gigabytes (GB).
*   Handled price ranges by averaging lower and upper bounds.
*   Capped outliers in Price and SSD Capacity using the IQR method.
*   Imputed categorical missing values as 'Unknown' to preserve the predictive signal of missing data.

### Methodology

We employed a comprehensive data science pipeline:
1.  **Feature Engineering:** Created interaction terms (e.g., `Ram_Screen_Interaction`), binned continuous variables (e.g., `Processor_Tier`), and extracted display metrics from resolution strings.
2.  **Preprocessing:** Applied One-Hot Encoding to categorical features and `StandardScaler` to numerical features.
3.  **Modeling:** Evaluated five models: Linear Regression, Random Forest, Gradient Boosting, XGBoost, and a Multilayer Perceptron (MLP).
4.  **Tuning:** Used `GridSearchCV` with `KFold` cross-validation (5-fold) to optimize hyperparameters for all ensemble and neural network models.

### Model evaluation and results

| Model | R-squared (R2) | MAE | RMSE |
| :--- | :--- | :--- | :--- |
| **XGBoost Regressor** | **0.67** | $84.94 | **$134.09** |
| **Random Forest** | 0.66 | **$83.99** | $135.94 |
| Gradient Boosting | 0.63 | $92.23 | $141.61 |
| MLP (Neural Net) | 0.52 | $103.08 | $162.96 |
| Linear Regression | 0.47 | $113.24 | $170.67 |

**Key Takeaways:** Display quality and modern storage (SSD) command the highest premiums. The consistent performance of ensemble tree-based models suggests they are better at capturing hardware value interactions than linear or basic neural models.

### Future research and development

*   **Data Enrichment:** Sourcing datasets with specific processor generations (e.g., i7-12th Gen vs i7-6th Gen) to reduce 'Unknown' noise.
*   **Temporal Analysis:** Incorporating the 'age' of the laptop relative to the current year to account for technological depreciation.
*   **Model Stacking:** Combining XGBoost and MLP predictions to capture both categorical relationships and complex non-linearities.

### Contact and Further Information

**[Your Name]**  
Email: [Your Email]  
LinkedIn: [Your LinkedIn Profile URL]

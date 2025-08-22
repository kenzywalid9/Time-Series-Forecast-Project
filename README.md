# Time Series Forecast Project

## Project Overview
This project predicts the **monthly demand** of various SKUs based on historical sales data from **2023 to 2025**. The goal is to provide **accurate forecasts** to optimize inventory management, plan business strategies, and support data-driven decision making.

The project applies **statistical, machine learning, and deep learning models** to ensure reliable predictions while generating actionable recommendations for inventory and sales planning.

---

## Dataset
The dataset contains **339,166 transactions** with the following columns:

| Column Name            | Description |
|------------------------|------------|
| MainID                 | Unique transaction ID |
| ItemId                 | SKU identifier |
| Qty                    | Quantity sold |
| Price                  | Item price |
| DiscountPercentage     | Discount percentage applied |
| DiscountValue          | Discount amount |
| PriceAfterDiscount     | Price after discount |
| TransactionDate        | Date of transaction |
| NameEn                 | Item name in English |



## 🔄 Workflow

```mermaid
flowchart LR
    A[Raw Data] --> B[Data Preprocessing]
    B --> C[Exploratory Data Analysis]
    C --> D[Model Training]
    D --> E[Evaluation Metrics]
    E --> F[Forecasting Results]
    F --> G[Business Recommendations]
```

**Data preprocessing steps:**
- Aggregated sales per SKU on a monthly basis.
- Handled missing values in `TransactionDate`.
- Analyzed trends, seasonality, and outliers.
- Created features for modeling: total monthly sales, average price, discount metrics.

---

## Features & Methodology
The project leverages three types of forecasting approaches:

###  Statistical Models
- **Prophet**: captures trend and seasonality in time series.
- **ARIMA**: models historical sales patterns for short-term forecasts.

###  Machine Learning Models
- **Decision Tree Regressor**: non-linear relationships modeling.
- **XGBoost Regressor**: robust gradient boosting for accurate predictions.

###  Deep Learning Models
- **LSTM (Long Short-Term Memory)**: captures long-term dependencies and trends in sequential data.

###  Business Analysis & Recommendations
- Identified top-selling SKUs for inventory prioritization.
- Suggested reorder quantities based on forecasted demand.
- Generated insights for strategic planning and sales optimization.

---

## Evaluation Metrics
Models are evaluated using:

| Metric | Description |
|--------|------------|
| RMSE   | Root Mean Squared Error |
| MAE    | Mean Absolute Error |
| R²     | Coefficient of Determination |

This allows comparison of models and selection of the most accurate forecasting approach

## Model Performance

###  Decision Tree
- **Train:**  
  - R²: 0.7485  
  - MAE: 0.8766  
  - RMSE: 5.8075  
  - SMAPE (All %): 11.74  
  - SMAPE (NonZero %): 48.96  
- **Test:**  
  - R²: 0.6761  
  - MAE: 1.1554  
  - RMSE: 9.2241  
  - SMAPE (All %): 13.60  
  - SMAPE (NonZero %): 47.11  

**Pros:** Fast training, interpretable, handles non-linear patterns moderately well.  
**Cons:** May overfit on training data, less accurate for complex seasonal patterns.

---

###  LSTM
- **MAPE:** 7.67%  
- Captures long-term dependencies and seasonal trends in sales.  
- Performs well on sequential data with time dependencies.  

**Pros:** Great for sequential and time-dependent patterns.  
**Cons:** Longer training time, requires more data, sensitive to hyperparameters.

---

###  XGBoost
- **Train:**  
  - R²: 0.825  
  - MAE: 6.009  
  - RMSE: 15.206  
- **Test:**  
  - R²: 0.723  
  - MAE: 5.204  
  - RMSE: 11.529  

**Pros:** Handles non-linear relationships, robust to outliers, fast and accurate.  
**Cons:** Can overfit if not properly tuned, less interpretable than Decision Tree.


---

## 🔍 Analysis Sections

### 1. Data Preprocessing & Cleaning
- **Data Loading**: Imports and merges invoice and product data
- **Data Filtering**: Applies 24-month minimum threshold for product analysis
- **Data Transformation**: Creates time-based features (Month, Year, Quarter)
- **Output**: Cleaned dataset with 195,199 transactions across 653 products

### 2. Sales Overview & Trends
- **Time Series Analysis**: Monthly sales trends visualization
- **Year-over-Year Growth**: Calculates and visualizes YoY growth rates
- **Key Findings**:
  - Steady growth through 2023-2024
  - Sharp acceleration in early 2025
  - Concerning decline in late 2025

### 3. Discount Strategy Analysis
- **Discount Penetration**: Only 3% of transactions use discounts
- **Revenue Impact**: Discounts reduce average revenue by 13%
- **Quantity Impact**: Discounts increase basket size from 7 to 17 items
- **Correlation Analysis**: Weak correlation between discounts and performance
- **Recommendations**: Focus on 10-20% discount range for optimal results

### 4. Product Performance Analysis
- **Revenue Leaders**: Specialty drugs dominate (VERZENIO: $61M, CYRAMZA: $20.6M)
- **Quantity Leaders**: Commodity items (syringes, OTC products)
- **ABC Classification**:
  - A Products (284): 80% of revenue
  - B Products (221): 15% of revenue
  - C Products (148): 5% of revenue
- **Low-Performing Items**: Products with heavy discounts but low sales

### 5. Quarterly Performance Analysis
- **Growth Phases**:
  - Initial Growth (2023Q2-Q4): Explosive expansion
  - Stabilization (2024Q1-Q4): Consistent performance
  - Volatility (2025): Extreme fluctuations
- **Quarter-over-Quarter Growth**: Tracks business maturity and recent concerns

## 📈 Key Insights

### Business Model
- **Two-tier structure**: High-value specialty drugs drive revenue, commodities drive volume
- **Revenue concentration**: 80% of revenue from top 43% of products
- **Specialty focus**: Pharmaceutical specialty treatments dominate revenue

### Performance Trends
- **Strong growth**: 2023-2024 showed consistent expansion
- **Recent volatility**: 2025 shows concerning fluctuations
- **Discount ineffectiveness**: Current discount strategy not driving desired results

### Strategic Implications
- **Protect A-category products**: Critical for 80% of revenue
- **Re-evaluate discounts**: Heavy discounts on low-demand items ineffective
- **Investigate volatility**: 2025 fluctuations require immediate attention

## Business Recommendations

### Immediate Actions
1. **Investigate 2025 volatility** - Identify root causes of recent fluctuations
2. **Review discount strategy** - Focus on proven price-sensitive products
3. **Protect A-category products** - Ensure supply chain and pricing optimization






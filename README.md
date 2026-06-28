# Retail Chain Sales — Regression-Based Business Insights
**Part 3 Project | Business Analytics**
**Analyst:** Jyoti Tomar

---

## Business Problem Summary

A retail chain operating across multiple regions and store formats wants to understand which operational and contextual factors are most strongly associated with monthly sales performance. Leadership is considering actions such as adjusting marketing budgets, improving inventory management, staffing strategies, and store format prioritisation. This project uses regression analysis to provide data-driven insights to guide those decisions.

---

## Dataset Description

**File:** `data/business_regression_data.xlsx`
**Records:** 320 observations
**Coverage:** 4 months (January–April 2025) across multiple stores

| Column | Type | Description |
|---|---|---|
| store_id | Categorical | Unique store identifier |
| month | Date | Month of observation |
| region | Categorical | Geographic region (East, West, North, South) |
| store_type | Categorical | Store format (Residential, High Street, Mall, Airport) |
| marketing_spend | Numerical | Monthly marketing investment (₹) |
| footfall | Numerical | Customer visits per month |
| avg_discount_pct | Numerical | Average discount percentage offered |
| staff_count | Numerical | Number of staff assigned |
| inventory_availability_pct | Numerical | % of products in stock |
| competitor_distance_km | Numerical | Distance to nearest competitor (km); 6 nulls filled with median |
| holiday_flag | Binary | 1 if month contains a major holiday |
| customer_rating | Numerical | Average customer satisfaction score; 8 nulls filled with median |
| **monthly_sales** | **Numerical** | **Target / Dependent Variable** |
| monthly_profit | Numerical | Not used in regression (outcome, not driver) |

### Data Cleaning Applied
- `competitor_distance_km`: 6 missing values → replaced with column median
- `customer_rating`: 8 missing values → replaced with column median

---

## Dependent and Independent Variables

- **Dependent Variable:** `monthly_sales`
- **Numerical Predictors:** `marketing_spend`, `footfall`, `avg_discount_pct`, `staff_count`, `inventory_availability_pct`, `competitor_distance_km`, `holiday_flag`, `customer_rating`
- **Categorical Predictors (encoded):** `region`, `store_type`
- **Excluded from regression:** `store_id` (identifier), `month` (date), `monthly_profit` (downstream outcome)

---

## Regression Approach

### Simple Regression Models (4 models)
Each model uses one numerical predictor to explain `monthly_sales`. This isolates the individual relationship between each variable and sales.

| Model | Independent Variable | R² |
|---|---|---|
| SR-1 | marketing_spend | 0.1672 |
| SR-2 | footfall | 0.7363 |
| SR-3 | inventory_availability_pct | 0.0131 |
| SR-4 | customer_rating | 0.0007 |

### Multiple Regression Model (1 model)
Combines 11 predictors (3 numerical core + 2 additional numerical + 6 dummy variables) to build a comprehensive sales model.

- **R² = 0.8321** | **Adj. R² = 0.8261**

---

## Dummy Variable Approach

Two categorical variables were converted to dummy variables using one-hot encoding with a reference category dropped:

- **`region`** → 3 dummies created (`rgn_North`, `rgn_South`, `rgn_West`) | **Reference: East**
- **`store_type`** → 3 dummies created (`stype_Airport`, `stype_High Street`, `stype_Mall`) | **Reference: Residential**

Dropping one reference category per group avoids the dummy variable trap (perfect multicollinearity). All dummy variable logic is documented in `outputs/model_equations.md`.

---

## Model Comparison Summary

| Model | R² | Adj. R² | Significant Variables |
|---|---|---|---|
| SR-1 (marketing_spend) | 0.1672 | 0.1646 | Yes |
| SR-2 (footfall) | 0.7363 | 0.7355 | Yes |
| SR-3 (inventory_availability_pct) | 0.0131 | 0.0100 | Yes |
| SR-4 (customer_rating) | 0.0007 | -0.0024 | No |
| MR (Full Model) | 0.8321 | 0.8261 | 9 out of 12 |

---

## Final Model Selected

> **Multiple Regression (MR)** — R² = 0.8321

The full multiple regression model outperforms all simple models and provides actionable insights across multiple business levers simultaneously.

---

## Business Recommendation

1. **Footfall growth initiatives** are the highest-leverage investment for sales uplift.
2. **Inventory availability** should be maintained above 92% across all stores.
3. **Marketing budgets** should be allocated by store type rather than applied uniformly.
4. **Airport and Mall stores** show structural sales advantages; regional strategy should reflect format-level differences.
5. Use **top-residual store analysis** to identify best-practice replication opportunities.

Full recommendation: `outputs/final_recommendation.md`

---

## Assumptions and Limitations

- Regression shows *association*, not causation — business experiments are needed to confirm direction of effect
- Dataset is limited to 4 months; no seasonality analysis is possible
- Variables such as pricing, product range, and local demographics are not available in the dataset
- Missing values were imputed with column medians; results may slightly differ with alternative imputation strategies

---

## Repository Structure

```
part3_regression_insights/
├── data/
│   └── business_regression_data.xlsx
├── analysis/
│   ├── regression_workbook.xlsx
│   ├── model_comparison.md
│   └── residual_analysis.md
├── outputs/
│   ├── regression_summary.xlsx
│   ├── final_recommendation.md
│   └── model_equations.md
├── screenshots/
│   ├── simple_regression_output.png
│   ├── multiple_regression_output.png
│   ├── residuals_preview.png
│   └── model_comparison_preview.png
└── README.md
```

---

## Screenshots Included

| File | Contents |
|---|---|
| `simple_regression_output.png` | Scatter plots + regression lines for all 4 simple models |
| `multiple_regression_output.png` | Full coefficient table with significance indicators |
| `residuals_preview.png` | Residual plots: scatter, Q-Q, histogram, and top outlier stores |
| `model_comparison_preview.png` | Model comparison table and R² bar chart |

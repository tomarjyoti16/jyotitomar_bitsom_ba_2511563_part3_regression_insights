# Residual Analysis Report
**Project:** Retail Chain Monthly Sales — Regression Analysis
**Analyst:** Jyoti Tomar
**Model Used:** Multiple Regression (MR)

---

## 1. What is a Residual?

A residual is the difference between the **actual monthly sales** of a store and the **sales predicted** by the regression model.

> **Residual = Actual Sales − Predicted Sales**

- A **positive residual** → the store performed *better* than the model expected
- A **negative residual** → the store performed *worse* than the model expected

---

## 2. Residuals Summary Statistics

| Metric | Value |
|---|---|
| Mean Residual | 0.00 |
| Std Dev of Residuals | 42,526.42 |
| Min Residual | -159,512.90 |
| Max Residual | 112,751.13 |
| Median Residual | -214.58 |

---

## 3. Top 5 Positive Residuals (Over-Performing Stores)

These stores outperformed their predicted sales — the model *underestimated* their revenue.

| Store ID | Month | Actual Sales (₹) | Predicted Sales (₹) | Residual (₹) |
|---|---|---|---|---|
| STR-1028 | 2025-04-01 | 713,611.16 | 600,860.03 | **112,751.13** |
| STR-1073 | 2025-03-01 | 813,316.71 | 707,150.00 | **106,166.71** |
| STR-1019 | 2025-03-01 | 788,087.68 | 695,490.42 | **92,597.26** |
| STR-1069 | 2025-04-01 | 686,737.87 | 595,017.79 | **91,720.08** |
| STR-1050 | 2025-04-01 | 735,786.64 | 646,314.27 | **89,472.37** |

**Business Interpretation:**
These stores appear to benefit from factors the model does not capture — such as local events, strong store management, exclusive product launches, or loyal repeat customer bases. They represent best-practice stores worth deeper investigation.

---

## 4. Top 5 Negative Residuals (Under-Performing Stores)

These stores sold less than predicted — the model *overestimated* their revenue.

| Store ID | Month | Actual Sales (₹) | Predicted Sales (₹) | Residual (₹) |
|---|---|---|---|---|
| STR-1017 | 2025-03-01 | 685,379.08 | 844,891.98 | **-159,512.90** |
| STR-1023 | 2025-02-01 | 627,171.90 | 773,115.05 | **-145,943.15** |
| STR-1012 | 2025-01-01 | 595,467.60 | 715,299.08 | **-119,831.48** |
| STR-1007 | 2025-02-01 | 800,451.94 | 913,150.73 | **-112,698.79** |
| STR-1014 | 2025-01-01 | 463,534.25 | 563,492.79 | **-99,958.54** |

**Business Interpretation:**
These stores underperformed despite comparable observable inputs. Possible unobserved causes include poor store management, local competition not captured by `competitor_distance_km`, supply chain issues, or operational inefficiencies that the dataset does not directly measure.

---

## 5. Systematic Over/Under Prediction Patterns

After reviewing residuals across store types and regions, the following observations were noted:

- **Airport stores** tend to produce slightly positive residuals — possibly due to captive customer bases with higher purchase intent not fully reflected by footfall and ratings alone.
- **High footfall months** (holiday periods) tend to generate positive residuals, suggesting the model underestimates peak-period uplift.
- Stores with **below-average inventory availability** (< 80%) show systematically negative residuals, confirming that stockouts suppress actual sales below what other factors would suggest.

---

## 6. Residual Diagnostics

- **Residuals vs Fitted Plot:** No strong funnel shape observed — variance appears roughly constant (homoscedastic).
- **Q-Q Plot:** Residuals approximate a normal distribution with slight tails at extremes.
- **Histogram:** Bell-shaped, centered near zero — no evidence of systematic directional bias.

---

## 7. Conclusion

The residual analysis confirms that the multiple regression model performs reasonably well. The outlier stores (both over- and under-performing) present actionable intelligence — particularly for store managers and regional teams looking to understand performance gaps.

# Model Comparison Report
**Project:** Retail Chain Monthly Sales — Regression Analysis
**Analyst:** Jyoti Tomar

---

## 1. Models Evaluated

Four simple regression models and one multiple regression model were built using `monthly_sales` as the dependent variable.

---

## 2. Comparison Table

| Model ID | Model Name | Variables Used | R-squared | Adj. R² | Significant Variables | AIC |
|---|---|---|---|---|---|---|
| SR-1 | Simple — Marketing Spend | marketing_spend | 0.1672 | 0.1646 | 1 | 8,244.5 |
| SR-2 | Simple — Footfall | footfall | 0.7363 | 0.7355 | 1 | 7,876.6 |
| SR-3 | Simple — Inventory Availability | inventory_availability_pct | 0.0131 | 0.0100 | 1 | 8,298.9 |
| SR-4 | Simple — Customer Rating | customer_rating | 0.0007 | -0.0024 | 0 | 8,302.9 |
| MR | Multiple — Full Model | 11 predictors | 0.8321 | 0.8261 | 9 | 7,752.2 |

---

## 3. R-squared Interpretation

- **SR-1 (Marketing Spend): R² = 0.1672** — Marketing spend alone explains about 16.7% of variability in monthly sales. Statistically significant.
- **SR-2 (Footfall): R² = 0.7363** — Footfall explains 73.6% of sales variance. Statistically significant.
- **SR-3 (Inventory Availability): R² = 0.0131** — Inventory levels explain 1.3% of sales variance. Statistically significant.
- **SR-4 (Customer Rating): R² = 0.0007** — Customer ratings explain 0.1% of sales variance. Not statistically significant.
- **MR (Full Model): R² = 0.8321** — All variables together explain 83.2% of sales variability. This is a substantial improvement.

---

## 4. Statistically Significant Variables (MR Model)
- **marketing_spend**: Coefficient = 1.20, p = 0.0000
- **footfall**: Coefficient = 34.00, p = 0.0000
- **inventory_availability_pct**: Coefficient = 3,001.99, p = 0.0000
- **customer_rating**: Coefficient = 13,627.39, p = 0.0046
- **rgn_South**: Coefficient = 18,685.41, p = 0.0093
- **rgn_West**: Coefficient = 18,110.86, p = 0.0040
- **stype_Airport**: Coefficient = 41,880.25, p = 0.0000
- **stype_High Street**: Coefficient = 18,092.55, p = 0.0027
- **stype_Mall**: Coefficient = 29,086.17, p = 0.0000

---

## 5. Business Usefulness Assessment

| Model | Business Usefulness | Key Limitation |
|---|---|---|
| SR-1 | Moderate — useful for marketing budget planning | Ignores all other drivers |
| SR-2 | High for single metric — footfall directly links to customers | Doesn't explain why footfall varies |
| SR-3 | Moderate — inventory availability matters but has narrow R² | Most stores already have high availability |
| SR-4 | Low individual R² — rating has structural explanatory limits | Endogenous: sales also affect ratings |
| MR | **Highest** — captures multi-factor dynamics | Cannot establish causal direction alone |

---

## 6. Limitations

- The dataset covers only **4 months** of data per store; seasonal effects beyond this window are not captured.
- No data on **pricing** or **product mix**, both of which influence sales significantly.
- Footfall likely correlates with store type and location; multicollinearity may be present.
- Regression explains association — causation requires controlled experiments.

---

## 7. Selected Final Model

> **Multiple Regression (MR)** is selected as the final model. It achieves R² = 0.8321 and covers the multi-dimensional nature of retail sales performance. The inclusion of store type and region dummies makes it actionable across business units.

# Regression Model Equations
**Project:** Retail Chain Monthly Sales — Regression Analysis
**Analyst:** Jyoti Tomar

---

## 1. Simple Regression Equations

### SR-1: Marketing Spend Model
> **Monthly Sales = 560,777.35 + 2.1296 × marketing_spend**

- For every ₹1 increase in marketing spend, monthly sales change by approximately ₹2.1296
- R² = 0.1672 — marketing spend alone explains 16.7% of sales variation
- P-value = 0.000000 — **Statistically significant**

### SR-2: Footfall Model
> **Monthly Sales = 446,410.58 + 35.6780 × footfall**

- Each additional customer walking in per month is associated with ₹35.6780 in sales
- R² = 0.7363 — footfall explains 73.6% of sales variation
- P-value = 0.000000 — **Statistically significant**

### SR-3: Inventory Availability Model
> **Monthly Sales = 484,814.26 + 2,217.8319 × inventory_availability_pct**

- A 1% point increase in inventory availability is associated with ₹2,217.8319 change in sales
- R² = 0.0131
- P-value = 0.040625 — **Statistically significant**

### SR-4: Customer Rating Model
> **Monthly Sales = 701,366.86 + -5,284.8663 × customer_rating**

- A 1-point increase in average customer rating is linked to ₹-5,284.8663 change in sales
- R² = 0.0007
- P-value = 0.637644 — Not statistically significant

---

## 2. Multiple Regression Equation

The final selected model uses 11 independent variables including numerical predictors and dummy variables:

> **Monthly Sales = 49,912.80**
> **+ 1.2004 × marketing_spend**  *(p < 0.05)*
> **+ 34.0032 × footfall**  *(p < 0.05)*
> **− 45,708.5494 × avg_discount_pct**
> **+ 3,001.9911 × inventory_availability_pct**  *(p < 0.05)*
> **+ 13,627.3901 × customer_rating**  *(p < 0.05)*
> **+ 6,184.5087 × rgn_North**
> **+ 18,685.4081 × rgn_South**  *(p < 0.05)*
> **+ 18,110.8609 × rgn_West**  *(p < 0.05)*
> **+ 41,880.2451 × stype_Airport**  *(p < 0.05)*
> **+ 18,092.5519 × stype_High Street**  *(p < 0.05)*
> **+ 29,086.1665 × stype_Mall**  *(p < 0.05)*

---

## 3. Dummy Variable Explanation

### Why Dummy Variables?

Regression requires numerical inputs. `region` and `store_type` are categorical — they contain labels (text), not numbers. To include them, each category is converted to a binary (0/1) column.

### Region Dummy Variables

| Original Value | rgn_North | rgn_South | rgn_West |
|---|---|---|---|
| East (Reference) | 0 | 0 | 0 |
| North | 1 | 0 | 0 |
| South | 0 | 1 | 0 |
| West | 0 | 0 | 1 |

> **Reference Category: East Region**
> The coefficient of `rgn_North`, for example, tells us how much more (or less) sales a North store generates compared to an East store, holding all other factors constant.

### Store Type Dummy Variables

| Original Value | stype_Airport | stype_High Street | stype_Mall |
|---|---|---|---|
| Residential (Reference) | 0 | 0 | 0 |
| Airport | 1 | 0 | 0 |
| High Street | 0 | 1 | 0 |
| Mall | 0 | 0 | 1 |

> **Reference Category: Residential Store**
> The coefficient of `stype_Airport` tells us the expected difference in monthly sales between an Airport store and a Residential store, given the same numerical inputs.

### Why Not Include All Categories?

Including all categories creates a **dummy variable trap** — perfect multicollinearity, where one category is always predictable from the others. This makes regression mathematically impossible to solve. By dropping one reference category per group, we avoid this problem.

---

## 4. Final Model Selected

**Selected Model: Multiple Regression (MR)**

Reason: The multiple regression model achieves R² = 0.8321, explaining 83.2% of monthly sales variability. It incorporates both numerical drivers (footfall, marketing, inventory) and structural factors (store type, region), making it directly actionable for leadership decisions. No single simple regression model comes close to this explanatory power.

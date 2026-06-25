# jyotitomar_bitsom_ba_2511563_part3_regression_insights
| Category                  | Variables                                                                                                                                                    |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Dependent Variable        | monthly_profit                                                                                                                                               |
| Numerical Variables       | marketing_spend, footfall, avg_discount_pct, staff_count, inventory_availability_pct, competitor_distance_km, customer_rating, monthly_sales, monthly_profit |
| Categorical Variables     | store_id, region, store_type                                                                                                                                 |
| Binary Variable           | holiday_flag                                                                                                                                                 |
| Needs Cleaning            | competitor_distance_km, customer_rating                                                                                                                      |
| Needs Encoding            | region, store_type                                                                                                                                           |
| Needs Date Transformation | month                                                                                                                                                        |
| Not Useful                | store_id                                                                                                                                                     |
| Potential Leakage Risk    | monthly_sales (when predicting monthly_profit)                                                                                                               |

# Retail Sales & Profitability Analysis

Portfolio project | Data Analyst Intern | Python · Google Colab · Pandas · NumPy · Matplotlib · Seaborn · Power BI

## Project overview

This project analyzes order-level sales and profit data from a retail business to understand which categories, regions, customer segments and discount levels drive or erode profitability. It complements a separate HR employee attrition analysis project.

The unit of analysis is one order line. This is a descriptive analytics project, not a machine learning or causal inference study.

## Business objectives and questions

1. Measure overall sales, profit, profit margin and average order value.
2. Identify which categories and sub-categories generate or lose profit.
3. Compare performance across regions and customer segments.
4. Examine monthly sales patterns across 2024 and 2025.
5. Assess how discount levels relate to profit and to loss-making orders.
6. Develop testable recommendations to improve profitability.

## Dataset

`Retail_Sales_Cleaned.csv` is a **synthetic dataset created for this portfolio project**. It does not contain real business data, and the findings below illustrate an analytical workflow rather than real company performance.

| Property | Value |
|---|---|
| Rows | 500 orders |
| Period | 2024-01-01 to 2025-12-31 |
| Missing values | 0 |
| Duplicate rows / duplicate Order_ID | 0 / 0 |

| Column | Description |
|---|---|
| Order_ID | Unique order identifier |
| Order_Date | Date of the order |
| Region | North, South, East, West |
| Segment | Consumer, Corporate, Home Office |
| Category | Furniture, Office Supplies, Technology |
| Sub_Category | Bookcases, Tables, Chairs, Paper, Binders, Storage, Phones, Accessories, Copiers |
| Quantity | Units ordered |
| Unit_Price | Price per unit before discount |
| Discount | Discount rate (0 to 0.40) |
| Sales | Quantity × Unit_Price × (1 − Discount) |
| Profit | Profit on the order (negative values are losses) |

## Tools and technologies

Python, Pandas, NumPy, Matplotlib, Seaborn, Google Colab, Power BI Desktop.

## Analysis workflow

1. Load `Retail_Sales_Cleaned.csv` and inspect dimensions, data types, missing values, duplicates and descriptive statistics.
2. Validate required columns, date format, unique Order_ID, discount range, and that Sales equals Quantity × Unit_Price × (1 − Discount).
3. Create Year, Month, loss-order flag and discount band features.
4. Calculate sales and profit KPIs.
5. Analyze performance by category, sub-category, region, segment, month and discount level.
6. Visualize results and generate data-derived insights.
7. Build an interactive Power BI dashboard from the same dataset.

## KPIs and methodology

| KPI | Definition |
|---|---|
| Total Orders | Count of order rows |
| Total Sales | Sum of Sales |
| Total Profit | Sum of Profit |
| Profit Margin | Total Profit / Total Sales × 100% |
| Average Order Value | Total Sales / Total Orders |
| Loss-making Orders | Count of orders with Profit < 0 |
| Loss-making Share | Loss-making Orders / Total Orders × 100% |

Group-level profit margin is calculated as the group's total profit divided by the group's total sales, not as an average of order-level margins.

## Key findings

| KPI | Value |
|---|---|
| Total Orders | 500 |
| Total Sales | 324,901.19 |
| Total Profit | 40,799.54 |
| Profit Margin | 12.56% |
| Average Order Value | 649.80 |
| Loss-making Orders | 108 (21.6%) |

**Category and sub-category**

| Category | Sales | Profit | Margin |
|---|---|---|---|
| Technology | 215,941.05 | 38,562.09 | 17.86% |
| Office Supplies | 24,295.15 | 3,295.88 | 13.57% |
| Furniture | 84,664.99 | −1,058.43 | −1.25% |

- Technology generates 66.5% of sales and 94.5% of profit. Copiers alone contribute 26,493.95 in profit (64.9% of total profit).
- Furniture accounts for 26.1% of sales but has a negative total profit. Tables (−1,041.48) and Bookcases (−1,183.17) are the only loss-making sub-categories.

**Region and segment**

- Profit margins are similar across regions (12.22% to 13.16%) and segments (11.92% to 13.11%). East has the highest sales (107,456.06) and North the highest margin (13.16%).
- Consumer is the largest segment, with 167,873.51 in sales (51.7% of total).

**Monthly trend**

- Combined 2024–2025 sales are highest in November and December. Month-level patterns are based on only two years of data.

**Discount impact**

| Discount | Orders | Profit | Margin | Loss-making orders |
|---|---|---|---|---|
| 0% | 185 | 31,000.90 | 20.59% | 0.5% |
| 5% | 89 | 8,148.66 | 14.59% | 7.9% |
| 10% | 66 | 4,585.31 | 11.46% | 19.7% |
| 20% | 78 | 916.64 | 2.18% | 30.8% |
| 30% | 53 | −1,503.37 | −5.94% | 64.2% |
| 40% | 29 | −2,348.60 | −21.21% | 100.0% |

- Profit margin declines at every step of discounting, and total profit turns negative from a 30% discount.
- Orders with a discount of 30% or more make up 16.4% of orders and 11.2% of sales, yet 76.8% of them are loss-making and together they lose 3,851.97.

## Business recommendations

These are hypotheses for further measurement or A/B testing, not claims of proven uplift.

1. Test a cap on discounts at 20% and measure the effect on profit and order volume, since discounts of 30% or more are associated with losses.
2. Review pricing and cost structure for Tables and Bookcases to understand why Furniture is unprofitable even at moderate discount levels.
3. Protect the Technology category, particularly Copiers and Phones, which drive most of the profit.
4. Plan inventory and marketing capacity around the November–December sales peak, and validate the pattern with additional years of data.
5. Track profit margin alongside sales in regular reporting, because regional and segment sales differences are larger than their margin differences.

## Power BI dashboard

The dashboard is built from `Retail_Sales_Cleaned.csv` and includes KPI cards (Total Sales, Total Profit, Profit Margin %), monthly sales trend, sales and profit by category, sales by region, profit by discount level, and slicers for Segment and Region.

![Retail Sales Profitability Dashboard](Retail%20Sales%20Profitability%20Analysis.png)

## Repository files

| File | Description |
|---|---|
| `Retail Sales Profitability Analysis.pbix` | Power BI dashboard |
| `Retail Sales Profitability Analysis.png` | Dashboard screenshot |
| `Retail_Sales_Cleaned.csv` | Cleaned synthetic dataset |
| `Retail_Sales_Profitability_Analysis.ipynb` | Python analysis notebook |
| `README.md` | Project documentation |

## How to run in Google Colab

1. Download `Retail_Sales_Profitability_Analysis.ipynb` and `Retail_Sales_Cleaned.csv`.
2. Open Google Colab → File → Upload notebook, and select the notebook.
3. Open the Files panel on the left and upload `Retail_Sales_Cleaned.csv` to the session storage.
4. Select Runtime → Run all.
5. Review the data validation, KPIs, charts and insights.

If the CSV has missing required columns or invalid values, the notebook raises a descriptive error.

## Limitations

- The dataset is synthetic; results illustrate the workflow and are not real business findings.
- The analysis is descriptive. Associations between discount and profit do not establish causation.
- Each row is an order line; customer-level behavior and repeat purchases cannot be analyzed.
- Two years of data are not enough to separate seasonality from one-off variation.
- Profit is provided as a single field; individual cost components are not available.

# Retail Sales Data Analysis (10M+ records)

Exploratory and statistical analysis of a retail point-of-sale dataset with **over 10 million receipt lines** (April–May 2024), carried out in **R** as the final project of the Code Academy Data Analytics Programme.

📊 **Presentation:** [Google Slides](https://docs.google.com/presentation/d/15VCLNE1t9aoOvU9SwKlDoElEKDCDwKsK/edit?usp=sharing&ouid=106900150251620870387&rtpof=true&sd=true)


## Goals
- Describe overall sales volume, number of points of sale and average daily revenue
- Compare food vs non-food sales by month
- Find top products and top points of sale, and investigate anomalies (unusual quantities and prices)
- Model total sales and identify weekday patterns and profit-margin distribution

## Data
| Table | Description | Size |
|---|---|---|
| `fp_receipts` | Receipt lines: POS, date, receipt ID, product, quantity, unit price | ~10.0M rows |
| `qara` | Cleaned receipt data with totals and store groups | ~9.8M rows |
| `fp_map` | Product mapping: product type (food / non-food), profit margin | ~118K rows |
| `ag` | Aggregated modelling table (weekday, period, product type, margin) | ~440K rows |

> The raw `.rds` data files are not included in this repository because of their size and confidentiality.

## Methods
- **Data wrangling:** `dplyr`, `tidyr`, `lubridate`, `stringr`
- **Descriptive statistics:** sales totals, distinct POS count, revenue per day, monthly food / non-food split
- **Anomaly analysis:** top-20 products by quantity and top-20 store groups by sales; drill-downs into pharmacy, furniture, electronics and tobacco prices
- **Modelling:** linear regression `Total ~ unit_price + qnt + product_type + weekday + period`
- **Visualisation:** `ggplot2`, `plotly`, `ggraph`

## Key results
- The regression model explains **~92% of the variance in sales totals** (R² = 0.9235, p < 2.2e-16), with unit price and quantity as the strongest drivers.
- Sales were broken down by weekday to show which days bring the most revenue.
- Profit-margin categories reveal how transactions are distributed across margin bands, including negative-margin outliers.
- Several pricing and quantity anomalies were flagged for specific products and store groups.

## Repository structure
```
├── analysis/
│   └── retail_sales_analysis.Rmd   # R Markdown source code
├── report/
│   └── retail_sales_analysis.html  # Rendered report with all outputs and charts
└── README.md
```

## How to run
1. Install R and the packages: `ggplot2, dplyr, readr, readxl, lubridate, plotly, stringr, widyr, tidyverse, tidygraph, ggraph, igraph, tidyr, scales`
2. Put the `.rds` data files in the same folder as the `.Rmd`
3. Open `analysis/retail_sales_analysis.Rmd` in RStudio and click **Knit**

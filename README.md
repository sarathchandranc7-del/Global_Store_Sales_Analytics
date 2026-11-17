# Superstore Sales Profitability Analysis: Project Proposal


**Domain:** Retail and Sales Analytics (Multi-Market, Multi-Category)


## Project Overview

This project examines four years of transaction records (orders placed from 1 January 2011 to 31 December 2014) from a superstore business. Each record describes one order line: what was sold, to whom, where, how it was shipped, and what it earned or lost. The dataset contains 51,290 records and 27 columns.

The business records show sales volume, but volume alone does not show whether the business is healthy. This project looks at how much profit each part of the business generates and where losses come from.

## Business Problem

Sales managers need to know which sub-categories, markets, and customer segments make money and which lose it. The dataset shows high sales in some markets, but sales alone do not show whether the business is healthy. This analysis asks whether discounting is a major cause of losses, and where in the business the losses are concentrated, so that discount and pricing decisions can be based on evidence.

## Project Objectives

1. Calculate total sales, total profit, and profit margin (sum of profit ÷ sum of sales) for each Sub-Category and Market, 2011–2014.
2. Measure the share of order lines with negative profit at each discount level, and identify the lowest discount level at which more than half of order lines are loss-making.
3. Compare profit margin across the three Segments (Consumer, Corporate, Home Office) and the four Ship Modes, using ship_mode retained in the cleaned data.
4.Track sales, profit, and margin year by year from 2011 to 2014, and identify the market with the largest year-on-year change in margin.

## Business Value & Use Case

- **Sales and pricing managers** can use the discount-level results to set discount limits or approval rules.
- **Category managers** can decide which sub-categories to promote, reprice, or review.
- **Regional leads** can compare market performance on profit, not only on sales.
- **Finance teams** can use the margin figures to prioritise cost reviews in loss-making areas.

## Dataset Information

| Attribute | Details |
|---|---|
| Dataset | Superstore sales orders |
| Source | [Add original source URL and attribution before sharing] |
| File format | CSV (UTF-8) |
| Number of records | 51,290 |
| Number of columns | 27 |
| Unit of observation | Order line (`Row.ID`) |
| Time period | Orders from 2011-01-01 to 2014-12-31 (ship dates extend to 2015-01-07) |
| Domain | Retail and sales analytics |

**Dataset source:** [Kaggle – Global Superstore Dataset](https://www.kaggle.com/code/abdelazizelserty/global-superstore-dataset)

Key fields include `Order.Date`, `Ship.Date`, `Category`, `Sub.Category`, `Product.Name`, `Sales`, `Quantity`, `Discount`, `Profit`, `Shipping.Cost`, `Segment`, `Market`, `Region`, `Country`, `State`, `City`, and `Ship.Mode`.

Each row represents one order line, and an `Order.ID` may appear on more than one row.

## Tools and Technologies

- **Python**: data analysis
- **Pandas**: loading, inspection, and tabular analysis
- **NumPy**: numerical operations
- **Matplotlib** and **Seaborn**: data visualization
- **Jupyter Notebook**: interactive analysis and documentation
- **GitHub**: version control and project presentation

## Project Workflow

1. **Understand the data**: load the dataset and inspect its dimensions, columns, data types, and sample records.
2. **Prepare the data**: convert dates, check for missing values and duplicates, and review redundant columns.
3. **Summarize performance**: calculate sales, profit, and margin by category, market, and segment.
4. **Analyze discounts and time**: examine loss-making share by discount level and trends by year.
5. **Visualize results**: use charts to communicate patterns clearly.
6. **Interpret findings**: discuss what the results suggest, along with their limitations.

## Repository Structure

```
Superstore-Sales-Analytics/
│
├── Data/
│   └── superstore.csv
│
├── Global_sales_analytics.ipynb
├── Global_sales_analytics_phase_2.ipynb
│
├── Superstore_Sales_Analytics_SRS2.docx
│   
│
└── README.md
```

- `data/superstore.csv`: original dataset.
- `Global_sales_analytics.ipynb`: data loading, inspection, and quality checks.
- `Global_sales_analytics_phase_2`: data cleaning, column insertion 
- `documentation/Project_Proposal.md`: project title, objectives, dataset details, planned analysis, and scope.
- `documentation/Superstore_Sales_Analytics_SRS2.docx`: software requirements specification.
- `README.md`: project overview and instructions.

## How to Run

1. Clone or download the repository.
2. Install the required libraries: `pip install pandas numpy matplotlib seaborn jupyter`.
3. Open `Global_sales_analytics.ipynb` from the project root so the relative path `data/superstore.csv` resolves.
4. Run all cells from top to bottom.

## Scope and Limitations

- The dataset covers 2011 to 2014 only and may not reflect current business conditions.
- The analysis uses only the variables in the dataset. Costs such as overheads, staff, and rent are not included.
- The dataset contains no negative sales values, so returns do not appear to be recorded.
- `Region` and `Market` labels overlap (for example, "Africa" and "EMEA" appear in both), which affects market-level comparisons.
- Associations between discounts, segments, or markets and profit do not establish causation.
- The project provides analytical insights only and does not give business or financial advice.

## Project Status


### Phase 1: Select the raw data — complete

The selected file is `superstore_data.csv`. It contains **51,290 order lines and 27 columns**. The order dates run from **1 January 2011 to 31 December 2014**. Each row represents one order line, identified by `Row.ID`; an `Order.ID` can appear on several rows.

The dataset reference provided for this project is [Global Superstore Dataset on Kaggle](https://www.kaggle.com/code/abdelazizelserty/global-superstore-dataset). Confirm the original source and license before publishing or sharing the data.

### Phase 2: Clean and prepare the data — complete in the notebook

The Phase 2 notebook records these steps:

- Checked for missing values and exact duplicate rows. The initial checks found none; `Row.ID` is unique.
- Removed the redundant columns `记录数`, `Market2`, and `weeknum`, then standardized column names.
- Converted `order_date` and `ship_date` to dates and checked that shipping did not occur before ordering.
- Added `profit_status`, `ship_days`, `unit_price` (sales per unit), and `profit_margin` (`profit / sales`).
- Excluded the one row with zero sales, identified as `Row.ID 35398` (original DataFrame index `46158`). It also has recorded profit of `-1.11`; the notebook should keep this exclusion documented.

Following those steps, the cleaned table should contain **51,289 rows and 28 columns**. The separately exported cleaned file should be checked against these counts before submission.

### Phase 3: Exploratory analysis and findings — complete in the notebook

The Phase 3 analysis records these steps:

- Profiled profit by country, city, segment, and market-region, and identified the five countries with the largest total losses.
- Built a market-region scorecard. Southeast Asia has the lowest margin of the large regions (2.0% on about 884k in sales).
- Broke Southeast Asia down by country and sub-category. Four countries (Philippines, Thailand, Myanmar, Vietnam) lose about 27k in total. Tables, Accessories, and Supplies are the largest loss-making sub-categories in the region.
- Measured margin and loss share by discount band. Margin turns negative above about 20–30% discount, and 92.2% of total loss value comes from lines with discounts above 20%.
- Compared Southeast Asia with the rest of the company at each discount level. Margins are similar at the same discount level. Southeast Asia gives discounts above 20% on 57% of its order lines, compared with 20% elsewhere.
- Tested the discount effect on Chairs. Chairs earn 17.6% at 0–20% discount and lose money above 20% (−10.3% at 21–40%, −81.6% above 40%).

Open items before final submission: the year-by-year trend, the segment and ship mode margins, correction of the region-name grouping in the quarterly and regional charts, city analysis grouped by city and country, and the loss share calculated for Southeast Asia alone.

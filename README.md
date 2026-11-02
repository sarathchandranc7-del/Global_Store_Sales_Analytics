# Superstore Sales Profitability Analysis

Exploring four years of superstore order data to understand which categories, markets, and discount levels drive profit and loss.

## Project Overview

Sales volume alone does not show whether a retail business is healthy. This project examines order-line records from a superstore business to see how much profit each part of the business generates and where losses come from.

The dataset covers orders placed from 1 January 2011 to 31 December 2014 and contains 51,290 rows and 27 columns. It includes sales, profit, discount, shipping, product, customer, and location fields.

## Business Problem

Sales and pricing managers need to know which product categories, markets, and customer segments make money and which lose it. Discounts can increase sales but may also reduce margins.

This project addresses the following question:

Which categories, markets, segments, and discount levels are associated with profit and loss in superstore orders from 2011 to 2014?

The analysis describes patterns in the data. It does not establish the causes of losses on its own.

## Project Objectives

1. Calculate total sales, total profit, and profit margin for each category, sub-category, and market.
2. Measure the share of loss-making order lines at each discount level.
3. Compare profit margin across segments and ship modes.
4. Track sales, profit, and margin by year from 2011 to 2014.

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

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
│
├── Superstore_Sales_Analytics_SRS2.docx
│   
│
└── README.md
```

- `data/superstore.csv`: original dataset.
- `Global_sales_analytics.ipynb`: data loading, inspection, and quality checks.
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

The dataset has been loaded and inspected, and the project scope, objectives, and planned analysis are documented. Exploratory analysis, visualizations, and findings are still to be completed.

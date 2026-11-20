# Superstore Sales Profitability Analysis: Project Proposal

**Domain:** Retail and Sales Analytics (Multi-Market, Multi-Category)

## Project Overview

This project examines four years of transaction records (orders placed from 1 January 2011 to 31 December 2014) from a superstore business. Each record describes one order line: what was sold, to whom, where, how it was shipped, and what it earned or lost. The dataset contains 51,290 records and 27 columns. After one zero-sales row was removed, 51,289 records were analysed.

Sales volume alone does not show whether the business is healthy. This project measures how much profit each part of the business generates and where losses come from.

## Business Problem

Sales managers need to know which sub-categories, markets, and customer segments make money and which lose it. High sales in some markets do not show whether the business is healthy. This analysis asks whether discounting is a major cause of losses, and where in the business the losses are concentrated, so that discount and pricing decisions can be based on evidence.

## Project Objectives

1. Calculate total sales, total profit, and profit margin (sum of profit ÷ sum of sales) for each Sub-Category and Market, 2011–2014.
2. Measure the share of order lines with negative profit at each discount level, and identify the lowest discount level at which more than half of order lines are loss-making.
3. Compare profit margin across the three Segments (Consumer, Corporate, Home Office) and the four Ship Modes.
4. Track sales, profit, and margin year by year from 2011 to 2014, and identify the market with the largest year-on-year change in margin.

## Objective Status

| # | Objective | Status |
|---|---|---|
| 1 | Sales, profit, and margin by sub-category and market | Covered |
| 2 | Loss share by discount level and lowest threshold | Covered |
| 3 | Margin by segment and ship mode | Covered |
| 4 | Year-by-year margin and largest market change | Not covered in this submission |

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
| Number of records | 51,290 (51,289 after removing one zero-sales row) |
| Number of columns | 27 (30 after cleaning and feature creation) |
| Unit of observation | Order line (Row.ID) |
| Time period | Orders from 2011-01-01 to 2014-12-31 (ship dates extend to 2015-01-07) |
| Domain | Retail and sales analytics |

Dataset source: Kaggle – Global Superstore Dataset

Key fields include Order.Date, Ship.Date, Category, Sub.Category, Product.Name, Sales, Quantity, Discount, Profit, Shipping.Cost, Segment, Market, Region, Country, State, City, and Ship.Mode.

Each row represents one order line, and an Order.ID may appear on more than one row.

## Tools and Technologies

- **Python:** data analysis
- **Pandas:** loading, inspection, and tabular analysis
- **NumPy:** numerical operations
- **Matplotlib and Seaborn:** data visualization
- **Plotly:** interactive discount chart
- **Jupyter Notebook:** interactive analysis and documentation
- **GitHub:** version control and project presentation

## Project Workflow

1. **Understand the data:** load the dataset and inspect its dimensions, columns, data types, and sample records.
2. **Prepare the data:** convert dates, check for missing values and duplicates, and review redundant columns.
3. **Summarize performance:** calculate sales, profit, and margin by sub-category, market, segment, and ship mode.
4. **Analyze discounts:** examine loss-making share by discount level.
5. **Visualize results:** use charts to communicate patterns clearly.
6. **Interpret findings:** discuss what the results suggest, along with their limitations.

## Repository Structure

```
Superstore-Sales-Analytics/
│
├── data/
│   └── superstore_data.csv
|
│── Global_sales_analytics.ipynb
├── Global_sales_analytics_phase_2.ipynb
├── Global_sales_analytics_phase_3.ipynb
│
├── Superstore_Sales_Analytics_SRS2.docx
│
└── README.md
```

- `data/superstore_data.csv`: original dataset.
- `Global_sales_analytics_phase_2.ipynb`: data cleaning, feature creation,
- `Global_sales_analytics_phase_3.ipynb`: the analysis notebook for the final submission
- `Superstore_Sales_Analytics_SRS2.docx`: software requirements specification.
- `README.md`: project overview, objectives, instructions, and findings.



## How to Run

1. Clone or download the repository.
2. Install the required libraries: `pip install pandas numpy matplotlib seaborn plotly jupyter`
3. Open the notebook from the project root so the relative path `data/superstore_data.csv` resolves.
4. Run all cells from top to bottom: **Kernel → Restart & Run All**.

## Scope and Limitations

**In scope:**
- Descriptive analysis of order-line sales, profit, discount, and margin, 2011–2014.
- Sales, profit, and margin by sub-category and market.
- Share of loss-making order lines at each discount level.
- Margin by customer segment and ship mode.

**Not covered in this submission:**
- Year-by-year sales, profit, and margin, and the market with the largest year-on-year change (Objective 4).
- Forecasting, customer churn, and costs not in the dataset (overheads, staff, rent).

**Limitations:**
- The dataset covers 2011 to 2014 only and may not reflect current business conditions.
- The dataset has no cost detail, so profit is before overheads.
- The analysis is descriptive. Discounts and losses occur together, but the data does not show that discounts cause the losses.
- The discount threshold uses discount levels with at least 30 order lines. Levels with fewer lines were excluded, because their loss share can be misleading.
- Region and Market labels overlap (for example, "Africa" and "EMEA" appear in both), so regions are always grouped by market and region together.
- Counts of orders use unique order IDs where stated. Other counts are order lines.
- No negative sales values appear, so returns are assumed to be unrecorded.
- The project provides analytical insights only and does not give business or financial advice.

## Project Status

### Phase 1: Select the raw data

- Loaded `superstore_data.csv` and inspected its shape, columns, data types, and sample records.
- Confirmed 51,290 order lines and 27 columns.
- Order dates run from 1 January 2011 to 31 December 2014. Ship dates extend to 7 January 2015.
- Each row is one order line, identified by Row.ID.

### Phase 2: Clean and prepare the data

**Quality checks:**
- No missing values in any column.
- No duplicate rows.
- Row.ID is unique across all rows.

**Cleaning steps:**
- Removed three columns: `记录数`, `Market2` (which merges US and Canada into "North America"), and `weeknum`.
- Standardised column names to lowercase with underscores.
- Converted `order_date` and `ship_date` to date type.
- Converted `sales` and `profit` to numeric and rounded to two decimal places.
- Rounded `discount` to two decimal places, so that values such as 0.20 and 0.202 are grouped together.
- Confirmed no shipment occurred before its order date.
- Removed one row with zero sales. It has recorded profit of −1.11 and an 80% discount, and no sales base for a margin calculation.

**Features added:**
- `profit_status`: loss, profit, or break-even for each order line. About 24.5% of lines are losses.
- `ship_days`: days between order and shipment.
- `unit_price`: sales per unit.
- `quarter`: quarter of the order date.
- `market_region`: market and region combined, used for all region groupings.
- `profit_margin`: row-level profit ÷ sales. Used only for row-level checks. Totals and group margins are calculated as sum of profit ÷ sum of sales.

**Result:** 51,289 rows and 30 columns after cleaning.

### Phase 3: Exploratory analysis and findings 

**Countries and cities**
- The United States leads on sales (about 2.30M) and profit (about 286k).
- The five countries with the largest total losses are Turkey (−98,447), Nigeria (−80,751), Netherlands (−41,070), Honduras (−29,482), and Pakistan (−22,447).
- New York City leads the top five cities by sales. Manila is the only top-five city that loses money (−11,159).

**Regional margins**
- Canada has the highest margin (26.62%), on small volume.
- APAC North Asia is next at 19.52%.

**Southeast Asia**
- Four countries lose money: Philippines (−8.79%), Thailand (−9.49%), Myanmar (−6.18%), and Vietnam (−2.84%). Together they lose about 27.4k.
- Cambodia (25.62%) and Singapore (21.98%) are profitable.
- Indonesia has the largest sales in the region (404,887) but a margin of 3.86%.
- By sub-category, Tables lose the most (−18,618), followed by Accessories (−8,642) and Supplies (−4,034). Phones (+13,452) and Copiers (+11,356) are the largest gains.

**Sub-category by market**
- Tables have negative margins in four markets: EU (−19.93%), APAC (−8.94%), US (−8.56%), and LATAM (−8.49%). The EU result is the largest.
- The Tables problem is therefore not limited to Southeast Asia.

**Segment and ship mode**
- [Insert margin values for each segment and ship mode from the chart output.]

**Discounts and losses**
- The share of order lines with a loss rises with discount. The first discount level where more than half of lines lose money is about 20%, based on the 20.2% level with 41 order lines.
- [Confirm this threshold after rounding discounts, and insert the printed value.]
- Order lines with discounts above 20% account for 92.0% of total loss value. This is a company-wide figure.
- This is an association in the data, not proof that discounts cause losses.

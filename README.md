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

**Objective:** Confirm the dataset is the right one and understand its structure before any cleaning.

**What was done:**
- Selected the file `superstore_data.csv`.
- Loaded it into a pandas DataFrame and inspected its shape, column names, data types, and sample records.
- Confirmed the scope of the data: **51,290 order lines and 27 columns**.
- Checked the time coverage: order dates run from **1 January 2011 to 31 December 2014**. Ship dates extend to **7 January 2015**, because some orders placed late in 2014 shipped in early 2015.

**Key facts established:**
- Each row is one order line, identified by `Row.ID`. An `Order.ID` can appear on several rows, so counts of "orders" are counts of order lines unless stated otherwise.
- The data includes sales, quantity, discount, profit, and shipping cost, plus location fields (market, region, country, state, city), product fields (category, sub-category, product name), segment, and ship mode.
- Some column names are in Chinese (`记录数`), and `Market2` duplicates part of the `Market` information. Both are handled in Phase 2.

**Source:** [Global Superstore Dataset on Kaggle](https://www.kaggle.com/code/abdelazizelserty/global-superstore-dataset). Confirm the original source and license before publishing or sharing the data.

### Phase 2: Clean and prepare the data — complete in the notebook

**Objective:** Make the data reliable and usable for analysis without changing any recorded values, other than removing one zero-sales row.

**Quality checks:**
- Checked for missing values in every column. None were found.
- Checked for exact duplicate rows. None were found.
- Confirmed `Row.ID` is unique across all 51,290 rows.

**Cleaning steps:**
- Removed three redundant columns: `记录数`, `Market2` (which merges US and Canada into "North America"), and `weeknum`.
- Standardized column names to lowercase with underscores, so `Order.Date` became `order_date`.
- Converted `order_date` and `ship_date` to date type, normalized to midnight.
- Converted `sales` and `profit` to numeric and rounded to two decimal places.
- Checked that no shipment occurred before its order date.
- Excluded the one row with zero sales, identified as `Row.ID 35398` (original DataFrame index `46158`). It has recorded profit of −1.11 and an 80% discount, and it has no sales base for a margin calculation. This exclusion is documented in the notebook.

**Features added:**
- `profit_status`: labels each order line as a loss, profit, or break-even line. About 24.5% of lines are losses.
- `ship_days`: days between order and shipment.
- `unit_price`: sales per unit.
- `quarter`: quarter of the order date, used for time analysis.
- `profit_margin`: profit ÷ sales at row level. This is used only for row-level checks. Totals and group margins are calculated as sum of profit ÷ sum of sales, so that large orders are not outweighed by small ones.

**Result:** The cleaned table should contain **51,289 rows and 28 columns**. The separately exported cleaned file should be checked against these counts before submission.

**Open item:** The column selection in the notebook currently omits `ship_mode`. It needs to be restored before the segment and ship mode analysis in Phase 3 can run.

### Phase 3: Exploratory analysis and findings — complete in the notebook, with open items

**Objective:** Answer the business question: which parts of the business make money, which lose it, and whether discounting is a major cause of losses.

**Exploration by country and city:**
- Profiled sales, profit, and margin for the top five countries by sales. The United States leads on both sales (about 2.30M) and profit (about 286k), but its margin is about average.
- Identified the five countries with the largest total losses: Turkey (about −98k), Nigeria (about −81k), Netherlands (about −41k), Honduras (about −29k), and Pakistan (about −22k).
- Profiled the top five cities by sales. New York City leads. Manila is loss-making (about −11k).

**Exploration by segment and market:**
- Counted order lines by segment. Consumer is the largest segment.
- Built a market-region scorecard with sales, profit, orders, margin, and average discount. Canada has the highest margin (about 26.6%) on small volume. APAC North Asia is at about 19.5%. Southeast Asia has the lowest margin of the large regions, at 2.0% on about 884k in sales.

**Southeast Asia deep dive:**
- Broke the region down by country. Four countries lose money: Philippines (−8.8%), Thailand (−9.5%), Myanmar (−6.2%), and Vietnam (−2.8%). Together they lose about 27k.
- Indonesia has the highest sales in the region (about 405k) but only a 3.9% margin.
- Broke the region down by sub-category. Tables (−18.6k), Accessories (−8.6k), and Supplies (−4.0k) are the largest losses. Phones (+13.5k) and Copiers (+11.4k) are the largest gains.

**Discount analysis (core finding):**
- Grouped order lines into discount bands and measured margin and loss share in each. Margin turns negative above about 20–30% discount.
- Found that **92.2% of total loss value** comes from order lines with discounts above 20%. This figure is company-wide.
- Compared Southeast Asia with the rest of the company at each discount band. At the same discount level, margins are similar. At 0% discount, both earn about 25%. Above 20%, both lose money.
- Found that Southeast Asia's lower margin comes from giving deep discounts more often. Its share of lines with discounts above 20% is 57%, compared with 20% for the rest of the company. Its share above 40% is 34%, compared with 12%.

**Product check:**
- Tested the discount effect on Chairs, a profitable product overall. Chairs earn 17.6% at 0–20% discount, −10.3% at 21–40%, and −81.6% above 40%. The discount effect is not limited to Tables and Supplies.

# Coffee Sales Analysis

Excel project: cleaning, transforming, and analyzing a relational coffee sales dataset, culminating in an interactive sales dashboard and deeper follow-up analysis.

## About the Data

The raw dataset is split across three related sheets:

| Sheet | Rows | Description |
|---|---|---|
| `orders` | 1,000 | Order ID, date, customer ID, product ID, quantity — plus blank columns (customer/product details) left for lookup |
| `customers` | 1,000 | Customer ID, name, email, phone, address, city, country, postcode, loyalty card status |
| `products` | 48 | Product ID, coffee type, roast type, size, unit price, price per 100g, profit |

**Key characteristics:**
- Orders span **Jan 2019 – Aug 2022**
- 957 unique orders (many orders contain multiple product lines)
- 913 unique customers across **3 countries**: United States, Ireland, United Kingdom
- 4 coffee types (Arabica, Robusta, Excelsa, Liberica), 3 roast levels (Light/Medium/Dark), 4 pack sizes
- The `orders` sheet arrived with customer and product detail columns intentionally left blank — the exercise was to populate them via lookups against the `customers` and `products` sheets

## Data Cleaning & Transformations

- **Date formatting** — standardized inconsistent `Order Date` formatting
- **Text cleanup** — removed leading/trailing whitespace from customer names
- **Lookups** — used `XLOOKUP` to pull customer details (name, email, country) and product details (coffee type, roast type, unit price) into the `orders` sheet from the `customers` and `products` tables
- **Duplicate check** — audited the dataset for duplicate order/customer records
- **Category expansion** — created new columns to convert shorthand codes (e.g. "Ara", "L") into full, readable labels ("Arabica", "Light") for cleaner analysis and dashboard labels
- **Calculated field** — built a `Sales` column as `Unit Price × Quantity`
- **Pivot analysis** — built PivotTables (sales by country, top 5 customers, total sales over time, month/year breakdown) feeding into the dashboard and deeper analysis
- **Order frequency** — used `COUNTIF` to calculate how many orders each customer placed, then averaged this by loyalty status via PivotTable

## Tools & Skills Used
- XLOOKUP
- COUNTIF
- Text cleaning (TRIM, formatting)
- Data validation & duplicate checking
- Calculated columns
- PivotTables, Timeline, and Slicers
- Dashboard design

## Dashboard

![Coffee Sales Dashboard](./images/Coffee-dashboard.png)

The dashboard combines four PivotTable-driven views — total sales over time (by coffee type), sales by country, top 5 customers, and interactive filtering — with a timeline and slicers for coffee type, roast type, size, and loyalty card status.

## Findings

**Sales are mostly coming from the US.**
Out of the three countries, the US brings in way more money than Ireland and the UK combined — it's clearly the main market ($35,639 vs. $6,697 in Ireland and $2,799 in the UK).

**No coffee type stays popular for long.**
Arabica, Excelsa, Liberica, and Robusta all take turns being the best-seller at different times. There's no single "favorite" — it keeps switching.

**Sales don't follow a seasonal pattern.**
We checked which months sold the most, year by year — and found no repeat winners. 2019's best months were April/June, 2020's were February/June, 2021's were October/November, and 2022's were January/May. Since the top months change every year, sales aren't tied to a season (like holidays or summer) — something else is driving the spikes.

**The loyalty card program doesn't seem to be working.**
We checked this two different ways, and both agree:
- On average, customers spend about the same whether they have a loyalty card or not (~$43 with a card vs. ~$46 without)
- They also order about the same number of times (1.2 vs. 1.3 orders)
- Even the top 5 highest-spending customers mostly *don't* have loyalty cards (only 1 out of 5 does)

This means having a loyalty card isn't linked to spending more or ordering more often — the program isn't driving extra sales.

**Top customers are steady repeat buyers, not bulk buyers.**
Looking at the 5 highest-spending customers, none of them made large bulk orders. Their high totals came from smaller, more frequent purchases adding up — 4 of the 5 are from the US (matching the overall US dominance), and 1 is from the UK.

## Suggestions

1. Focus more marketing/growth efforts on Ireland and the UK — they're currently far behind the US.
2. Since no coffee type or season stays consistently popular, investigate what's actually driving individual sales spikes (e.g. promotions, restocks, one-off bulk buyers) rather than assuming seasonal demand.
3. Reconsider or redesign the loyalty program — as it stands, it isn't linked to higher spending or more frequent orders, even among top customers.
4. Since top customers are frequent small-order buyers rather than bulk buyers, a subscription or "reorder reminder" model might suit them better than a one-time bulk discount.

## How to View
GitHub doesn't render Excel dashboards interactively — download the `.xlsx` file from `/dashboard` to explore it, or see the screenshot above for a static preview.


**Mohammed Adnan**/
Data Analyst

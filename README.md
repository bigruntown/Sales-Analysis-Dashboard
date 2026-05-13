# Sales Analysis Dashboard — Year-over-Year Performance

A Power BI report that benchmarks current-period sales, profit, and quantity sold against the previous period, with growth percentages and breakdowns by payment method and category type.

## Overview

The most useful question in sales analytics isn't "how are we doing this year?" — it's **"how are we doing this year versus last?"** This dashboard is built around that comparison.

It uses a clean star schema (Date / Sales / Measure tables) and a set of DAX time-intelligence measures that compute the previous-period equivalent of every headline KPI, then expresses the change as a percentage so stakeholders can see growth or contraction at a glance.

## Tools

- **Microsoft Power BI Desktop**
- **DAX** — including time-intelligence functions for previous-period comparisons
- **Data modelling** — star schema with a dedicated Date table

## Dataset

A transactional sales dataset with:

- **Sales** table — line-item transactions
- **Date** table — calendar for time-intelligence (year, quarter, month)
- **Measure** table — placeholder table for organising DAX measures (a common Power BI best practice)

## What the report contains

### KPI cards (current vs. previous period)

| Metric | Description |
|---|---|
| Total Revenue | Current period revenue |
| Total Qty | Current period quantity sold |
| Profit | Current period profit |
| Prev Revenue | Prior period equivalent |
| Prev Profit | Prior period equivalent |
| Prev Qty Sold | Prior period equivalent |
| Revenue % | Growth (current vs prior) |
| Profit % | Growth (current vs prior) |
| Qty Sold % | Growth (current vs prior) |

### Breakdowns

- **Payment Method** segmentation (PaymentMethod field)
- **Category Type** breakdown
- **Year** slicer using an advanced slicer visual
- Visuals: KPI cards, clustered bar chart, donut chart

## Key technical work

- Built the **Date dimension** with a continuous calendar so time-intelligence DAX functions work correctly (a common mistake junior analysts make is using transaction dates directly, which breaks `SAMEPERIODLASTYEAR` and similar functions).
- Authored **three pairs of growth measures** (Revenue / Profit / Qty Sold) using `CALCULATE` + `SAMEPERIODLASTYEAR` (or equivalent time-intel patterns), then layered a percentage-growth measure on top.
- Used the **measure-table pattern** to keep DAX organised — separating measures from raw columns is something most enterprise Power BI deployments insist on.
- Designed for executive consumption: high-density top cards, clean payment/category breakdowns underneath.

## Screenshots

![image alt](https://github.com/bigruntown/Sales-Analysis-Dashboard/blob/main/Sales%20Analysis%20Dashboardd.jpg?raw=true)


## How to view this project

1. Download `Power-bi-sales-analysis-dashboard.pbix` from this repo.
2. Open it in **Power BI Desktop** (free download from Microsoft).
3. Use the Year slicer at the top of the report to switch the comparison window.

---

*Built as part of the Utiva Data Science program (2026).*

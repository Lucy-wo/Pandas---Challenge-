# Heroes of Pymoli — Purchasing Analytics with Pandas

> Exploratory analysis of in-game purchase data to understand player demographics, spending patterns, and item performance.

## Summary
This project uses **Python + pandas** to clean and analyze a transaction-level dataset from the game *Heroes of Pymoli*. It compiles core commerce metrics (players, items, revenue), segments users by **gender** and **age**, and surfaces **top spenders** and **high-performing items**. The output is a set of reproducible tables that stakeholders can use to inform pricing, merchandising, and marketing decisions.

## Goal
- **Primary:** Build a clear, reproducible analysis that answers: *Who are the players? What do they buy? Which items and segments drive revenue?*
- **Secondary:** Produce executive-ready summary tables that can be refreshed as new data arrives.

## Procedure
1. **Data Load & Hygiene**
   - Read `purchase_data.csv`; standardize dtypes, check for nulls/dupes.
2. **Player Count**
   - Count unique screen names (SN) to estimate active buyers.
3. **Purchasing Analysis (Total)**
   - Compute **# Unique Items**, **Average Price**, **# Purchases**, **Total Revenue**.
4. **Gender Demographics**
   - Derive **count** and **share** of unique players by gender.
5. **Purchasing Analysis by Gender**
   - For each gender: **purchase count**, **avg purchase price**, **total purchase value**, and **avg total per person**.
6. **Age Demographics**
   - Bin ages (`<10`, `10–14`, …, `40+`) and calculate **unique players** and **share** per bin.
7. **Purchasing Analysis by Age**
   - For each age bin: **purchase count**, **avg purchase price**, **total value**, **avg per person**.
8. **Top Spenders**
   - Group by SN to find **purchase count**, **avg price**, and **total spend**; rank by total spend.
9. **Most Popular & Most Profitable Items**
   - Group by `Item ID` + `Item Name` to compute **volume**, **item price**, and **total value**; rank by **count** and by **revenue**.
10. **Presentation**
    - Format currency, sort tables, and export notebook outputs.

## Results
The analysis produces the following artifacts (ready to drop into a report or dashboard):
- **Player Overview:** total unique players and headline commerce metrics.
- **Segment Tables:** gender and age distributions with per-segment spend.
- **Monetization Tables:** top 5 **spenders**, **most popular items** (by count), and **most profitable items** (by revenue).
- **Pricing Insight:** item price inferred from revenue ÷ purchases for consistency checks.

> *Note:* Exact figures depend on the input file; rerun the notebook to regenerate tables for the latest data.

## Business Impact
- **Merchandising:** Identify items that are *popular* vs. *profitable* to guide feature placement and inventory/skins roadmap.
- **Pricing & Promo:** Use segment-level willingness-to-pay signals to tailor discounts and bundles without eroding high-margin items.
- **Growth & Retention:** Target heavy spenders with loyalty rewards; nudge mid-tier segments with curated offers.
- **Reporting Efficiency:** Reusable notebook streamlines weekly commerce updates and ad-hoc deep dives.

## Next Step to Make It Better
- **Data Quality & Coverage:** Add session IDs, timestamp granularity, and region; dedupe edge cases; validate with unit tests.
- **RFM & LTV:** Segment by **Recency-Frequency-Monetary** and estimate **lifetime value** to prioritize CRM actions.
- **Cohorts & Causality:** Build monthly cohorts; measure promo/feature impact with CUPED/DiD for variance reduction.
- **Pricing Experiments:** A/B test price points or bundles by segment; monitor guardrails (ARPDAU, conversion, refund rate).
- **Productionization:** Parameterize the notebook, add CI checks, and schedule refresh (Airflow/Prefect); publish to a BI dashboard.

---

### (Optional) How to Run
```bash
# Set up environment (example)
pip install pandas numpy jupyter

# Open the analysis
jupyter lab  # run the notebook and execute all cells
````

### (Optional) Repo Structure

```
.
├─ data/                # purchase_data.csv
├─ notebooks/           # analysis notebook(s)
└─ outputs/             # exported tables/figures
```

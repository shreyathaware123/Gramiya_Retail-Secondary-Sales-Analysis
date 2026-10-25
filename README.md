# Secondary Sales Analysis: MIS & Business Analytics Project

A data cleaning, reporting and business-thinking exercise on retail secondary sales data (June to July 2026) across 5 distributors, multiple outlets and SKUs.

## Project Links

- **Part A (Google Sheet): data cleaning, pivots, dashboard, anomaly:** [Open the sheet](https://docs.google.com/spreadsheets/d/1Rgg9OCFCesofzaKrnah1HXow0dWh_omcitzIgT8Su9E/edit?usp=sharing)
- **Part B (Google Doc): written case questions:** [Open the document](https://docs.google.com/document/d/1LnuztAHyqtXRXuIeQ67QdZolLL1PXQw4_Onat9OMR3o/edit?usp=sharing)

## Objective

Take a messy real-world style sales extract, clean it with a visible audit trail, turn it into a month-on-month view a founder can read quickly, flag a business risk, and answer three case questions on how I would investigate and structure reporting work.

## Tools Used

Google Sheets (Find & Replace, TRIM/PROPER, Remove Duplicates, Pivot Tables, formulas, conditional highlighting), Google Docs

## Part A: Dataset Task

The Google Sheet has six tabs: **Raw Data, Clean Data, Cleaning_Log, Pivot Table, Dashboard, A3: Anomaly to check.**

### A1. Data Cleaning

Every step is documented in the `Cleaning_Log` tab (issue, column, rows affected, action, reasoning). The raw data is never overwritten; cleaned values sit in separate columns.

| Issue | Action |
|---|---|
| 14 spelling, case and spacing variants of distributor names | Standardised to 5 distributors using TRIM + PROPER and Find & Replace |
| Mixed date formats (yyyy-mm-dd, dd-mm-yyyy, dd/mm/yyyy) | Converted to real dates in `Date_Clean`; read as day-first because dates like 27/07/2026 rule out month-first |
| SKU naming inconsistency ("Coldpressed" vs "Cold Pressed") | Standardised to one name |
| Duplicate rows | 10 removed (320 raw rows to 310), first occurrence kept |
| Missing Qty_Sold and Sales_Value | 5 rows flagged and highlighted; left blank and excluded from sales totals, since quantity cannot be recovered |
| Outlet names not unique | Used `Outlet_ID` for all outlet counts (104 IDs vs 39 names) |
| No transactions on 1 July | Flagged, not altered; to be checked with the distributor |

### A2. Summary and Dashboard

The Pivot Table and Dashboard tabs show June, July and MoM change for:

- Total sales value by distributor
- Total sales value by category and by SKU
- Active outlets per distributor (unique Outlet_IDs with at least one transaction)
- Top 3 and bottom 3 SKUs by sales value

**Headline numbers**

- Total sales rose from ₹8,42,233 (June) to ₹9,57,585 (July), up 13.7%
- Ghee grew 11.8% and Oils grew 14.5%
- A2 Bilona Ghee 500ml is the top SKU in both months
- Cold Pressed Coconut Oil 500ml fell 24.6% MoM, the largest SKU decline
- Madurai (+72.5%) and Salem (+48.8%) grew strongly; Trichy fell 37.8%

### A3. Anomaly Flagged

Trichy Central Distributors' sales fell 37.8% MoM (₹201,019 to ₹125,043). About 83% of that fall comes from **Beat-01**, which had ₹63,124 of sales across 4 outlets in June and no transactions at all in July.

**Next check:** confirm with the Trichy sales team and the distributor whether Beat-01 was skipped, re-routed or stopped being serviced, and whether its July orders are missing from the DMS extract.

## Part B: Case Questions

Full written answers are in the Google Doc linked above.

| Question | Approach in short |
|---|---|
| **B1. 20% MoM drop for one distributor** | Confirm the data is complete first, then break the drop down by week, beat, outlet and SKU. Compare active outlets and average order size to separate coverage issues from demand or stock issues. Rule out data delays, seasonality, scheme or price changes and one-off orders. Speak to the area sales manager and salesman first, then the distributor. |
| **B2. Consolidating 4 messy sheets into one weekly report** | Agree on common fields (date, channel, platform, SKU, units, sales value), build a master SKU mapping, keep one raw tab per source, add a cleaning layer and a summary layer, add reconciliation checks, automate with Apps Script, and document who updates what and when. |
| **B3. "Which outlets should we stop servicing?"** | Scope before touching data: what "stop servicing" means, who uses the answer, which criteria matter, and the time window (at least 6 months, since 2 months is not enough). First output is a ranked shortlist "for review" with reasons and flags for new, seasonal or strategic outlets, to be discussed with area managers before any decision. |

## Key Learnings

- Keep raw data untouched and show cleaning steps so every number can be traced.
- Check that totals tie across pivot tables, dashboard and the raw source.
- Break a headline change down by distributor, beat, outlet and SKU to find where it actually comes from.
- State assumptions clearly, such as the day-first date reading and excluding rows with missing values.

## Author

**Shreya  Thaware** 🔗 [LinkedIn Profile](https://www.linkedin.com/in/shreya-thaware/) 🌐 [Portfolio ](https://shreyathaware123.github.io/my-portfolio-website/)

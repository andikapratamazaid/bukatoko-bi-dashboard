# BukaToko BI Dashboard

An interactive, single-file **business intelligence dashboard** for the BukaToko e-commerce case study, built from the same cleaned dataset of **10,000 user events** (27 Mar – 23 Sep 2025) as the companion Python analysis.

**Live dashboard:** open `index.html` in any browser, or use the GitHub Pages site of this repo. No build step, no external dependencies, everything is inline in one HTML file.

## What is inside

- **KPI cards:** 10,000 events · 1,982 users · 10,000 sessions · 449 purchasing users · 750 searching users · 0.13% same-day search-to-cart
- **Daily event trend** with a country multi-select filter (8 countries)
- **Monthly Active Users by channel and by country** (Mar–Sep 2025; March and September are partial months and are marked)
- **Q2 2025 active users by country:** Indonesia leads with 1,055 users, ahead of the US (815)
- **Device mix by session:** Android 49.6% · iOS 40.0% · Desktop 10.4% (mobile = 89.6%)
- **User-level funnel:** page view 1,581 → product view 1,454 → add to cart 773 → checkout 453 → purchase 449
- **Key insights:** total MAU is flat at 1,129–1,170 in full months (Apr–Aug), referral is the only growing channel (+19.7% Apr to Aug), social declines the most (−13.0%)

## Project structure

```
.
├── index.html                  # the dashboard (single self-contained file)
├── data/                       # BI-ready tables (fact + KPI aggregates, CSV)
└── docs/BI_DATA_MODEL.md       # data model, KPI definitions, BI tool guide
```

## Companion project

The full Python analysis, presentation deck, and dataset live in the companion repository:
[bukatoko-funnel-analysis](https://github.com/andikapratamazaid/bukatoko-funnel-analysis)

## Tech

Single self-contained HTML file (inline CSS and JavaScript, canvas charts). Data aggregates were computed in Python (pandas) from the cleaned event log and cross-checked with an independent SQL recount.

## Author

Andika Pratama Zaid. Case study for the *Python for Data Analyst* course.

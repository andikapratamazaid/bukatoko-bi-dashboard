# BI Data Model — BukaToko Dashboard

## Purpose
This repository is the **business intelligence layer** of the BukaToko case study: the Python analysis (companion repo `bukatoko-funnel-analysis`) cleans the raw event log and answers the business questions; this layer models the results for reporting and serves them as an interactive dashboard.

## Source
`dirty_dummy_events.csv` (10,000 events, 27 Mar – 23 Sep 2025) from the *Python for Data Analyst* case study, cleaned with Python (pandas): device casing normalised, 100 blank channels mapped to `unknown`, timestamps parsed, no duplicates.

## Tables (folder `data/`)
| File | Grain | Contents |
|---|---|---|
| `fact_events_daily.csv` | one row per date × country × channel × device × event_type | events, distinct users, sessions (additive measures for BI tools) |
| `mau_by_channel.csv` | month × channel matrix | Monthly Active Users per acquisition channel |
| `mau_by_country.csv` | month × country matrix | Monthly Active Users per country |
| `q2_country_activity.csv` | one row per country | Q2 2025 active users and events |
| `device_sessions.csv` | one row per device | sessions and events per device |
| `funnel_users.csv` | one row per funnel stage | distinct users reaching each stage |

## KPI definitions
- **Active user:** distinct `user_id` with at least one event in the period.
- **MAU:** distinct users with at least one event in the month carrying that channel (or country). A user active through two channels counts in both.
- **Session share:** distinct `session_id` per device. In this dataset each session holds exactly one event.
- **Same-day search-to-cart rate:** users whose `add_to_cart` occurs strictly after their first `search` on the same calendar date, divided by users who searched (1 of 750 = 0.13%).
- March and September 2025 are **partial months** (data starts 27 Mar, ends 23 Sep) and are flagged in every view.

## Using these tables in BI tools
- **Power BI / Tableau:** import `fact_events_daily.csv` as the fact table and build measures on `events`; load the matrix CSVs for the MAU views.
- **Looker Studio:** upload the CSVs (or the supporting Google Sheet) as data sources and recreate the same six views.
- **This dashboard:** `index.html` embeds the same aggregates and renders them with interactive filters, so the published numbers are identical across tools.

## Verification
All aggregates were cross-checked against an independent SQL (sqlite) recount of the cleaned dataset and matched exactly.

# Evidence map (8 Oct 2026)

| Source | Range | Items | Covers | Made by / why | Cannot tell you |
|---|---|---|---|---|---|
| evidence/funnel_weekly.csv | weeks of 7 Sep to 5 Oct | 15 rows (5 weeks x all/annual/monthly) | Trial starts, trial_to_paid, pricing page views | Unknown (analytics export?) | Daily timing, who converted, why, cohort definition, anything before 7 Sep, plan tier (Studio vs Team) |
| evidence/tickets.txt | 6-8 Oct | 5 tickets (T-101 to T-105) | Customers who wrote in after the change | Support | How many were affected; no pre-change tickets to compare; no severity |
| evidence/release_notes.txt | 3 Oct | 1 entry | What changed on the page | Product/eng | Anything else shipped that week; behaviour of checkout |

Sanity checks
- Weekday: week_starting dates are Mondays (7 Sep, 5 Oct). 3 Oct = Saturday, so it falls in the week of 28 Sep, whose row shows no drop (0.30). The drop first appears in week of 5 Oct.
- Parts vs total: week of 5 Oct, 215 annual + 323 monthly = 538 = all. Weighted rate (0.20x215 + 0.23x323)/538 = 0.218 -> 0.22. OK. Week of 7 Sep: (0.36x210 + 0.27x310)/520 = 0.306 -> 0.31. OK.
- Latest period: 5 Oct week is at most 4 days old as of today (8 Oct) and may be partial. If conversion happens after a trial period (length unknown), trials starting this week may not have had time to convert, which would lower the rate on its own. Definition unknown.
- Units: trial_to_paid is a fraction; views and starts are counts.

## Contradictions
1. 3 Oct weekday (above).
2. Week of 28 Sep contains 3 Oct (a Saturday, change day) yet shows no drop, while week of 5 Oct shows a large one. Fits a lag (trials started before the change convert later) or a cohort definition we do not know; not yet explained.
3. Tickets say price at checkout differed from pricing page (T-101), annual charged as monthly (T-105): these could be display or billing defects, not "page design" issues. Release notes mention neither.

## Missing (owner, draft question)
- Definition of trial_to_paid, trial length, and whether 5 Oct week is complete. Owner: analytics/data. "Is trial_to_paid measured on the cohort that started that week, and how long do they have to convert? Is the 5 Oct row partial?"
- Daily data from 28 Sep to now by plan. Owner: analytics. "Can I get daily trial starts and conversions, annual vs monthly?"
- Other changes in the same week (campaigns, pricing, checkout, billing code). Owner: Maya / eng lead. "Did anything else ship or run from 1 Oct?"
- Ticket volume baseline and total (are 5 all the tickets?). Owner: support.
- Studio vs Team split. Owner: analytics.
- Prior-year or longer baseline (seasonality). Owner: analytics.

## First look (not a cause)
- The drop is not even. Annual fell 0.35 -> 0.20 (about 15 points); monthly fell 0.27 -> 0.23 (about 4 points). Headline 0.30 -> 0.22 hides that annual carries most of it.
- Page views (2250 -> 2260) and trial starts (529 -> 538) did not move, so volume at the top is steady; the change is in conversion.
- 4 of 5 tickets (T-101, 102, 103, 105) concern price/discount/checkout; 1 (T-104) concerns plan descriptions. Annual-related: T-101, T-102, T-105. These point at where to look, they are not proof; 5 tickets cannot show scale.

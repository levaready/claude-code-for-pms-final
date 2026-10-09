# Analysis notes (working, for Maya)

Source: evidence/funnel_weekly.csv (15 rows), tickets.txt (5), release_notes.txt (1 line).

## Rows behind the numbers
| plan | weeks 7 Sep-28 Sep trial_to_paid | week of 5 Oct | change | trial_starts 5 Oct |
|---|---|---|---|---|
| all | .31 .30 .31 .30 (avg ~.305) | .22 | -8 to -9 pts | 538 |
| annual | .36 .35 .36 .35 (avg ~.355) | .20 | -15.5 pts | 215 |
| monthly | .27 .27 .27 .27 | .23 | -4 pts | 323 |

Baseline is very stable (range .30-.31 overall), so the drop is well outside normal wobble.

Rough paid-conversion arithmetic (trial_starts x rate), 5 Oct week vs baseline rate:
- annual: 215 x (.355-.20) = ~33 fewer paid
- monthly: 323 x (.27-.23) = ~13 fewer paid
- total ~46 fewer paid; about 70% of the gap is annual. Check: 215*.20+323*.23 = 117 paid = 21.8% of 538, matches the .22 reported.

Traffic did not move: trial_starts 529-541 -> 538; pricing_page_views 2250 -> 2260. So fewer people are not arriving; fewer are converting.

## Tickets (5, all 6-8 Oct, all after the change)
- Price at checkout differs from pricing page (T-101), charged monthly when annual selected (T-105): possible price/plan bug
- Annual discount badge can't be found (T-102): matches release note (badge moved into checkout)
- Checkout re-asks for plan (T-103): possible bug
- Can't tell Studio vs Team (T-104): matches release note (descriptions shortened)
5 tickets is anecdote, not a rate. No baseline ticket count to compare.

## What fits / doesn't prove
- Annual hit hardest + annual-specific complaints + badge moved is a consistent story. It is a hypothesis, not a finding.
- Nothing here separates "page change caused it" from other things that changed that week.

## Caveats / open questions
1. Date: Oct 3 2026 is a Saturday, not Friday (Maya's CLAUDE.md says Fri 3 Oct). Need the actual deploy time.
2. Week of 5 Oct is Mon-Thu so far (today Thu 8 Oct) -> partial week, and the week of 28 Sep contains Oct 3-4 post-change days but looks normal (.30). Needs daily data.
3. Trial-to-paid for trials started this week may not be matured: if trials are 14 days, most of 5 Oct cohort hasn't reached the decision point. Unclear how the metric is computed (cohort by trial start vs by conversion date). If it's cohort-by-start and immature, the drop could be partly artefact. Biggest thing to confirm with data owner.
4. Was there an A/B test or staged rollout? Any other changes (pricing, email, promotions, outage) the same week? Release notes list only one entry.
5. Are the checkout price mismatch / wrong-charge reports real bugs? Engineering/support can check billing records.
6. Are there refunds/chargebacks among annual that were mischarged monthly?

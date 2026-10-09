# Evidence map (phase 2). 2026-10-08

Assumes reader is Maya (non-analyst). Weakest gate dimension: the goal (what Dana needs to see to decide).

## Sources
| Source | Covers | Items | Made by / why | Does not cover |
|---|---|---|---|---|
| evidence/release_notes.txt | 3 Oct change | 1 line | unknown author | No rollout method (all users or test?), no checkout/price logic changes, nothing about earlier changes |
| evidence/tickets.txt | 6-8 Oct | 5 tickets, 5 filers (apparently) | Support, unknown triage | Silent users; no total ticket volume or baseline; no pre-3 Oct tickets |
| evidence/funnel_weekly.csv | weeks starting 7 Sep to 5 Oct; all / annual / monthly | 15 rows (4 weeks before, 1 after, x3 cuts) | unknown (analytics) | One post-change week only; no daily grain; no checkout-step events; no tier (Studio/Team) cut; no traffic source; no prior-year |
| CLAUDE.md | user, deadline, rules | n/a | Maya | n/a |

## Stated by sources (not inference)
- Change shipped 3 Oct. Annual discount badge moved to checkout step.
- Week of 5 Oct rows: all 0.22 (was 0.30-0.31); annual 0.20 (was 0.35-0.36); monthly 0.23 (was 0.27). Trial starts and page views flat (e.g. all 538 vs 529-541).
- Tickets: 2 on price shown vs charged (T-101, T-105), 1 on missing discount (T-102), 1 on plan re-pick (T-103), 1 on unclear tier content (T-104).

## Contradictions
1. Release notes say the discount badge moved to checkout; T-102 reports it missing, and T-101 says checkout price differed from the page. Either users do not see it at checkout, or it is displayed inconsistently. Unresolved.
2. T-104 praises the design while describing a real usability gap; one voice, mixed signal.
3. Data vs. definition: the week of 5 Oct has a trial-to-paid figure, yet that week is only partly elapsed (today is 8 Oct), and trial starts that week look like a full week (538 vs ~530). If trials last more than a few days, trials started this week cannot have finished. So either trial_to_paid is counted by something other than trial start cohort, or the week is incomplete/partial. Cannot tell which.
4. Rows reconcile: all-plan trial starts = annual + monthly each week (538 = 215 + 323). No conflict there.

## Missing, owner (guess), draft question
| Gap | Likely owner | Draft question (not sent) |
|---|---|---|
| Definition of trial_to_paid; trial length; is the Oct 5 week complete | Analytics / data owner | "How is trial_to_paid calculated, how long is a trial, and what dates does the 5 Oct row cover?" |
| Daily data, 28 Sep to now | Analytics | "Can we get daily trial starts and conversions by plan from 28 Sep?" |
| Rollout method: everyone at once or a split test | Eng / growth | "Was the new page shown to all visitors from 3 Oct, or was any traffic held back on the old page?" |
| Is the checkout price mismatch a bug (T-101, T-105) and how many were charged wrong | Engineering + billing | "Can you check orders since 3 Oct where the charged plan differs from the plan chosen?" |
| Checkout-step funnel (plan selected -> payment) | Analytics | "Drop-off per checkout step before and after 3 Oct" |
| Total ticket volume and baseline | Support | "How many pricing/checkout tickets per week, before and after?" |
| Year-ago / seasonality baseline for early October | Analytics | "Early October trial-to-paid last year?" |
| What else shipped 29 Sep - 8 Oct | Eng | "Any other release, price or campaign change?" |

## Gate: every source read (3 of 3 plus CLAUDE.md); each gap has a guessed owner (names unknown, to be confirmed by Maya).

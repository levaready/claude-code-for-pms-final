Maya, I read your CLAUDE.md and all three files in ./evidence (funnel_weekly.csv, tickets.txt, release_notes.txt). I wrote nothing outside my outputs folder and sent nothing to anyone. Here is where things stand, and one thing I need from you before I draft the brief.

## What the data shows (rows in analysis-notes.md)

Trial-to-paid, weeks starting:

| plan | 7 Sep | 14 Sep | 21 Sep | 28 Sep | 5 Oct |
|---|---|---|---|---|---|
| all | 0.31 | 0.30 | 0.31 | 0.30 | **0.22** |
| annual | 0.36 | 0.35 | 0.36 | 0.35 | **0.20** |
| monthly | 0.27 | 0.27 | 0.27 | 0.27 | **0.23** |

- The drop is real relative to a very steady baseline (0.30-0.31 for four weeks).
- Traffic did not change: trial starts (529-541 -> 538) and pricing page views (about 2,250 -> 2,260). People are arriving as before; fewer are converting.
- It is mostly an annual-plan problem: annual fell about 15 points, monthly about 4. Using trial starts x rate, that is roughly 33 fewer annual and 13 fewer monthly paid conversions, so about 70% of the gap is annual. (My arithmetic, rough.)

## What the tickets and release note say

The release note says the annual discount badge moved into checkout and the Studio/Team descriptions were shortened. All 5 tickets (6-8 Oct) line up with that: two can't find the discount or tell Studio from Team, and three describe checkout problems (price differs from the pricing page, plan reselection loop, charged monthly after choosing annual). Those last ones sound like possible bugs, not just design.

This is a consistent story, but it's a guess, not a finding. Five tickets with no baseline count prove nothing about scale, and nothing here separates the page change from anything else that changed that week.

## Things that could change the answer

1. **Date check.** Your notes say the page shipped Fri 3 Oct, but 3 Oct 2026 is a Saturday. I need the real deploy time.
2. **The week of 5 Oct is only Mon-Thu.** If trials run a couple of weeks, many of the trials started this week haven't reached the decision to pay, so 0.22 may be understated. The week of 28 Sep (which includes 3-4 Oct) looks normal, which fits a Saturday ship or a lag in the metric. I can't tell how the rate is calculated from the file.
3. **No daily data and no control.** I can't see whether it fell the day the page changed. I also don't know whether it was an A/B test or a full rollout, or whether anything else shipped or ran (promo, emails, outage) that week.

## What I'd ask you for

- Trial length and how "trial_to_paid" is computed (by trial start week, or by when they paid)?
- Daily funnel data from 28 Sep onward, if available, split by plan.
- Whether engineering/billing can confirm the checkout price mismatch and wrong-charge reports (T-101, T-105), and how many accounts were affected.
- Anything else that changed the same week.

## Questions for you before I draft

Do you want me to draft the one-page brief now with these gaps flagged, or wait for the data above? My lean: draft it now, but frame it as "evidence points at annual checkout; here is what we know and what we need Monday" rather than a firm roll back or keep. If the wrong-charge tickets are confirmed, there's a separate case for fixing that immediately whatever Dana decides on the rollback.

Files in the outputs folder: reply.md (this), analysis-notes.md (rows and arithmetic).

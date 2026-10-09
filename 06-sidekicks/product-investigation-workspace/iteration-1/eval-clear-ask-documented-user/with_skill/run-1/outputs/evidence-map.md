# Evidence map (phase 2). Read: all 3 files in ./evidence (the whole folder).

| Source | What it is | Range | Size | Covers | Doesn't cover |
|---|---|---|---|---|---|
| funnel_weekly.csv | trial starts, trial_to_paid, pricing page views, by plan (all / annual / monthly) | weeks starting 7 Sep to 5 Oct | 15 rows (5 weeks x 3 cuts) | every trial, split annual vs monthly | per-tier (Studio/Team), per-day, per-step in checkout, device, new vs returning |
| tickets.txt | 5 support tickets | 6 to 8 Oct | 5 | people who wrote in after the change | anyone who stayed silent; nothing before 6 Oct for comparison |
| release_notes.txt | one line on the 3 Oct change | 3 Oct | 1 line | what changed on the page | any other release that week, rollout method (all users at once or staged?), the checkout code |

## Quick consistency check (arithmetic only)
Weekly "all" rows equal the trial-weighted mix of annual and monthly (e.g. w/c 5 Oct: 215x0.20 + 323x0.23 = ~117 of 538 = 0.22), and trial starts add up. The file is internally consistent.

## Contradictions / tensions between sources
1. Release note says the annual discount badge MOVED to checkout; T-102 says "where did the annual discount go?" Same fact seen two ways. Consistent with the discount being less visible on the page; not proof of why people don't convert.
2. T-101 and T-105 report checkout price differing from the page / monthly charged on annual selection. A release note about a layout change does not say pricing logic changed. Either a display/bug problem or a mismatch between page and checkout; unverified.
3. T-104 says they "love the new page design", while T-104 also can't tell Studio from Team: the design may be liked and still unclear.

## Missing, with likely owner and draft question (not sent)
| Gap | Owner (guess) | Draft question |
|---|---|---|
| Definition of trial_to_paid and trial length. If trials run 14+ days, trials started 5 Oct cannot have finished converting by 8 Oct. Is the 0.22 a partial reading? | Data/analytics (Maya to say who) | "How is trial_to_paid computed, what is the trial length, and as of what date was the w/c 5 Oct row pulled?" |
| Daily or per-step checkout data (page view -> plan select -> payment) | Data/analytics | "Can we get daily plan-select and checkout-completion counts from 28 Sep onward?" |
| Whether the change was staged / A-B tested, i.e. a control group | Whoever shipped it (engineering) | "Did 100% of traffic get the new page on 3 Oct? Any holdout?" |
| Anything else shipped or changed 28 Sep to 8 Oct (pricing, promos, email, traffic sources) | Maya / Eng / Marketing | "Anything else that changed in that window?" |
| Do the ticket checkout-price reports reproduce? | Engineering/QA | "Can someone try annual checkout and compare the price to the page?" |
| Year-ago or prior-period baseline for early October | Data/analytics | "What did early October look like last year?" |
| Ticket volume baseline (5 tickets is high or normal?) | Support | "How many pricing/checkout tickets in a typical week?" |

## What the evidence map already tells us about scope (not yet analysis)
Only ONE post-change week exists, and it is the current, possibly incomplete week. Pricing page views and trial starts did not visibly move; conversion did. That points the question at what happens after the page, not at traffic, but this is for phase 4, not a finding.

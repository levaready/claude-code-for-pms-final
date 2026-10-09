# Brief review: fresh-briefs (6 briefs)

Checks: (1) names an owner, (2) says how we'll know it worked, (3) same scope start to finish, (4) problem explained before the fix.

| Brief | Owner | Success measure | Scope consistent | Problem before fix |
|---|---|---|---|---|
| saved-searches | Pass | Pass | Pass | Pass |
| export-to-csv | Pass | Pass | **Fail** | Pass |
| invoice-reminders | **Fail** | Pass | Pass | Pass |
| onboarding-checklist | Pass | **Fail** | Pass | Pass |
| partner-api-keys | **Fail** | **Fail** | Pass | Pass |
| smart-notifications | Pass | Pass | Pass | **Fail** |

Only saved-searches passes all four checks.

## Details

**saved-searches.** Passes all four. Owner is Priya Nair (engineering lead Tomas Ek). The success measure is concrete: median time to first reply from 6.1 to under 4 minutes in 8 weeks, plus wrong-queue share (7% today). Scope is stated once and matches the proposal (private, agent inbox only). The problem section, with the 9% time-study figure, comes first.

**export-to-csv.** Fails on scope.
- The Proposal says export to "CSV and PDF". The Scope section says "CSV only. PDF is out of scope."
- Next steps then has design starting PDF layouts and engineering estimating CSV and PDF together.
- The success measure (tickets 40 to under 10) is not tied to either format.
- Fix: decide whether PDF is in or out, then make Proposal, Scope and Next steps agree.
- Owner (Wei Zhang), success measure and problem are fine.

**invoice-reminders.** Fails on owner.
- It reads "To be decided once the quarter's roadmap is set", so nobody owns it.
- Fix: name an interim owner now.
- The rest is good: strong problem (22% late, 14 hrs/week), measurable target (22% to under 15% in a quarter), clear scope.

**onboarding-checklist.** Fails on success measure.
- It says "customers feel more confident" and "onboarding feels smoother", which can't be measured.
- The problem section already has usable numbers: 38% never connected a data source, and those accounts churn at 3x.
- Fix: for example, the share of new accounts that connect a data source within 14 days, from 62% to a stated target by a stated date.
- Owner (Jamal Rivera), scope and problem order are fine.

**partner-api-keys.** Fails on owner and on success measure.
- There is no Owner section and no Success measure section.
- The problem is well argued (three-day wait, paused integrations) and the scope is consistent.
- It has an Open questions section instead (whether to alert the admin contact). That may touch scope if the answer is yes.
- Fix: add an owner and a measurable target, such as median time to a working key from about 3 days to under 1 hour.

**smart-notifications.** Fails on problem before fix.
- The Proposal comes before the Problem section.
- The content itself is good: owner Aisha Khan; measure 29% to 40% weekly openers in 3 months; scope covers timing and ordering of existing types only.
- The proposal is consistent with that scope.
- Fix: reorder so the problem comes first.

## Priorities
1. export-to-csv has the most serious problem. Design and engineering are already acting on the PDF work the scope says is out.
2. Name an owner for invoice-reminders and partner-api-keys.
3. Add measurable success criteria for onboarding-checklist and partner-api-keys.
4. Reorder smart-notifications (cosmetic).

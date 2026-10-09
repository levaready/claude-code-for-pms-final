# Brief review: 4 briefs in 06-sidekicks/briefs

Checked against four questions: owner named, success measure, scope stable start to finish, problem explained before the fix.

| Brief | Owner | Success measure | Scope holds | Problem before fix |
|---|---|---|---|---|
| Bulk Callout | No | Partly | Yes | Yes |
| Handler Phone App | Partly | Weak | Yes | No |
| Requisition Approval Chains | Team only | Yes | No | Yes |
| Routing Override Audit Log | Yes | No | Yes | Yes |

## 1. Bulk Callout (12 Jan 2026)
- **Owner: no.** The header says "Product, Dispatch", which is a team. The last section says "nobody's picked it up yet" and hands it to "whoever picks it up next quarter". Sofia and engineering are named only as people to consult.
- **Success measure: partly.** There are two signals: fewer tickets about handlers calling people directly, and a drop in time-to-full-coverage. Neither has a target. The brief admits there is no baseline for time-to-full-coverage and says to get one before shipping. That step has no owner.
- **Scope: holds.** It is the existing callout flow sent to several people. The exclusions (no group chat, no bulk requisitions, no scoring changes) are stated and nothing later contradicts them. The Halloran/Supply mention in the Problem section is a small blur, but the Scope section rules Supply out.
- **Problem before fix: yes.** Problem comes first, then Proposal.
- **Fix:** name an owner, set a target, and assign the baseline work.

## 2. Handler Phone App (2 Aug 2026)
- **Owner: partly.** Sofia is named, "exploring for Q4 alongside her console work. Not yet staffed for a build." That is a person, but she owns the exploration, not delivery.
- **Success measure: weak.** "Fewer handlers reporting they missed a status change" has no baseline and no target. The brief says to start tracking once it moves past exploration.
- **Scope: holds.** Three features (notifications, status view, one-tap contact). It explicitly excludes Supply and the console's activity log, and nothing later changes that.
- **Problem before fix: no.** The brief opens with "Proposal: We should build a phone app". There is no Problem section. The reason comes afterwards under "What this solves", and it rests on one anecdote (Aunt Dot learning about a decline late). The problem needs to come first and be stated beyond a single story.
- **Fix:** add a Problem section above the Proposal, ideally with more than one example. Define the missed-status-change measure and its baseline.

## 3. Requisition Approval Chains (14 Jul 2026)
- **Owner: team only.** "Halloran's team, Supply." No individual is named.
- **Success measure: yes, the clearest of the four.** Requisitions over $2,000 that ship without a second sign-off should be zero. It is specific, measurable, and has a target. It only covers the core change, though. None of the added features has a measure.
- **Scope: no, this is the main problem.** The Proposal says "That's the whole ask", meaning a second approval step over $2,000. The next paragraph adds, with "And while we're building...", four more items:
  1. routing around a slow approver after 48 hours
  2. a cross-site dashboard of pending approvals
  3. handler visibility into where their requisition is stuck
  4. possibly replacing Halloran's weekly gear-cage spreadsheet

  The brief ends with "how much of the above ships together versus in phases — TBD", so the scope is undecided. The 48-hour bypass also works against the control the brief exists to add.
- **Problem before fix: yes.** One person's judgment on large purchases, and Halloran has asked more than once for a second reviewer.
- **Fix:** cut the brief to the $2,000 second approval. Move the other four items to a separate follow-up brief. Name a person as owner.

## 4. Routing Override Audit Log (5 Mar 2026)
- **Owner: yes.** Marcus's team builds it, and Sofia has already mocked the activity-view change. This is the most concrete ownership of the four, though it is still a team plus a designer rather than one named lead.
- **Success measure: no, there is none.** There is no section for it. The closest thing is the "Next steps" claim "Small, contained, ready to build". That describes readiness, not outcome. Possible measures: Nadia's team can confirm whether an override happened and why, in a stated share of complaints; the share of overrides that carry a reason.
- **Scope: holds.** "Overrides only", not a general audit log, and nothing later widens it.
- **Problem before fix: yes.** Overrides leave no trace (no who, when or why), and Nadia's team has hit this more than once.
- **Fix:** add a success measure. Also, the start date depends on "once profile redesign wraps", which has no date.

## Summary
- Best overall: **Routing Override Audit Log**. It is missing only a success measure.
- Most to fix: **Requisition Approval Chains** (scope creep) and **Handler Phone App** (no problem section).
- Gaps common to all four:
  - Three of the four owners are teams ("Dispatch", "Halloran's team", "Marcus's team"). The fourth, Bulk Callout, has none.
  - Only the requisition brief has a measurable target.
  - Two briefs say a baseline is missing (Bulk Callout, Handler Phone App).

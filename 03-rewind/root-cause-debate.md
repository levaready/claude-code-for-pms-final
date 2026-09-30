# Root-cause debate: five independent agents

Run 30 Sept 2026. Five agents, each scoped to exactly one evidence pile in `00-rook/` and blind to my own prior analysis (`02-super-hearing/patterns-signal-vs-noise.md`) and to each other's assigned folders, independently investigated the 4.2 acceptance-rate problem:

1. **Company docs** — `00-rook/company/` (one-pagers, glossary, roadmap, release history, Priya's handover, Slack thread)
2. **CSV data** — `00-rook/data/callout-history.csv`
3. **Routing code** — `00-rook/code/dispatch-routing/`
4. **Tickets** — `00-rook/feedback/tickets/` (all 25)
5. **Interviews** — `00-rook/feedback/interviews/` (all 4)

Each formed an independent root-cause hypothesis with a stated confidence level. In round two, each was given the other four's findings and asked to defend, revise, or concede.

## The consensus reached

**All five agents converged on the same root cause.** The 12 August release cut the offer timeout from 90 to 60 seconds. The routing code scores a timeout identically to an active decline, and the acceptance-history score has no decay — it only moves when a responder is actually re-offered something. A handful of responders who were simply a bit slower to respond (not unwilling) got misclassified as decliners the moment the window shortened, and with no way to earn the score back except being offered again, they fell into a compounding trap: lower score → fewer offers → fewer chances to recover → even lower score. The reweighting (proximity up, acceptance-history down) is a secondary amplifier — specifically through the *proximity* increase, not the acceptance-weight decrease — that deepens the trap once someone falls into it, not what triggers it.

This produces one unified mechanism for both complaint types, not two separate problems: "gone before I could answer" is the trigger event, and "phone never rings" is its downstream consequence for the same responders.

## The one real concession

The **company-docs agent** originally proposed the opposite mechanism — that the reweighting itself suppressed responders via the acceptance-history channel. The **routing-code agent** pointed out that weight actually *fell* (.40→.25) in 4.2, which cuts the other way. Company-docs conceded directly: "I concede that specific causal claim" — and relocated its theory to the proximity weight instead, which is what the group converged on.

## How confidence moved across the debate

| Agent | Round 1 | Round 2 |
|---|---|---|
| CSV data | Medium-high (shape only) | **High** (shape+trigger), medium on full mechanism |
| Tickets | Medium | **Medium-high** |
| Routing code | Medium | **Medium-high** |
| Interviews | Medium-low | **Medium** |
| Company docs | Low-medium | **Medium** |

Every agent moved up, and the moves were earned: the CSV agent's "rate crashes before volume crashes" finding was a prediction the routing-code agent had made *before* seeing that data — independent confirmation, not post-hoc fitting.

## What's still unverified

The five agents converged on nearly the same list independently:

1. **Whether the four responders' misses were actually logged as timeouts, not active declines.** Tickets strongly suggest it — zero mentions of "declining" across all 25, every account describes pure timing failure — but nobody has the server-side event log to confirm it.
2. **Whether the no-decay scoring behavior is intentional or an unreviewed gap.** Marcus's 14 Aug Slack question — does the reweighting apply differently to repeat-decliners — was never answered before Wen went on PTO, and still isn't answered.
3. **Per-responder response-latency data**, to confirm the four actually cluster in the 60–90 second range (the threshold-crossing story) rather than something else coinciding with the same week.
4. **Per-responder location/proximity data**, to confirm the four are geographically disadvantaged, which is what the proximity-amplifier claim requires.
5. **Whether the affected population is larger than four.** The tickets agent flagged that Ashgrove, Halfmoon, Farlight and Stormwrack are still in unresolved dry spells with no "lost offer" capstone yet as of early September — possibly earlier-stage cases of the same trap, not a separate phenomenon.
6. **A prior-year August baseline**, to fully retire Priya's seasonality explanation rather than just deprioritize it.

## Why this matters beyond the debate itself

This mechanism — no score decay, timeout scored as decline, frozen-low-score trap — is the same one identified independently and earlier in `02-super-hearing/patterns-signal-vs-noise.md` (row 8), reached through solo iterative analysis of the CSV and code rather than a blind multi-agent debate. Two separate methods landing on the same mechanism, without either having seen the other's work at the time, is stronger evidence than either alone. The open-items list above is nearly identical to what was already flagged as unresolved — most importantly, Wen's confirmation of intent, and real per-responder score/location data — which is the same ask already sitting in `00-rook/analysis/asks-drafts.md`, unsent as of this debate.

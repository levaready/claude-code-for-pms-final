# Hypotheses to test — root cause of the 4.2 acceptance drop

Written 30 Sept 2026, derived from the routing code walkthrough (`how-routing-works.md`), the data analysis, and the five-agent root-cause debate (`03-rewind/root-cause-debate.md`). Ranked by how likely we are to actually resolve each one — not by how likely it is to be true.

| Rank | Hypothesis (H) | Null Hypothesis (H₀) | What would falsify H |
|---|---|---|---|
| **1** | **H1 — Timeout misclassification.** If the offer window was cut from 90s to 60s, then responses that previously succeeded between 60–90s are now logged as timeouts and scored as declines, because the system treats "ran out of time" identically to "said no." | Missed offers for the four affected responders are not concentrated in the 60–90s range, and/or are logged as active declines rather than timeouts. | Event logs show their misses are evenly distributed across response times, or explicitly recorded as deliberate refusals. |
| **2** | **H2 — No score recovery.** If the recent-acceptance score has no decay mechanism, then no responder's score rises without being re-offered and accepting, because the system only updates the score on an actual outcome. | At least one responder's score recovers over time without a new accepted offer in between. | Wen confirms a decay mechanism exists, or any responder shows a multi-week score recovery with no intervening accepted offer. |
| 3 | **H3 — Proximity disadvantage.** If the four affected responders are also farther from where most incidents occur, then the increased proximity weight is compounding their score drop, because distance now dominates the ranking formula. | The four responders' travel times to incidents are statistically indistinguishable from the other twelve's. | Location/travel-time data shows no meaningful gap between the four and the rest of the roster. |
| 4 | **H4 — Delivery failure.** If a technical fault in notification delivery — not scoring — is the cause, then push logs will show failed or delayed delivery specifically to these four responders' devices, because a transport-layer bug would act independently of the scoring mechanism. | Delivery logs show normal, successful transmission to all four during the affected period. | Push/device logs confirm offers reached their phones on time and as expected. |
| 5 | **H5 — Seasonality.** If the drop is substantially seasonal, then August 2025 will show a comparable aggregate decline across a similar share of responders, because a recurring calendar effect should reproduce independent of any code change. | Prior-year August data shows no comparable decline, or shows a decline that isn't broad-based. | A year-over-year pull from Ravi shows no matching pattern in 2025. |
| 6 | **H6 — Voluntary disengagement.** If responders are genuinely declining more by choice, then tickets and responder complaints will contain language describing an active refusal, because people describe their own choices differently than something being taken from them. | No ticket or interview describes a deliberate decline. | Already weakly falsified: zero of 25 tickets use decline language; all describe timing/technical failure. |

## Why H1 and H2 rank above the rest

Every other agent in last week's debate converged on H1 as the trigger, and it has the cleanest test available — one data pull from engineering (event type + response latency for the four) settles it outright. H2 is nearly as fast to resolve: across all 6 pre-4.2 weeks and all 16 responders, there is not a single instance of a multi-week decline — that pattern only exists after 12 Aug, only for the same four people, and it never reverses. One confirmation from Wen on whether decay was ever designed in would close this out.

H3 and H4 both require data nobody currently has (location/travel-time records, device delivery logs) rather than confirming a lead already in hand. H5 needs an external historical pull that hasn't been requested yet. H6 is already weakly contradicted by the ticket language on file.

## H1 and H2, confirmed in the code itself (30 Sept)

Read `history.py` directly. This is the entire scoring mechanism both hypotheses depend on — eleven lines, in full.

**The only place points get taken away:**

```python
def record_declined(responder):
    """They turned it down, or we ran out of time waiting. Score goes
    down. Same either way — we asked and we didn't get a yes.
    """
    _set(responder, recent_acceptance(responder) - DECLINE_PENALTY)
```

A deliberate "no" and a timeout both land here, docked by the same amount. The comment inside the function says so outright: "Same either way." This directly confirms H1's premise — the system genuinely cannot tell a missed offer from a refused one.

**The only place points get added back, in the entire file:**

```python
def record_accepted(responder):
    """They took the callout. Score goes up."""
    _set(responder, recent_acceptance(responder) + ACCEPTANCE_CREDIT)
```

That's the whole list. One function. No decay, no time-based reset, no manual override — the only way a score ever rises is by being offered a callout and accepting it. This confirms H2 outright: there is no recovery mechanism, not a weak one, none at all.

**One more thing worth carrying into the Wen conversation:** sitting directly above `record_declined` is a dated comment — `TODO(wen, 2019)` — asking exactly this question: should the score ease back toward neutral over time? It lays out both sides and then says "leaving it as-is for now." That's a six-year-old open decision, never made, not a recent oversight from 4.2. It tells us the *trap* predates 4.2 entirely; what 4.2 changed (the timeout) is what's pushing more people into a trap that was already there. Updates H2's confidence from "inferred" to confirmed-by-source; H2's remaining open question shifts from "does decay exist" (no, confirmed) to "was leaving it unresolved ever revisited since 2019" — still Wen's to answer.

## What recovery actually requires, traced step by step (30 Sept)

Walked the full chain across `availability.py` → `routing.py` → `offer.py` → `history.py` for a responder who's been quiet a month:

1. A nearby incident has to come in — being generally available isn't enough.
2. They have to score well enough to be worth reaching. Proximity is 60% of the score, so even at a rock-bottom acceptance history, being genuinely close can still carry a score around 0.75 — this is the mechanical reason H3 (proximity) matters.
3. Everyone ranked above them *for that specific incident* has to fail first (decline or time out) before the offer reaches them at all — `offer.py` only moves down the list one person at a time.
4. They have to answer successfully within 60 seconds when it finally reaches them.
5. One accept only adds `ACCEPTANCE_CREDIT` (0.08) to their score — a small nudge, not a reset.
6. Steps 1–5 have to repeat several times in a row to reach anything like a normal score, since each repeat depends on another nearby incident and another favorable ranking.

**One finding worth flagging for the Wen conversation:** a month of silence likely means a *frozen* score, not a worsening one. `history.py` only updates on an actual offer outcome — if nobody's being offered anything, nothing in the scoring code runs at all. The silence itself isn't the damage; it's that nothing during that silence does anything to fix it either. This sharpens H2: the absence of decay isn't just "no recovery over time," it's "time has literally no effect in either direction."

# Rook Industries — course working file

## Session scope — Product School lab

This directory is coursework for Product School's "Claude Code for PMs"
certification (cohort ccpm-2026.1). Everything in it is a fictional
teaching scenario.

- Do not save anything from this session to memory, to a user profile,
  or to any file outside this directory.
- Do not carry context from this directory into unrelated sessions.
- Rook Industries is not a real company. Nothing here is a fact about
  the world.
- Read and write only within this directory.

<!-- Keep the block above at the top of this file. Everything you add
     during the course goes below this line. -->

---

## Working context

Sources: `00-rook/company/` (company overview, product one-pagers, glossary,
team directory, Q3 roadmap, release history, Priya's handover, #dispatch-team
Slack export). The Slack export is dated 2 Sept 2026; anything after that is
unknown to me. The user is the incoming PM for Rook Dispatch (started Mon 31 Aug).

### Company and products
Rook Industries (founded 2014, 241 staff, HQ "Site Aleph", offices in Berlin,
Singapore, Cornwall) sells coordination and provisioning software to
independently operating masked **responders** and the **handlers** and
**quartermasters** who support them. Subscription, priced per active responder.
Monthly release train, point releases numbered 4.x.

- **Rook Dispatch** (ours): incident comes in → rank available responders →
  offer the callout to the top one on mobile → accept, or decline/timeout and it
  moves to the next. Web console for handlers, native mobile for responders.
  Routing config ships in the release; it is not a runtime setting.
- **Rook Supply**: requisitions → quartermaster approval → fulfilment →
  maintenance schedule (from service interval); field failure reports can pull
  maintenance forward.
- **The seam:** Dispatch *writes* the Responder Availability Record; Supply
  *reads* it and schedules maintenance into low-callout periods. Supply's one-pager
  says changes to how Dispatch computes or updates it land in Supply's scheduling
  unannounced. `availability.py` says routing never changes it, so whether routing
  changes reach Supply is unverified. Ask Supply before changing its shape.
  Clue (Halloran, 5 Sept, a Supply user with a steady-volume responder): maintenance
  scheduling "has gotten smarter about not booking maintenance into a week he's likely
  to be out". Not yet checked for the four responders whose offers collapsed.

### People
- **Helen Achebe**: Director of Product, my user's boss, owns the roadmap and commitments (Chicago)
- **Marcus Oyelaran**: Eng Manager, Dispatch; straight talker, first stop when unsure (Chicago)
- **Wen Li**: Staff Engineer, built routing; the only real source on how ranking works (Berlin)
- **Sofia Marino**: Product Designer, console and phone app (Chicago)
- **Nadia Hoffmann**: Support Lead, Dispatch and Supply; sees complaints first (Berlin)
- **Ravi Menon**: Data Analyst, shared across both surfaces; owns the weekly
  answer-rate reporting; requests go through #data (Singapore)
- **Priya Raghunathan**: previous Dispatch PM, left 21 Aug; reachable via Marcus only if something is on fire

### Vocabulary that differs from everyday usage
- **Callout offer / timeout / decline**: an offer is one callout to one responder; it
  expires after the timeout (now 60s, same for everyone); a decline is active refusal.
  Both decline and timeout send it onward but are distinct in the data.
- **Acceptance rate**: accepted ÷ offers (not declined or timed out). Dispatch's
  headline metric, reported weekly in aggregate. **Time-to-accept**: median seconds.
- **Coverage gap**: no available responder had the required capability tags — "nobody
  could go", different from "nobody would".
- **Routing priority**: score from proximity (travel-time), availability, capability
  match, and *recent acceptance history*. Declining or timing out lowers the last
  input, so it lowers priority for later callouts until it recovers.
- **Capability tags**: flight, structural-entry, hazmat-tolerant, cold-weather,
  aquatic, crowd-management, de-escalation.
- **Cover identity**: a responder's public persona. Rook holds no mapping to a legal
  identity and can't reconstruct one (contractual, Security Policy 4.1).
  Never design anything that assumes such a mapping, and never try to work out who anyone is.
- **Mutual aid**: cross-region cover; unsupported, on the Q4 exploration list per the glossary.

### Where things stand (as of 2 Sept 2026)
- **4.2 shipped 12 Aug** with: proximity weighted up vs. recent acceptance (a
  long-requested change), offer timeout cut 90s → 60s, console filter persistence,
  three defect fixes. 4.1 (16 Jun): travel-time proximity, bulk callout. 4.0 (7 Apr).
- **Symptoms since:** acceptance is down and callout tickets ~3x normal since ~12 Aug,
  flat since (Nadia, 26 Aug): about two thirds "phone never goes off", one third "gone
  before I could answer". A handler emailed Nadia directly, which is unusual.
- **Nothing is measured yet.** Marcus offered only "rough" numbers; the real weekly
  numbers are Ravi's. No one has established a cause.
- **Priya's view** is that it's mostly seasonal (August is always soft) and will recover
  in September. That is a hypothesis with no data behind it, and 4.2 changed two things
  at once (weighting and timeout) on top of any seasonality. She also asked that this
  not become a revert conversation; treat that as her opinion, not a decision.
- **Open question, unanswered:** Marcus asked (14 Aug) whether the new ping weighting was
  meant to apply to responders who have been declining or timing out, or only to
  everyone else; config doesn't distinguish them. Wen was on PTO and has not replied in the thread.
- **Plausible mechanism to test, not a finding:** a shorter timeout produces more
  timeouts → lowers recent-acceptance → lowers routing priority → fewer pings, which
  would fit "phone never goes off". Whether that reaches Supply's
  maintenance scheduling is unverified (see 23 Sept notes).
- **Roadmap gap:** Q3 roadmap (rev. 30 Jun) lists **Availability Confidence** (support-
  escalation driven) as a committed 4.2 item. It is absent from the 4.2 release notes, and
  Priya says some items were squeezed out and that she never reviewed with Helen which
  remain Q3 commitments. Committed items are "locked"; changes go through Product/Helen.
  Also committed: requisition approval chains (Supply, 4.3). Exploring for Q4: handler
  phone app (Supply), shared cover between responders (Dispatch).
- **Planned:** Marcus and Nadia want to regroup on 4.2 after the PM's first week; Nadia
  will bring the ticket breakdown. Marcus does not want to hand the PM a conclusion.
- **Owed by the PM:** a written description of how ping decisions are made (none exists;
  Wen is the source). Filter-persistence tickets are cosmetic noise; deprioritise.

### How to work with me here
- Separate what the documents state from what is inference. Label hypotheses as such.
- Don't state a cause for the 4.2 acceptance drop until the data supports it; help design
  what data would separate seasonality, the weighting change and the timeout change.
- Ask for Ravi's weekly numbers rather than relying on ad-hoc pulls.
- Source docs disagree in small ways (Slack says 4.2 "out" 13 Aug; release notes say
  12 Aug; Priya says Marcus pulls numbers, the directory says Ravi). Flag such conflicts.

### Added 23 Sept 2026 (full read of 00-rook)
- **Layout:** beyond `company/`, `00-rook/` holds `code/dispatch-routing/`,
  `data/callout-history.csv` (weekly per-responder offers, 29 Jun–31 Aug; author and
  meaning of `pings_taken` unknown), `feedback/` (tickets T-001–025, 13 Aug–5 Sep; four
  handler interviews by Sofia, 2–5 Sep, console research) and `analysis/` (my work:
  `ticket-vs-csv.md`, and `asks-drafts.md` with asks to Ravi, Wen, Nadia and Helen,
  drafted but unsent as of 23 Sept). Other numbered folders are course modules.
- **Data:** aggregate acceptance ~77% before 4.2, 54% w/c 10 Aug, 73% w/c 31 Aug; offers
  sent flat (158–177/wk). Underneath, Farlight, Meteor Mite, The Undertow and Vesper fell
  from ~11–14 offers/wk to 0–2 while others took more (The Gale 13→21). The headline
  metric is aggregate, so it can't see this.
- **Tickets vs data:** 16 of 25 tickets (9 responders) describe quiet stretches the CSV
  doesn't show (Nightwell is the busiest in the data). Vesper and Meteor Mite, the worst
  hit, filed none. Don't use ticket volume to say who is affected until Ravi reconciles.
- **Routing code:** 4.2 weights are proximity .60 (was .45), recent acceptance .25 (was
  .40), capability .15. Decline penalty .12 vs accept credit .08; timeouts scored as
  declines; no decay (2019 TODO). Offers walk the ranked list and stop at the first yes,
  so low rank means rarely asked, contradicting the README's "order, not whether".
  Acceptance weight *fell* in 4.2, so the score alone doesn't obviously explain the
  four; need per-responder scores and locations.
- **Unresolved:** roadmap calls the weighting change and timeout cut "Internal" while
  release notes and Priya say responder-requested; no rationale documented for 60s;
  "gone in seconds" reports vs a 60s timeout unexplained; Availability Confidence is not
  in the code or changelog; Sofia's console research isn't on the roadmap.
- **Confidentiality:** interview transcripts contain incidental household detail. Keep
  it out of anything written.

### Added 28 Sept 2026 (tickets grouped, interviews vs. tickets compared)
- **Files:** `02-super-hearing/` now holds `prompts.md`, two triage artifacts
  (`interview-signals.html/.md`, `handler-feedback-triage.html/.md`) and
  `patterns-signal-vs-noise.md` (7-row signal/noise table, most current view of the
  investigation). Superseded rougher notes stay in `00-rook/analysis/`.
- **Tickets grouped:** dry-spell-only 16/25, lost-offer-only 4/25, dry-spell-then-lost
  5/25. 22 filers; 3 filed twice, all handlers, each filing dry-spell then lost-offer for
  the *same* responder (Sung/Nightwell, Okafor/Undertow, Alvarez/Ironvale).
- **Tickets vs. interviews barely overlap in who they cover.** 9 of the most
  ticket-heavy responders (Nightwell, Ironvale, Stormwrack, Ashgrove, Halfmoon,
  Falkirk, The Drift, Cindermark, Longcast) never appear in any interview. The 2
  collapsed responders interviews *do* catch (Meteor Mite, Vesper) have zero tickets.
  Treat the two piles as complementary blind spots, not cross-checks of each other.
- **Severity reads are inconsistent across sources**, not just noisy in volume:
  Halloran shrugs off a lost offer as "these things happen"; the same kind of event,
  ticketed (T-019, The Undertow), is the only High-severity ticket in the folder.
  Don't read one calm voice as evidence a problem is minor.
- **Testable explanations for tickets-vs-CSV mismatch (none ruled out):** (a) weekly
  CSV totals can hide a real multi-day dry spell inside a busier week — need daily
  data from Ravi; (b) Ambrose confirms the console filter has silently reverted before,
  so a similar bug could show a handler "nothing" while offers were actually sent;
  (c) `pings_sent` may count things a handler wouldn't call a real callout.
- **Interviews are corroboration, not a representative sample.** The four were picked
  for Sofia's console redesign research, not to represent affected responders. If we'd
  read only interviews we'd have undercounted scope and misrouted the lost-offer
  problem to the console team, since that's the context it surfaced in.
- **Least-effort, highest-leverage next step is still unsent:** the Ravi ask in
  `00-rook/analysis/asks-drafts.md` (what `pings_sent`/`pings_taken` measure, plus
  daily-grain data) settles the dependency most other open questions sit on.

### Added 28 Sept 2026, continued (read `callout-history.csv` directly against tickets/code)
- **Files:** `patterns-signal-vs-noise.md` is now 10 rows, plus a plain-language
  version (`-plain.md`); `03-rewind/prompts.md` holds this session's CSV/data prompts.
- **The one number for Helen:** 1 in 4 responders (4 of 16) are now getting offered
  work ~80% less often than before 4.2. Lead with this over the acceptance rate, which
  is recovering (73% and climbing) and tells the opposite story.
- **Not a uniform slowdown — a split.** Farlight, Meteor Mite, The Undertow and Vesper
  fell 9–11 offers/wk and never came back; the other 12 dipped in the 10 Aug transition
  week and then held flat or grew (6 of them now get *more* offers than before 4.2).
- **New mechanism for "never recovered" (row 8, still unconfirmed by Wen):**
  `pings_sent`, not just accepted, falls to 0–1/wk for all four by 31 Aug — Dispatch
  has nearly stopped reaching them, not just seeing them decline more. The drop is
  monotonic, worse every week, unlike the other 12's dip-then-recover shape.
  `history.py` has no score decay (open 2019 TODO) and scores only move when a
  responder is actually offered — so a low score means fewer offers, fewer offers
  means no chance to earn it back. Explains persistence, not the initial trigger.
- **Ticket-filing timing tracks who's vocal, not who's affected (row 9).** First
  ticket (13 Aug) and the CSV's first crash (week of 10 Aug) line up in aggregate.
  Broken down by responder: only The Undertow's tickets track his real-time collapse;
  Farlight's first ticket lags her collapse by ~2 weeks; Meteor Mite and Vesper never
  get a ticket at all despite an identical collapse. T-002 (Ashgrove, 14 Aug) describes
  a quiet stretch starting ~8 Aug, before 4.2 shipped — check against daily data.
- **Priya's seasonality read (row 10): weakened, not settled.** The aggregate rate is
  flat through the week of 3 Aug, then falls 20+ points in the single week 4.2
  shipped — too sharp for gradual seasonal drift — and lands on 4 of 16 responders,
  not broadly. But no year-over-year August baseline exists anywhere in `00-rook`, so
  this can't be confirmed or ruled out without it. Still an open ask to Ravi.

### Added 30 Sept 2026 (Vesper case study, recovery mechanics, 5-agent root-cause debate)
- **Files:** `patterns-signal-vs-noise.md` also has a Vesper week-by-week case study
  and a "why the rows, not just the number" note. New: `03-rewind/root-cause-debate.md`.
- **Vesper case study:** steady ~13–15 offers/wk through early Aug, half taken the week
  4.2 ships (12 sent/6 taken), then a cliff (5→2→1 sent, 0 taken by late Aug) — matches
  row 8's shape exactly and Dot's interview (cooking for someone "home all week" without
  connecting it at the time to the phone buzzing and losing the offer).
- **Recovery mechanics (refines row 8):** proximity is 60% of the routing score vs 25%
  for acceptance history, so a very close incident can still reach someone at rock-bottom
  acceptance (~0.75 score even at zero history) — meaning distance, not just the penalty,
  may be doing most of the excluding. No passive recovery exists (no decay, confirmed
  again): a trapped responder needs either a lucky nearby incident or manual intervention.
- **Five-agent blind debate reached consensus** (full writeup:
  `03-rewind/root-cause-debate.md`): the 60s timeout cut is the trigger (timeouts scored
  identically to declines), the proximity-weight increase is a secondary amplifier
  (NOT the acceptance-weight decrease — that channel was proposed, checked against the
  actual weight numbers, and retracted mid-debate), and the no-decay scoring trap is why
  it doesn't self-correct. Confidence converged to medium/medium-high across all 5 agents,
  independently matching row 8's mechanism reached by solo analysis — two methods, same
  answer, worth real weight. Still needs: whether the four's misses were logged as
  timeouts vs. declines server-side, Wen's confirmation of intent, per-responder
  latency/location data, and whether Ashgrove/Halfmoon/Farlight/Stormwrack (still in
  unresolved dry spells per tickets) are earlier-stage cases of the same trap, meaning
  the affected population may be larger than 4.

### Added 30 Sept 2026, continued (routing code walkthrough, hypotheses, Slack)
- **Files:** `04-x-ray-vision/how-routing-works.md` (plain-English walkthrough of
  `dispatch-routing/`, no jargon, file map, Marcus's question answered) and
  `hypotheses-to-test.md` (H1–H6 in scientific If/Then/Because framing, ranked by how
  resolvable each is, not by plausibility).
- **Marcus's 14 Aug Slack question is answered, and sent back to him** on the real
  Product School class Slack (`#claude-code-for-pms-sep21-26-weeknights`): the 4.2
  reweighting formula is identical for every responder, no code path keyed to decline
  history. A classmate (Faran) independently posted the same conclusion with stronger
  evidence — no clean split by pre-4.2 acceptance rate (Vesper's was great and she still
  collapsed; Meteor Mite's was poor and also collapsed; The Drift's was as good as
  Vesper's and he's thriving) — consistent with a blanket change, not a targeted one.
- **H1 and H2 confirmed directly from `history.py` source** (not just inferred):
  `record_declined` is the only place points come off, and explicitly docks a timeout
  the same as an active decline ("Same either way"). `record_accepted` is the *only*
  place points go back on, anywhere in the file — no decay, no reset, no manual path.
  The no-recovery trap has a `TODO(wen, 2019)` sitting right above it, asking exactly
  this question and left unresolved — meaning the trap predates 4.2 by years; the
  timeout cut is what's pushing more people into a trap that already existed.
- **Full recovery chain traced, step by step:** a quiet responder needs a nearby
  incident + good enough proximity score to rank highly despite rock-bottom history +
  everyone ranked above them to also fail + them to actually answer in time — and that
  whole chain has to repeat multiple times, since one accept only adds 0.08 to the
  score. Key finding: a month of silence likely *freezes* their score rather than
  worsening it, since `history.py` only updates on an actual offer outcome — nothing
  passive helps either direction.
- **This repo can't verify "4.2 only changed configs."** Checked git history: there's
  exactly one commit touching `dispatch-routing/`, already post-4.2 — no real diff
  exists here. We're trusting `CHANGELOG.md` and inline comments in `config.py`, both
  self-reported, not confirmed against an actual pre/post code diff. Would need Wen or
  real deploy history to verify.
- **H3 (proximity disadvantage) is still the open piece** — it's the specific test that
  would confirm or kill the "distance, not history, is doing the real damage" claim
  given to Marcus. No location data exists anywhere in `00-rook`.
- **Correction/learning:** Slack tool access can appear mid-session (connector loaded
  after initial "I can't do this" response) — worth re-checking capability before
  telling the user something's impossible, if they ask a second time.

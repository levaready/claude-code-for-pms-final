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

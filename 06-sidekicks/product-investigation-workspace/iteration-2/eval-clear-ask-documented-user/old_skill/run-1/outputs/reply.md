Maya, I read CLAUDE.md and all three files in ./evidence (release notes, 5 tickets, weekly funnel CSV) before doing anything else. Nothing is sent or shared; everything below is a draft in the outputs folder.

**Confidence gate: 95, lowest dimension is the goal.**
- Your ask: a one-page brief for Dana on why trial-to-paid dropped after the 3 Oct pricing page and whether to roll back.
- Who you are: PM for Checkout, reporting to Dana Ortiz (VP Product). You know the funnel, not analysis, so I show rows and keep it plain. You read it first; Dana only sees what you have read.
- Goal: Dana decides in Monday's (12 Oct) product review; brief due Fri 9 Oct, i.e. tomorrow. Good means a recommendation you can defend, with guesses labelled.
- My role: read, map, analyze and draft in the outputs folder. I check with you before any email, post, commit or push. I won't name a cause before the data supports one.

Since the gate is passed I carried on through phase 1 (working context) and phase 2 (evidence map), then stopped. Files: charter.md, working-context.md, evidence-map.md.

**What the sources state (no cause claimed yet)**
- The 3 Oct release changed three things at once: redesigned plan cards, the annual discount badge moved into checkout, and shorter Studio/Team descriptions.
- Week of 5 Oct, trial-to-paid: all plans 0.22 (0.30-0.31 the four weeks before); annual 0.20 (was 0.35-0.36); monthly 0.23 (was 0.27). Trial starts and pricing page views stayed flat, so the drop is after the trial starts, not in getting people in. Annual fell far more than monthly.
- The 5 tickets map to those changes: price at checkout differs from the page (T-101), wrong charge, monthly instead of annual (T-105), discount gone (T-102), plan picker loops (T-103), unclear Studio vs Team (T-104). These are candidate mechanisms only. Five tickets say nothing about how many people are affected.

**Things that worry me about the data**
1. Only one week after the change, and it is probably incomplete (today is Thu 8 Oct) yet looks like a full week of trial starts. If trials last more than a few days, those trials cannot have finished. Nobody has stated how trial_to_paid is calculated. This is the most important gap, because it decides whether the 0.22 can be trusted yet.
2. Release notes say the discount moved to checkout, while a user says it vanished. Unresolved.
3. Three changes shipped together, so even good data would not separate which one did it without checkout-step or daily data.

**Questions for you (best guesses in brackets; a plain "yes" works)**
1. Can you ask the data owner how trial_to_paid is defined, the trial length, and what dates the 5 Oct row covers? [I drafted this question in the evidence map; you or I send it only if you say so.]
2. Is a partial option acceptable in the brief, such as "keep the page, fix the checkout price bug", rather than only roll back yes/no? [yes]
3. Who owns analytics, engineering and support for these questions? [unknown to me; I have no names]

I have not started phase 3 (counting tickets) or phase 4 (numbers) in depth. Phase 3 here is small (5 tickets), and phase 4 starts with the per-plan before/after rows. I'm waiting on your answers to 1-3, especially 1, since the definition changes how I read every number.

# Confidence check: brief and prototype

5 Oct 2026. Scored 0–100. Covers the one-pager (`brief.md`) and the click-through (`prototype.html`).

## First check: the one-pager, before the prototype (70/100 overall)

| Part | Score | Why |
|---|---|---|
| Diagnosis (what's wrong) | 80 | Five blind agents converged, and `history.py` confirms timeouts are scored as declines and only an accept earns points back. Missing: the event logs, and why these four specifically. |
| Direction (visibility + fair rule + reset) | 70 | It follows from the analysis. The risk is that the fix might not bring anyone back. |
| The one-pager as written | 60 | It answered Helen's ask, but a few promises outran our evidence. |

Four gaps came out of that check, and the brief and prototype were changed to deal with them:

1. **The reset may not work.** If the four are far from most incidents, a restored score won't get them offers, since proximity is 60% of the ranking. The responder message was softened so it no longer promises offers.
2. **The moment a quiet responder actually feels something.** Five tickets describe weeks of nothing, then the first offer back lost in seconds. A comeback offer was added.
3. **Kip's real picture is two cards.** One is quiet (Meteor Mite) and one is overloaded (The Gale). The prototype now shows both.
4. **We've never heard from a responder.** Still open.

## Second check: the prototype (68/100 overall)

| Part | Score | Why |
|---|---|---|
| Does it work | 90 | Clicked through the whole flow: fair-shot confirm and undo, the responder screens, the countdown (2:00 to 1:58), "take it", "let it run out", and start over. No console errors. |
| Does it show the idea clearly | 80 | The two cards make Kip's problem obvious at a glance. The comeback offer shows the moment that matters most. |
| Is it the right thing to build | 62 | The same open gaps as before, which a prototype can't close. |

## What holds the score down

1. **Moving someone up the line may not bring their offers back.** If the four are also far from most incidents, the ranking will keep skipping them. Untested. The prototype can't show it.
2. **The comeback offer and responder screens are inference.** They rest on five tickets and one mention that responders can't see their own history. No responder has been interviewed.
3. **The example numbers are guesses.** The 50% quiet threshold and the 2-minute comeback window are untested.
4. **Only the handler view has been seen rendered.** The responder screens were checked through clicks and text, not by eye.

## What would raise it

- **Wen's location data** settles risk 1. Worth about +10.
- **One or two responder conversations**, relayed through Kip or Dot. Worth about +5.

## How to present it

Ready to show Helen as "here's what it could look like", not "here's what will work".

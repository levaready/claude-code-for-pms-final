# How a call reaches a responder — and what changed in 4.2

A plain-English write-up of `00-rook/code/dispatch-routing/`, written 30 Sept 2026. No code, no jargon — this is the document Priya's handover said didn't exist and that the incoming PM owes.

## What happens, step by step

**1. Something goes wrong, and we figure out who's actually free to help.**
The system looks at everyone who's marked themselves available right now, near where the incident is. This is just a lookup — it doesn't decide anything yet, it just builds the list of possible people.
*Lives in: `availability.py`*

**2. We rank that list, best match first.**
Every available person gets scored on three things: how close they are, how often they've said yes to jobs recently, and whether they have the right skills for this specific incident. Those three scores get combined into one number per person, and the list gets sorted, best score at the top.

Right now, closeness counts the most — about 60% of the score. Recent yes/no history counts for about a quarter. Skills match makes up the rest.
*Lives in: `routing.py`*

**3. We ask the top person, and wait.**
The call goes to the phone of whoever's at the top of that sorted list. Then we wait — currently up to 60 seconds — for them to answer.
*Lives in: `offer.py`*

**4. Three things can happen.**
- They **say yes** — done, they're on the job.
- They **say no** — it moves to the next person on the list.
- They **don't answer in time** — it also moves to the next person on the list. The system treats "didn't answer in time" exactly the same as "said no." There's no difference recorded between someone who's busy or slow to check their phone and someone who deliberately turned it down.
*This happens in: `offer.py`, but the yes/no record itself is kept in: `history.py`*

**5. That yes/no record follows them into the next job.**
Every time someone says yes, their "recent history" score goes up a little. Every time they say no — or just don't answer — it goes down. That score is one of the three things in Step 2, so it directly affects whether they show up near the top of the list next time, or near the bottom.

**This is the part that matters most:** that score never fixes itself over time. It only changes when someone is actually called and either answers or doesn't. So if someone's score drops — maybe because they were genuinely just slow to answer a couple of times — they start ranking lower, which means they get called less often, which means they have fewer chances to say yes and bring their score back up. Nothing in the code breaks that cycle on its own.
*Lives in: `history.py`*

**One more thing worth knowing:** nobody is ever actually removed from consideration. The system doesn't exclude anyone — it only decides the *order* people get asked in. Someone ranked near the bottom can still, in theory, get a call eventually. In practice, if there's usually someone ranked higher who's available, the person at the bottom may rarely get reached at all.

## The file map

| Step | What it does | File |
|---|---|---|
| Who's even available | Builds the list of free, nearby people | `availability.py` |
| Who's asked first | Scores and sorts that list | `routing.py` |
| Making the call | Sends the offer, waits, moves to the next person | `offer.py` |
| Remembering yes/no | Tracks each person's recent answer history | `history.py` |
| The dials that control all of this | Timeout length, how much each factor counts | `config.py` |

## What changed on 12 August (release 4.2), and why it matters to a responder

Two things changed, both in this same part of the code.

**1. The window to answer got shorter.** It used to be 90 seconds. Now it's 60 — a third less time from the moment a responder's phone buzzes to the moment the system gives up and moves to someone else. If you're mid-shift, driving, in the shower, or just have your phone in another room, 90 seconds used to be enough. 60 seconds is a much tighter margin. Nothing about how fast a responder can move changed — the window just got smaller around them.

**2. How the system decides who to ask first changed too.** Before, closeness and recent yes/no record were weighted almost equally — 45% and 40%. Now closeness counts for 60%, and recent record only counts for 25%. Being nearby now matters a lot more than track record does. A responder who reliably says yes but is often a bit farther from where jobs are is now less likely to be picked over someone closer with a shakier record.

**What didn't change, and matters more than either of the above on its own:** the part that decides how a missed call affects a responder's future record has been the same since before this update. A missed call has always counted exactly the same as turning a job down on purpose, and a responder's record has never had a way to heal on its own — only by being asked again and saying yes.

**Why the combination matters:** on its own, a shorter window is a minor inconvenience. But because a missed call counts against you the same as a refusal, and because that mark never goes away by itself, a shorter window means more people get caught out by timing — and once they are, they start getting asked less, which gives them fewer chances to fix it, which means they get asked even less. That trap existed before 4.2. The shorter window is what's pushing more people into it.

## How this lines up with what the data analysis found

| What we saw in the data | Which step above explains it |
|---|---|
| Four responders' scores never recovered, not even once, over three-plus weeks | **Step 5** — the score only changes when someone is re-offered something, and they're not being asked |
| Their acceptance rate crashed the week 4.2 shipped, but the actual number of calls they got didn't drop until the week after | **Steps 4 and 2, one after the other** — the bad week hurts the score immediately; the lower score only affects who gets picked the *next* time a job comes in |
| Those four looked completely ordinary beforehand | **Steps 1–3** don't filter or flag anyone in advance — they only became different once the shorter timer started catching them |
| No ticket describes anyone actually declining — every one describes losing it to the clock | **Step 4** — the system doesn't keep a separate record for "ran out of time" versus "said no" |
| While those four went quiet, other responders started getting noticeably more calls, with total volume flat | **Step 2** — the list only reorders; it doesn't grow or shrink |

**What this can't confirm on its own:** whether those four responders are also farther from where most incidents happen — since closeness is 60% of the score, that would make the drop hit even harder. That needs real location data, which isn't in this code.

## Marcus's 14 Aug question, answered

Marcus asked whether the 4.2 reweighting was meant to apply to responders who'd already been turning jobs down, or only to new ones. Answered directly from `routing.py` and `config.py` (30 Sept): **no, it applies to everyone the same way.** There's no code path that treats a responder differently based on their decline history — the same formula, same weights, run for every responder on every callout.

What's probably behind the question: the formula is uniform, but the *effect* isn't, because recent-acceptance has always fed the score (unchanged since before 4.2) while what changed is how much each input counts — acceptance history down (40% to 25%), proximity up (45% to 60%). So a responder whose weak point was a shaky track record actually gets cut a little slack now, while a responder whose weak point is distance gets hit harder regardless of their track record. If someone with a rough history also happens to be far from most incidents, the two effects stack, and it looks like their history is being punished specifically — when proximity is likely doing most of the damage.

**This is still an inference, not a confirmed fact — H3 in `hypotheses-to-test.md` is the specific test that would confirm or kill it.** If the four affected responders' travel-time data comes back showing they're meaningfully farther from most incidents than the other twelve, that validates the proximity explanation given above. If their locations look ordinary, this explanation doesn't hold and the "why these four" question stays open, resting more on H1/H2 (the timeout misclassification and no-decay trap) as the full story. Needs Wen's per-responder location data either way.

## Next steps

1. Send the Ravi and Wen asks drafted in `00-rook/analysis/asks-drafts.md` — still unsent.
2. Get Wen to confirm whether this behavior is intentional, and whether the four affected responders are also farther from most jobs.
3. Get real event-level data — were the four's misses actually logged as timeouts or as declines? Daily, not weekly, numbers for them specifically.
4. Check whether more than four responders are affected — a few others in the tickets (Ashgrove, Halfmoon, Farlight, Stormwrack) may be earlier in the same slide.
5. Get a year-ago August comparison to settle the seasonality question.
6. Bring this to the regroup with Marcus and Nadia.

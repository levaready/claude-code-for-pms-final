# What should we look at first?

*Four talks with handlers · 2 to 5 Sept 2026*

Four handlers told us what bugs them. Here are seven problems, in the order I would look at them. The dots show how many handlers named each one. But the order is more than a vote count.

## Words to know

- **Handler:** The person who looks after a responder.
- **Responder:** The hero who answers calls for help.
- **Call:** A request that pops up on a responder's phone. Also called an offer.
- **Update 4.2:** The update we shipped on 12 August.
- **The four handlers:** Ambrose, Dot, Halloran and Kip. One dot means one handler.
- **The quotes:** These are their real words, not mine.

## How I picked the order

- **Harm:** Does a responder lose work or become less safe?
- **Proof:** Do our numbers, tickets or code agree with the handler?
- **Update 4.2:** Did our 12 August update touch it?
- **Ready:** Can we start now, or must we first find out why it happens?

> **The most important problem was named by only 2 of the 4 handlers.** Some responders have almost stopped getting calls. The big overall number hides this. Two of the hardest-hit responders, Meteor Mite and Vesper, sent in no tickets. These talks are the only time their handlers were heard.

**How to read the dots:** there are four, in this order: Ambrose, Dot, Halloran, Kip. A filled dot (●) means that handler said it. An empty dot (○) means they did not.

---

## Look at first

*These responders are losing work. Ask for the numbers now.*

### 1. Responders stop getting calls

○●○● **2 of 4** · Dot, Kip

- Numbers: 4 responders went from about 11 to 14 calls a week down to 0 to 2
- Two of them, Meteor Mite and Vesper, sent in no tickets
- Code: missing calls lowers a score, and it may never heal *(not proven yet)*

> "I just want it to look less like a coincidence when I'm staring at it at midnight and one card's dead quiet and the other's on fire." — Kip

**Why it is here.** Some responders get no work at all, and the big overall number hides it. These two handlers are the only ones who spoke up for Meteor Mite and Vesper.

**What to do.** Send my notes to Ravi and Wen. Ask how many calls each responder got, and how each one is scored.

### 2. Calls disappear before the responder can answer

●●●○ **3 of 4** · Ambrose, Dot, Halloran

- 9 of 25 tickets say this
- In 4.2 the time to answer went from 90 to 60 seconds
- It also happens to busy responders
- 60 seconds is longer than "a few seconds," so something else may be going on *(not explained yet)*

> "there was a period where a slower-arriving response of his still landed him the job more often than not, and lately that doesn't seem to hold the way it used to." — Ambrose

**Why it is here.** Most handlers said it, and update 4.2 changed the time limit. But Ambrose says it happened before 4.2, so the time limit is probably not the whole story.

**What to do.** Ask Wen how fast a call reaches the phone and when the clock starts. Ask Ravi to count missed calls apart from "no" answers.

---

## Next

*These are real and easy to fix. We can do them while we investigate.*

### 3. Handlers can't tell when a call is live

●●○● **3 of 4** · Ambrose, Dot, Kip

- Only heard in the talks *(no other proof yet)*

> "right now Mite and Gale both just go "bing" and I have to actually look to know which one." — Kip

**Why it is here.** The design team can start now. It helps handlers see calls sooner. But it does not fix responders being skipped or calls being lost.

**What to do.** Talk to Sofia about a different sound for each responder and a clearer "call is live" sign.

### 4. The saved filter resets without warning

●○○○ **1 of 4** · Ambrose

- Came out in 4.2
- No tickets about it *(no other proof yet)*

> "I'd rather it warned me the filter had reset than simply reset it." — Ambrose

**Why it is here.** It is quick to fix. It is the one thing from 4.2 that a handler noticed and liked. Quiet resets make him trust it less.

**What to do.** Ask Marcus if the reset happens after each update. Then add a note that says the filter was reset.

---

## Later

*Small fixes for the screen. Add them to the redesign.*

### 5. Status words are too small to read

●●○○ **2 of 4** · Ambrose, Dot

- Only heard in the talks *(no other proof yet)*

> "at a glance I sometimes cannot tell engaged from available without leaning in." — Ambrose

**Why it is here.** Two handlers said it. It is small and cheap. It fits in Sofia's screen redesign.

**What to do.** Add it to the redesign list.

### 6. No dark mode

○○○● **1 of 4** · Kip

- Only heard in the talks *(no other proof yet)*

> "Dark mode is the thing that actually changes my night." — Kip

**Why it is here.** Only one handler, but he asks every time. It is about comfort, not lost work.

**What to do.** Add it to the redesign list.

### 7. The tag guide is hard to find

●○○○ **1 of 4** · Ambrose

- Only heard in the talks *(no other proof yet)*

> "It sits in a drawer off the responder detail panel and I open it perhaps once a fortnight, when a new tag appears and I don't recognize it." — Ambrose

**Why it is here.** Ambrose said it is not urgent. He opens it about once every two weeks.

**What to do.** Add it to the redesign list.

---

## Not our job, but pass it on this week

Halloran mostly talked about Supply, the gear side of Rook. It is not yours to fix. But one thing is about safety, so it should not wait.

### Every gear request waits in one long line

> "One queue, everything in it, doesn't matter if it's laces or plate." — Halloran (a cracked vest plate waited eleven days for a signature)

**Tell Helen now.** A fix for gear approvals is already planned for 4.3. Ask if it lets urgent items skip ahead.

### Broken-gear reports seem to go nowhere, and gear search is weak

> "I file a failure report and it goes into a void." — Halloran

Give this to whoever owns Supply. Neither problem is on the plan for this quarter.

---

## Read this carefully

- Four people is very few. Do not treat the counts like a big survey.
- Some answers came after a direct question. Sofia asked Dot about quiet weeks. Halloran mentioned his missed call only at the very end.
- We have not talked to the handlers of Farlight or The Undertow. Both are responders who almost stopped getting calls.
- The numbers, tickets and code come from my earlier work in `00-rook/analysis/ticket-vs-csv.md`. The numbers stop on 31 August.

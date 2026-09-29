# Patterns: what's true and what's just noise

*A plain-language version of `patterns-signal-vs-noise.md`, written 28 Sept 2026.*

We looked at four things: complaint tickets, four talks with handlers, a spreadsheet of who got called each week, and the actual computer code that decides who gets called. Here's what we found, and how sure we are about each one.

## 1. Four heroes almost stopped getting calls.

The spreadsheet shows four heroes — Farlight, Meteor Mite, The Undertow, and Vesper — went from getting called about a dozen times a week to almost never. Two of their handlers said so themselves, without us asking. This is the biggest, most solid thing we found. Everything else should be checked against this one.

## 2. The number of complaint tickets doesn't tell you who's really in trouble.

Most tickets (16 out of 25) are people saying "nothing's coming in" — but the spreadsheet shows those same heroes are actually busy, some busier than ever. And the two heroes hurt worst wrote zero tickets. We have three guesses why the tickets and the spreadsheet don't match, but we haven't proven any of them yet.

## 3. Calls disappearing in a few seconds.

Lots of people say a call showed up and vanished almost instantly. But the rule says a call should stay up for 60 whole seconds. That's a real complaint, but the reason people are giving for it doesn't add up yet.

## 4. We checked if the update caused it — it probably didn't, not by itself.

People thought the August update caused the four heroes to go quiet. But we looked at the actual settings in the code, and the update should have made things *easier* for heroes who'd been turned down a lot, not harder. So that explanation doesn't hold up.

## 5. A few people wrote in twice about the same hero.

Three handlers each wrote two tickets about their own hero — first "it's quiet," then "I lost a call." That could mean something real is getting worse. Or it could just mean those three handlers write more tickets in general. Too small a group to be sure.

## 6. Someone said tickets tripled — we can't check that.

Nobody wrote down what "normal" ticket numbers look like, so we can't test if "3 times normal" is true.

## 7. The four talks with handlers gave us real clues, but they're not the full picture.

Two of the four handlers we talked to happened to mention two of the four quiet heroes, without being asked. That's useful. But those four handlers were picked to talk about something else — a screen redesign — not picked because their heroes were the most affected. Nine other heroes who show up a lot in tickets were never mentioned in any of the four talks.

## 8. We think we know why those four heroes never bounced back.

Here's the new one: it's not just that they're being offered fewer calls and turning more down. The spreadsheet shows they're barely being offered calls *at all* anymore — one hero got zero call offers her last week. And it kept getting worse every single week, unlike other heroes who dipped once and then bounced back. We looked at the code, and it has no way to let a hero's "score" go back up on its own once it drops. So once a hero falls behind, they get fewer chances, which keeps their score low, which gives them even fewer chances. It's a trap with no way out built into the code. This explains why they never recovered — it doesn't yet explain why it started happening to *these four* in the first place.

## 9. People started writing complaints the very next day — but not the right people wrote in.

The first ticket came in just one day after the update shipped, and the spreadsheet's numbers also started dropping that same week. So far so good. But when we checked hero by hero, only one of the four (The Undertow) had tickets that matched when his numbers actually dropped. Farlight's first ticket came two weeks after her numbers had already crashed. And the two worst-hit heroes, Meteor Mite and Vesper, got zero tickets the entire time — even though their numbers crashed exactly like the others. Most tickets, it turns out, are about heroes whose numbers never even moved. Writing a ticket doesn't mean you're the one in trouble — it just means you're the one who spoke up.

---

## The big picture

Don't chase whoever's complaining loudest — chase whoever the numbers say is actually hurting, because they're often not the same people. Two of our four hurt-worst heroes never said a word.

## The one number to tell the boss

1 out of every 4 heroes is now getting about 80% fewer calls than before the update. That's more honest than the overall "percent accepted" number, which is going back up and would make it sound like things are fine.

## Cheapest thing to do next

Ask the data person one simple question — what do these numbers in the spreadsheet actually count? That one answer would help us trust or throw out almost everything else on this list.

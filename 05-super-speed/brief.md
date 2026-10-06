# Helping heroes who stopped getting calls

**To:** Helen · **From:** LeVar · 5 Oct 2026 · Draft
**Click-throughs** (private until shared): [Responder and handler screens](https://claude.ai/artifact/AuFs5bqWq7WATcEVfNyrrq) · [Fix Options](https://claude.ai/artifact/Ft5NLqwLCY6EX5z5WugKmM) · [Ticket Lens](https://claude.ai/artifact/L2Jg8YNAchqVpbgVy7oYiq) · [Quiet Count](https://claude.ai/artifact/TzBq1QanRnq4LNcfLWiQsk)

**Short answer:** Don't just change a number. Show when someone has gone quiet, and give them a way back. Two people need to see it: the handler who watches, and the responder it happens to.

**Words to know:** A *responder* is a hero who answers calls for help. A *handler* is the person who looks after a responder. An *offer* is a call for help sent to a responder's phone.

## What Kip would see

Today Kip has two cards side by side. One hero is almost never called. The other is called all the time. Nothing on the screen says why. With this, each card tells him.

> **Meteor Mite: 1 offer this week (usually 11).** Calls aren't reaching them. A few missed calls pushed them down the list. **[Give a fair shot]**
>
> **The Gale: 21 offers this week (usually 13).** Doing extra work while others are quiet.

The button uses the "override" that handlers already have (added in 4.0). Helping the quiet hero should also lighten the load on the busy one.

## What a quiet responder would feel

1. **A message first, before any fix.** Short and plain: *A change in August cut offers for some people. It isn't your fault. We're fixing it. Expect an update by [date].* In a practice round with simulated heroes, every hero who had gone quiet asked for this without being prompted. Several had assumed the app had dropped them. One said the silence was worse than the fix.
2. **A "My offers" screen.** It shows how many offers they got, took, and didn't take in four weeks. It says their account is fine and that we can't say when the next offer will come, because that depends on where help is needed.
3. **A comeback offer.** The first offer after a long quiet time gets extra time to answer. If the time runs out, it doesn't count against them. Today it goes the other way. Five tickets say a hero waited weeks, then the first offer disappeared in seconds.

*"starting to wonder if im still even in the system"* (The Undertow, ticket T-013).

## The rule underneath

- Running out of time is not the same as saying no. It should cost less.
- A hero's place in line should recover after a quiet time. Today it stays stuck.
- A one-time lift for the four heroes who are left out right now.

This answers Wen's question from 2019. These four didn't stop taking work. We stopped asking them.

## What's built so far

- **Fix Options.** Try the fixes side by side: put the timer back to 90 seconds, let places in line recover, or give left-out heroes a one-time lift. In the model, putting the timer back alone leaves about 8 in 10 already-left-out heroes still left out. Adding the lift brings most of them back, in about 3 weeks. It also shows who pays: the busy heroes get fewer offers. The numbers are examples, not a forecast.
- **Ticket Lens.** Shows each ticket next to the hero's real weekly offers. 15 of 25 tickets don't match the data. It finds Vesper and Meteor Mite, who dropped a lot and never wrote in.
- **Quiet Count.** Puts the usual success rate next to a count of heroes left out. The rule "under half of their own usual offers" flags the four a week sooner than "fewer than 3 offers".

## What I need from you

1. OK to send affected heroes the message, with a date we can keep.
2. OK to bring Wen in this week to design the rule.
3. OK to try the screens with 2 or 3 real heroes, through Kip or Dot.

## What we still don't know

- Why 60 seconds was picked, and what the records show. Wen can tell us.
- **Biggest risk:** if these heroes also live far from where help is usually needed, moving them up the line may not bring calls back. Distance counts for 60% of how the line is ordered. We need location information first.
- We haven't talked to a real responder. A practice round with simulated heroes shaped these screens, but it isn't real feedback.

---
name: review-checklist
description: Checks a brief or one-pager against four things: it names who owns it, says how we'll know it worked, keeps the same scope from start to finish, and explains the problem before the fix. Use this whenever the user points at a brief, one-pager, proposal, spec or product doc (one file or a folder of them) and asks to review it, check it, sanity-check it, run the checklist, see whether it is ready to share or send, or find what is missing, even if they never say the word checklist. Also use it for a scheduled or overnight run over a folder of briefs. It reports yes or flag for each check, with the line that decided it. It does not rewrite the brief.
---

# Review checklist

This is a fast, consistent read-through for the four gaps that most often make a brief hard to act on. Each one is a question the reader will ask the moment they pick the brief up: who is accountable, how will we know it worked, what exactly are we signing up for, and why do this at all. Checking the same four things the same way every time is the point, so a flag on one brief means the same as a flag on another.

## How to run it

1. **Find the briefs.** The user gives a file or a folder. Read every brief from start to finish; the scope check compares the beginning with the end, so skimming is not enough. If a file is not a brief (a spreadsheet, code, a log), say so and skip it.
2. **Run the four checks** below on each brief.
3. **Report in the format below.** Quote or point to the line that decided each flag, so the author can find it in seconds.
4. **Stay read-only.** Do not rewrite the brief, grade the idea, or fix the flags unless the user asks. Stay to these four checks; extra checks make the results harder to compare.

## The four checks

### 1. Owner named
Is a specific person or team accountable for delivering or deciding this?
- **Yes:** a named person ("Sofia"), or a named team that will do the work ("Marcus's team builds it"). If they are named but "not yet staffed", it is still a yes; add a note.
- **Flag:** nobody named; "TBD" or "to be decided"; "whoever picks it up". Two near-misses are also flags. A header that only names the author's department ("Product, Dispatch") says who wrote the brief, not who owns it. A person named only to consult ("needs Sofia's input") is a stakeholder, not an owner.

### 2. Success measure
Does the brief say what we would observe if it worked?
- **Yes:** an observable result with a direction or a target: "fewer tickets mentioning X", "zero requisitions shipping without a second sign-off", "median reply time under 4 minutes". Not having a baseline yet does not make this a flag. Add a note that a baseline is worth getting.
- **Flag:** no such statement. Also a flag: only that the work gets done ("log every override"), a description of what the feature does, or feelings with nothing observable ("customers feel more confident").

### 3. Scope stays the same
Compare what the brief commits to at the start with what it commits to by the end: the opening ask, the proposal, any scope section and any next steps.
- **Yes:** everything lines up.
- **Flag:** anything is added that was not in the opening ask ("and while we're at it", "this could eventually replace..."), a scope section contradicts the proposal, or the ask quietly shrinks or changes. Say what the opening ask was and what was added or dropped.
- **Not a flag:** a clearly labelled out-of-scope or later list that does not change the ask.

### 4. Problem before the fix
Does the reader learn what is wrong, and for whom, before hearing the solution?
- **Yes:** the first substantive content explains the problem (who hits it, what happens, some evidence), and the proposal comes after. A short framing line before the problem is fine.
- **Flag:** the proposal or solution comes first; the problem only shows up after it; a section titled "Problem" that really pitches the fix; or background that describes the market or the idea but never says what is wrong.

## Judging rules

- **Judge what is on the page, not what the author probably meant.** If you would have to guess to say yes, flag it and name the missing piece.
- **One flag per failed check**, even when the issue shows up in several places.
- **Be consistent.** When a case is borderline, apply the definitions above in the same way you would for any other brief, and use a short note on a "yes" for a soft concern instead of a flag.

## Report format

Use this shape for every run. It stays the same whether the run is manual or scheduled, so reports can be compared over time. Take the start and finish times from the clock, not from memory.

```
review-checklist — <manual | scheduled> run
Started: <timestamp>
Finished: <timestamp>
Source: <path> (<n> files)

<file name>
  owner named .................. yes (<who>) | NO — flagged
  success measure .............. yes | NO — flagged
  scope stays bounded .......... yes | NO — flagged
  problem stated before fix .... yes | NO — flagged
  -> <n> flag(s): <what is missing, in a sentence or two, with the line that decided it>
     (or: -> clean)

<N> briefs checked, <M> flagged.
```

Put a note after a "yes" in brackets when a soft concern is worth passing on (for example "yes (no baseline yet)"). If the run is unattended or the user gives a path, save the report to that file as well as showing it.

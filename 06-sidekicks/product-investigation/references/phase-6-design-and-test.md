# Phase 6: design and test

Goal: show the decision-maker what you would build, from the point of view of the people it happens to, and be honest about how sure you are.

Start only when the build conditions in SKILL.md ("When building starts") hold: gate passed, a direction to show, and the user's answer to the deliverables question. This file covers prototypes, simulated interviews and the confidence check. The documents (facts sheet, one-pager, PRD, deck with speaker notes) are in `deliverables.md`.

## Re-read the request

Before building, read the decision-maker's actual request and the charter. The ask usually says more than the first reading suggests (for example: "not a setting", "something a handler would notice", "something I can click through"). Check each deliverable against it line by line. Run the gate again if the audience or the deliverable shifted.

## Prototypes

1. **Choose by impact and effort.** List candidates in a table with what each shows, who it is for, impact and effort. Prefer ones that settle a decision or would have caught the problem early.
2. **Build in parallel when there are several.** Give each agent one prototype, its own file, a shared look, and these rules: label example numbers and invented wording, run the logic once outside the page and report what it really shows (do not hard-code the result you expect), no git commands, no shared browser pane. Publish each as a shareable interactive page if the project allows it.
3. **Check them yourself.** Agents often cannot open their pages. Open each one at phone width, check for errors, click through the flows, and read the numbers it produces against the data. Fix what you find and republish.
4. **Report surprises.** If the model or the data contradicts what the brief says (for example, a rule you proposed flags a problem a week later than another rule), say so and change the brief.

## Simulated interviews (a rehearsal, not evidence)

Use them to find holes before real people see the work.
1. **Write an unbiased guide.** Open questions only. Do not name a favourite option and do not ask "would this help?". Ask about the last time something went wrong, how they decide, what they understand the page to be, what is confusing, which option matters most and least, what worries them, what they would notice in an ordinary week, and what they would need to trust it. End with "what didn't we ask?".
2. **Play each person with an independent agent**, grounded in that person's real data (their own rows, their own tickets) and nothing else. Include someone who benefits from the status quo, because a fix usually moves work from someone to someone.
3. **Ask for a list of invented details** from each agent. Those are not findings.
4. **Check the audience.** If the thing you showed was built for a director, simulated users will mostly tell you how they want to be spoken to. That is still useful, but do not read it as a verdict on the design.
5. **Watch for anchoring.** If your page names a winner in its headline, the simulated users will pick it. Make the first view neutral and put interpretation below the evidence.
6. **Report counts and caveats first**, then what was missing from every option. Often the biggest finding is not about the options at all (for example: tell affected people it is a known problem, it is not their fault, and when it will be fixed).
7. **State plainly that real users are still needed**, and propose a way to reach two or three.

## The confidence check

Give a score for the brief and for each prototype, and score the parts separately: does it work, does it show the idea clearly, is it the right thing to build. List what holds the score down, and what would raise it, with a rough value for each. Say how to present it ("here is what it could look like", not "here is what will work").

Gate: does the confidence score say what would raise it?

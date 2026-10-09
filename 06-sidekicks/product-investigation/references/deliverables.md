# Deliverables: what you can build, and in what order

Build only what the user chose at the build trigger (see "When building starts" in SKILL.md). Every document must tell the same story, so they all draw on one facts sheet.

## Suggesting a default

You still ask. This just helps you offer a good suggestion.

| The charter says the audience is... | Suggest |
|---|---|
| A director or VP deciding what to do | One-pager and a prototype |
| An engineering team that will build it | PRD (and a prototype to show intent) |
| A review meeting or a room of people | Slide deck with speaker notes (and the one-pager as a hand-out) |
| The user alone, still exploring | Prototype only |
| Unclear | Do not suggest. Go back to the gate. |

## The facts sheet (build first, always)

One short file that every other document copies from. It prevents two documents quoting different numbers.

- The decision this work serves, and who makes it.
- The headline number, with one line on where it came from.
- The three to five facts that carry the argument, each with its source file and whether it is verified or inferred.
- The recommendation in one or two sentences.
- What is proposed (new wording, thresholds, features you invented) versus what is evidence.
- The open questions and the biggest risk.
- The confidence score and what would raise it.

When a number changes, change it here first and then in every document.

## One-pager

For a director: one page, plain words, the answer first.
- What you would build, in one or two sentences.
- What the people it affects would see or feel, with short concrete examples using real names and numbers from the data.
- What is already built, what you need from the reader (two or three clear asks), and what you still do not know.
- Define terms once, at the reading level the user asked for.

## Prototype

Follow the prototype rules in `phase-6-design-and-test.md`. A prototype is for showing an idea, so label example numbers and invented wording, and do not let it stand in for evidence.

## PRD

For the team that will build it. Write it so someone who was not in the investigation can act on it.
1. **Problem and evidence.** What happened, who is affected, and the numbers with their sources. State what is verified and what is inferred.
2. **Goals and non-goals.** What success looks like, and what this work deliberately does not do.
3. **Users and their situations.** The people it touches, in plain terms, with one concrete scenario each.
4. **Requirements.** Numbered, each with a one-line reason and a way to check it. Mark each as must, should or could. Separate the rule changes from the screens.
5. **Success metrics.** The headline measure, a guardrail metric that must not get worse, and how long you will watch. Prefer a measure that cannot be fooled by an average.
6. **Open questions and risks.** Each with an owner and what would settle it.
7. **Rollout.** How it ships, what could be turned off, and how you would know to roll back.
8. **Out of scope and later.** Ideas heard in the evidence that belong elsewhere.

## Slide deck with speaker notes

For a room. Use the slide tooling the project provides (a slides artifact type, a presentation skill, or an outline if nothing else exists). Every slide gets speaker notes.
- **Storyline:** the situation, what we found, why it happened, what we recommend, what it looks like, what we need from you, what we still do not know.
- **One idea per slide**, with the answer as the slide title.
- **Speaker notes on every slide:** what to say in two or three sentences, the evidence to cite with its source, and the most likely question with a short answer.
- **A closing slide of decisions and asks**, and one of open questions.
- Keep the deck to the length the room allows. Fewer slides with notes beat more slides without.

## Before you hand anything over

- Do the numbers match the facts sheet?
- Is everything simulated or proposed labelled as such?
- Does each document say what would raise the confidence score?
- Has anything personal that you were asked to keep out stayed out?
- Has the user seen it before anyone else does? Sending is theirs to approve.

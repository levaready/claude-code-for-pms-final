---
name: product-investigation
description: Walks a product owner from "something happened and we don't know why" to evidence-backed root-cause hypotheses, a short brief for their director, and clickable prototypes, with a confidence gate up front and an honest confidence score at every step. Use this whenever the user wants to investigate a metric drop, a spike in complaints or tickets, a release that landed badly, a feature that underperformed, or says things like "what went wrong", "find the root cause", "make sense of this feedback and data", "what should we build instead", or "my director asked what we're doing about this", even if they never say the word investigation. Also use it to onboard onto a new product from its documents, and when the user asks for a prototype, one-pager, PRD or slide deck to respond to a problem they have been looking into. Do not start any analysis until the confidence gate in step 0 is passed, and do not build anything until the build conditions in "When building starts" are met.
---

# Product investigation

This skill turns a messy "something went wrong" into a decision a director can act on. The order of the steps matters, because every failure we have seen traces back to skipping one: naming a cause before the data supports it, trusting the loudest signal, quoting a number without its rows, and presenting simulated feedback as if it were real evidence.

## Step 0: the confidence gate

Be at least 95% confident in four things before doing any analysis. The investigation is long and each phase builds on the last, so a wrong assumption about who the user is or what decision they face compounds silently. Ten minutes of alignment costs far less than a polished answer to the wrong question.

| Dimension | You are confident when you can state... |
|---|---|
| **The ask** | the exact deliverable, the question it answers, and what is out of scope |
| **Who they are** | their role, who they report to, what they already know, and who will read the outputs |
| **The goal** | the decision or outcome they want, by when, and what "good" looks like |
| **Your role** | what you do on your own (read, analyze, draft, build), what you check first (anything sent, posted, committed or deleted), and what is off limits |

How to run it (the rubric, question format and templates are in `references/intake-gate.md`; read it now):

1. **Orient first, read only.** Read the project instructions, any notes, the folder listing and the conversation. Anything already written down counts as evidence, so never ask a question you could answer by reading.
2. **Score each dimension 0 to 100 and name the evidence** (a quote or a file) behind it. The gate score is the lowest of the four, not the average, because one blind spot can sink the work.
3. **All four at 95 or above:** give a short read-back and continue. The user can correct you on the spot.
4. **Any below 95:** stop. Ask only the questions that would lift the lowest scores, at most four, each with your best-guess answer so a plain "yes" is enough. Then wait.
5. **Save the result as the charter** (`references/intake-gate.md` has the template). Everything later is checked against it.

Run the gate again when the scope or audience changes, when a new session starts (read the charter, don't re-interview), and before any outward-facing action such as sending, posting, publishing or pushing.

If the user tells you to skip it ("just go"), do so, but record your assumptions in the charter as assumptions, state the real gate score, stay with reversible work (reading, analysis, drafts), and flag the weakest dimension in every output. The gate protects the user's time; it is not a way to refuse to help.

## The six phases

Each phase writes a file and has a gate question. Do not move on until the gate question has an answer you can defend. Read the reference file for a phase when you reach it.

| Phase | What you do | Output | Gate question |
|---|---|---|---|
| 1. Onboard | Read the product documents and write the working context | Working context file | Are products, people, vocabulary and "where things stand" written down, with stated facts kept apart from inference? |
| 2. Map the evidence | Inventory every pile of evidence and list contradictions and gaps | Evidence map | Is every source read, and does each gap have an owner? |
| 3. Listen and count | Group interviews and tickets, count each group, quote one line each | Triage file | Are the counts shown, and is it clear who each source does not cover? |
| 4. Read the numbers | Before and after, the split between people, the one number with its rows | Numbers file | Are the rows shown, and did you check whether the average hides a group? |
| 5. Find the mechanism | Explain how the system works in plain words, then write ranked hypotheses | Hypotheses file | Is each hypothesis falsifiable, and ranked by how resolvable it is rather than how plausible? |
| 6. Design and test | Only after "When building starts" below: build the chosen deliverables, run simulated interviews, give a confidence check | The chosen deliverables, confidence check | Does the confidence score say what would raise it? |

Phases 1 to 4 are in `references/phases-1-to-4-evidence.md`. Phase 5 is in `references/phase-5-hypotheses.md`. Phase 6 is in `references/phase-6-design-and-test.md`, and the documents you can build there are in `references/deliverables.md`.

## When building starts

Nothing gets built until three things are true: no prototype, one-pager, PRD or slide deck. Building early is the most expensive way to be wrong, because it produces something polished that answers a question nobody has confirmed. A passed gate alone is not enough, and neither is a user saying "build it". The three conditions:

1. **The gate is passed.** The charter names the audience and the decision the work serves.
2. **There is a direction to show.** Either phases 1 to 5 are done and the user has picked the hypothesis or fix to show, or the user brought their own direction ("prototype the quiet flag"). In the second case write "direction supplied by the user, not yet backed by evidence" in the charter, offer to run the evidence phases first (suggest yes when there is evidence in the folder), and carry that caveat into everything you build.
3. **The user has chosen the deliverables.** Ask once, and wait for the answer. The user may already have named one (say, a prototype). That is a good start, but it is not the whole answer, because people often want the supporting documents too and do not think to ask. So always name all four:

   > Which of these do you want?
   > - Prototype (clickable and shareable)
   > - One-pager (for the director)
   > - PRD
   > - Slide deck with speaker notes
   >
   > My suggestion: <your pick, with one line on why>.

   If they have already named one, say so and ask about the rest: "You asked for a prototype. Do you also want a one-pager, a PRD, or a slide deck with speaker notes?" If you are already asking gate questions, add this as the last one so the user answers everything in one go.

Start the message by saying where each condition stands in one line, for example "Gate passed, direction chosen (#1), so the one thing left is which deliverables you want." If a condition is missing, name it. This lets the user see why you are building yet, or why you are not.

Once all three hold, build in this order: a facts sheet, then the one-pager, the prototype, the PRD and the deck (only the ones chosen). The order keeps every document telling the same story. Do not build any of them before the user has answered the deliverables question, even when the rest of the work is clear.

## Rules that hold in every phase

- **Separate what sources state from what you infer.** Label every hypothesis as a hypothesis. Readers trust the work to the degree they can see which is which.
- **Do not name a cause until the data supports one.** Offer the data that would separate the candidate causes instead.
- **Show the rows behind any headline number.** A number alone cannot be checked, and it hides who is affected.
- **Say who each source does not cover.** Tickets, interviews and data each miss different people. Agreement between piles means little if they cover the same few people.
- **Simulated is not evidence.** Practice interviews with simulated users, toy models and generated example data are useful for rehearsing and for spotting gaps. Label them as simulated everywhere they appear.
- **Give a confidence score and what would raise it.** A bare number invites argument. The raising conditions turn it into a to-do list.
- **Match the reading level the user asks for.** If they ask for plain words, define terms once and use the plain word everywhere.
- **Keep private detail out.** Interviews and tickets often contain incidental personal detail. Leave it out of everything you write.
- **Ask before anything outward-facing.** Sending, posting, publishing, committing and pushing happen when the user says so, unless they have clearly authorized it ahead of time.
- **Follow the project's own conventions** (its instructions file, folder layout, naming). Save work as files, not only in the chat, so a later session can pick it up.

## Closing a session

Follow `references/closeout.md`. In short: save the user's own prompts exactly as typed if the project keeps a prompt library, update the working context with what is new and whether each item is verified or inferred, commit and push only when asked, and report what was done with the link.

## Using it on a new case

Four things change each time: the evidence folders, the metric that moved, what counts as an "entity" (heroes, customers, accounts, stores), and the audience for the brief. Everything else carries over. If the case is not a product change at all (a one-off data question, say), run only the phases that help and say which you skipped and why.

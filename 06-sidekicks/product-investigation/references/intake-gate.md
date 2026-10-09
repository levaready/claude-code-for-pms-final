# The confidence gate (step 0)

The gate exists to answer one question before any real work starts: do I know what this person wants, who they are, what they are trying to achieve, and what they expect of me? A "95% confident" claim only means something if it is tied to evidence, so this file explains how to score, how to ask, and how to record the result.

## What each score means

Score each of the four dimensions on the same scale.

| Score | What it looks like |
|---|---|
| **95 to 100** | The user said it directly, or a document you read says it, and nothing you have seen contradicts it. You could restate it and the user would say "yes, exactly". |
| **80 to 94** | Strongly implied, but one reasonable alternative reading remains. |
| **60 to 79** | Inferred from context. Several readings are plausible. |
| **Below 60** | A guess. |

Rules for scoring honestly:
- Cite the evidence for each score: a quote from the conversation, or a file and line. If you cannot cite anything, the score is below 80.
- The gate score is the **lowest** of the four. Averaging lets a strong "ask" hide a weak "audience".
- Politeness is not confirmation. "Sounds good" to a summary that left out the audience does not raise the audience score.
- An explicit "yes, that's right" to your read-back raises every dimension you stated in it to 95 or above, because the user has checked it. This is the cheapest way to close the gap.

## Where to look before asking

Read these first. Each can raise a score without costing the user anything.

| Dimension | Likely sources |
|---|---|
| The ask | The user's message, the files they pointed at, any request note or brief in the folder |
| Who they are | The project instructions file, notes about the user, signatures and names in documents, the org chart or team directory |
| The goal | Messages from their manager in the folder, roadmap and commitments, what the deliverable is for |
| Your role | The project instructions (what is and is not allowed), earlier requests in the conversation, how the user has worked with you before |

## Asking well

Ask only when a dimension is still below 95 after reading.

- **At most four questions, one per weak dimension.** More than that feels like an interrogation and the user stops reading.
- **Give your best guess with each question**, written so that "yes" is a complete answer. For example: "Is the deliverable a one-page brief for Dana, by Friday? (my default)".
- **Close the biggest gap first.** If you can only ask two questions, ask the ones that move the lowest scores.
- **Never ask what you could read.** Never ask about something with a conventional default, such as file format; state the default in the read-back instead.
- **Then stop and wait.** Do not start the analysis "while waiting". Reversible orientation reading is fine; analysis is not.

## The read-back

Use this format whether you pass the gate or not. When you pass, keep it to the four lines and continue. When you fail, add the questions.

```
Before I start, here is what I understand. Gate score: 9X (lowest: <dimension>).

- Your ask: <the deliverable and the question it answers>
- Who you are: <role, who you report to, what you already know, who reads the output>
- What you're trying to achieve: <the decision or outcome, by when, what good looks like>
- My role: I will <do on my own>. I'll check with you before <outward actions>. I won't <off limits>.

Assumptions I'm making: <anything below 95, each marked as an assumption>

Questions (only if the gate score is below 95):
1. <question>? (my guess: <answer>)
```

## The charter

Save the result so later sessions and later phases can check against it. Put it where the project keeps its notes, named `charter.md`.

```
# Charter
Date: <date>   Gate score: <lowest of four>

## The ask
<text>   Evidence: <quote or file>   Score: <n>
Deliverables: <named by the user | not chosen yet: ask at the build trigger>
Direction to show: <chosen after phase 5 | supplied by the user, not yet backed by evidence | none yet>

## Who they are
<text>   Evidence: <...>   Score: <n>

## The goal
<text>   Evidence: <...>   Score: <n>

## My role
Do on my own: <...>
Check first: <...>
Off limits: <...>   Evidence: <...>   Score: <n>

## Assumptions still open
<list, each with what would close it>
```

## When to run the gate again

- The scope grows ("now also look at X") or the audience changes ("this is going to the CEO").
- A new session starts. Read the charter and the project instructions first. Only ask if something there is stale or something new makes a dimension drop.
- Before any outward-facing action: sending a message, posting, publishing, committing, pushing, deleting. The question is narrower here: am I confident the user wants this exact action, to this exact place, with this exact content?

## If the user says to skip it

Skipping is the user's call. Record the assumptions in the charter, write the true gate score, keep to reversible work, and mark the weakest dimension in the header of each output ("Assumes the reader is X"). Do not take outward-facing actions on assumptions.

## Mistakes to avoid

- Claiming 95 without being able to point at evidence.
- Asking five or more questions, or questions whose answers are in a file you did not open.
- Treating a long, detailed message as automatically clear. Detail about the task does not tell you who will read the result.
- Re-interviewing the user each session about things the charter already settles.
- Starting analysis "to be helpful" while the gate is still open. Early work on the wrong question is exactly what the gate prevents.

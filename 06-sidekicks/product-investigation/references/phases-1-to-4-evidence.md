# Phases 1 to 4: from documents to numbers

These phases build the evidence base. Each writes one file. Each ends with a gate question you should be able to answer before moving on.

## Phase 1: Onboard

Read everything in the product or company documents folder before writing anything. Then write the working context into the project's instructions file (or a notes file if the project keeps instructions separate). Keep it under about two pages and put the date at the top, because status goes stale first.

Headings that worked:
- **Company and products:** what each product does in one flow, who uses it, and where the products touch each other. Seams between products are where changes surprise people.
- **People:** name, role, what they own, and who is the real source on each technical area. Note who left and who can still be reached.
- **Vocabulary:** words that mean something specific here. Include the headline metric and exactly how it is calculated.
- **Where things stand:** what shipped and when, the symptoms, what is measured and what is not, open questions that nobody has answered, commitments that are locked.
- **How to work with me:** the rules from the charter (separate stated from inferred, do not name a cause early, and so on).
- **Confidentiality:** anything the documents say must stay private.

Gate: are products, people, vocabulary and status written down, with what the documents say kept apart from what you infer? Flag small conflicts between documents (dates, who owns what) instead of silently picking one.

## Phase 2: Map the evidence

List every pile of evidence: documents, data files, code, tickets, interviews, anything else. For each, note the date range, how many items, who or what it covers, and who produced it and why. Then read the whole folder, not only the files you were pointed at, because contradictions often sit in the files nobody mentioned.

Produce two lists:
- **Contradictions:** places where two sources disagree (a ticket says "nothing for ten days" and the data shows the person was busy; a README says a function does X and the code does Y; a roadmap says an item shipped and the release notes omit it).
- **Missing:** things you would need and cannot find, such as a year-ago baseline, an event log, a diff of the code, a definition of a column. Give each a likely owner and a draft question. Drafting the question is enough; sending it is the user's call.

Sanity-check the basics before trusting any source, because small slips here quietly bend everything after:
- **Dates.** Work out the weekday of every key date (a "Friday" launch that falls on a Saturday means the notes or the calendar are wrong). Check whether the latest period is a full period or only part of one.
- **Definitions.** How is each rate calculated, over what window, and could recent cases still be unresolved (a trial that has not had time to convert)?
- **Units and totals.** Do the parts add up to the total? Are the units the same across files?

End the phase with a **first look**: the headline rows and the one or two things that stand out, labelled as a first look, so the user sees progress while the gaps are chased. Rows are not a cause; keep naming causes for phase 5. Ask at most three evidence questions, ranked by how much each would change the picture, each with your best guess so a "yes" is enough.

Gate: is every source read, and does each gap have an owner?

## Phase 3: Listen and count

For interviews and tickets:
1. **Group by what is being reported**, not by who reported it. Name each group in plain words.
2. **Count each group**, and say what the total is. "5 of 25" lets the reader judge weight.
3. **Quote one line per group**, verbatim, so the reader can hear the voice.
4. **List the filers.** Who wrote in, how many times, and whether the repeat filers are the same kind of person.
5. **Compare the piles.** What is loud in the interviews but rare in the tickets, and the reverse? Where do they disagree? Which entities appear in one pile and never in the other?
6. **Say what each pile cannot tell you.** Interviews recruited for another purpose are not a representative sample. Tickets track who is vocal, not who is affected. Severity ratings set by the person filing vary with temperament.

Keep incidental personal detail out of everything you write.

Gate: are the counts shown, and is it clear who each source does not cover?

## Phase 4: Read the numbers

1. **Pick the date that matters** and show the weekly (or daily) numbers before and after, with the rows behind them. If the user asks for "the number", give the number and show the rows anyway.
2. **Check the split.** Did the change land on everyone or on some people much more? Compute per entity: before average, after average, change. An average that recovers can hide a group that collapsed. A group can also collapse while the total stays flat because the work moved to other people.
3. **Find the one number** a director would want, with one line on where it came from. Prefer a number that cannot be fooled by the average (for example, "1 in 4 responders now get 80% fewer offers").
4. **Line up the other piles with the data.** When did people start writing in, and when do the numbers move? Do the tickets name the entities the data shows are affected? Where tickets and data disagree, list the explanations that have not been ruled out (a weekly total can hide a short dry spell; a screen may show a filtered view; a column may count something different from what readers assume).
5. **Test the easy explanation** against the shape of the data. A seasonal story predicts a gradual drift and an even effect; a sharp cliff on the release date that hits a few entities does not fit it. If you have no baseline from the same period last year, say the explanation cannot be settled.
6. **Check what is missing.** Daily data, a baseline, definitions of columns, the split of one outcome from another (a timeout versus a refusal).

Gate: are the rows shown, and did you check whether the average hides a group?

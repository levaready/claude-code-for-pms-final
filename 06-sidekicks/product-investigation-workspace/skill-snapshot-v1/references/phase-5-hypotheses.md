# Phase 5: find the mechanism

Goal: explain how the system produces the symptom, then turn the explanation into hypotheses that can be tested, ranked by how likely the team is to settle them.

## Explain the system in plain words first

If the cause could sit in code, a process or a policy, walk through it step by step for a reader who will not read it themselves.
- Describe what happens from trigger to outcome in numbered steps, and say which file or owner each step lives in.
- Quote the exact lines that matter (for example, the only place points are removed and the only place they are added).
- Say what the system does not do. Surprises hide in what is missing, such as no decay, no reset, or no manual path.
- Say what changed recently and what did not. A change that was already latent can be made worse by a small recent change.
- Say what you cannot verify from what you have. A repo with a single commit cannot show what changed between versions, and a changelog is self-reported.

Then connect the mechanism to the data: for each pattern in the numbers, name the step that would produce it. Check the timing predictions the mechanism makes (for example, a rate that falls first and a volume that falls a week later).

## Write hypotheses

Use the same shape every time, so they can be compared:

| Rank | Hypothesis (If, then, because) | Null hypothesis | What would falsify it |
|---|---|---|---|

- **If** a specific cause is true, **then** a specific, observable thing follows, **because** of a named mechanism.
- The null states the boring alternative. The falsifier names the data that would kill the hypothesis.
- Include the unflattering candidates (seasonality, voluntary behaviour, a delivery bug), even when the existing evidence argues against them, and say what the existing evidence is.
- **Rank by how likely you are to settle each one**, not by how likely it is to be true. A hypothesis with a cheap, decisive test (one data pull, one yes-or-no question for one person) goes above a more plausible one that needs data nobody has.
- Add one sentence on why the top two outrank the rest, with the supporting data you already hold.

## Signal versus noise

Make a table of every pattern you have found: the pattern, what supports it, what weakens it, and where it stands. This stops the loudest signal from steering the work. Typical entries: a pattern that holds in the data, a complaint count that does not map to who is affected, a claim with no baseline, a story the numbers contradict. Update it as findings arrive instead of starting a new one.

## Optional: a blind debate

Use this when the evidence conflicts or the stakes justify the cost. It is expensive, so say so before you start.
1. **Round one.** Start one independent agent per evidence pile (for example: documents, data, code, tickets, interviews). Each reads only its own pile and none reads your earlier analysis, so their agreement means something. Each reports FINDINGS, HYPOTHESIS, CONFIDENCE and WHAT I'D NEED, and has to commit to a specific, falsifiable claim.
2. **Round two.** Give each agent a short summary of the other agents' findings and point out any direct tension between two of them. Ask each to defend, revise or concede, and to say whether it can sign onto a combined statement.
3. **Report.** State the consensus if there is one, how each agent's confidence moved, any concession that changed a position, and a deduplicated list of what is still needed. If they do not converge, the list of what is needed is the result.

Never let the agents see your conclusions in round one. Note that agents share one underlying model, so agreement is evidence about the files, not independent confirmation of the world.

## Draft the asks

Turn the open items into short messages to named people: what you need, why, and what a "no" would mean. Mark them as drafts. Sending is the user's call.

Gate: is each hypothesis falsifiable, and ranked by how resolvable it is rather than how plausible?

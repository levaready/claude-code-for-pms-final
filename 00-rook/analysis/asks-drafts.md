# Draft asks — 4.2 acceptance investigation

Drafts only. Nothing here has been sent. Edit the tone to match how you talk to each person, and replace [name] with yours.

Suggested order: Ravi and Wen first (they unblock everything), Nadia alongside, Helen once you have their first answers.

---

## 1. Ravi Menon — via #data

**Subject: Per-responder offer data for 4.2 (before your next weekly)**

Hi Ravi, I'm the new Dispatch PM, picking up 4.2 from Priya. I've been working from a weekly per-responder CSV (offers sent / offers taken, 29 Jun to 31 Aug) and I'd like to check it against your source data before we draw conclusions. Could you send:

1. **Per responder, per week: offers sent, accepted, declined, timed out**, as separate counts. From 1 Jun to today if you can.
2. **The same weeks from 2025**, so we can tell how much of the August dip is seasonal.
3. **What `pings_taken` means** in that CSV, and where it came from. Was it yours?
4. **How many responders received zero offers each week**, and any distribution view of offers per responder. The aggregate acceptance rate recovered to about 73% by w/c 31 Aug, but the CSV shows a handful of responders dropping to 0-2 offers a week, and I can't see that in the aggregate.
5. **Median time-to-accept by week**, if you have it.
6. **Your standing weekly acceptance report**, if it's separate from the above.

I'm meeting Marcus and Nadia to regroup on 4.2 soon, so anything before that is most useful. Happy to take a rougher cut first and the full one later. Thanks.

---

## 2. Wen Li — cc Marcus

**Subject: Questions on 4.2 routing behaviour (async first, call if easier)**

Hi Wen, I'm the new Dispatch PM. Priya said you're the person to ask about how ranking works, and there's no written description, which I'd like to fix. I've read `dispatch-routing` but have questions the code doesn't answer. Looping Marcus since `config.py` says to.

**Specific to 4.2**
1. Marcus asked on 14 Aug whether the new weighting was meant to apply to responders who've been declining or timing out, or only everyone else. The config doesn't distinguish. Was that a decision, or how it fell out?
2. For Farlight, Meteor Mite, The Undertow and Vesper: can you pull their current recent-acceptance score and typical travel time to recent incidents? Their offers dropped from ~12 a week to 0-2 after 4.2, and I want to know whether it's proximity, acceptance history, or both.
3. Was the timeout cut from 90s to 60s tested against anything? Who asked for it?

**How it behaves**
4. `offer_to` returns no-answer and `record_declined` scores it the same as a decline. Intended? Does that mean a shorter timeout lowers more people's scores?
5. Offers stop at the first yes, so a low-ranked responder is rarely asked. Once a score is low, is there any way back in practice? I saw the 2019 TODO about easing toward neutral.
6. Handlers and responders describe offers vanishing within seconds, but the timeout is 60s. What's the push-to-phone latency? Could the timer start before the offer is visible?
7. Bulk callout (4.1) isn't in this service. Where does it live, and does it offer in parallel?

**For the write-up**
8. Could we book 45 minutes so you can walk me through how a responder gets ranked? I'll write it up and send it back for you to correct.

Whatever's quickest to answer in writing is fine. Thanks.

---

## 3. Nadia Hoffmann

**Subject: Ticket data for the 4.2 regroup**

Hi Nadia, thanks for offering the ticket breakdown. Before the regroup, could you help me with a few things:

1. **Baseline:** what did callout-related ticket volume look like per week before 12 Aug, so I can size the "3x"?
2. **Full set:** I have 25 tickets (T-001 to T-025, 13 Aug to 5 Sep). Is that everything, or a sample? Anything since 5 Sep?
3. **Theme by responder:** do you track which responder each ticket is about, and the quiet / lost-offer split you mentioned? I've been mapping tickets to weekly offer data, and some handlers describe "nothing for ten days" for responders who are still getting offers. That may be perception, or the data may be off, and I want your read on it.
4. **Who isn't filing:** two responders whose handlers came up in interviews (offers dropped sharply) have no tickets. Would support have any way to spot that?
5. **What handlers see:** can a handler see a responder's offer history in the console? One ticket says responders can't see their own.
6. **The direct email** from a handler on 26 Aug: any chance you could share the gist, without names if that's better?

Could we also set up the standing fifteen minutes? Thanks.

---

## 4. Helen Achebe

**Subject: Dispatch: two things I need from you, and an early signal on 4.2**

Hi Helen, I've been through the handover and the 4.2 material. Two things I need your help with, plus a heads-up.

**Asks**
1. **Q3 commitments.** The roadmap (rev. 30 Jun) shows Availability Confidence as committed for 4.2, but it isn't in the release notes or code. Priya said items got squeezed out and that you two hadn't yet gone through which are still Q3 commitments. Could we do that in the next week or two?
2. **Rationale for 4.2.** The roadmap lists the weighting change and the timeout cut as "Internal", but the release notes call the weighting change "long-requested by responders". I can't find anything in the feedback that shows who asked for either. Do you know, or who would?
3. **Decision rights.** If I find something in routing config that needs changing before the next release, what's the process, given committed items are locked and changes go through you?

**Early signal (not a conclusion)**
The aggregate acceptance rate dipped to 54% in the week of 12 Aug and has recovered to about 73%, but a few responders appear to have almost stopped receiving offers, and the aggregate hides them. I'm confirming with Ravi and Wen and will bring you a fuller picture after the regroup with Marcus and Nadia. Flagging it now so it doesn't surprise you.

[Optional: cut the "Early signal" block if you'd rather hold it until the data is confirmed.]

Could we find 30 minutes this week or next? Thanks.

# 04 · X-Ray Vision — prompts

**Context:** You joined Rook two weeks ago as PM on Dispatch.
Release 4.2 shipped on 12 August, just before you arrived, and
landed badly. Last session the numbers showed you what happened: a
ping used to wait ninety seconds and now it waits sixty, people
missed pings they used to catch, and missing one counts the same as
turning one down — so four responders stopped hearing from us
altogether.

At the end of the session, ask Claude Code to save the prompts you
wrote yourself below — not the starter prompt. The closing slide has
the exact prompt to paste. By Module 6 this file is a prompt library
built from your own questions.

---

### 1.

Open the folder 00-rook/code/dispatch-routing/. This is the part of our software that decides who gets asked to take a job. I have never read code before and I am not going to start now. Walk me through what happens from the moment something goes wrong somewhere to the moment a responder's phone buzzes, in plain English, no jargon. Then tell me which file each step lives in.

### 2.

interesting, how do you think this could infer what we saw from some of the data analysis

### 3.

Has anything in this code changed recently? Walk me through what's different, and why it would matter to a responder.

### 4.

save this to file, but before give me a quck tl;dr on what we need to do next?

### 5.

Based on what we found after looking at the code, help me create hypothesis statements that we should go test. Rank the hypotheses based on how likely we're able to identify the root cause. Put this into a table and add another column that will give me a brief 1 sentence explanation on why we recommend #1 and #2 over the others, and give me some data that will support the recommendation

### 6.

Rewrite the hypotheses statements using scientific method framing and put it in a table format

### 7.

save as a new one

### 8.

commit this and push it

### 9.

Marcus
Aug 14, 2:47 PM
Quick one, did the change to who gets asked first apply to responders who'd already been turning jobs down, or just new ones? Can't tell from the code and don't want to guess on this. Anyone know?

### 10.

add to the synthesis file

### 11.

what hypothesis would otherwise confirm this?

### 12.

add to file and re-draft the slack message to marcus with this info

### 13.

Which file has last session's numbers in it? Read that alongside this code. Does it back up what I found in Lab A? And does that answer Marcus's question above?

### 14.

lab A us the 00-rook?

### 15.

can we confirm nothing changed in the code pre 4.2? it is really just configs?

### 16.

for your point of view, what should we do next?

### 17.

lets send the message to marcus on this slack channel https://product-school.slack.com/archives/C0B8LTV13EJ

### 18.

try it again now

### 19.

Find me the part of this code that takes points off somebody when they miss a ping or turn one down. Show it to me and explain it in plain English. Then find me every single thing in this code that puts points back on.

### 20.

add to hyphosis file

### 21.

commit and push

### 22.

Somebody has been quiet for a month. Walk me through, step by step, exactly what would have to happen for them to start getting work again.

### 23.

add to hyphosis file

### 24.

commit and push

### 25.

According to my findings in the code, for someone who's gone quiet, they would need to ___.

### 26.

According to my findings in the code, for someone who's gone quiet, they would need to ___. fill in the blank

### 27.

put the message into the slack channel

### 28.

i want you to be creative and rethink this UI. Use bold ideas and rich super hero like colors to design this experience.

### 29.

we started off with an onboarding exercise to learn about rook industries, then looked at customer interview data, tickets and ping data to identify patterns and root cause of what happened in 4.2. Then we identified a hypothesis and built a prototype. if we want to follow that same framework in the future, for this rook dispatch product or something else, what could a suitable skill look like?

### 30.

start with the full investigation skill and make sure we have a confidence gate (e.g. you are 95% confident in my ask, who I am, what I'm trying to achieve, and your role in helping me achieve it)

### 31.

When does the prototype get built? the eval-loop? fix the trigger condition, then use the second version. I addition to the prototype, also ask if i want to create a one-pager, prd, slide deck with speaker notes as well.

### 32.

why are you asking me to write the evals?

### 33.

done reveiwing

### 34.

its fine to read my downloads folder

### 35.

where is the skill at right now and can we actually run it?

### 36.

Make a skill called review-checklist. When I point it at a brief, it checks that the brief: names who owns it, says how we'll know it worked, keeps the same scope start to finish, and explains the problem before the fix.

### 37.

commit and push

### 38.

explain to me how the review checklist works?

### 39.

what words or statement trigger the review checklist skill?

### 40.

Schedule review-checklist to run every Monday morning, and let me know what it finds. Nothing needs to be ready for it to fire today. I'm setting the habit, not waiting on the result.

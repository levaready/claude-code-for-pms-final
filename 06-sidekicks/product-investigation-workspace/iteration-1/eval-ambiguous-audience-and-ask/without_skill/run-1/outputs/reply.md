I read both files in the folder before starting. I haven't built anything yet, because the one decision that shapes the prototype is still open.

**What I found**
- `churn-analysis.md` (draft, 2 Oct): churn rose from 3.1% to 4.4% over 8 weeks. The biggest rise is in accounts under 90 days old, at 5.9%. The causes are open: onboarding drop-off, a pricing change, or support wait times.
- `dashboard-notes.txt`: the idea is "something that shows early-warning accounts." The audience isn't settled. The note says "maybe for CS? maybe for the exec review? ask Priya." It also says to check whether finance wants the same view.

**Why I'm stopping**
The note says to ask Priya and I don't see her answer anywhere. A CS dashboard and an exec-review dashboard are different things:
- **CS:** a worklist of individual accounts to call this week. It has account names, risk signals, owners, and filters.
- **Exec review:** a few headline numbers and trends. It shows the 3.1% to 4.4% move and the under-90-day cohort, with little per-account detail.
- **Finance:** probably framed around revenue at risk.

If I guess, there's a good chance I build the wrong one.

**Questions**
1. Who is this for first: CS, the exec review, or finance? Has Priya answered yet? If you can ask her, that settles it.
2. What does "early-warning" mean here? The analysis doesn't name any account-level signals. It only says accounts under 90 days old churn more, and the causes (onboarding, pricing, support waits) are unconfirmed. Do you have specific signals in mind, such as low usage, a long support wait, or a missed onboarding step? Or should the prototype use the under-90-day cohort as a placeholder?
3. Is there any account-level data I can use? I only have the summary numbers. If there's none, I'll build it with clearly fake sample data and label it as such.
4. Format: should I make a clickable HTML mock you can open in a browser, or do you want a sketch or wireframe?

**If you want me to start now**
Tell me "just pick" and I'll build the CS version as an HTML mock. It would have the 3.1% to 4.4% trend at the top, an "accounts under 90 days" at-risk list with sample data, and the three open questions as placeholder filter chips. It would be easy to restyle into an exec view later. I'd label it as a draft built on an assumed audience.

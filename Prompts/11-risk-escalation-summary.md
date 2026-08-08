> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 11: Risk & Escalation Summary

**Stage in JOR AI Product Delivery Framework:** Deliver

**Job to be done:** Assess whether a blocker or risk warrants escalation, produce a concise, factual escalation summary if warranted, and formalize the issue into a structured risk log entry using proper risk management discipline (likelihood, severity, response, ownership), a discipline learned independently, after leaving the role, through PMP study.

**Organizational context this prompt assumes (fictional, illustrative):** Compliance and Legal are separate advisory functions with different typical response times. In this example, Compliance is reachable within a few days by email, while Legal requires a scheduled discussion booked a week or two out. Because that scheduling lead time is long, consolidating all open questions into a single session matters more than the wait itself: each additional round of "we have a new question" triggers another full scheduling cycle, so incomplete question-batching becomes a bigger practical risk than the underlying wait time. Escalation is expected to be rare, and a Product Owner is generally expected to resolve blockers independently. The scope here is internal delivery blockers, not customer or channel escalations, which would follow a different process entirely.

---

## Prompt (v1.1)

```
You are acting as an experienced Product Owner in a regulated financial
services environment (banking/fintech). I will give you a situation
involving a delay, blocker, or risk. Your job is to help assess whether
it warrants escalation, and if so, produce escalation materials — while
also formalizing it into a structured risk log entry using proper risk
management discipline (likelihood, severity, response/mitigation,
ownership, status).

ESCALATION THRESHOLD: Normal turnaround varies by advisory function and
should not be treated as a single fixed number — one group may answer by
email in days, while another may need a scheduled session booked a week
or two out. Ask me what the norms are rather than assuming. Because
scheduling lead time can be long, the bigger practical risk is often NOT
the initial wait itself, but having to go back to the same group multiple
times because a new question surfaced after the first round — each
additional round can trigger another full scheduling cycle. When
assessing escalation-worthiness, consider both (a) whether the current
wait exceeds that department's typical turnaround, and (b) whether poor
upfront question-batching is creating avoidable repeat cycles — the
second is often the more fixable and more consequential problem. The
Product Owner is generally expected to resolve blockers independently;
escalation is reserved for delays meaningfully beyond typical turnaround,
or for situations requiring authority/influence beyond the Product
Owner's own.

For the situation provided, produce:

1. ESCALATION ASSESSMENT
   State plainly whether this appears escalation-worthy yet, and why.
   If relevant, distinguish between "this wait is abnormal" and "this
   wait is normal, but repeat cycles from incomplete question-batching
   are the real problem" — these call for different responses (escalating
   a delay vs. tightening internal preparation before the next session).

2. RISK LOG ENTRY (structured, per standard risk management practice)
   - Risk description
   - Likelihood of occurrence (Low/Medium/High, with brief rationale)
   - Severity/impact if unresolved (schedule, scope, compliance, other)
   - Risk response/mitigation (e.g., accept, mitigate, escalate, avoid —
     state which and how)
   - Owner
   - Status (Active / Monitoring / Escalated / Resolved)
   - Date identified
   Note: this should be maintained as a living, centrally-stored project
   artifact (e.g., alongside other project documentation), not a one-time
   capture that goes stale.

3. ESCALATION SUMMARY (if warranted)
   A concise, factual written summary suitable for a direct manager:
   state the blocker plainly, what's been tried already, how long it's
   been outstanding relative to that department's typical turnaround, and
   what's being asked for. Note that supporting correspondence/
   attachments would typically accompany this in practice.

4. IF NOT YET ESCALATION-WORTHY
   Suggest what continuing to monitor looks like, and at what point (time
   or condition) this should be revisited. If the real issue is
   incomplete question-batching rather than an abnormal wait, recommend
   consolidating all outstanding questions before the next scheduled
   session, rather than escalating the wait itself.

Here is the situation:
"{{SITUATION}}"
```

---

## Sample Input

> Situation: A follow-up question about audit trail requirements emerged after our last session with Legal. Getting time with Legal typically requires booking a session 1-2 weeks out. This is the second time we've had to go back to them with a new question since the initial session. The first round took 2 weeks to schedule and resolve, and this second round is already on a similar timeline. This is blocking Epic 4 (Technical Feasibility) from finalizing its design.

---

## Claude Output (v1.1)

**1. Escalation Assessment**
This isn't primarily a case of an abnormal wait. A 1-2 week scheduling cycle with Legal is typical. The real issue is that this is the second round triggered by a new question surfacing after the first session, effectively doubling the total elapsed time (potentially 4 weeks total across two cycles) through avoidable repeat cycles rather than one abnormally long wait. This is escalation-adjacent, but the more useful intervention right now is tightening preparation: consolidating any remaining open questions before this second session, so a third round doesn't become necessary. If a third round were required after this, that would cross into genuinely escalation-worthy territory.

**2. Risk Log Entry**

- **Risk description:** Repeat consultation cycles with Legal (multiple rounds of new questions after initial session) are extending audit trail requirement clarification beyond a single normal turnaround cycle, delaying Epic 4 finalization.
- **Likelihood of occurrence:** Medium — a third round is plausible if all outstanding questions aren't fully consolidated before this session.
- **Severity/impact if unresolved:** Medium-High — each additional round adds 1-2 weeks; two rounds already consumed roughly a month, putting downstream design finalization and the MVP1 timeline at risk if a third round occurs.
- **Risk response/mitigation:** Mitigate — before this second session, consolidate all currently known open questions (not just the one that triggered this round) to minimize the chance of a third cycle being needed.
- **Owner:** Product Owner (Business Cards Delivery POD)
- **Status:** Active — monitoring, with mitigation in progress
- **Date identified:** [insert actual date]

*This entry should be maintained as a living artifact alongside other project documentation, updated as the situation evolves, rather than captured once and left stale.*

**3. Escalation Summary**
*(Not yet warranted as a formal escalation. See recommendation below instead.)*

**4. If Not Yet Escalation-Worthy**
Before the next scheduled session with Legal, consolidate every currently open or anticipated question related to this initiative, not just the one that triggered this second round, to minimize the risk of needing a third cycle. Revisit escalation-worthiness if a third round becomes necessary, since that would indicate either an unusually complex issue or an internal preparation gap worth raising with a manager.

---

## Jason's Edited Version

**On the escalation threshold:** This matches the assumption the scenario sets up. Where advisory functions have long scheduling lead times, the discipline that matters is getting every open question answered in one session. Going back to those groups after uncovering new information becomes the real source of delay, more so than any single wait. The prompt is built around that distinction rather than around raw wait time.

**On the risk log format:** Knowing what I know now, I'd follow proper PMP-style risk management practice: a real risk register with likelihood of occurrence, severity, risk response, and ownership, kept as a living, centrally-stored project artifact alongside other project documentation. The format in this file reflects that discipline accurately.

**On escalation scope:** No changes needed. This project existed specifically because of known channel escalations that had already surfaced. There weren't new customer/channel escalation types that would emerge mid-project that we didn't already know about going in.

---

## Lessons Learned

- "Normal turnaround" isn't a single number. Different advisory departments (Compliance vs. Legal) have genuinely different response patterns, and treating them identically would misjudge escalation-worthiness in either direction.
- The bigger practical risk in advisory-heavy initiatives is often not the initial wait, but repeat consultation cycles caused by incomplete question preparation. Each repeat cycle can cost as much time as the original wait, especially when scheduling lead times are long. Tightening internal preparation before each session is often a more valuable intervention than escalating a wait that is, on its own, still within normal range.
- Formal risk register discipline (likelihood, severity, response, ownership, centrally maintained) is something I learned after leaving this role, through independent PMP study. Recognizing that gap and closing it on my own is a relevant, honest data point about how I approach continuous improvement.
- Not every project generates novel escalation types. This initiative was born directly from known, already-surfaced channel escalations, so the risk/escalation focus here was about internal delivery blockers, not net-new customer-facing escalations.

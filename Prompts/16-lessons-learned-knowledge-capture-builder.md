> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 16: Lessons Learned / Knowledge Capture Builder

**Stage in JOR AI Product Delivery Framework:** Review

**Job to be done:** Capture recurring organizational knowledge, who to go to for what, what a team will or won't do, answers to questions that keep getting re-asked, in a form built for discoverability, not just storage. This is not a project-closure retrospective; it's a continuous practice for preventing knowledge from living only in people's heads and disappearing when they leave.

---

## Purpose

Solves a discoverability problem, not a documentation-effort problem. The real historical failure wasn't that knowledge went uncaptured; it was that when it was captured, it lived in a personal drive folder, a spreadsheet, or a single project-tracking artifact that nobody else knew existed or would think to search. This prompt builds every entry to be found by someone who doesn't already know it exists, distinguishes knowledge that decays (who to go to, what a team will or won't do) from knowledge that's relatively stable (how a process actually works), and treats knowledge capture as a running practice tied to recurring questions, not a one-time exercise performed at the end of a project.

## Prompt (v1.0)

```
You are helping capture recurring organizational knowledge, the kind of 
question that gets asked and answered repeatedly (who to go to for X, 
what a given team will or won't do, how a process actually works) in a 
way built for discoverability, not just storage. This is not a 
project-closure retrospective; it's an ongoing practice for capturing 
knowledge that would otherwise live only in people's heads and get lost 
when they change roles or leave.

INPUTS I WILL PROVIDE:
- A question that was asked and answered, or a piece of knowledge worth 
  capturing
- The answer, and how I know it (told directly, observed, documented 
  somewhere)
- Whether this is factual/process knowledge or routing/contact knowledge 
  (who to go to, what a team does or doesn't do)
- Where this would actually be stored, if I know

STEP 1 - CAPTURE IN REUSABLE FORM
Rephrase the question in general, reusable terms, not tied to the one 
specific instance that prompted it (e.g., "Who owns fraud threshold 
decisions for commercial card accounts" rather than "Who do I ask about 
this specific account"). Capture the answer, its source/basis, and 
today's date.

STEP 2 - CLASSIFY KNOWLEDGE TYPE
Distinguish two types explicitly, since they need different handling:
  a) FACTUAL/PROCESS knowledge — how something works, what a policy is. 
     Relatively stable over time.
  b) ROUTING/CONTACT knowledge — who to go to, what a team will or won't 
     do. This decays faster, since people change roles and leave. Flag 
     every routing/contact entry with a revalidation reminder rather 
     than treating it as a permanent fact.

STEP 3 - CHECK FOR DUPLICATES OR RELATED ENTRIES BEFORE ADDING
Ask whether a similar question has already been captured. If so, this is 
a candidate to consolidate or update the existing entry, not create a 
near-duplicate under different phrasing. Do not assume the answer; ask.

STEP 4 - BUILD FOR DISCOVERABILITY, NOT JUST STORAGE
Assign a category/subject and enough alternate keywords that someone 
searching in different words would still find this entry. Explicitly ask 
where this will actually live. If the intended location is something 
only one person would think to check (a personal drive folder, a single 
project-tracking ticket nobody else knows exists), flag this as a 
discoverability risk, not just a storage detail. The goal is a shared, 
searchable home, not an archive.

STEP 5 - PRODUCE THE ENTRY, RETRIEVAL-READY
Output: Category, Reusable Question, Answer, Source/Basis, Type 
(Factual/Process or Routing/Contact), Revalidation Flag (if 
routing/contact), Date Captured, Alternate Search Terms.

STEP 6 - DEMONSTRATE RETRIEVAL
Given a growing set of captured entries, show how a future question 
would actually be answered from this repository: search by category or 
keyword, surface the matching entry, and if a routing/contact entry is 
past a reasonable revalidation window, flag that it may be stale before 
presenting it as current fact.

STEP 7 - WORST-PRACTICE CHECK
Flag any of: capturing knowledge somewhere only one person would find, 
leaving duplicate or conflicting entries unresolved, treating 
routing/contact knowledge as permanently valid with no revalidation 
flag, capturing an answer without its source, and treating this as a 
one-time exercise rather than an ongoing practice that runs continuously 
across every initiative, not just at project close.
```

## Sample Input

**Recurring questions from Business Cards team knowledge, previously kept informally or in a .doc/.xlsx nobody consistently referenced:**

1. "Who do I contact for a fraud escalation on a commercial card account?"
2. "Does Legal need to be looped in for a straightforward policy clarification, or is Compliance enough?"
3. "What's the typical turnaround time to get time with Legal?"

**Source:** direct experience and prior consultation history (consistent with what's already documented in prompt 11, Risk & Escalation Summary).

**Intended storage, previously:** a .doc or spreadsheet, format not yet worked out for actual searchability.

## Claude Output

**Step 1-2, Captured Entries.**

*Entry 1*
- Category: Escalation / Fraud
- Reusable Question: Who owns fraud escalation for a commercial card account?
- Answer: [routing detail specific to org structure]
- Source/Basis: Direct experience
- Type: Routing/Contact — flagged for revalidation
- Date Captured: [today's date]
- Alternate Search Terms: fraud contact, who handles fraud, card fraud escalation path

*Entry 2*
- Category: Advisory Consultation / Legal & Compliance
- Reusable Question: For a policy clarification, is Compliance sufficient or does Legal need to be involved?
- Answer: Depends on whether the clarification touches contractual or liability exposure (Legal) versus audit/control requirements (Compliance); straightforward policy language questions are typically Compliance-only, escalate to Legal if liability or consent language is affected.
- Source/Basis: Direct experience
- Type: Factual/Process — relatively stable, not flagged for revalidation
- Date Captured: [today's date]
- Alternate Search Terms: when to involve legal, compliance vs legal, policy clarification routing

*Entry 3*
- Category: Advisory Consultation / Legal & Compliance
- Reusable Question: What's the typical turnaround time to get time with Legal?
- Answer: in this scenario, Legal requires a scheduled discussion booked a week or two out, while Compliance is reachable by email in a few days. (Consistent with prompt 11.)
- Source/Basis: Direct experience, cross-referenced with prompt 11's Risk & Escalation Summary
- Type: Routing/Contact — flagged for revalidation, since turnaround norms can shift with staffing changes
- Date Captured: [today's date]
- Alternate Search Terms: legal response time, how long does legal take, scheduling legal

**Step 3, Duplicate Check.** Entries 2 and 3 are related (both concern Legal/Compliance engagement) but answer genuinely different questions (which group to involve, versus how long it takes once involved). Kept as separate entries under a shared category rather than merged, since merging would force two distinct answers into one entry a searcher might not fully read.

**Step 4, Discoverability.** Storage location not yet specified in the input. Flagged directly: a .doc or spreadsheet is a real discoverability risk unless it's centrally located, indexed, and actively pointed to from somewhere people would already be looking (a team wiki, a pinned resource, a searchable internal tool). Without that, this becomes exactly the failure mode described: knowledge that exists somewhere but that nobody else knows to look for.

**Step 5, Retrieval-Ready Format.** See entries above; each is structured for scanning and search, not narrative prose.

**Step 6, Retrieval Demonstration.** A future team member asking "how long until I can talk to Legal" would search "legal," "turnaround," or "scheduling," any of which surfaces Entry 3 via its alternate search terms. Since Entry 3 is flagged Routing/Contact, its answer should be checked against how long ago it was captured before being treated as current; if significantly stale, note it explicitly ("this was accurate as of [date]; confirm it's still current") rather than presenting a possibly outdated norm as settled fact.

**Step 7, Worst-Practice Check.** No entry was captured without its basis. Routing/contact entries are flagged for revalidation, factual/process entries are not. The discoverability question was asked directly rather than assumed solved by writing the entry down. This is framed throughout as a continuous, running practice, not a one-time cleanup exercise.

## Jason's Edited Version

No material corrections needed to the output structure. Confirms this addresses the real gap directly: the earlier attempt to build this kind of FAQ was correct in spirit but never got past "where does this actually live and how would someone find it," and that question is now built into the prompt itself rather than left as an afterthought.

## Lessons Learned

- The real failure wasn't that knowledge went uncaptured. It was that when it was captured, it lived somewhere (a personal drive folder, a spreadsheet, a single JIRA ticket) that nobody else knew existed or would think to search. Discoverability is the actual problem, not documentation effort.
- Routing/contact knowledge (who to go to, what a team will or won't do) and factual/process knowledge (how something works) decay at different rates and need different handling. Treating "who owns fraud escalation" with the same permanence as "how the fraud threshold policy works" produces stale answers presented with false confidence.
- This is fundamentally different from a project-closure retrospective. The knowledge that actually needed capturing wasn't tied to any single project's timeline; it was organizational knowledge that outlived every individual initiative and got lost specifically when the people holding it moved on.
- The same questions getting asked and answered repeatedly is itself a signal worth acting on. If a question recurs, that's evidence it should exist somewhere searchable, not evidence that everyone should keep re-deriving the answer from scratch or re-asking whoever happens to remember.

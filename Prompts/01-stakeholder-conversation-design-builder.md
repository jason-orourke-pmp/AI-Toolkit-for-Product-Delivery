> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 01: Stakeholder Conversation Design Builder

**Stage in JOR AI Product Delivery Framework:** Discover

**Job to be done:** Decide who belongs in a stakeholder conversation, and who should be approached separately, when no formal project team or mandate exists and people's time is borrowed rather than assigned. Apply a give-or-receive value test per stakeholder, and add the missing layer of going to a business leader before approaching individual contributors directly.

---

## Purpose

Decides how to structure stakeholder conversations for an initiative that has no formal project team or mandate, where people's time is being borrowed from their actual roles rather than formally assigned. Preserves the individual-level judgment call that already worked in practice (would this person actually give or receive something in this room) and adds the layer that was missing: going to a business leader before approaching their people directly, so the time ask carries legitimacy a persistence-based approach can't provide, and so those same leaders become the natural pool for a working group and an eventual decision-point meeting.

## Prompt (v1.0)

```
You are helping decide how to structure stakeholder conversations for an 
initiative that has no formal project team or mandate, where people's 
time is being borrowed from their actual roles rather than formally 
assigned.

INPUTS I WILL PROVIDE:
- The initiative and its current phase (early exploration, drafting, 
  nearing a decision point)
- Stakeholders under consideration, and what each might give (expertise, 
  approval, input) or receive (impact on their operations, a decision 
  that affects them) from being involved
- Whether a formal project team or mandate exists for this initiative
- Whether any conversations need to happen repeatedly over time (e.g., 
  iterative drafting) versus a single input session

STEP 1 - APPLY THE VALUE TEST PER STAKEHOLDER
For each stakeholder under consideration, ask what they would give or 
receive from being in a given conversation. If the honest answer is 
neither, they don't belong in that conversation, regardless of whether 
their group is nominally connected to the initiative. Do not default to 
including someone for completeness or because excluding them feels 
awkward. Protecting people's time is the default, not an exception.

STEP 2 - GROUP BY SHARED VALUE, NOT BY CONVENIENCE
Where two or more stakeholders each pass the value test for the same 
conversation, because they'd genuinely give or receive something from 
hearing the same discussion, group them together. Where stakeholders 
pass the test individually but for unrelated reasons (different 
questions, no overlap in what they need from each other), keep them in 
separate conversations even if combining them would be logistically 
easier. A larger group is only justified by genuine shared value, not 
by scheduling convenience.

STEP 3 - IDENTIFY AND APPROACH THE BUSINESS LEADER BEFORE INDIVIDUALS
Ask whether a formal project team or mandate exists. If not, before 
approaching individual contributors, identify the business leader for 
each stakeholder group. Ask me whether this leader is already known 
from my own org knowledge (the way some stakeholder contacts are known 
outright from past initiatives) or needs its own discovery step (asking 
a manager or colleague who the right leader is). Do not assume a leader 
is known by default; ask which case applies for each group. Once 
identified, the ask to that leader should state the initiative plainly, 
specify who is needed and roughly how much time, and get buy-in before 
approaching their people directly. Note: this prompt stays focused on 
deciding who to approach and in what order. Drafting the actual message 
to the leader is a separate task.

STEP 4 - DECIDE IF A STANDING WORKING GROUP IS WARRANTED
A one-off conversation is enough when the goal is a single round of 
input or clarification. A standing working group is warranted when the 
task requires iterative refinement across multiple sessions (e.g., 
drafting policy or procedure language together). Ask which applies 
before defaulting to either recurring meetings or one-off conversations.

STEP 5 - TRACK ENGAGED LEADERS AS THE FUTURE DECISION-POINT POOL
Maintain a running list of the business leaders engaged through Step 3, 
across the initiative's life. These are the natural candidates for any 
eventual decision-point or launch conversation, since they already have 
context and have already given buy-in on their team's involvement. This 
list is a byproduct of doing Step 3 correctly, not a separate exercise.

STEP 6 - WORST-PRACTICE CHECK
Flag any of: including a stakeholder in a group conversation where they 
have no give-or-receive value, combining stakeholders into one 
conversation for scheduling convenience rather than genuine shared 
value, approaching an individual contributor directly for sustained time 
when no formal mandate exists and their leader hasn't been looped in, 
defaulting to a standing working group when a single conversation would 
do (or the reverse), and losing track of which leaders were engaged 
early, leaving no natural pool to draw on when a decision-point meeting 
is eventually needed.
```

## Sample Input

**Initiative:** early exploration phase of the commercial card automation work, before any formal decision to draft policy changes, the "snowball" period of individual conversations with different stakeholder groups.

**Phase:** early exploration, no formal project team or mandate exists yet.

**Stakeholders under consideration:** Legal, Compliance, Risk, the Commercial Banking channel, the branch channel, the contact centre channel, Development/Platform team.

**Known leader relationships:** Risk, Compliance, and Legal contacts and their leads are already known from prior work and existing domain knowledge. The right business leader within the Commercial Banking channel for this specific initiative is not yet known; would require asking a manager or colleague who the right person is.

**Repeat conversations needed:** yes, once the initiative reaches the point of drafting actual policy changes, but not yet during early exploration.

## Claude Output

**Step 1, Value Test.**
- Legal: gives input on legal exposure of any policy change; would receive nothing from most of the exploratory conversations except where a specific legal question arises. Include only when a legal question is live.
- Compliance: same pattern as Legal, advisory and narrowly scoped to specific questions.
- Risk: gives input on fraud/risk exposure; similarly narrow, relevant when a specific risk question is live.
- The Commercial Banking channel: gives input on how the change affects their customer segment and distribution; receives real value, since any policy change affects how they sell and service the product. Genuine two-way value.
- The branch channel and the contact centre channel: at this early exploratory stage, unclear whether they'd give or receive anything yet, since no concrete process change has been proposed. Flagged as premature to include; revisit once exploration produces something concrete enough to affect their operations.
- Development/Platform team: gives technical feasibility input; receives direction on what's being considered. Relevant once exploration reaches the point of asking "could this be built."

**Step 2, Grouping.** Legal, Compliance, and Risk each pass the value test individually but for different, non-overlapping questions at this stage; keep separate rather than combining into one call for convenience. The Commercial Banking channel's involvement is substantive enough to warrant its own dedicated conversation rather than folding into a broader group. Development/Platform team conversations are naturally separate, since the questions (technical feasibility) don't overlap with the policy/risk questions the other groups are addressing.

**Step 3, Leader Identification.** Risk, Compliance, and Legal: leaders already known from domain knowledge; approach directly is appropriate, consistent with how these relationships already work. The Commercial Banking channel: leader not yet known for this specific initiative; requires a discovery step, asking a manager or colleague who the right business leader is before approaching anyone on their team directly, since no formal mandate exists to justify bypassing that step.

**Step 4, Standing Working Group.** Not warranted yet. Early exploration calls for one-off conversations to test whether an idea is viable, not a recurring structure. Per the initiative's real history, a standing working group becomes warranted once the group moves into iterative drafting of policy language, which comes later.

**Step 5, Engaged Leaders Pool.** Running list starts with the known Risk, Compliance, and Legal leads engaged during exploration, plus the Commercial Banking channel leader once identified. This list becomes the natural pool to draw on for a working group during drafting, and eventually for a decision-point or launch conversation.

**Step 6, Worst-Practice Check.** The branch channel and the contact centre channel correctly excluded at this stage rather than included for completeness. No convenience-based grouping recommended (Legal, Compliance, Risk kept separate despite the ease of combining them). The Commercial Banking channel correctly routed through a leader-discovery step rather than assuming a contact could be approached directly. No standing working group recommended prematurely.

## Jason's Edited Version

No material corrections to the Claude output on this one. The value-test logic held up against the real case without needing to be overridden. The key finding in developing this prompt was not in the output itself but in naming the missing layer: the habit of going to a business leader first was not a formalized step in practice, it was something done inconsistently depending on existing relationships. The prompt makes it explicit and required.

## Lessons Learned

- The individual-level judgment call, would this person actually give or receive something in this room, was already the right instinct and didn't need fixing. What was missing was the layer above it: going to a business leader first when no formal mandate exists, which legitimizes the time ask in a way persistence alone cannot.
- Approaching a business leader first accomplishes two things at once. It gets a real answer on whether and how much time can be borrowed, and it builds a running list of engaged leaders who are the natural people to include when a decision-point or launch conversation eventually happens.
- A stakeholder passing the value test for their own concerns doesn't mean they belong in the same room as another stakeholder who also passes it for unrelated concerns. Grouping should be driven by genuine shared value in the same conversation, not by how convenient it would be to combine two calls.
- A standing working group is warranted by the nature of the task (iterative drafting) rather than by default. Most stakeholder engagement in an exploratory phase is better served by one-off conversations until the work actually requires repeated collaborative sessions.

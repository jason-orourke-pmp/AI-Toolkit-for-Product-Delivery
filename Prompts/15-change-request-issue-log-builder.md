> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 15: Change Request / Issue Log Builder

**Stage in JOR AI Product Delivery Framework:** Deliver

**Job to be done:** Build a lightweight change and scope-decision log for an initiative with no formal change-control process, capturing scope history rather than only current state, distinguishing a full future vision from what's actually committed, and recording who decided a scope question and why, even when that authority was informal.

---

## Purpose

Builds a change and scope-decision log for initiatives where scope changes happen entirely through conversation and memory, with no written record beyond whatever the current scope happens to be. Preserves version history instead of silently overwriting prior scope. Separates a broader future vision from the committed increment, so "eventually we'd want this too" doesn't get confused with what's actually being built. Identifies the real constraint being negotiated, since not every initiative is limited by budget and deadline; some are limited purely by shared team capacity, which calls for different evaluation language. Captures informal decision authority and its reasoning explicitly, since real delivery expertise substituting for a formal process isn't the problem, losing the reasoning behind that judgment is.

## Prompt (v1.0)

```
You are helping build a lightweight change and scope-decision log for an 
initiative that has no formal change-control process, no fixed budget, 
and no external deadline, where the real constraint being negotiated is 
calendar time from a shared developer team against competing priorities, 
not dollars or a hard launch date.

INPUTS I WILL PROVIDE:
- The current committed scope
- A proposed change or expansion, and who raised it
- Any broader "eventually we'd want this too" vision that's wider than 
  what's currently committed
- Who actually decided on the change, even if their authority was 
  informal rather than a named role
- Whether this decision was ever written down anywhere, or only existed 
  in conversation

STEP 1 - CAPTURE THE CHANGE WITH VERSION HISTORY, NOT JUST CURRENT STATE
For every scope change, record what the scope was before, what it 
changed to, and what triggered the change. Do not silently overwrite 
prior scope with the new version. Ask whether a record of past scope 
already exists; if only the current scope is known, say so explicitly 
rather than backfilling a history that was never captured.

STEP 2 - DISTINGUISH THE FULL VISION FROM THE COMMITTED INCREMENT
When a scope idea is broader than what's being committed to now (e.g., 
"eventually for every ownership type and every reason someone would 
currently fax something in" vs. "this phase, single-owner card creation 
only"), do not treat the full vision as current scope. Log it as a 
separate, deferred future-scope item with its own one-line rationale for 
why it's deferred, not folded into or confused with what's actually 
committed.

STEP 3 - IDENTIFY THE ACTUAL CONSTRAINT BEING WEIGHED
Before evaluating whether a change should be accepted, ask what's 
actually being negotiated: a formal budget/deadline constraint, or a 
capacity constraint (competing priorities for a shared team's time, no 
incremental dollar cost, no hard external deadline). Do not default to 
cost/schedule framing if the real constraint is capacity negotiation; 
the evaluation question in that case is closer to "is this realistic 
within the time we can actually get," not "can we afford it."

STEP 4 - RECORD WHO DECIDED AND ON WHAT BASIS
Capture the actual decision-maker, even when their authority is informal 
(a peer whose judgment is deferred to because of real delivery 
experience, not a formally assigned approval role). State the basis for 
the decision explicitly, e.g. "assessed as unrealistic within the team's 
available capacity," not just "declined." Ask for the reasoning if it 
isn't provided rather than leaving it blank; a decision that becomes 
"the new understanding" with no recorded reason is exactly the gap this 
log exists to close.

STEP 5 - FLAG CONCENTRATED INFORMAL DECISION AUTHORITY AS A PATTERN
If the same person's informal judgment is consistently the deciding 
factor across multiple logged changes, note this as a pattern across 
entries, not just repeat it silently in each one. This isn't inherently 
a problem, real delivery experience is valuable input, but it's worth 
being visible in the log rather than invisible, since it means the 
record of "why scope is what it is" is substantially shaped by one 
person's risk tolerance and estimation.

STEP 6 - PRODUCE THE LOG
Output a running table: date, proposed change, requested by, 
classification (committed scope change vs. deferred future-vision item, 
per Step 2), constraint type invoked (per Step 3), decision, 
decision-maker, basis for the decision, and status. Keep this 
deliberately lightweight. It exists to prevent the specific failure mode 
of scope becoming "the new understanding" with no recoverable reasoning, 
not to impose a heavy formal change-control process onto a team that 
doesn't have one.

STEP 7 - WORST-PRACTICE CHECK
Flag any of: overwriting scope history instead of preserving what came 
before, folding a future-vision item into current committed scope as if 
it were already decided, defaulting to cost/schedule evaluation language 
when the real constraint is negotiated capacity, letting a decision go 
unrecorded because it emerged through conversation rather than a formal 
request, and failing to surface a pattern of one person's informal 
judgment repeatedly deciding scope without that pattern being visible.
```

## Sample Input

**Current committed scope:** automated card creation workflow for single-owner ownership applications only, replacing the fax-triggered manual the card platform re-key for that segment.

**Proposed change, raised in conversation:** the Commercial Banking channel wanted the automation to eventually cover all ownership types (not just single-owner), and to replace the fax entirely as the mechanism for every reason it was currently used, not just new card creation, but ownership changes, adding authorized users, and removing users.

**Broader vision vs. committed scope:** the full ask (all ownership types, full fax replacement) was always wider than what was actually being built. It was never formally logged as deferred; it just existed as a known "eventually" without a documented decision to defer it.

**Constraint actually in play:** no fixed project budget and no external deadline. All contributors, including developers, were already salaried; the real cost was calendar time and getting developer capacity prioritized against everything else competing for it. Technically, any additional scope could have been included, since there was no hard financial or time ceiling forcing exclusion.

**Decision-maker:** a peer Product Owner with significantly more delivery experience held an informal veto, based on judgment about what could realistically get built in a reasonable timeframe. This wasn't a formally assigned approval role.

**Documentation:** none. The scope simply became "the new understanding" after the conversation, with no record of what was proposed, who decided, or why.

## Claude Output

**Step 1, Version History.** No prior record exists; only the current committed scope (single-owner card creation) is known. Per this step's rule, that gap is stated explicitly rather than backfilled: prior conversations about broader scope happened, but no version history of what the scope looked like at each point was ever captured.

**Step 2, Full Vision vs. Committed Increment.** Two items logged separately from current committed scope, both as deferred future-vision items, not as part of what's built now:
- All ownership types (not just single-owner) for automated card creation.
- Full fax replacement for every current use case, not just new card creation: ownership changes, adding authorized users, removing users.
Neither is folded into current scope. Both are logged with the same one-line deferral rationale: assessed as broader than what could realistically be delivered in the available timeframe, per the informal decision described below.

**Step 3, Actual Constraint.** Capacity constraint, not budget/schedule. No fixed project budget, no external deadline, all contributors already salaried. The real limiting factor was calendar time and getting developer capacity prioritized against competing initiatives. Evaluation question used: "is this realistic within the time we can actually get," not "can we afford it."

**Step 4, Decision and Basis.** Decision-maker: a peer Product Owner with more delivery experience, holding an informal veto based on realistic-timeframe judgment rather than a formally assigned approval role. Basis for the decision, as best captured after the fact: the broader scope (all ownership types, full fax replacement) was assessed as unrealistic to deliver within a reasonable timeframe given available developer capacity, so the committed scope was narrowed to single-owner card creation as the achievable increment.

**Step 5, Concentrated Informal Authority.** Flagged as a pattern rather than a one-off: this same peer's informal judgment appears to have been the deciding factor here, and the input doesn't indicate a different decision-maker for other scope questions on this initiative. Worth noting explicitly in the log rather than treating each entry as independently decided, since it means the recorded rationale largely reflects one person's risk tolerance and estimation of what's achievable.

**Step 6, Log.**

| Date | Proposed Change | Requested By | Classification | Constraint Type | Decision | Decision-Maker | Basis | Status |
|---|---|---|---|---|---|---|---|---|
| [undated, reconstructed] | Expand to all ownership types | the Commercial Banking channel | Deferred future-vision | Capacity (developer time negotiation) | Deferred, not rejected outright | Senior peer PO (informal) | Assessed as unrealistic within available timeframe | Deferred, no target date |
| [undated, reconstructed] | Replace fax entirely (ownership changes, add/remove users) | the Commercial Banking channel | Deferred future-vision | Capacity (developer time negotiation) | Deferred, not rejected outright | Senior peer PO (informal) | Assessed as unrealistic within available timeframe | Deferred, no target date |

**Step 7, Worst-Practice Check.** No scope history was fabricated to fill the gap; the absence of prior records was stated directly. The two deferred items were kept explicitly separate from committed scope. Capacity framing was used instead of defaulting to cost/schedule language, consistent with the real constraint described. The informal decision-maker and their reasoning were captured rather than left as an unrecorded "understanding." The pattern of one person's judgment deciding both items was surfaced rather than logged twice without comment.

## Jason's Edited Version

No material corrections to the Claude output. The reconstruction accurately reflects how this actually worked: broader scope was raised, informally declined based on one experienced person's realistic-timeframe judgment, and never written down anywhere. Worth being clear that this prompt is deliberately not a reconstruction of good practice at the time. This is not how scope decisions were actually documented, since they weren't documented at all. It's a forward-looking tool for what should exist going forward.

## Lessons Learned

- A scope log that only holds current state, with no history of what changed and why, loses exactly the information a new team member or a future version of yourself would need most: not what the scope is, but why it isn't broader than it is.
- Not every initiative is constrained by budget and deadline. Where the real constraint is negotiated capacity (shared developer time against competing priorities, no incremental dollar cost, no hard external deadline), evaluating a scope change against cost/schedule framing asks the wrong question. The real question is closer to "is this realistic given what capacity we can actually get."
- Informal decision authority based on real delivery experience isn't inherently a governance failure. Deferring to someone who genuinely knows what's achievable in a given timeframe is often the right call. The failure is when that judgment and its reasoning are never captured, so the decision becomes "the new understanding" with no recoverable basis if anyone asks why later.
- When the same person's informal judgment repeatedly decides scope, that's worth surfacing as a visible pattern in the record, not treating each decision as independently arrived at. It doesn't need to be treated as wrong, but it should be visible.

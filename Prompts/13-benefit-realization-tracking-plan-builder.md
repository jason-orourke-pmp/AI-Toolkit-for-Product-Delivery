> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 13: Benefit Realization Tracking Plan Builder

**Stage in JOR AI Product Delivery Framework:** Review

**Job to be done:** Build a forward-looking plan for tracking whether a business case's promised benefit actually materialized. Distinguish benefits with a natural owner from those with none by default, and refuse to assign a tracking mechanism that isn't real.

---

## Purpose

Builds a benefit realization tracking plan to include in a business case, so that whether an initiative's promised benefit actually materialized has a real, owned mechanism to find out, rather than being left unmeasured or measured somewhere nobody sees. Distinguishes benefits that have a natural owner (risk-type benefits a function like Risk or Finance tracks as standard practice) from benefits that have no defined owner by default (sales lift, satisfaction, retention), and refuses to paper over the second category with an assumed tracking process that doesn't actually exist. This prompt is forward-looking: it is built to be included in future business cases, not to reconstruct a benefit-tracking history that, in practice, mostly didn't happen or was never visible.

## Prompt (v1.0)

```
You are helping build a benefit realization tracking plan to include in 
a business case, so that whether the initiative's promised benefit 
actually materialized has a real, owned mechanism to find out, rather 
than being left unmeasured or measured somewhere nobody sees.

INPUTS I WILL PROVIDE:
- The business case's stated benefits (Measurable / Economic / 
  Qualitative, per the Business Case Builder's own categories)
- Whether each benefit already has a natural owner (e.g., a risk-type 
  benefit that Risk or Finance would track as a matter of course)
- Whether a similar past initiative had any post-launch tracking, and 
  whether the outcome of that tracking was ever shared back

STEP 1 - SORT BENEFITS BY WHETHER THEY HAVE A NATURAL OWNER
Some benefits (fraud exposure, compliance breaches, cost overruns) 
naturally get tracked because a function like Risk or Finance owns that 
metric regardless of this specific initiative. Others (sales lift, 
customer satisfaction, adoption, retention) often have no natural owner; 
no function is automatically responsible for confirming whether they 
materialized. For each benefit, ask me which category it falls into. Do 
not assume a benefit will get tracked just because it's measurable in 
principle; ask specifically who would track it and whether that's 
already someone's defined job.

STEP 2 - FOR BENEFITS WITHOUT A NATURAL OWNER, DESIGN THE MECHANISM
For each benefit without a natural owner, build a tracking mechanism 
using the same structure that worked for the risk-owned benefit:
  - The specific metric, defined precisely enough to measure (not "sales 
    should improve," but a named number with a source system)
  - A defined tracking period with its own cadence
  - A named owner who agrees to actually pull and report the number, not 
    just "someone should check this"
  - A defined threshold or comparison point (e.g., against the 
    business case's projected target, or against a pre-launch baseline)
If I can't identify a plausible owner for a given benefit, say so 
plainly rather than assigning one by default. An unowned benefit is a 
real finding, not a gap to paper over. Before finalizing a mechanism for 
any benefit, confirm with me that the data source it depends on actually 
exists and is realistically accessible post-launch, rather than assuming 
a dashboard or data cube is available.

STEP 3 - DEFINE WHAT HAPPENS WITH THE RESULT
State explicitly what happens once the benefit is measured, whichever 
way it goes: who reviews the result, whether it's shared back to the 
people who built the business case, and what decision it feeds into 
(continue, adjust the initiative, feed the finding into the next 
business case as a data point). A tracking plan that measures something 
but never routes the result anywhere is functionally the same as not 
measuring it at all.

STEP 4 - NAME THE LIMITATION HONESTLY
This plan can specify who should track a benefit and how. It cannot 
guarantee that tracking actually happens once the initiative is out of 
active focus, since follow-through depends on organizational priorities 
that shift after launch. State this limitation directly rather than 
implying the plan itself solves the follow-through problem. Where 
relevant, note that "no one tracked this, or it was tracked somewhere 
I never saw" is a normal and common outcome, not a personal failure to 
account for.

STEP 5 - WORST-PRACTICE CHECK
Flag any of: assuming a benefit will get tracked because it's 
measurable in principle, assigning ownership for tracking a benefit 
without a real named person or function agreeing to it, designing a 
tracking mechanism against a data source that hasn't been confirmed to 
exist, a tracking mechanism with no defined end point or comparison 
threshold, and describing the plan as if it guarantees follow-through 
rather than naming that limitation directly.
```

## Sample Input

**Business case benefits (from the restricted-address policy change and the commercial card automation case, combined for illustration):**
- Fraud exposure from the loosened delivery-address rule (has a natural owner: Risk/Finance already track fraud as standard practice, per prompt 12)
- Applicant drop-off reduction from faster time-to-card (measurable in principle via existing application and card-creation dashboards, but with no confirmed owner assigned to check it post-launch)
- General sales or customer satisfaction impact from the policy change (no defined measurement mechanism exists in this scenario, and it is left unclear whether it would be measured at all)

## Claude Output

**Step 1, Sorting Benefits.**
- Fraud exposure: natural owner exists (Risk/Finance), consistent with the mechanism already built in prompt 12.
- Applicant drop-off reduction: no natural owner. Retention is directly relevant to Product, but nothing in the case as described assigned anyone to actually check this number post-launch.
- Sales/satisfaction impact: no natural owner, and no defined mechanism ever existed to my knowledge. This is flagged as a real finding, not filled in with an assumed tracking process that didn't actually exist.

**Step 2, Designing the Mechanism (for the two unowned benefits).**

*Applicant drop-off reduction:*
- Metric: applicant drop-off rate between approval and card delivery, sourced from existing application-volume and card-creation dashboards, confirmed to exist and be realistically accessible post-launch.
- Cadence: monthly for the first 6 months post-launch, then quarterly.
- Owner: to be named at business case approval, not left open. If no plausible owner can be identified at the time the case is approved, that should be raised as a condition of approval, not assumed to resolve itself later.
- Comparison point: measured against the business case's original projected drop-off reduction target.

*Sales/satisfaction impact:*
- No plausible owner or mechanism could be identified from the input provided. Per Step 2's rule, this is stated plainly as an unowned benefit rather than assigned a default tracker. If this benefit is included in a future business case, the case itself should either name a real owner at approval time or drop the benefit from the case rather than claim a benefit that has no way of being confirmed.

**Step 3, Result Routing.** For applicant drop-off, the named owner reports the result back to the original business case's approver and to Product leadership. The result feeds a specific decision: if the benefit materialized as projected, no action needed; if it fell short, the finding feeds into the next related business case rather than being discarded.

**Step 4, Limitation.** This plan defines who should track each benefit and how. It cannot guarantee anyone actually does it once other priorities take over post-launch. In this scenario that is exactly what happens to the sales and satisfaction benefit on the restricted-address change: no confirmed mechanism, and no reason to assume one exists elsewhere. That is treated here as a normal, common outcome rather than something to account for as a personal gap.

**Step 5, Worst-Practice Check.** No benefit assumed trackable just because it's measurable in principle. The sales/satisfaction benefit was not assigned a fabricated owner or mechanism to make the plan look complete. The applicant drop-off mechanism was only finalized after confirming its data source actually exists. The plan states its own limitation (design without guaranteed follow-through) directly rather than implying it solves the problem it's actually just naming.

## Jason's Edited Version

No material corrections to the Claude output. The key structural finding, that downside risk benefits track themselves through existing functions while upside benefits typically have no automatic owner, held up cleanly against both real cases used here. The cross-reference to prompt 12 (Change Management / Rollout Readiness Builder) is accurate: that file contains the monitoring plan for the fraud risk, while this file addresses what was missing alongside it.

## Lessons Learned

- Downside risk (fraud, compliance) tends to get tracked automatically because a function like Risk or Finance owns that metric regardless of any specific initiative. Upside benefit (sales lift, satisfaction, adoption) usually has no automatic owner, and assuming it will get measured just because it's measurable in principle is how it quietly goes untracked.
- Not knowing whether a benefit was ever tracked, or having it tracked somewhere never shared back, is a common and realistic outcome, not a personal oversight to account for or paper over in a case study.
- A tracking mechanism is only as real as its data source. Confirming a dashboard or data cube actually exists and is accessible post-launch, rather than assuming one does, is the difference between a credible plan and an aspirational one.
- A tracking plan that measures a result but never states who reviews it or what decision it feeds into is functionally equivalent to not tracking it at all. Routing the result somewhere is as important as capturing it.
- This prompt is deliberately forward-looking rather than a retrospective reconstruction, since the actual history of benefit tracking on past initiatives was mostly absent or unknown, and building a false record of past tracking would misrepresent what actually happened.

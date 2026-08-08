> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 03: Business Case / Executive Presentation Builder

**Stage in JOR AI Product Delivery Framework:** Discover

**Job to be done:** Build a business case and VP-ready executive deck from raw Finance and dashboard inputs. Separate verified data from inherited or new assumptions, classify the case's real justification pattern, and keep the sequence of when each pattern became known accurate rather than implied from the outset.

---

## Purpose

Turns raw inputs (Finance data, dashboard pulls, a prior business case if one exists, and my own working assumptions) into a complete business case and a VP-ready executive deck structure. Built for the situation where I am the sole builder: nobody else produces a presentable version for me. The prompt encodes PMI and SAFe business case conventions (problem statement, conceptual solution, justification, measurable/economic/qualitative benefit categories, worst-practice checks) so I do not need the certification to apply the discipline.

Reference sources: PMI, "Make Your Case" (PM Network, 2003), and a standard corporate business case template (Project Summary, Business Context, Business Benefits, Risks, Financial Appendix).

## Prompt (v1.0)

```
You are helping build a business case and its executive presentation from
raw inputs, not from an already-finished document. I am the sole builder.
Nobody else produces a presentable version for me.

INPUTS I WILL PROVIDE:
- Finance-sourced figures (cost data, current volumes, unit economics)
- Dashboard/data cube pulls (current-state acquisition or operational data)
- A prior business case on the same or a similar topic, if one exists
- My own assumptions where data does not exist yet

STEP 1 - DATA TRIAGE
Sort everything I give you into three buckets:
  a) Verified data (has a named source: Finance, a dashboard, a report)
  b) Inherited assumption (came from a prior case, not re-validated)
  c) New assumption (my own estimate, no source yet)
Flag every inherited assumption explicitly. If a prior case existed and was
not funded, ask me whether the reason is known. Treat "unknown" as the
default and normal answer, not a gap I need to fill in. Do not speculate on
my behalf about why it failed unless I tell you.

STEP 2 - IDENTIFY THE JUSTIFICATION PATTERN(S) AND THEIR TIMELINE
Before writing the benefits section, classify which pattern(s) this case
fits. More than one can apply at once:
  a) Visible improvement: the customer or business directly experiences
     the change (faster, cheaper, new capability).
  b) Foundational/invisible: the change prevents friction, risk, or a
     capacity ceiling the customer does not see day to day, and is only
     noticed when it is missing or when volume/complexity increases.
  c) Competitive parity: the capability already exists at comparable
     competitors, so the risk is falling behind rather than gaining ground.
  d) Strategic enabler/prerequisite: this initiative is a required
     building block for a separate, named external or strategic
     commitment (a partnership, a product launch, a regulatory deadline)
     that cannot proceed without it.

For each applicable pattern, ask me directly: "Was this known when the
case was first built, or did it surface later?" If a pattern surfaced
after work began, state it in the case as reinforcing an already-justified
initiative, not as part of the original rationale. Never imply foresight
that did not exist. This distinction matters for the case's own integrity
and for how it holds up if someone later asks why the case was built the
way it was.

If (b), (c), or (d) applies, do not force the case into a "customer
benefit" narrative it cannot honestly support. Build the justification
around the pattern that actually applies (cost of inaction, competitive
benchmark, capacity/scale risk, or the named downstream commitment), and
say so plainly rather than dressing it up as a customer-facing win. Where
a strategic dependency exists alongside a direct measurable benefit,
present both, in the order they actually occurred.

STEP 3 - BUILD THE CASE BODY
Structure the case as:
  - Problem/Opportunity: current state, ideal state, quantified gap.
    No solution language here.
  - Root Cause: one level deeper than the symptom. If this has been
    deprioritized before, consider whether the root cause is the business
    logic itself or a lack of executive sponsorship. Do not assume
    sponsorship history is the cause unless I tell you it is.
  - Proposed Business Solution: the business change only, no system detail
  - Scope: in and out, executive-level only
  - Benefits: separate Measurable / Economic / Qualitative, each with a
    baseline and target metric, and a named owner who would sign off.
    Mark any figure that has not been confirmed by its named source as
    [Finance-pending] or equivalent rather than filling it with a
    plausible-looking number.
  - Dependencies: if a strategic-enabler pattern applies, name the
    downstream commitment explicitly, state what happens if this
    initiative does not proceed, and state clearly whether it originated
    the case or reinforced an already-justified one.
  - Costs: total investment, plus ongoing operating cost after go-live
  - Risks to Benefit Realization: top 3-5, mitigation for each. Where a
    foundational, parity, or dependency pattern applies, include the risk
    that the case reads as "nice to have" to a reviewer who has not been
    shown that pattern explicitly.

STEP 4 - EXECUTIVE CONTENT CHECK
Give me an explicit three-column check for every section: Missing (a VP
would need this to decide and it is not here), Sufficient (right level of
detail for a decision), Excess (belongs in an appendix, not the body). Do
not skip this even if everything looks fine.

STEP 5 - TRANSLATE TO DECK STRUCTURE
Convert the checked case into slide-by-slide content:
  1. Title slide: "In order to [X], we are doing [Y], which is worth [Z],
     measured by [W]." Add a second sentence only if a dependency
     reinforced the case after the fact; state it as reinforcement, not
     as the founding rationale.
  2. Problem/Opportunity
  3. Root Cause
  4. Proposed Solution and Scope
  5. Benefits (founding rationale first, in the order it actually occurred)
  6. Dependencies (if applicable, labeled clearly as origin or reinforcement)
  7. Costs
  8. Risks
  9. Recommendation and Ask
Make the formatting and pacing decisions for me. One point per slide, plain
language, no more than what a VP reads once before asking a question.

STEP 6 - WORST-PRACTICE CHECK
Flag any of: unstructured narrative, no tie to organizational strategy,
price-only vendor framing, no other stakeholders consulted, unsupported
assumptions stated as fact, cost transfer mislabeled as cost saving, a
foundational/invisible or strategic-enabler benefit forced into a false
customer-facing narrative, treating sponsorship history as if it were
proof of a flawed business case, and implying a dependency was known
before it actually surfaced.
```

## Sample Input

**Verified data (Finance/dashboard sourced):**
- Approximately 12,000 commercial card applications processed annually (illustrative figure)
- Current process: frontline employee completes a customer-signed PDF, faxes it to a central processing team, who manually re-key the data into the card platform
- Current time-to-card: up to 20 business days for commercial cards, versus 3 to 5 for retail cards (illustrative figures)
- Compliance and Legal are advisory stakeholders on this workflow, not approval-holders

**Original justification, known from the start:** the case for automating the single-owner ownership path was already strong on retention grounds alone. Bringing time-to-card closer to consumer-card timelines was expected to reduce applicant drop-off between approval and card delivery.

**Inherited context (prior attempt, reason not confirmed):** a similar automation effort had been raised in some form previously and did not move forward. The specific reason it was not funded is not known. Leadership priorities shifted multiple times over several years before the initiative resurfaced.

**Justification that surfaced after mapping work began:** partway through the work, it emerged that a separate, already-funded programme to retire the legacy paper intake channel depended on this workflow being automated first. This did not originate the case. It reinforced urgency on a case already being built.

**Scope of the actual work:** mapped and designed the automated workflow for the single-owner ownership path. Multi-owner and complex-ownership applications continue through the existing manual process. Automating the single-owner path does not eliminate the Operations team; it creates a bifurcated process.

## Claude Output

**Step 1, Data Triage.** Verified: application volume, time-to-card figures, current manual process steps, stakeholder roles, the intake-retirement dependency. Inherited assumption: a prior attempt existed and did not proceed. Reason not confirmed, no cause assigned. New assumption: the drop-off reduction estimate, flagged as needing Finance sign-off before it appears in any benefit table.

**Step 2, Justification Pattern and Timeline.** Two patterns apply, in sequence. Pattern (a), visible improvement, known from the start: reducing time-to-card was expected to directly reduce applicant drop-off, a measurable retention benefit. Pattern (d), strategic enabler, surfaced after mapping began: the workflow was later identified as a required dependency for the separate intake-retirement programme. The retention benefit is presented as the case's founding rationale. The dependency is presented as a reinforcing development discovered mid-work, not as part of the original justification.

**Step 3, Case Body.**

*Problem/Opportunity.* Commercial card applications currently take up to 20 business days to reach the customer, against 3 to 5 for retail cards (illustrative figures), because the process relies on a signed PDF faxed to a central processing team for manual re-keying into the card platform across roughly 12,000 applications a year (illustrative figure). The gap between actual and achievable time-to-card is the opportunity.

*Root Cause.* The manual re-key step exists because the commercial card application path was never brought into the same digital infrastructure as retail cards. This is an infrastructure gap, not a resourcing gap, and it persisted across leadership changes for reasons not tied to the case's own merit. The automation case was justified independently on this basis before any external dependency was identified.

*Proposed Business Solution.* Mapped and designed an automated card creation workflow addressing manual review across several dozen data points per application, for the single-owner ownership path. This design serves as a key dependency enabling future end-to-end automation.

*Scope.* In scope: automated data capture and card platform entry for single-owner applications. Out of scope: multi-owner and complex-ownership applications, which remain manual under the current process. This is stated as a deliberate scope decision, not an oversight.

*Benefits.*
- Measurable: reduced applicant drop-off between approval and card delivery, tied to closing the time-to-card gap. This was the case's original and independently sufficient justification. Baseline and target: **[Finance-pending]**.
- Dependency-linked: after mapping work began, this workflow was identified as a required building block for the separate intake-retirement programme. This did not create the case. It added urgency to a case already justified on its own terms. Not converted into a fabricated dollar benefit of its own.

*Dependencies.* A separate, already-funded programme to retire the legacy paper intake channel requires this workflow to be automated first. This automation is a named building block of that programme, identified after the case was already underway. If it does not proceed, the intake retirement cannot complete.

*Costs.* Total build cost and ongoing operating cost after go-live: **[Finance-pending]**.

*Risks to Benefit Realization.*
- Drop-off reduction assumption is unvalidated. Mitigation: confirm with Finance/FP&A before this becomes a headline number.
- Reviewers may read this as "nice to have" if the dependency is not stated plainly. Mitigation: name the intake-retirement dependency explicitly in the deck rather than leaving it implied.
- Multi-owner applications remaining manual could be read as an incomplete solution. Mitigation: state the bifurcation explicitly as a scope decision.

**Step 4, Executive Content Check.**

| Section | Status |
|---|---|
| Problem/Opportunity | Sufficient |
| Root Cause | Sufficient |
| Benefits (Measurable) | Missing until Finance confirms baseline/target |
| Dependency | Sufficient; sequencing (reinforcement, not origin) must stay explicit |
| Costs | Missing, Finance input required |
| Multi-owner scope decision | Sufficient, needs one explicit sentence so it reads as a decision, not a gap |

**Step 5, Deck Structure.**
1. Title: "In order to close the business-card time-to-card gap, we are automating single-owner application processing, worth reduced applicant drop-off, measured by time-to-card and completion rate. This work has since become a required building block for the separate intake-retirement programme."
2. Problem/Opportunity
3. Root Cause
4. Proposed Solution and Scope
5. Benefits (retention presented as founding rationale)
6. Dependency: Intake Retirement Programme (labeled as reinforcement, discovered after work began)
7. Costs **[Finance-pending]**
8. Risks
9. Recommendation and Ask

**Step 6, Worst-Practice Check.** No fabricated cost-transfer language. Dependency stated as reinforcement, not origin. One flag carried forward: the drop-off benefit rests on an unvalidated assumption and should not be presented as final until Finance signs off.

## Jason's Edited Version

Corrected two things Claude got wrong on the first pass, both material:

1. The dependency (the intake-retirement programme) was **not** known when the case was first built. The case for automating the single-owner path was already strong on retention grounds alone. The dependency surfaced later, mid-work, and reinforced urgency on a case already underway. The prompt now asks explicitly, for every applicable pattern, whether it was known at the outset or surfaced later, and refuses to imply foresight that did not exist.
2. Reason for the prior case's non-funding is genuinely unknown, not a plausible guess I supplied after being asked. The prompt now treats "unknown" as the default, normal answer rather than a gap to be filled with speculation.

Kept the [Finance-pending] placeholder convention rather than illustrative mock numbers, since a rounded number here would be indistinguishable from a real one and would undercut the point of flagging what still needs sign-off.

## Lessons Learned

- A business case can carry more than one justification pattern at once (here, a direct measurable benefit plus a strategic dependency), and the two should not be collapsed into a single number or a single narrative thread.
- Sequencing integrity matters as much as content accuracy. Stating a dependency as though it were known from the start, even unintentionally, misrepresents why a decision was originally made and can undermine the case's credibility if questioned later.
- Foundational or invisible-to-the-customer work (automation the customer never sees) fails in front of executives not because the math is wrong, but because it gets framed as a customer benefit it cannot honestly claim. The fix is naming the actual pattern (cost of inaction, competitive parity, strategic prerequisite) rather than forcing a customer-facing story.
- "Why did the prior case fail" is very often genuinely unknown to the person picking the work back up, especially after multiple leadership changes. The prompt should treat that as the expected default, not prompt the builder to invent a plausible-sounding reason.
- Placeholder discipline (marking unconfirmed figures explicitly rather than substituting rounded illustrative numbers) is worth preserving even in a reference file, since the whole point of the pattern is visible, honest flagging of what still needs sign-off.

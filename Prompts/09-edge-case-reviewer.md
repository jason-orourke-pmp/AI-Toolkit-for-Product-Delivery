> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 09: Edge Case Reviewer

**Stage in JOR AI Product Delivery Framework:** Validate

**Job to be done:** Stress-test a written story before it enters a sprint. This catches both missing edge cases and stories that have gone stale relative to the actual solution design. The goal is to identify where a human (Product Owner, BA, or reviewer) needs to step in and correct a possible issue, not to auto-generate scope changes.

**Organizational context this prompt assumes:** No dedicated business-analyst support for this kind of review, so edge cases surface informally, often from a colleague's recollection of prior scoping attempts, rather than from a formal review step. This is a common enough setup to be worth designing the prompt around. Automating the standard (single-owner) path does not eliminate the Operations team. Multi-owner and other excluded cases continue business-as-usual via the existing manual fax-based process. This is a process bifurcation (two parallel paths, one automated and one manual), not a full elimination of the manual process or the team supporting it.

---

## Prompt (v1.1)

```
You are acting as an experienced Product Owner in a regulated financial
services environment (banking/fintech), reviewing a user story (or set of
stories) for gaps before it goes into a sprint. Your job is to identify
edge cases that are NOT currently addressed by the story's acceptance
criteria.

BEFORE identifying edge cases, confirm whether the story's acceptance
criteria still match the actual intended process/solution design. If the
constraints provided describe a different mechanism than what the
acceptance criteria assumes (e.g., criteria describes validating a
manual/paper submission, but the actual solution is a digital form with
upstream validation already handled elsewhere), flag this as a STORY
ACCURACY ISSUE first, before generating new edge cases. Do not add edge
cases on top of a story that no longer reflects the real process.

Distinguish between two categories of edge case:

1. TECHNICAL/PROCESS EDGE CASES — things that could go wrong in execution
   (e.g., missing data, illegible submissions, system timeouts,
   duplicate requests, partial failures).

2. BUSINESS/ENTITY COMPLEXITY EDGE CASES — variations in the underlying
   business scenario that may fall outside intended scope (e.g.,
   different customer/entity types, ownership structures, jurisdictions,
   product variants). These are often the more consequential kind in
   regulated financial products, and are frequently handled by
   DELIBERATELY EXCLUDING them from an early phase, not by solving for
   them. If an exclusion means an entire alternate process (e.g., the
   original manual process) continues to operate in parallel for the
   excluded cases, state this explicitly as a process bifurcation, not
   simply a scope note. This matters for workforce/operational planning,
   since it means the manual process and its supporting team are not
   being retired, only partially offloaded.

IMPORTANT: I may already know some real-world constraints or historical
scoping decisions (e.g., "this only applies to single-owner businesses;
multi-owner or complex ownership structures are out of scope"). If I
provide these, treat them as authoritative. Do not contradict or expand
scope beyond what I've stated. Your job in that case is to (a) confirm
the story's acceptance criteria correctly reflect the stated exclusion,
and (b) surface any OTHER edge cases I have not already mentioned, rather
than re-litigating ones I've already scoped out.

If I have NOT provided known constraints, ask me directly whether there
are historical scoping decisions or known exclusions before assuming full
scope is intended. Do not silently assume the story should handle every
possible variation.

For the story provided, produce:

1. STORY ACCURACY ISSUE (if any)
   Flag if the story/acceptance criteria appear to describe an outdated
   or incorrect version of the process, based on the constraints given.

2. EDGE CASES ALREADY HANDLED
   Confirm which edge cases (if any) the current acceptance criteria
   already address, explicitly or implicitly.

3. TECHNICAL/PROCESS EDGE CASES TO CONSIDER
   List plausible technical/process edge cases not currently covered.

4. BUSINESS/ENTITY COMPLEXITY EDGE CASES TO CONSIDER
   List plausible business/entity variations not currently covered,
   clearly separating:
   - Cases already told to be OUT of scope. Confirm these are correctly
     excluded, and briefly note the likely business rationale if
     inferable, as well as whether the exclusion implies a parallel
     manual process continuing to run (a bifurcation), rather than a
     simple scope trim. Do not re-argue for including these.
   - Cases that may be genuinely undecided and worth flagging as an open
     scope question

5. RECOMMENDATION
   For each new edge case surfaced, suggest one of: (a) add to this
   story's acceptance criteria, (b) create a new story, (c) explicitly
   document as an out-of-scope exclusion for this phase, or (d) flag as
   an open question for the Product Owner/business stakeholder to decide.

Do not assume more scope than stated. Do not treat every possible edge
case as something that must be solved now. Deliberately phased scope is
a valid and common decision in regulated financial products. The goal of
this review is to identify where a human needs to step in and make a
decision or correction, not to resolve every issue automatically.

Here is the story and any known constraints:
"{{STORY_AND_CONSTRAINTS}}"
```

---

## Sample Input

> Story: As an Operations Analyst, I want the automated system to validate submitted commercial card creation documents, so that incomplete or erroneous submissions are rejected before entering the queue.
> Acceptance Criteria: System checks for required fields; system flags missing signatures; system rejects illegible scans.
> Known constraints:
>
> - This phase only supports single-owner businesses (sole proprietorships and single-owner corporations). Multi-owner corporations, partnerships, and complex ownership structures are out of scope, even under a full end-to-end future vision — no committed timeline for expansion, because the majority of applications are single-owner. Excluded cases continue business-as-usual via the existing manual, fax-based process. Operations is not being eliminated, only offloaded for the single-owner segment.
> - Both legal name and trade/business (DBA) name are on file; the trade name is used on the card.
> - All owners must sign the credit agreement authorizing a card (not just a designated signer).
> - Sole proprietorships can convert to corporations, but cards are only requested against the final account type after conversion, never mid-change.
> - In the future-state automated process, submission occurs via a smartform (pre-populated fields plus manual entry), not a fax. Signed documentation is collected and filed separately for compliance/KYC purposes before card creation, and it is not validated as part of this step.

---

## Claude Output (v1.1)

**1. Story Accuracy Issue**
The acceptance criteria ("flags missing signatures," "rejects illegible scans") describe the legacy paper-based, manually-reviewed process. This is the kind of checking Operations previously performed by hand. Per the stated future-state design, submission occurs via a smartform with pre-populated fields; signed documentation is collected and filed separately (for compliance/KYC) before card creation, not validated at this step. **Recommend rewriting the acceptance criteria** to reflect smartform validation (required fields, format/data validation on manually-entered fields) rather than manual-review failure modes, which no longer apply here. A smartform should catch what Operations' manual review previously caught.

**2. Edge Cases Already Handled**

- Required field validation (covered, though should be reframed around smartform fields, not paper forms)

**3. Technical/Process Edge Cases to Consider**

- Duplicate submission (e.g., branch resubmits the smartform after not receiving confirmation)
- Pre-populated field is incorrect or stale (e.g., core system data changed since pre-population) but not corrected by the submitter
- Manually-entered field passes format validation but is factually wrong (e.g., valid-format but incorrect account number)

**4. Business/Entity Complexity Edge Cases to Consider**

*Already excluded (confirmed, with rationale):*

- Multi-owner corporations, partnerships, complex ownership structures. Excluded because single-owner businesses represent the majority of applications; intended as MVP1 scope with no committed timeline for expansion. **This is a process bifurcation, not a full retirement of the manual process.** Excluded cases continue via the existing fax-based, manually-processed workflow, meaning Operations retains this workload indefinitely for excluded cases even as their single-owner workload is largely automated away.

*Not applicable (ruled out by clarification, not genuine edge cases):*

- DBA vs. legal name — both names are on file; trade name is used on the card, no ambiguity.
- Non-owner signer — all owners must sign the credit agreement; within single-owner scope, this means the one owner signs personally.
- Mid-conversion entity type — cards are only requested against the final account type after conversion completes, never mid-change.

**5. Recommendation**

- Rewrite acceptance criteria to reflect smartform-based validation, not paper-based validation (**highest priority, the story itself is out of date**)
- Duplicate submission handling → add to this story's acceptance criteria
- Stale pre-populated data → add to this story's acceptance criteria (require re-confirmation of key pre-populated fields at submission)
- Factually-incorrect-but-valid-format data → flag as an open question for Tech/Ops during feasibility (likely a downstream reconciliation/matching concern, not something the smartform itself can catch)

---

## Jason's Edited Version

**On the Story Accuracy Issue:** This catch is accurate and still holds. The smartform should catch what Operations previously caught by hand during manual review. That's the correct way to frame it, rather than describing it narrowly as "no more fax." The underlying point is the same either way: the story was testing against a manual review step that the new design removes entirely for the automated path.

**On the technical/process edge cases:** These still feel accurate to real risks I'd actually watch for. I can't point to anything more important that's missing, though I wouldn't assume this list is exhaustive either. It's a solid starting set, not a guaranteed complete one.

**On the business/entity complexity section:** Important correction here. Automating the single-owner path does not eliminate the Operations team. Multi-owner and other excluded cases continue business-as-usual via the existing fax-based, manual process. This is why Operations as a whole can't be eliminated. It's a bifurcation between an automated single-owner path and an unchanged manual path for everything excluded, not a full retirement of the manual workflow.

---

## Lessons Learned

- Edge case review isn't only about finding what's missing. Sometimes the real finding is that the story itself describes the wrong process entirely (in this case, testing manual-review failure modes against a smartform-based future state). Catching that is more valuable than any list of new edge cases.
- Real edge-case knowledge in this project came from institutional memory (a colleague who knew the project's scoping history), not a formal review step. This prompt exists to formalize that kind of check going forward, using stated constraints as authoritative input rather than inventing plausible-sounding but ungrounded scenarios.
- Deliberately scoping out complexity (multi-owner, partnerships) is a legitimate product decision, not a gap to be filled, but it's important to state precisely what "excluded" actually means operationally. In this case, exclusion means an entire parallel manual process continues indefinitely, not that the excluded segment simply waits for a future phase. This distinction matters for workforce and operational planning, not just technical scope.

> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 07: User Story Generator

**Stage in JOR AI Product Delivery Framework:** Prioritize

**Job to be done:** Take an Epic and break it into properly-framed User Stories (stakeholder need, not PO activity) with baked-in acceptance criteria, while separating out PO/delivery tasks that don't belong in story format.

**Organizational context this prompt assumes:** No dedicated Scrum Master or Business Analyst. The Product Owner performs BA-type work themselves. Technology/Development sits in a separate department, functioning as an external advisory/delivery partner rather than an embedded team member. The "team" or "POD" is a group of Product Owners who may each independently own different products (including adjacent roles like marketing partners or campaign-focused POs). Some of these peers may still be genuine stakeholders with real, distinct needs, not merely disguised versions of the author's own coordination work.

---

## Prompt (v1.2)

```
You are acting as an experienced Product Owner in a regulated financial
services environment (banking/fintech). I will give you an Epic
(objective, scope, key activities) from a quarterly plan. Your job is to
break it into User Stories in the format:
"As a [role], I want [goal], so that [benefit]."
Acceptance criteria should be written as simple bullet points directly
under each story (not Given/When/Then).

IMPORTANT — Distinguish stories from tasks:
A true User Story represents a need or outcome experienced by an actual
stakeholder (e.g., an Operations Analyst, a Retail Branch Representative,
a Compliance Reviewer, a Customer) — something changes for them, or they
gain a capability, once this is delivered.

A TASK is coordination or delivery work the Product Owner or delivery
team does (e.g., holding a meeting, gathering information, documenting a
process) that does not represent a stakeholder's need in itself.

Do NOT write stories from the Product Owner's own point of view (e.g.,
"As a Product Owner, I want to consult with X, so that I understand Y" is
a TASK, not a story). Be alert to disguised PO-perspective stories: if a
"stakeholder" story is really just the Product Owner's own team or
working group with no distinct need, treat it as a TASK. However, a peer
within the same POD CAN be a genuine stakeholder with a real story if
their work reflects a distinct need from the Product Owner's own
coordination work (e.g., a marketing partner, or a Product Owner for an
adjacent product/campaign who depends on this initiative's output for
their own separate purposes). The test is whether the need is distinct
from the author's own coordination activity — not whether the person
shares a POD or reporting line.

ACCEPTANCE CRITERIA SOURCING: Acceptance criteria must only include facts
the named role can actually attest to from their own direct knowledge or
vantage point. Do not include criteria that would actually be sourced
from a different party (e.g., error rates known only to a downstream
reviewer, or volume/frequency data known only to leadership or
reporting) — if a criterion belongs to a different source, move it to
that source's own story or a separate data-gathering task, rather than
attaching it to the wrong role.

Additional context: this Product Owner may operate without a dedicated
Scrum Master or Business Analyst, performing BA-type work themselves, and
Technology/Development may sit in a separate department rather than an
embedded team member. Reflect this by treating Technology/Development as
an external advisory stakeholder, not as an internal team resource,
unless stated otherwise.

For this Epic, produce:

1. USER STORIES
   For each genuine stakeholder need within this Epic's scope, write:
   - Story: "As a [specific role], I want [goal], so that [benefit]."
   - Acceptance Criteria: 2-5 simple bullet points describing what must
     be true for this story to be considered done, sourced correctly per
     the rule above.

2. SUPPORTING TASKS (NOT STORIES)
   List coordination/delivery activities from this Epic that are
   necessary but do not belong in story format. Label these clearly as
   tasks, not stories.

3. NOTE ON AMBIGUOUS CASES
   If an activity or acceptance criterion is borderline, briefly explain
   the reasoning for how you classified it.

Keep roles specific to the actual organizational stakeholders named in
the Epic (e.g., "Operations Analyst," "Retail Branch Representative,"
"Compliance Reviewer") rather than generic terms like "user" or
"customer," since this is an internal workflow initiative.

Here is the Epic:
"{{EPIC}}"
```

---

## Sample Input

*(Epic 2: Current-State Process Mapping — from 06-epic-generator.md)*

---

## Claude Output (v1.2, with corrected acceptance criteria attribution)

**1. User Stories**

- **Story:** As an Operations Analyst, I want to describe the current manual card-creation process step by step, so that automation opportunities and rework causes are accurately captured before any solution is designed.

  * *Acceptance Criteria:*
    + Analyst has walked through the full process from document receipt to card creation
    + Top causes of rework/errors (as observed during Operations' own review) are identified and documented
    + Time-per-step is estimated for each stage of Operations' own process

- **Story:** As a Retail Branch Representative, I want to describe how I currently submit card creation documents, so that the automated intake process reflects how documents are actually generated and submitted today.

  * *Acceptance Criteria:*
    + Current submission method (fax or digital) and document format are documented
    + Any known friction points from the branch's own perspective (e.g., time spent completing the form, signature capture process) are noted

**2. Supporting Tasks (Not Stories)**

- Schedule and hold process walkthrough sessions with Operations
- Schedule and hold intake discussions with Retail, the Commercial Banking channel, Commercial Banking, and Contact Centre representatives
- Draft and maintain the current-state process map as the Product Owner (no dedicated BA support), for use in Epic 4
- Gather channel volume/frequency data from leadership reporting or Business Cards data (not from individual branch representatives)
- Consolidate rework-cause data (sourced from Operations, not from branch reps) into a summary for use in Epic 4 (Technical Feasibility)

**3. Note on Ambiguous Cases**
Two acceptance criteria were reattributed in this version. "Common submission errors from the branch side" was moved off the Retail Branch Representative story. A branch representative believes their submissions are correct, since errors are only discovered downstream during Operations' review; this criterion now lives on the Operations Analyst story instead, where it accurately reflects who can attest to it. Similarly, "volume/frequency from this channel" was removed from the branch representative story and converted into its own task, since an individual branch representative doesn't have visibility into channel-wide volume. That data comes from leadership reporting or Business Cards data, not a frontline conversation.

---

## Jason's Edited Version

**On acceptance criteria misattribution (Retail Branch Representative story):** The original acceptance criteria mixed information sources that don't belong together. A branch rep can confirm their submission method and document format. That's their own direct experience. But "common submission errors" isn't something a branch rep can identify, since errors are only discovered once Operations reviews the document; from the branch's perspective, they believe they've submitted correctly every time. Similarly, "volume/frequency from this channel" isn't something an individual branch rep would know. That comes from leadership reporting or Business Cards data, not a frontline conversation. This version correctly splits those out.

**On the POD-stakeholder rule:** Worth softening the earlier version of this rule. It's true in the original example (the "Delivery POD member" story was really just my own coordination need restated). But a peer Product Owner in the same POD absolutely can be a genuine stakeholder with a real story. For example, a marketing partner, or a PO for retail cards or a campaign initiative, might have a real dependency on this work that's distinct from my own delivery activity. The test should be whether the need is genuinely different from my own coordination work, not simply whether the person shares a POD or reporting structure.

**On story granularity:** No changes needed here. These stories reflect how I'd actually break things down: as small, individually verifiable pieces of work.

---

## Lessons Learned

- The practice this prompt was written against wrote every story from my own Product Owner point of view. Not correct Agile practice, since a story should represent a distinct stakeholder's need, not the PO's own coordination activity.
- A subtler, generalizable discipline: acceptance criteria must be sourced from the same role the story is written from. It's easy to write a factually true and useful criterion, but attach it to the wrong stakeholder's story simply because it's related to the same topic. The test is whether that specific role can actually attest to that specific fact from their own vantage point.
- The "disguised PO story" rule needed softening. A peer in the same POD isn't automatically a fake stakeholder. The real test is whether their need is genuinely distinct from the PO's own coordination work, not whether they share a reporting structure or team label.
- I acted as my own BA (no dedicated BA support), and developers sat in a separate department. This shapes how stakeholder roles and story ownership should be modeled, not just an organizational footnote.

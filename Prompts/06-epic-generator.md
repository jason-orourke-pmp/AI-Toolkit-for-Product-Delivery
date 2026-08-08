> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 06: Epic Generator

**Stage in JOR AI Product Delivery Framework:** Prioritize

**Job to be done:** Take a discovery document and break it into Epics suitable for quarterly planning, organized by workstream/activity type rather than by functional solution slices, reflecting how work is often actually organized in a regulated, multi-stakeholder environment.

---

## Prompt (v1.2)

```
You are acting as an experienced Product Owner in a regulated financial
services environment (banking/fintech). I will give you a discovery
document for a Feature-level initiative. Your job is to break this into
Epics suitable for quarterly planning.

Use this organizing principle: Epics should be organized by WORKSTREAM/
ACTIVITY TYPE (e.g., discovery and stakeholder alignment, current-state
process mapping, technical feasibility and design, build and testing,
rollout/change management) rather than by functional slices of the end
solution. Several Epics typically run within a single quarter, and some
may extend across two quarters. Present this as ONE reasonable way to
break down the work, not the only correct structure — the specific
number and grouping of Epics is a judgment call the Product Owner makes
based on the situation, not a fixed template.

For each Epic, produce:

1. EPIC NAME
2. OBJECTIVE
3. SCOPE (including what is explicitly NOT included, to avoid overlap)
4. KEY ACTIVITIES (3-6 items)
5. DEPENDENCIES (what it depends on, what depends on it)
6. LIKELY DURATION (in quarters, with rationale)
7. STAKEHOLDER ROLE — for each stakeholder involved, classify as:
   - APPROVER/DECISION-MAKER (has final say / go-ahead authority)
   - ADVISOR (provides guidance, risk input, or requirements, but does
     not have final approval authority)
   Do not default to calling every involved function an "approver" —
   distinguish clearly between advisory input (e.g., Legal, Compliance
   typically advise on risk/requirements) and actual decision authority
   (typically the product-owning business group). Include the
   requesting/delivery team itself in the stakeholder list, and be
   explicit about its role (delivery vs. approval), rather than only
   listing external groups.

   IMPORTANT: Advisory stakeholders (e.g., Legal, Compliance, Risk) are
   often not bounded to a single Epic — their guidance may be needed on
   an ongoing basis as new details surface throughout the initiative,
   including in later Epics. Do not assume a single "Compliance/Legal
   Review" Epic captures all necessary advisory input; note where
   advisory consultation is likely to recur across multiple Epics
   instead. Also be open to the possibility that new information may
   require looping back to an earlier Epic (e.g., Discovery) rather than
   assuming strictly linear progression — flag this as a realistic risk,
   not a process failure.

After listing all Epics, include:

8. APPROVAL CHAIN CLARIFICATION (as an activity within Epic 1)
   In regulated, multi-stakeholder environments, it's common for advisory
   groups to each expect the others to have been consulted first (e.g.,
   Legal asks if Compliance signed off, Compliance asks if Legal signed
   off), creating a circular back-and-forth before work can proceed. If
   this risk is plausible given the stakeholders involved, include a
   specific activity within Epic 1 whose purpose is to clarify who needs
   to weigh in, in what order, and who holds final decision authority,
   before deeper workstreams begin. Frame this as real risk mitigation,
   not bureaucratic overhead.

9. FUNDING/PRIORITIZATION MODEL CHECK
   Before recommending a formal "Final Go-Ahead" or budget-gated decision
   Epic, ask (or infer from context) which funding model applies:
   - INFORMAL/INTERNAL-VENDOR MODEL: no dedicated project budget; all
     contributors (including a separate developer department) are
     already salaried employees, and "resourcing" means negotiating
     prioritization against competing demands on their time, not
     securing spend approval. In this model, do NOT recommend a formal
     budget-gated decision Epic — instead, frame ongoing prioritization
     negotiation as a continuous activity, not a single approval moment.
   - FORMAL BUDGET MODEL: applicable for larger-scale initiatives (e.g.,
     external partner integrations, system rebuilds, cloud migrations)
     that require actual budget approval and spend tracking. In this
     model, a formal go/no-go decision Epic is appropriate.
   If unclear which applies, ask rather than defaulting to a formal gate.

10. SEQUENCING NOTE
   Explain logical order and which Epics can run concurrently. Note
   explicitly where "concurrently" may still involve informal
   back-and-forth between advisory groups, and that advisory consultation
   (e.g., Legal, Compliance) may run alongside multiple Epics rather than
   sitting in one bounded phase. Note this should be actively managed
   rather than assumed to resolve itself.

Keep language internal-facing and specific to a regulated banking context.

Here is the discovery document:
"{{DISCOVERY_DOCUMENT}}"
```

---

## Sample Input

*(Output from Prompt 01: Requirements Clarifier — see 01-requirements-clarifier.md)*

---

## Claude Output (v1.1, prior to the v1.2 prompt refinements above)

**Epic 1: Discovery, Stakeholder Alignment & Approval Chain Clarification**

- *Objective:* Confirm the business problem and scope, and establish who needs to weigh in, in what order, and who holds final decision authority, before deeper workstreams begin.
- *Scope:* Stakeholder interviews (Retail, the Commercial Banking channel, Commercial Banking, Contact Centre, Business Cards Delivery POD, Business Credit Cards product group); confirmation of volume (~80K/year) and scope boundary; explicit mapping of the approval chain to avoid circular consultation loops between Legal, Compliance, and the Product group. Does NOT include process mapping detail or technical design.
- *Key Activities:* Stakeholder interviews; confirm success metrics; map approval chain (who advises, who decides, in what order); secure scope sign-off from Business Credit Cards.
- *Dependencies:* None upstream; all other Epics depend on this reaching sign-off.
- *Likely Duration:* 1 quarter.
- *Stakeholder Roles:*
  * **Business Credit Cards (AVP)** — APPROVER/DECISION-MAKER (owns the product; final scope sign-off)
  * **Business Cards Delivery POD (AVP)** — DELIVERY (this initiative's own team; drives the work, does not hold approval authority)
  * **Retail Cards (AVP)** — ADVISOR/benchmark reference only
  * **Canada Credit Cards (VP)** — escalation path only if Business Cards and Delivery POD cannot align; not routinely involved
  * **Retail, the Commercial Banking channel, Commercial Banking, Contact Centre** — ADVISOR/input (front-line process detail)

**Epic 2: Current-State Process Mapping**

- *Objective:* Document the end-to-end current-state workflow to identify automation opportunities and rework triggers.
- *Scope:* Map fax intake → Operations manual entry → error/rework loop → card creation. Does NOT include future-state design.
- *Key Activities:* Process walkthroughs with Operations; identify rework causes; quantify time-per-step.
- *Dependencies:* Depends on Epic 1 scope sign-off; feeds Epic 4.
- *Likely Duration:* 1 quarter, may run partially parallel with late-stage Epic 1.
- *Stakeholder Roles:* Operations — ADVISOR (process detail); Technology — ADVISOR (informed).

**Epic 3: Compliance & Legal Advisory Review**

- *Objective:* Gather regulatory, audit, and control requirements that any automated solution must preserve.
- *Scope:* Audit trail, dual-control/segregation-of-duties, consent/disclosure requirements. Does NOT include solution design.
- *Key Activities:* Compliance review sessions; Legal review of consent implications; Risk review of adjudication boundary; produce a constraints document.
- *Dependencies:* Runs concurrently with Epic 2 once Epic 1 sign-off is secured; Epic 4 depends on this Epic's constraints document.
- *Likely Duration:* Likely spans 2 quarters. Advisory review typically takes longer and may involve iterative back-and-forth.
- *Stakeholder Roles:* Legal — ADVISOR (not an approver; flags consent/disclosure risk); Compliance — ADVISOR (flags audit/control requirements); Risk — ADVISOR (flags adjudication/control risk). None of these three hold final decision authority. That remains with Business Credit Cards.

**Epic 4: Technical Feasibility & Solution Design**

- *Objective:* Assess feasibility of automating intake/validation and design the target solution within confirmed constraints.
- *Scope:* Feasibility assessment, validation rule design, integration approach. Does NOT include build/testing.
- *Key Activities:* Feasibility assessment with Tech/Ops; solution options and recommendation; updated future-state process map.
- *Dependencies:* Depends on Epic 2 and Epic 3 reaching sufficient maturity; feeds Epic 5 and the Final Go-Ahead Epic.
- *Likely Duration:* 1 quarter; may start before Epic 3 fully closes if constraints are directionally clear.
- *Stakeholder Roles:* Technology/Development — ADVISOR (recommends solution options); Business Credit Cards — APPROVER (approves solution direction).

**Epic 5: Final Go-Ahead / Decision Gate**

- *Objective:* Secure the formal go/no-go decision from Business Credit Cards once advisory input (Legal, Compliance, Risk, Tech feasibility) has been consolidated.
- *Scope:* Consolidate advisory input into a single decision package; present to Business Credit Cards; obtain explicit go-ahead before build begins. Does NOT include re-litigating advisory feedback. That should be resolved before this Epic.
- *Dependencies:* Depends on Epics 2-4 reaching sufficient maturity.
- *Likely Duration:* Brief. Typically a single decision session, but timing depends on Epic 3/4 completion.
- *Stakeholder Roles:* **Business Credit Cards (AVP) — sole APPROVER here**; all advisory groups (Legal, Compliance, Risk, Technology) — input already captured upstream, ADVISOR only at this stage.

**Epic 6: Build, Test & Rollout Readiness**

- *Objective:* Build and validate the automated solution, and prepare channels/Operations for go-live.
- *Scope:* Development, UAT, training materials, go-live checklist. Does NOT include post-launch monitoring.
- *Key Activities:* Build; UAT with Operations; channel communication/training; go-live readiness checklist; rollback plan.
- *Dependencies:* Depends on Epic 5 go-ahead.
- *Likely Duration:* 1 quarter.
- *Stakeholder Roles:* Business Cards Delivery POD — DELIVERY (drives execution); Technology, Operations — ADVISOR/execution partners; originating channels — informed/trained.

**Sequencing Note:** Epics 2 and 3 often run concurrently in principle, but this concurrency requires active management by the Delivery POD. Advisory groups (Legal, Compliance) may each expect confirmation that the other has weighed in, creating a circular loop that can stall progress if not proactively coordinated. The Approval Chain Clarification activity in Epic 1 exists specifically to pre-empt this by establishing upfront who advises, who decides, and in what order. Epic 5 (Final Go-Ahead) is intentionally separated from the advisory Epics so there is one clear moment where Business Credit Cards, not Legal or Compliance, makes the actual decision, rather than the decision emerging ambiguously from parallel advisory conversations.

---

## Jason's Edited Version

**On the Epic structure overall:** The 6-Epic breakdown is a reasonable illustration, but it overstates how linear and discrete this actually was. Compliance/Legal isn't really a bounded, one-time Epic. They're a consulted stakeholder throughout the entire initiative, since their guidance evolves as more detail gets uncovered and new stakeholders raise new questions. In practice, this wasn't a clean sequential handoff between Epics; we sometimes had to loop back to Discovery when something new surfaced. A more accurate representation treats Compliance/Legal consultation as an ongoing thread running alongside the other Epics, not a single phase that starts and finishes.

**On "Final Go-Ahead" as its own Epic:** This is more formal than what actually happened, for this kind of project. There was no dedicated project budget. Everyone involved (including developers from a separate department) was already a paid bank employee, and "funding" this work meant negotiating and prioritizing our initiative ahead of other competing demands on their time, not securing a discrete go/no-go budget approval. That said, this isn't universal. Larger initiatives (e.g., external partner integrations like a major retail or airline partnership, a system rebuild, or a cloud migration) genuinely do require formal budget approval and spend tracking. For a project like this one, though, I'd reframe "Final Go-Ahead" as an ongoing prioritization negotiation, not a formal decision gate.

**On the Finance/data/channel addition:** Agreed this belongs in Discovery, not a later step. We can't scope or business-case anything without it. It's broader than Finance alone: the Data team (who holds the actual credit card data) and the distribution channels themselves (who have direct anecdotal experience of how bad the process gets when it fails) should also be included at this stage.

---

## Lessons Learned

- The practice this prompt was written against didn't follow a fixed template. Epic structure was a judgment call made on the fly, not a prescribed method. The prompt presents this as one reasonable approach, not the only correct one.
- Advisory input (Legal, Compliance, Risk) is rarely bounded to a single phase in practice. It recurs throughout an initiative as new information surfaces, and progress isn't always strictly linear; looping back to earlier work is realistic, not a failure.
- "Approver" is not the same as "advisor." Legal, Compliance, and Risk typically advise; only the product-owning business group (Business Credit Cards) holds actual decision authority.
- Whether a formal budget-gated decision point makes sense depends heavily on the funding model. Informal, internally-resourced initiatives (common in a large bank's product pods) rarely have a discrete go/no-go budget moment. Prioritization is a continuous negotiation. Larger, externally-scoped or infrastructure-level initiatives are a different story and do warrant formal gates.
- The delivery team itself (the POD) is a stakeholder that's easy to omit. It should always be named explicitly, with its role (delivery, not approval) stated.

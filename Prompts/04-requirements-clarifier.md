> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 04: Requirements Clarifier

**Stage in JOR AI Product Delivery Framework:** Clarify

**Job to be done:** Turn a vague stakeholder request into a structured discovery document (business problem, scope, assumptions, open questions, risks, stakeholders) suitable for a Product Owner kickoff conversation.

---

## Prompt (v1.0)

```
You are acting as an experienced Product Owner in a regulated financial
environment (banking/fintech), with a background in credit card
acquisition/sales. I will give you a short, informal stakeholder request.
Your job is NOT to design a solution yet — it is to turn the request into
a structured discovery document a Product Owner would bring into a kickoff
conversation.

Produce the following sections:

1. BUSINESS PROBLEM
   Restate the request as a clear problem statement, distinguishing what's
   stated vs. implied. Include both the operational angle and the
   commercial angle if the requester's role suggests a commercial
   motivation. If a root-cause bottleneck is described (e.g., a manual
   handoff, rework loop, or specific delay point), summarize it clearly as
   part of the problem statement, not just as a symptom.

2. SCOPE BOUNDARY (STATED OR ASSUMED)
   State clearly where the process is understood to begin and end. Flag
   this as something to confirm, not assume silently. Explicitly note any
   adjacent processes that appear similar but are likely OUT of scope
   (e.g., related request types that touch the same system/output but
   originate differently), so scope isn't silently conflated.

3. CURRENT-STATE VS FUTURE-STATE SNAPSHOT
   Briefly describe what is implied about the current manual process, and
   what a best-case future state might look like, based on the request.

4. OPEN QUESTIONS FOR THE REQUESTER
   List clarifying questions grouped by theme: current-state process,
   desired future-state/best case, scope boundaries, systems/data,
   business impact (sales/volume/experience), and success metrics. Always
   include a question about current volume (e.g., transactions/requests
   per month or year) if not already stated — this is foundational to any
   later business case.

5. ASSUMPTIONS TO VALIDATE LATER
   List assumptions being made based on the limited information given.
   For each, note which downstream function would need to validate it
   (Compliance, Risk, Legal, Tech/Ops) — but do NOT recommend looping
   those teams in yet. Note explicitly: technical/feasibility validation
   with Tech/Ops should happen only once there is enough direction to
   avoid over-committing before feasibility is confirmed.

6. STRATEGIC EXPANSION QUESTION
   Note whether a more complete/end-to-end automation may be possible
   beyond the immediate ask, benchmarked against a comparable process. If
   the comparable process is more mature/automated, ask why the gap
   exists (e.g., product complexity, risk profile, historical scope
   decisions) rather than assuming parity is simply achievable.

7. RISKS
   Identify likely risks: operational, compliance/regulatory, technical,
   stakeholder/change-management. Be specific to a regulated banking
   context where relevant (e.g., audit trail, dual control, data
   accuracy). If automation would materially reduce or eliminate a
   team's current role/workload, name this explicitly as a workforce/
   change-management risk requiring deliberate planning — do not treat it
   only as an efficiency win.

8. STAKEHOLDERS
   List likely internal stakeholders to consult or inform, with a
   one-line reason each. Distinguish between teams that OWN the product
   (accountable for strategy/outcomes) and teams that DELIVER the
   improvement (accountable for execution), where the request implies
   this distinction. Note that a single sales/requester description may
   represent multiple channels (e.g., retail, business banking,
   commercial banking, contact centre) — list them individually rather
   than as one generic group.

Keep the tone professional and internal-facing. Assume this is an internal
workflow/process improvement, not an external customer-facing product,
unless stated otherwise.

Here is the stakeholder request:
"{{STAKEHOLDER_EMAIL}}"
```

---

## Sample Input

> Jason,
> the Commercial Banking channel has asked us to reduce manual effort in card creation. Currently frontline employees manually enter information into a PDF and Operations team manually enter that data into the card platform. We'd like to automate as much as possible. We'd like to begin discovery.
> Thanks.

**A note on methodology:** the email above is deliberately brief. Realistically, a stakeholder request often arrives this vague. The detailed process knowledge that follows in this document (the fax/digital-fax handoff, the central processing queue, the card platform re-entry, and the scope of what automation would and wouldn't touch) was supplied by me iteratively, correcting and expanding the AI's first-pass output, the same way a Product Owner would actually surface this detail through real stakeholder conversations, not something the AI inferred from the email alone. This mirrors how the prompt is meant to be used in practice. It is a structure for organizing and interrogating what you know or are actively gathering, not a substitute for gathering it.

---

## Claude Output (v1.0, incorporating corrected process detail)

**1. Business Problem**
Frontline employees currently capture card creation information by manually completing a PDF, which the customer signs (in person with a pen, or via digital signature). The signed PDF is then transmitted, by physical fax from the branch, or a digital "fax" equivalent, to a central processing team, who pick it up from a queue, review it for accuracy, and manually re-key all required information into the card platform to create the card. This creates two separate manual data-entry points (frontline PDF completion, then Operations re-entry into the card platform) plus a transmission and review step in between, extending total time-to-card. The commercial angle worth confirming: automating this wouldn't be an acquisition play. The business case is more likely retention-based, tied to reducing customer drop-off between approval and card-in-hand, and reducing central processing' manual workload.

**2. Scope Boundary (Stated or Assumed)**
Begins post-adjudication/approval, once frontline captures the card creation request (currently via PDF, potentially via a smartform in the future state). Ends once the card record is created in the card platform (card delivery/fulfillment remains business-as-usual). Out of scope, to confirm: multi-owner and other complex-ownership edge cases, which would likely continue to route to Operations for manual handling even after automation. This needs explicit confirmation, since it defines how much of Operations' current workload actually goes away.

**3. Current-State vs. Future-State Snapshot**
Current: frontline completes a PDF, customer signs it, it's faxed (physically or digitally) to an central processing queue; Operations reviews for accuracy and manually types the data into the card platform. Future (implied): frontline captures the same information directly into a validated smartform, which integrates with the card platform to create the card automatically, removing the Operations re-entry step (and likely the review step) entirely for standard, single-owner cases.

**4. Open Questions for the Requester**

- *Current-state:* What is the typical Operations queue turnaround time today? What's the current error/rework rate on the PDF submissions? Do submission volumes differ between in-person pen signatures and digital signatures?
- *Future-state/vision:* Does "automate as much as possible" mean automating frontline capture only, backend card platform integration only, or both end-to-end? Does the card platform support a direct integration/API for card creation, or would this require a new interface to be built?
- *Scope boundaries:* Confirm multi-owner/complex-ownership cases remain manually routed to Operations even in the future state.
- *Volume:* What is the current annual/monthly volume of commercial card creation requests through this process, and how does it split between in-person and digital signature capture?
- *Team impact:* If the re-entry step goes away for standard cases, what does that mean for the team's remaining workload? Is this already being considered, or is it a separate conversation this initiative should flag?
- *Success metrics:* Time-to-card, error rate reduction, Operations capacity redeployed, or some combination?

**5. Assumptions to Validate Later**

- Existing pen and digital signature methods already satisfy legal/consent requirements, and this won't change under automation (validate with Legal).
- The card platform supports some form of direct integration (API or otherwise) suitable for automated card creation (validate with Tech/Ops and the card platform vendor relationship).
- The manual Operations review step, beyond data entry, isn't currently catching errors or issues that a smartform validation wouldn't also catch (validate with Operations). Removing a human review checkpoint should not be assumed risk-free without confirming what that review currently catches.
- Audit trail and dual-control/segregation-of-duties requirements must be preserved in an automated flow (validate with Compliance).

*Tech/Ops feasibility validation should happen once there is enough direction on scope and desired outcomes, not before, to avoid over-committing to a solution path before feasibility is confirmed.*

**6. Strategic Expansion Question**
Consumer credit cards likely already have a more direct, less manual card-creation process. Worth confirming with the requester what specifically makes commercial card creation more complex (e.g., business verification, authorized signer requirements, multiple owners). This affects whether full parity with retail cards is realistically achievable, or whether a partial-automation target (excluding multi-owner cases) is the appropriate scope for this phase.

**7. Risks**

- *Operational:* Removing the Operations review step could also remove a quality-control checkpoint that currently catches certain errors before card platform entry. This needs to be understood, not assumed away.
- *Team/Change Management:* Automating the standard path would change what the central processing team spends most of its time on. That is a change-management consideration, not just an efficiency gain, and should be raised explicitly and early rather than left as a downstream surprise.
- *Vendor/Technical:* the card platform's integration capability for automated card creation is unconfirmed; may require vendor engagement or a new interface.
- *Compliance/Regulatory:* Audit trail and dual-control/segregation-of-duties must be preserved; signature capture (pen vs. digital) must continue to meet consent requirements in an automated flow.

**8. Stakeholders**

- **the Commercial Banking channel** – originating channel and requester
- **Retail Branches, Commercial Banking, Contact Centre** – other frontline channels likely affected if this extends beyond the Commercial Banking channel's initial ask
- **Central Processing Team** – current process owner; also a key stakeholder because automation changes their day-to-day work, not just a delivery partner
- **Business Credit Cards Product Group (Canada Credit Cards)** – product owner; this initiative delivers improvements supporting their roadmap
- **Technology/Development** – feasibility assessment, including card platform integration options
- **Card platform (vendor)** – may need to be engaged directly to confirm integration capability
- **Risk** – confirm no change to approval/adjudication controls
- **Compliance** – confirm audit trail and control requirements preserved, including signature/consent methods
- **Legal** – confirm no new disclosure/consent requirements
- **Finance / Data team** – to understand potential financial impact (e.g., reduced drop-off between approval and card-in-hand) and identify what metrics (e.g., daily card spend) would be needed to build a business case later

---

## Jason's Edited Version

**On the Business Problem (Section 1):** This isn't an acquisition play; it doesn't help us sell more cards upfront. The real financial case is retention-based: some customers who are approved drop out of the funnel between adjudication and card delivery, and faster/error-free card creation reduces that drop-off. The actual business case requires quantifying average time saved per card (aggregated across the portfolio), the reduction in drop-off this enables, and the resulting financial benefit, measured through incremental spend/revenue from getting a customer their card in X days instead of Y.

**On length/detail (Sections overall):** I'd keep the document close to its current length. Very few stakeholders, even at leadership levels, actually understood the mechanics of this process or how different it was from the retail card experience, so this level of explanation earns its place.

**On a missing consideration (Section 4, Open Questions):** The discovery document should also flag a need to loop in Finance early, not to build the full business case yet, but to understand at a high level what metrics we'd need to track (e.g., daily card spend patterns) and get a directional sense of potential financial impact before investing further in solution design. This is broader than Finance alone. The Data team (who holds the actual credit card data) and the distribution channels themselves (who have direct anecdotal experience of how bad the process gets when it fails) should also be included at this stage.

---

## Lessons Learned

- The AI's specificity in this document (fax handoffs, central processing, the card platform re-entry, turnaround times) came from my own domain knowledge fed in iteratively, not from the AI inferring it from a vague email. The prompt's real value is structuring and interrogating what I already know or am actively gathering, not generating knowledge I haven't supplied.
- A generic "efficiency" framing missed the actual business case: this was a retention play (reducing drop-off between approval and card-in-hand), not an acquisition play. Getting the actual commercial rationale right matters more than defaulting to a plausible-sounding one.
- Automating a manual process can eliminate a team's core function, not just improve efficiency. A good discovery document surfaces this as a workforce/change-management risk explicitly and early, rather than treating headcount impact as an afterthought to a technical efficiency story.
- Removing a manual step (like Operations' review) can also remove a quality-control checkpoint that isn't obvious until you ask what that step currently catches. Worth treating as an assumption to validate, not something automation solves by default.

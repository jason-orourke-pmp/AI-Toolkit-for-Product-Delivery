> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 02: Stakeholder Alignment / RACI Builder

**Stage in JOR AI Product Delivery Framework:** Discover

**Job to be done:** Turn an informal, referral- and domain-knowledge-based stakeholder discovery process into a documented RACI artifact. Run a completeness check before documenting known stakeholders, distinguish confirmed decision authority from a late-stage ask backed by leverage, and flag stakeholders affected by internal-only impacts the customer never sees.

---

## Purpose

Turns an informal, relationship- and referral-based stakeholder discovery process into a documented artifact, without pretending the informal process was a weakness. Distinguishes what I already knew from domain experience, what surfaced through referral, and what emerged later from a related but separate initiative. Flags scope or governance disagreements as they actually occur, including late-stage asks from stakeholders without current formal authority, and keeps observed/secondhand context clearly separated from confirmed fact. Produces a one-page stakeholder map that did not exist before, the kind of artifact meant to be shown to a manager or a new team member as "here's who's involved and why." Also runs a completeness check before documenting known stakeholders, since the stakeholders most likely to get missed are the ones nobody thinks to ask about, and relying on any one person's memory (a manager included) doesn't hold up when departmental turnover is high.

## Prompt (v1.0)

```
You are helping me turn an informal, referral-based stakeholder discovery
process into a documented artifact, and surface scope or governance
disagreements between stakeholders before they become friction in a
live meeting.

INPUTS I WILL PROVIDE:
- The initiative or workflow being scoped
- Stakeholders identified so far, and how each entered the picture
- Any known points of disagreement between stakeholder groups (scope
  boundary, cadence, ownership) if I'm aware of them
- Whether any of my information comes from a conversation I observed but
  wasn't a formal party to

STEP 0 - COMPLETENESS CHECK (before documenting known stakeholders)
This step exists because the stakeholders I miss are exactly the ones I 
don't think to ask about, and because turnover in past departments meant 
individual people, including managers, couldn't reliably be counted on to 
remember who belongs on a given initiative.

Part A - Standing checklist. The first time we use this prompt on a real 
initiative, build a checklist of stakeholder categories that reliably 
surface across nearly every initiative in this environment (e.g., Risk, 
Compliance, Legal, Finance/FP&A, a development team), based on what I 
tell you, not on general assumptions about how organizations are 
structured. Do not pre-seed this list yourself. Ask me to confirm or edit 
it once it exists, then reuse it as a running baseline for future 
initiatives, since a role-based checklist survives staff turnover in a 
way that relying on any one person's memory does not.

Part B - Discovery questions, for what the standing checklist doesn't 
cover. Ask me a short set of prompting questions specific to this 
initiative:
- Who approves the budget or funding for this, and have they been named?
- Who would be affected operationally but has no visible role in the 
  initiative yet (an internal-only impact, per Step 1)?
- Is there a team or function downstream that will inherit this work 
  once it's live, and are they represented?
- For anyone identified via referral (Step 1b), have they been asked 
  who else they'd loop in, given how often that surfaces someone not 
  otherwise obvious?
Do not attempt to name specific missing stakeholders yourself based on 
general assumptions about how organizations are structured. Surface the 
right questions for me to answer, since I know the actual structure and 
you don't.

STEP 1 - CAPTURE THE DISCOVERY CHAIN
For each stakeholder, capture how they entered the picture, using three
distinct sources, not one generic "how they were surfaced" field:
  a) Known from my own domain knowledge at the outset (I already knew
     this stakeholder belonged, nobody told me)
  b) Surfaced via referral (a manager, a colleague, or a working session
     suggested them)
  c) Emerged later as scope evolved (a related or dependent initiative
     surfaced a need for this stakeholder, but on a different timeline
     than my own project's initiation)
Ask me which applies for each stakeholder rather than assuming referral
is the default source.

Additionally, for each stakeholder, flag whether their involvement is due
to an INTERNAL-ONLY IMPACT: their team's process, workload, or day-to-day
operations change as a result of this initiative, even though the
customer's experience is unaffected or unchanged. This is common in
back-office and infrastructure work and is easy to under-communicate,
since there is no visible customer-facing signal to justify their
inclusion. State this plainly in the artifact rather than leaving their
reason for inclusion implicit.

If a stakeholder or a discussion belongs to a related but separate
initiative (different scope, different owner, different ART or team), do
not include it in this project's stakeholder map or discovery chain. Note
it as a related, adjacent initiative instead, with a one-line description
of the dependency, and keep it visibly out of this artifact's
Responsible/Accountable scope. My project's stakeholder map should reflect
who I actually needed for my own deliverable, not absorb the governance of
something downstream that depends on it.

STEP 2 - ASSIGN RACI
For each stakeholder, assign Responsible / Accountable / Consulted /
Informed based on what I tell you about their actual, confirmed
involvement (funding secured, approval authority exercised, formal
assignment). Do not infer authority level from title, seniority, or
proximity to the initiative alone. If a stakeholder is pushing for a role
or scope inclusion they don't yet formally hold, do not upgrade their
RACI role to match their ask. Record the ask as an Open Item instead (see
Step 3), not as a change in their formal role.

STEP 3 - FLAG SCOPE/GOVERNANCE DISAGREEMENTS AND LATE-STAGE ASKS
Treat these as two distinct patterns, not one:
  a) Genuine disagreement between two parties with comparable standing
     (e.g., two co-owners who don't agree on scope or cadence)
  b) A late-stage ask from a stakeholder without current formal authority
     over the initiative, using leverage (funding, relationship, timing)
     to request inclusion or scope expansion after the initiative is
     already in motion
For (b), do not treat it as a tie needing a tie-breaker. State it as what
it is: a request that the confirmed owner (or the authority above them)
would need to accept or decline. Name who has that authority based on
what I tell you; do not assume it is me unless I confirm it.

For any item where my information comes from a conversation I wasn't a
formal party to, or from secondhand context, label it explicitly as
observed/inferred rather than confirmed, and keep
it separate from stakeholder facts I've directly confirmed (assignments,
approvals, funding). Ask me directly if unsure which category something
falls into.

STEP 4 - PRODUCE THE ARTIFACT
Output a one-page stakeholder map: name, department, RACI role, discovery
source (a/b/c from Step 1), internal-only-impact flag where applicable,
and a separate "Open Items" section listing any unresolved scope/cadence
disagreements or late-stage asks, each with: item, type (Pattern a or b),
confidence (confirmed or observed/inferred), resolution owner, and days
open. This is the artifact meant to be shown to a manager or a new team
member as "here's who's involved and why," which did not exist before.

STEP 5 - WORST-PRACTICE CHECK
Flag any of: assigning Accountable to someone whose actual authority is
unconfirmed, resolving a scope disagreement silently instead of
escalating it, listing a stakeholder without stating how they were
identified, treating the artifact as replacing the relationship-based
discovery process rather than documenting it, presenting a late-stage ask
(Pattern b) as if it were a tie between equals (Pattern a), presenting
observed/secondhand information with the same confidence as confirmed
fact, and folding a separate initiative's stakeholders or disputes into
this project's scope.
```

## Sample Input

**Initiative:** commercial card application automation, single-owner ownership path (the same case as the business case prompt).

**Discovery chain:**
- Known from domain knowledge at outset: the Commercial Banking channel (the card is sold through that channel), Risk, Compliance, Legal (customer application data is involved)
- Surfaced via manager referral: the development team, needed to map the workflow and then build it
- Consulted, internal-only impact: the contact centre channel and the branch channel, because they would follow a different internal submission process going forward, even though the customer's experience of card creation itself is unchanged
- Emerged later, separate initiative: a broader end-to-end online application programme, owned by a different delivery group. This surfaced well after this project's initiation, and carried its own unresolved scope and cadence questions between the Commercial Banking channel and the Card Products team.

**Confirmed:** the Card Products team holds Accountable. Funding and approvals for the single-owner automation were already secured; the initiative was proceeding regardless of the Commercial Banking channel's position.

**Observed/inferred, not confirmed:** secondhand context suggested the Commercial Banking channel wanted additional ownership types included in the initial build rather than a later one, which would require them to bring funding and approvals of their own. Everything in this paragraph is observed rather than confirmed, and is recorded as such. It had no bearing on the mapping work itself and belonged to the separate end-to-end programme, not this project.

**Governance, still unresolved:** sync cadence between Business Cards and the Commercial Banking channel not yet agreed, within the separate end-to-end initiative.

## Claude Output

**Step 1, Discovery Chain.**

| Stakeholder | Source | Note |
|---|---|---|
| The Commercial Banking channel | (a) Domain knowledge | Known at outset, sells the product |
| Risk | (a) Domain knowledge | Known at outset, customer application data |
| Compliance | (a) Domain knowledge | Known at outset, customer application data |
| Legal | (a) Domain knowledge | Known at outset, customer application data |
| Development Team | (b) Manager referral | Needed to map, then build |
| The contact centre channel | (a) Domain knowledge, internal-only impact | New internal submission process; customer's card-creation experience is unchanged |
| The branch channel | (a) Domain knowledge, internal-only impact | Same as above |

**Adjacent Initiative (out of this project's scope):** a broader end-to-end online application programme, owned by a different delivery group. Surfaced well after this project's initiation, and carries its own unresolved scope and cadence questions between the Commercial Banking channel and the Card Products team. Not included in this stakeholder map or its RACI, since it belongs to a different deliverable with different ownership. Noted here only as a dependency this project's output feeds into.

**Step 2, RACI Assignment.**

| Stakeholder | Role | Basis |
|---|---|---|
| Jason (Product Owner) | Responsible | Mapped and designed the workflow |
| Development Team | Responsible | Owns technical build |
| The Card Products team | Accountable | Confirmed: funding and approvals secured, initiative proceeding independent of other stakeholders' input |
| Risk | Consulted | Advisory, not an approval-holder |
| Compliance | Consulted | Advisory, not an approval-holder |
| Legal | Consulted | Advisory, not an approval-holder |
| The contact centre channel | Consulted | Internal-only impact, new submission process |
| The branch channel | Consulted | Internal-only impact, new submission process |
| The Commercial Banking channel | Consulted | Sells the product; not Accountable. A stated interest in expanded scope is recorded as an ask (see Open Items), not a formal role |

**Step 3, Disagreements and Late-Stage Asks.** This item belongs to the adjacent initiative, not this project, and is noted here only for completeness. Pattern (b) applies: the Commercial Banking channel is not a co-equal owner in a standoff with the Card Products team. They are a Consulted stakeholder in this project requesting scope inclusion in the separate end-to-end initiative after the Card Products team had already secured funding and approval to proceed. This is a request the confirmed owner, or the authority above both, would need to accept or decline, not a tie requiring a tie-breaker. The entire item is labeled observed/inferred rather than confirmed, since it did not come from a conversation directly participated in.

**Step 4, Artifact.**

*Stakeholder Map (this project only)*

| Name/Group | Department | RACI | Source | Internal-Only Impact |
|---|---|---|---|---|
| Jason | Product | Responsible | Original assignment | No |
| Development Team | Technology | Responsible | Manager referral | No |
| The Card Products team | Product | Accountable | Domain knowledge, confirmed | No |
| Risk | Risk | Consulted | Domain knowledge | No |
| Compliance | Compliance | Consulted | Domain knowledge | No |
| Legal | Legal | Consulted | Domain knowledge | No |
| The contact centre channel | Operations | Consulted | Domain knowledge | Yes |
| The branch channel | Distribution | Consulted | Domain knowledge | Yes |
| The Commercial Banking channel | Commercial Banking | Consulted | Domain knowledge | No |

*Open Items*

| Item | Type | Confidence | Resolution Owner | Days Open |
|---|---|---|---|---|
| The Commercial Banking channel requesting scope inclusion in the separate end-to-end initiative (multi-owner, bundled credit) | Late-stage ask (Pattern b), adjacent initiative | Observed/inferred | Unconfirmed, likely above both business lines | [date raised] |
| Sync cadence between Business Cards and the Commercial Banking channel (adjacent initiative) | Governance gap | Confirmed | Unconfirmed | [date raised] |

**Step 5, Worst-Practice Check.** The Commercial Banking channel was not upgraded to Accountable despite the friction; the late-stage ask stayed a flagged Open Item. The ask was labeled Pattern (b), not treated as a tie between equals. Observed and secondhand information was kept explicitly separate from confirmed facts such as the Card Products team's funding and approval status. The adjacent initiative's open questions were noted for context but excluded from this project's own RACI and scope.

## Jason's Edited Version

Three corrections made through review, all material:

1. **RACI accuracy.** the Card Products team held Accountable outright; the Commercial Banking channel was never a co-equal owner. Funding and approvals were already secured and the initiative was proceeding regardless. The first draft incorrectly gave both parties Accountable, which misrepresented a settled ownership question as an unresolved tie.
2. **Discovery source breakdown.** Most stakeholders (the Commercial Banking channel, Risk, Compliance, Legal) were known from domain knowledge at the outset, not surfaced via referral. Only the development team was surfaced by a manager. The original draft flattened all discovery into a generic referral chain, which understated existing domain expertise.
3. **Scope boundary of the artifact itself.** The friction between the Commercial Banking channel and the Card Products team, and the end-to-end online application programme it concerned, belonged to a separate initiative owned by a different delivery group and surfaced well after this project's start. It does not belong in this project's stakeholder map or RACI, and folding it in would have misrepresented whose project it was.

Added the internal-only-impact flag as a standing category, not a one-off note, since several past initiatives involved stakeholders affected by a workflow change the customer never sees.

## Lessons Learned

- Referral is only one of several legitimate discovery sources. Domain knowledge accumulated over a career is a real, separate source, and flattening it into "someone told me" understates existing expertise.
- A stakeholder pushing for a role or scope they don't formally hold should never get their RACI role upgraded to match the ask. The ask belongs in Open Items, not the RACI itself.
- Two parties both marked Accountable on the same line is not automatically a tie between equals. It can also be one confirmed owner already in motion and one stakeholder attempting to buy into scope late, which calls for a different response (accept or decline the ask) than a genuine standoff (escalate to a tie-breaker).
- Observed or secondhand information (a conversation watched but not formally part of) must be labeled with a different confidence level than confirmed fact (funding secured, approval exercised), even when the read feels obvious in hindsight.
- A related initiative's stakeholders and disputes, even when directly caused by or connected to this project, do not belong inside this project's own stakeholder map if they belong to a different owner, team, or ART. Keeping that boundary honest matters more than making the map look comprehensive.
- A stakeholder can be legitimately affected by a workflow change that the customer never sees at all. This is common enough in back-office and infrastructure work that it deserves its own explicit flag, rather than being left implicit and under-communicated.
- Documenting known stakeholders and surfacing unknown ones are two different problems, and a prompt that only does the first hasn't solved the harder half. A role-based standing checklist, built from real experience rather than inferred by Claude, survives staff turnover in a way that asking any one person, manager included, does not.

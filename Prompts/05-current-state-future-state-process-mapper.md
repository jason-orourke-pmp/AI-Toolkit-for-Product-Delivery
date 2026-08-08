> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 05: Current State to Future State Process Mapper

**Stage in JOR AI Product Delivery Framework:** Map

**Job to be done:** Decompose a process into every real step and decision point per actor, pin the actual technical trigger behind the current-state problem, and test a proposed future state against whether its ideal integration target is actually stable before committing to it.

---

## Purpose

Maps a process from current state to future state using real operational decomposition (procedure documentation plus direct validation with the people doing the work), not a generic swimlane template. Tests every future-state design against whether its ideal integration target is actually stable, since designing toward a system that is being replaced or is otherwise uncertain produces a future state that's obsolete before it ships. Calibrates how much trade-off justification gets spelled out based on whether the audience already shares the context. Refuses to compress a real step-by-step decomposition into a small illustrative count for the sake of a tidy-looking output.

## Prompt (v1.0)

```
You are helping map a process from current state to future state, based 
on real operational detail, not a generic swimlane template.

INPUTS I WILL PROVIDE:
- Existing documented procedures for each party/actor in the process 
  (e.g., a submitting side and a receiving side)
- Notes or context from direct conversations with the people doing the 
  work, if available
- Technical/platform team input on system constraints and integration 
  options
- Known future-state uncertainty (a system being replaced, a cost or 
  prioritization constraint, a separate initiative the future state 
  needs to remain compatible with)

STEP 1 - DECOMPOSE CURRENT STATE
For each actor/party in the process, break the documented procedure into 
every discrete step it actually contains, and classify each step as 
either a Decision Point (a branch, a judgment call, an approval) or a 
Task (a mechanical action with no branching). Do this separately for 
each party in the process (e.g., the submitting side and the receiving 
side), since combining them into one flow too early hides where the 
actual handoff and its failure points sit.

Do not compress the decomposition to a small illustrative number of 
steps for readability. A process with 100+ discrete data points or 
actions should be decomposed to that actual granularity, not summarized 
down to a handful of representative steps. If the full step-by-step 
detail hasn't been provided yet, ask for it rather than estimating or 
inventing a plausible-sounding count.

STEP 2 - VALIDATE AGAINST ACTUAL PRACTICE
Documented procedure and actual practice often diverge. Ask me whether 
the current-state map was built purely from existing documentation, or 
validated through direct conversation with the people doing the work. If 
validated directly, ask whether anything surfaced that contradicted the 
documented procedure. For any discrepancy found, ask whether it actually 
affects the design decision at hand (a step described differently than 
practiced, in a way the future-state design would need to account for) 
or whether it's incidental drift (an antiquated step nobody follows 
anymore, a documentation gap unrelated to what's being redesigned). Flag 
only the former as something needing reconciliation before the map is 
finalized; note the latter as an observation, not a blocker.

STEP 3 - IDENTIFY THE TECHNICAL ROOT CAUSE
Work with what I tell you from the technical/platform team to identify 
the specific mechanical trigger or constraint causing the current-state 
inefficiency (e.g., "a faxed form is what triggers the next step," not 
just "the process is manual"). Keep this at the level of the actual 
technical handoff, not a vague description of the problem.

STEP 4 - TEST FUTURE STATE AGAINST SYSTEM STABILITY
Before designing the future state, ask me: is the system the future 
state would ideally integrate with itself stable, or is it being 
replaced, sunset, or otherwise uncertain? If the ideal integration target 
is unstable, do not design the future state as if it were solid ground. 
Instead, favor a decoupled or interim design that solves the immediate 
inefficiency without hard-coupling to a system whose future is uncertain.

STEP 5 - STATE THE TRADE-OFF, CALIBRATED TO AUDIENCE
When the future-state design is a deliberate compromise (an interim 
solution favored over the ideal architecture because of cost, timeline, 
or system uncertainty), ask me whether the relevant stakeholders already 
share the context for why (e.g., they already know the target system 
can't be integrated with, or is being replaced). If so, the trade-off 
does not need to be spelled out as a separate justification for them; 
stating the resulting design decision plainly is enough. Reserve the 
fuller explicit trade-off statement (what the ideal would have been, why 
it wasn't chosen, what would change) for audiences who don't already 
share that context, such as a future business case, a new team member, 
or a downstream team inheriting the design. Do not assume every audience 
needs the full justification restated; ask which audience this output is 
for before deciding how much of the trade-off reasoning to spell out.

STEP 6 - DESIGN FOR FORWARD COMPATIBILITY
Where the future state is intentionally decoupled from an uncertain 
system, describe how the interim solution is expected to plug into 
whatever system or initiative comes next, based on what I tell you about 
known future direction. Do not invent a specific future system if I 
haven't described one; state the forward-compatibility intent generally 
if specifics aren't yet known.

STEP 7 - PRODUCE THE MAP
Output: a current-state map per actor listing every actual step and 
decision point (not a compressed count), the identified technical root 
cause, the future-state design, the trade-off statement calibrated to 
audience, and the forward-compatibility rationale. If the step count is 
large, organize it into logical sub-groups (e.g., by form section or 
process phase) for readability, but do not reduce the actual number of 
steps captured. If the full step-by-step detail hasn't been provided, 
say so explicitly and ask for it rather than filling the gap with an 
estimate.
```

## Sample Input

**Current state, submitting side (frontline):** a documented step-by-step procedure exists and was validated through direct conversation with frontline staff. The full breakdown lives in internal source documentation and is not reproduced here; at a high level, it covers determining the card product, confirming ownership structure, completing a customer-signed PDF application (spanning several dozen individual data points), and faxing the completed application to central processing. Documentation held up in conversation; discussion mainly added detail rather than surfacing contradictions.

**Current state, receiving side (Operations):** same approach, procedure documented and validated with the Operations team. A couple of discrepancies surfaced ("we don't do that anymore"), tied to antiquated or undocumented steps unrelated to the form-to-platform sequence being redesigned.

**Technical root cause:** identified with the Platform (development) team, who determined the API calls and system-to-system communication needed. Root cause: card creation is triggered by a faxed, customer-signed form reaching Operations for manual re-key into the card platform.

**System stability check:** the ideal future state would integrate directly into the existing adjudication system. In this scenario that system has no committed long-term future, and integration would have been costly and difficult to prioritize even otherwise.

**Future-state design:** a smartform replacing the fax as the automation trigger, designed to be adjudication-system-agnostic so it could plug into whichever system exists later, or into the future end-to-end platform.

**Trade-off documentation:** understood directly by the person mapping this and the Platform team. The Card Products team already knew integration with the existing platform wasn't viable, so there was no need to spell out the full justification to them, only to state that the trigger would be smartform-based.

## Claude Output

**Step 1, Current-State Decomposition.** The frontline procedure spans several dozen individual data points across the application form, plus at least one confirmed decision point (ownership structure). The full step-by-step breakdown was not provided in this input, only a high-level summary. Per this prompt's own rule, I am not going to compress or estimate that decomposition into a small illustrative list. **To produce an actual current-state map, I need the real source documentation for both the frontline procedure and the Operations receiving procedure.** Once provided, each discrete field, task, and decision point will be captured at its real granularity, organized into logical sub-groups (e.g., by application form section) for readability, without reducing the actual count.

**Step 2, Validation.** Both sides were validated through direct conversation with the people doing the work, not documentation alone. Frontline documentation held up fully. Operations documentation surfaced a couple of discrepancies, correctly classified as incidental drift rather than something requiring reconciliation, since neither affects the form-to-platform re-key sequence being redesigned.

**Step 3, Technical Root Cause.** The mechanical trigger for card creation is a faxed, customer-signed form reaching Operations, manually re-keyed into the card platform. This is the specific handoff being redesigned, correctly stated at the level of the actual technical trigger rather than a general "the process is manual" description.

**Step 4, System Stability Check.** The ideal future state, direct integration into the existing adjudication system, was tested against stability and failed it: the system has no committed long-term future in this scenario, and integration would have carried significant cost and prioritization difficulty regardless. The future-state design correctly avoided treating that system as solid ground.

**Step 5, Trade-off Statement, Calibrated to Audience.** For the Card Products team and the Platform team, who already understood the existing system couldn't be integrated with, no separate trade-off justification was needed; stating the resulting design decision (smartform-triggered automation) was sufficient. The fuller version, for an audience that doesn't already share that context, is preserved here: the ideal would have been direct adjudication-system integration; it wasn't chosen because that system has no committed long-term future in this scenario, alongside cost and prioritization difficulty; it would become viable again only with a stable, funded target system to integrate with.

**Step 6, Forward Compatibility.** The smartform is designed as adjudication-system-agnostic, able to plug into whichever system replaces the current one, or into the future end-to-end application platform, without requiring the automation to be rebuilt around a specific system.

**Step 7, Map Output.**
- Current state (Frontline): full decomposition pending real source documentation; known scope is several dozen data points plus at least one confirmed decision point (ownership structure)
- Current state (Operations): full decomposition pending real source documentation; two incidental discrepancies noted, neither affecting the redesign
- Technical root cause: fax-triggered manual re-key into the card platform
- Future state: smartform-triggered automation, adjudication-system-agnostic
- Trade-off (full version, for audiences needing it): ideal integration rejected due to the target system's uncertain future and cost/prioritization difficulty; smartform chosen as decoupled interim solution
- Forward compatibility: designed to integrate with a future adjudication system or the broader end-to-end platform, whichever materializes

## Jason's Edited Version

The first draft compressed the frontline and Operations decomposition to "4 steps, 1 decision point" for a tidy-looking sample output. That was fabricated detail, invented for readability rather than reflecting the real process, which spans several dozen data points. Corrected by adding an explicit rule against compressing or estimating step counts, and by having the output ask for the real source documentation rather than inventing a plausible-sounding number when the full breakdown isn't available.

## Lessons Learned

- A future-state design built toward an "ideal" integration target is worthless if that target system's own future is unstable. Testing system stability before designing the future state, not after, avoids building toward ground that won't be there.
- Not every trade-off needs to be spelled out to every audience. Stakeholders who already share the relevant context (here, that the existing adjudication system couldn't be integrated with) only need the resulting decision stated plainly. The fuller justification is for audiences who don't already have that context, such as a future business case or a new team inheriting the design.
- Documented procedure and actual practice diverge often enough that direct validation is worth doing every time, but not every discrepancy found matters. Distinguishing "this affects the redesign" from "this is incidental drift nobody reconciled" keeps the map focused on what's actually relevant.
- Compressing a real, granular decomposition into a small illustrative count for a cleaner-looking artifact is its own form of fabrication, even when no one intends it that way. A prompt built to produce accurate deliverables should refuse to estimate a step count and ask for the real detail instead.

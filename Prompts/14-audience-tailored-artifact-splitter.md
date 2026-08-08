> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 14: Audience-Tailored Artifact Splitter

**Stage in JOR AI Product Delivery Framework:** Discover

**Job to be done:** Split a completed business case and/or process map into separate, audience-tailored artifacts, rather than one document trying to serve every stakeholder. Correct the specific real-world failure mode of under-detailing an advisory/compliance audience, which historically caused costly repeat consultation cycles, while giving channel/operational audiences a short, benefit-framed version instead of the full case.

---

## Purpose

Takes a completed business case (per the Business Case Builder) and/or process map (per the Process Mapper) and produces separate artifacts tailored to each stakeholder audience, rather than one deck or document trying to serve everyone. Classifies audiences into three genuinely different types, each requiring a different kind of artifact, not just a shorter or longer version of the same one. Deliberately corrects the real historical pattern of under-detailing advisory/compliance audiences (Legal, Compliance), since trimming detail for that audience previously caused repeat consultation cycles that cost as much time as the original wait.

## Prompt (v1.0)

```
You are helping split a completed business case and/or process map into 
separate, audience-tailored artifacts, since one document trying to 
serve every stakeholder either overwhelms some audiences or 
under-informs others.

INPUTS I WILL PROVIDE:
- The completed business case (per the Business Case Builder) and/or 
  process map (per the Process Mapper)
- The stakeholder groups needing their own version, using the RACI/
  stakeholder map (per the Stakeholder Alignment Builder) as the source 
  of who's actually involved
- For each stakeholder group, which of three audience types they fall 
  into (see Step 1)

STEP 1 - CLASSIFY AUDIENCE TYPE
Sort each stakeholder group into one of three types, since each requires 
a fundamentally different artifact, not just a shorter or longer version 
of the same one:
  a) CHANNEL/OPERATIONAL — groups whose day-to-day work changes as a 
     result of this initiative (e.g., a distribution channel, a 
     frontline team). They need to know what changes for them 
     specifically: current state vs. future state in their own terms, 
     and the measurable benefit framed around their own experience 
     (less rework, fewer rejections, reduced friction), not the full 
     business case.
  b) TECHNICAL/DELIVERY — groups who need the full mapping detail to 
     assess feasibility and design a solution (e.g., a development or 
     platform team). If a process map (per the Process Mapper) already 
     exists, this audience's artifact IS that map; do not create a 
     separate, thinner version for them. Note explicitly what will 
     remain a verbal, exploratory conversation (open feasibility 
     questions, design brainstorming) rather than trying to force 
     everything into a written document.
  c) ADVISORY/COMPLIANCE — groups whose job is to find gaps and raise 
     questions before signing off (e.g., Legal, Compliance, Risk). See 
     Step 3; this audience gets different treatment than the other two.

STEP 2 - BUILD THE CHANNEL/OPERATIONAL ARTIFACT
For each channel/operational audience, produce a short artifact with: 
what they currently do, what changes (in their own workflow terms, not 
system/technical terms), and the measurable benefit that matters to 
them specifically. Do not include the business case's full financial 
justification, dependency analysis, or technical architecture; this 
audience needs the "what changes for you and why it's worth it" version, 
not the executive case.

STEP 3 - BUILD THE ADVISORY/COMPLIANCE ARTIFACT WITH DELIBERATE 
OVER-ANTICIPATION
This is the audience most likely to be under-served by a minimal 
document, since their function is specifically to probe for what's 
missing. Do not apply the same "include only what's necessary" instinct 
used for other audiences. Instead:
  - Include the full current-state and future-state detail relevant to 
    their function (e.g., data handling, audit trail, control points), 
    not a summary
  - State the "why" behind the ask explicitly, not just the "what"
  - Proactively list the categories of question this audience is likely 
    to ask, based on their function (e.g., for Compliance: data 
    retention, consent, audit trail; for Legal: contractual/liability 
    exposure), and answer what's answerable now, flagging clearly what 
    isn't yet. Generate these categories from what the function 
    typically cares about, even if some categories turn out not to apply 
    to this particular initiative; the goal is to prompt broader thinking 
    about what should be asked, not to limit the list to questions 
    already known to be relevant.
  - State this explicitly: the cost of under-scoping this document is 
    not just a longer read, it's a repeat consultation cycle, which per 
    past experience can cost as much time as the original wait. 
    Erring toward more detail here is cheaper than erring toward less.

STEP 4 - DO NOT DEFAULT TO TRIMMING
Across all three audience types, do not apply a single "keep it short" 
instinct uniformly. Channel/operational audiences genuinely benefit from 
brevity and plain framing. Advisory/compliance audiences do not; for 
them, brevity that omits anticipated questions is a false economy. Ask 
me explicitly which audience type applies before deciding how much 
detail to include, rather than assuming shorter is always better.

STEP 5 - WORST-PRACTICE CHECK
Flag any of: giving a channel/operational audience the full business 
case instead of a "what changes for you" version, creating a separate 
thinner document for a technical/delivery audience when the process map 
already serves that purpose, applying the same brevity standard to an 
advisory/compliance audience that would be appropriate for a channel 
audience, and failing to proactively anticipate likely compliance/legal 
questions before the document goes out.
```

## Sample Input

**Source artifacts:** completed business case and process map for the commercial card automation initiative (the single-owner smartform automation).

**Stakeholder groups needing tailored versions, per the RACI:**
- The Commercial Banking channel, the branch channel, the contact centre channel — channel/operational
- Development/Platform team — technical/delivery
- Legal, Compliance — advisory/compliance

**Known history:** Development/Platform received a structured process-mapping document plus ongoing verbal detail; this worked well. Legal and Compliance received a document covering current/future state and the rationale, but it was under-detailed; they came back with questions requiring follow-up sessions, each of which cost roughly 1-2 weeks to schedule.

## Claude Output

**Step 1, Audience Classification.**
- The Commercial Banking channel, the branch channel, the contact centre channel: Channel/Operational.
- Development/Platform: Technical/Delivery.
- Legal, Compliance: Advisory/Compliance.

**Step 2, Channel/Operational Artifact.**
*What changes for you:* Today, a commercial card application is completed on paper, signed, and faxed to a central processing team for manual entry, taking up to 20 business days (illustrative) to reach the customer. Going forward, for single-owner businesses, the same application will be submitted through a smartform instead of a fax. What this means for you: fewer rejected or incomplete submissions, less time spent on rework when something comes back incomplete, and a faster path to card delivery for your customer. Multi-owner and more complex ownership structures continue through the existing process for now.

**Step 3, Advisory/Compliance Artifact.**
Current state: [full detail from the process map, including the fax-based intake and manual the card platform re-key]. Future state: [full detail, including the smartform design and what data it captures]. Why this change: retention-driven, closing the time-to-card gap between business and retail cards; the automation also serves as a foundation for a separate future initiative. Anticipated questions, addressed proactively:
- *Compliance:* How is signed documentation for KYC/compliance purposes handled if the form itself is digital? [Answer: collected and filed separately from the automated card-creation step, not part of this step's validation.] What audit trail exists for the smartform submission itself? [Flag: not yet fully specified, open item.] What is the data retention period for smartform submissions versus the current faxed documents? [Flag: not yet specified, open item, included here specifically because it's a category Compliance typically asks about, even though it wasn't raised in the original consultation.]
- *Legal:* Does this change any consent or disclosure language the customer sees? [Answer or flag as open, based on actual case detail.] Does liability shift in any way for a smartform-originated application versus a faxed one? [Flag as open if not yet addressed.] Are there any jurisdiction-specific considerations for digital signature or consent capture? [Flag as open; included as a standard Legal category even though it may not apply here.]
This document deliberately includes more anticipated detail than the minimum needed to describe the change, since under-scoping this audience previously required follow-up sessions costing 1-2 weeks of scheduling lead time each.

**Step 4, No Uniform Trimming.** The channel/operational artifact above is intentionally short and benefit-framed. The advisory/compliance artifact above is intentionally longer and anticipatory, including categories of question that may not end up being relevant to this specific initiative but are included to prompt broader thinking. Both are correct for their audience; neither should be edited toward the other's length as a default instinct.

**Step 5, Worst-Practice Check.** Channel audiences did not receive the full business case. Development/Platform was not given a separate thinner document; the existing process map is confirmed as their artifact. The advisory/compliance document was built with deliberate over-anticipation rather than trimmed to a same-length standard as the other two, including plausible question categories beyond what was strictly known to be relevant.

## Jason's Edited Version

No material corrections to the Claude output. The core finding, that Legal and Compliance specifically were under-served by a minimal document while every other audience was appropriately scoped, matched real experience directly. Confirmed that the anticipated-questions approach should generate plausible categories based on the function generally, not just questions previously asked, since the value is in prompting broader thinking about what should be raised, even when some generated categories turn out not to apply.

## Lessons Learned

- Splitting one document into audience-specific versions is not the same task for every audience. A channel/operational audience benefits from a shorter, benefit-framed version. An advisory/compliance audience needs the opposite instinct: more anticipated detail than feels minimally necessary, because their function is specifically to probe for gaps.
- The real historical failure here wasn't over-inclusion anywhere. Small, deliberately scoped meetings meant most audiences got appropriately trimmed information. The one place trimming caused a real cost was Legal and Compliance, where under-detailing led directly to repeat consultation cycles, each carrying a real scheduling cost (per prompt 11).
- A technical/delivery audience doesn't always need its own separate written artifact. When a process map already exists at the right level of detail, that map is the artifact; building a second, thinner version for the same audience adds redundant work without adding value.
- Generating plausible categories of likely question, even ones that may not end up applying to a specific initiative, has real brainstorming value. The goal isn't a perfectly scoped list of only-relevant questions; it's prompting the builder to think through categories they might not have considered on their own.

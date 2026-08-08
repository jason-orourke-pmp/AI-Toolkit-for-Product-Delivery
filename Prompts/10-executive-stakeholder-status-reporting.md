> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 10: Executive/Stakeholder Status Reporting

**Stage in JOR AI Product Delivery Framework:** Deliver

**Job to be done:** Take one underlying project status and produce audience-calibrated versions for different stakeholders (AVP: frequent, spoken, brief; VP: infrequent, high-altitude; peer POD: FYI; distribution channels: business-impact framing), without hiding or softening routine blockers, but without over-explaining them either.

**Organizational context this prompt assumes:** A layered reporting structure of the kind common in larger delivery organizations. Direct leadership receives brief, frequent, spoken updates in a shared forum where each initiative gets a minute or less of airtime. Senior leadership receives infrequent, higher-altitude updates. Peer product teams are often already covered by the shared reporting structure rather than by separate outreach, so a distinct "peer FYI" version is mainly useful for genuinely separate peers outside that structure. Distribution channels receive periodic, business-impact-focused updates rather than delivery-detail ones.

---

## Prompt (v1.1)

```
You are acting as an experienced Product Owner in a regulated financial
services environment (banking/fintech), preparing a status update on a
delivery initiative for multiple audiences. I will give you the current
project state (progress, blockers, upcoming work). Your job is to
produce audience-calibrated versions of the same underlying status — not
one generic update repeated verbatim.

Default tone: state blockers plainly and factually (e.g., "waiting on
Legal," "waiting on Compliance"). Do NOT soften, hide, or over-explain a
routine wait on a small advisory team (e.g., a 1-2 week turnaround from
Legal/Compliance) as if it were a crisis — this is normal and expected in
this environment. Reserve escalation language only for genuinely
abnormal delays beyond what I indicate is typical.

Produce FOUR versions of the update, calibrated as follows:

1. AVP / DIRECT LEADERSHIP VERSION (frequent cadence — e.g., weekly/
   biweekly "scrum of scrum" style update)
   This version must work as a SPOKEN update, not a written report —
   assume roughly 10-15 seconds of airtime in a meeting where the
   Product Owner may be reporting on several other projects in the same
   session. Keep it to 2-3 short sentences maximum: current state, any
   blocker (named plainly), and overall status. Do NOT include workforce/
   staffing-impact information here — that follows a separate, more
   sensitive communication path (see note below).

2. VP / SENIOR LEADERSHIP VERSION (infrequent cadence — e.g., quarterly)
   Higher altitude. Focus on overall progress against the roadmap/
   timeline, material risks, and any decision or support needed from this
   level. Omit routine operational detail unless it represents a material
   risk to the timeline or requires their intervention.

3. PEER / POD FYI VERSION (informational only, no shared dependencies)
   Brief. A short, factual summary suitable for peers who do not depend
   on this work and cannot act on blockers, but benefit from situational
   awareness. Note: if peer Product Owners for adjacent products already
   receive this information through the shared reporting structure
   (common AVP/VP), a distinct version may be unnecessary — only produce
   this if there's a genuinely separate audience not covered that way.

4. DISTRIBUTION CHANNEL / BUSINESS LINE VERSION (e.g., monthly, to the
   channels that submit or service the work)
   Business-impact framing, not internal process detail. Go beyond
   generic "we're improving this for you" language — specifically
   address what changes for THEM: reduced rework, fewer failed
   handoffs, faster and simpler submission. If a high-effort process is
   measurably slowing the channel down, name that plainly rather than
   describing only the future improvement.

For each version, keep length appropriate to the audience.

SEPARATE NOTE ON ORGANIZATIONAL IMPACT: If an initiative changes how a
team's work is structured, do not fold that into the four standard
versions above. It typically warrants its own communication, on its own
timing and to its own audience, rather than being handled inside a
routine status update.

Here is the current project state:
"{{PROJECT_STATE}}"
```

---

## Sample Input

> Project: Commercial card creation automation at Northvale Financial (fictional scenario). Discovery and process mapping (Epics 1-2) complete. Compliance/Legal advisory consultation (ongoing) currently focused on audit trail requirements, normal pace. Technical feasibility (Epic 4) has started in parallel. No material risks beyond the routine advisory wait. Target: MVP1 (single-owner businesses only) still expected within the original timeline. Channel context: commercial card applications involve more documentation and system steps than retail applications, so submissions take the channel noticeably longer to complete and are more prone to rework when a field is missing or a transmitted form is unreadable.

---

## Claude Output (v1.1)

**1. AVP / Direct Leadership Version** *(spoken, ~10-15 seconds)*
Discovery and process mapping are complete. We're in ongoing compliance/legal consultation on audit trail requirements, normal pace, no concerns. Feasibility work has already started in parallel, so MVP1 is still on track for the original timeline.

**2. VP / Senior Leadership Version**
The commercial card automation initiative remains on track for its original MVP1 timeline. Discovery and current-state mapping are complete, and compliance/legal consultation is progressing normally as an ongoing part of the initiative. No material risks or decisions needed from your level at this time.

**3. Peer / POD FYI Version**
*(Not separately needed here. Adjacent product teams already receive this information through the shared reporting structure, so a distinct FYI version would be redundant.)*

**4. Distribution Channel / Business Line Version**
We know the commercial card application process asks a lot of your team today. Documentation requirements and system steps go well beyond a retail application, and completing one takes real time. We're working to fix that: the goal is a simpler, faster submission process with far less risk of rework from something like an unreadable transmitted form or a missing field. We don't have a firm launch date yet, but we're on track with our original plan, and we'll keep you posted as we get closer to a pilot. No action needed from your side right now.

---

## Jason's Edited Version

**On the distribution channel version:** This version needed to say more than the first draft did. What a submitting channel actually wants to hear about is accurate information capture, no transmission or image problems, and no rework loops. Naming the current friction plainly matters, because a message that only describes a future improvement reads as vague reassurance. The correction was to state the present-day cost to the channel first, then the fix.

**On organizational impact and the leadership version:** Correct to keep this out of the routine leadership update. It is not a status-update topic. Where an initiative changes how a team's work is structured, that belongs in the business case and in its own separate communication, on its own timing.

**On the peer/POD audience:** Adjacent product teams are often already in the loop through the shared reporting structure rather than through a separate update, which is why a distinct FYI version was unnecessary here. The processing team, however, should still be recognized as a genuine stakeholder, since their work changes materially even though their communication path differs from the routine reporting cadence.

---

## Lessons Learned

- A "business-impact" message to a distribution channel isn't complete if it only describes the future improvement. It has to name the current cost to that audience plainly first, or it reads as generic reassurance and gets ignored.
- Organizational-impact communication follows a fundamentally different path than routine status reporting: different audience, different timing, different sensitivity. It shouldn't be forced into the same four-audience structure as a routine update.
- Not every "adjacent" stakeholder needs a separately generated update. Sometimes the reporting structure itself already covers that audience, and producing a redundant version adds noise rather than value.

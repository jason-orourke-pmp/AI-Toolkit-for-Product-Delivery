> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 12: Change Management / Rollout Readiness Builder

**Stage in JOR AI Product Delivery Framework:** Deliver

**Job to be done:** Build a rollout readiness and change management plan. Identify when a change structurally requires an all-at-once rollout instead of a phased pilot, and build risk-specific post-launch monitoring with a real metric, a stepped-down cadence, thresholds calibrated to historical data, and a defined handoff back to standard operations.

---

## Purpose

Builds a change management and rollout readiness plan for a policy, procedure, or system change affecting multiple channels or teams. Correctly identifies when a change structurally requires an all-at-once rollout rather than a phased pilot, rather than defaulting to piloting as a universal best practice. Treats post-launch monitoring as a real, time-bound plan with a specific risk-tied metric, calibrated thresholds, named escalation authority, and a defined handoff back to standard operations, not a vague "track performance after launch" instruction.

## Prompt (v1.0)

```
You are helping build a change management and rollout readiness plan for 
a policy, procedure, or system change affecting multiple channels or 
teams.

INPUTS I WILL PROVIDE:
- The change itself, in plain terms
- Which channels/teams need to operate differently once it launches
- Whether this is a policy/procedure change or a system change
- What change management support exists per channel, if any
- The specific risk this change touches, if one exists (fraud, 
  compliance, customer harm, financial exposure)

STEP 1 - CLASSIFY THE CHANGE TYPE AND ROLLOUT SHAPE
Ask whether this is a policy/procedure change or a system change. If 
policy/procedure, and the change requires uniform application across all 
channels (the same rule can't apply in one channel and not another 
without creating an inconsistency or a loophole), state plainly that a 
phased pilot is not viable and an all-at-once rollout is required. Do 
not default to recommending a pilot group as a best practice without 
first checking whether the change type actually allows one.

STEP 2 - MAP CHANNELS AND OWNERSHIP
For each channel or team affected, identify: what specifically needs to 
change (procedure pages, scripts, job aids), and who provides change 
management support for that channel (drafting comms, scheduling sessions 
with the right groups, access to leadership). Ask me to distinguish 
between my own role (subject matter expert facilitating sessions, 
answering questions) and each channel's dedicated change management 
function, since channels often have different change management 
processes and it should not be assumed one model fits all of them.

STEP 3 - BUILD THE COMMUNICATION AND READINESS PLAN
Based on Step 1's rollout shape, build the plan: what communications go 
out, to whom, and when; whether live sessions or Q&A are held; what 
procedure or job aid updates are required per channel. State explicitly 
whether this goes out all at once or in phases, and why, tying back to 
the Step 1 classification.

STEP 4 - BUILD THE RISK-SPECIFIC MONITORING PLAN
If the change touches a specific risk (ask if unclear rather than 
assuming none exists), do not describe monitoring generically as "track 
performance after launch." Build it with:
  - The specific metric being tracked, tied directly to the risk (e.g., 
    fraud rate attributable to the specific change, not general fraud 
    rates)
  - A defined heightened-watch period with its own cadence (e.g., 
    weekly for an initial period, then monthly for a following period)
  - Named thresholds (e.g., green/yellow/red) calibrated against actual 
    historical data for the relevant population (e.g., existing fraud 
    rates for the account type in question), not arbitrary round 
    numbers. Ask me for the real tolerance levels if known; do not 
    invent plausible-sounding percentages if they are not provided.
  - A named escalation point at each threshold and the actual decisions 
    available to them (continue monitoring, re-educate frontline, halt 
    the change), not just "escalate to management" without specifying 
    what management can actually do

STEP 5 - DEFINE THE TRANSITION BACK TO STANDARD MONITORING
State explicitly when the heightened-watch period ends and what happens 
after: does monitoring revert to standard/business-as-usual cadence, and 
where does accountability sit once it does (e.g., individual channels or 
business units become accountable for adherence to procedure going 
forward, rather than the initiative owner continuing to track it 
indefinitely). A monitoring plan without a defined end point and a clear 
answer to "then whose job is it" is incomplete.

STEP 6 - WORST-PRACTICE CHECK
Flag any of: recommending a phased pilot for a change that structurally 
requires uniform application, treating all channels as if they share one 
change management process, describing post-launch monitoring without a 
risk-specific metric or a defined cadence, inventing threshold numbers 
instead of asking for real historical tolerance levels, naming an 
escalation step without stating what the escalation point can actually 
decide, and leaving the monitoring period open-ended with no defined 
handoff to standard operations.
```

## Sample Input

**The change (fictional scenario):** an updated delivery-address policy that permits a previously prohibited address type, where the original prohibition existed for fraud-risk reasons. Requires updates to many procedure pages across channels that explicitly instruct against it.

**Channels affected:** Retail frontline, phone channel, the Commercial Banking channel, Operations.

**Change type:** policy/procedure change. Uniform application required across all channels since inconsistent application (one channel allowed, another not) would create both confusion and a loophole. Phased pilot not viable for this reason, not for lack of consideration.

**Change management support:** varied per channel. Each channel had a different change management process; per-channel support handled drafting comms and scheduling access to the right groups. Direct facilitation and Q&A at sessions was handled personally, across all channels.

**Risk touched:** fraud, specifically tied to loosening a previously fraud-motivated restriction.

**Monitoring plan, as designed in this example:** weekly fraud tracking for the first 3 months, monthly for the following 3 months, covering a 6-month heightened-watch period. Thresholds are set against a baseline rate rather than picked arbitrarily. Using illustrative figures for this example: a green band at or below the existing baseline, a yellow band at roughly double it, and a red band above that. Yellow or red triggers senior management involvement, who determine next steps: continue monitoring, re-educate frontline, or reverse the policy change. After the 6-month period, monitoring reverts to standard ongoing practice, with individual channels accountable for their own results if procedure isn't followed.

## Claude Output

**Step 1, Change Classification.** Policy/procedure change requiring uniform application across all channels. A rule permitting restricted-address delivery in one channel and prohibiting it in another would create both an inconsistent customer experience and an exploitable gap. Phased pilot correctly ruled out as structurally unviable for this change type, not simply skipped.

**Step 2, Channel Mapping.**

| Channel | What Changes | Change Management Support |
|---|---|---|
| Retail Frontline | Procedure pages removing restricted-address prohibition | Channel-specific change management team drafted comms, scheduled sessions |
| Phone Channel | Same | Channel-specific change management team |
| The Commercial Banking channel | Same | Channel-specific change management team |
| Operations | Same | Channel-specific change management team |

Direct facilitation and Q&A across all four channels handled personally, distinct from each channel's own change management support function, which handled comms drafting and scheduling rather than delivery.

**Step 3, Communication and Readiness Plan.** All-at-once rollout across all four channels, consistent with Step 1's classification. Communications issued to each channel, followed by live sessions with Q&A to address questions directly. Procedure pages updated across all affected channels concurrently, not staggered.

**Step 4, Risk-Specific Monitoring Plan.**
- Metric: fraud incidence directly attributable to restricted-address delivery, not general fraud rates.
- Cadence: weekly tracking for the first 3 months, monthly tracking for the following 3 months, a defined 6-month heightened-watch period.
- Thresholds, calibrated against a measured baseline rate rather than arbitrary numbers: a green band at or below the baseline, a yellow band at roughly double it, and a red band above that (illustrative bands for this example).
- Escalation: yellow or red triggers senior management involvement. Senior management's actual available decisions are named: continue monitoring, re-educate frontline, or shut the policy change down. This is not an open-ended "escalate and see" step.

**Step 5, Transition to Standard Monitoring.** The 6-month heightened-watch period has a defined end point. After it, fraud monitoring reverts to standard, ongoing practice. Accountability shifts explicitly: individual businesses or channels own their own results if fraud occurs due to procedure not being followed, rather than the initiative owner continuing to track this specific change indefinitely.

**Step 6, Worst-Practice Check.** No phased pilot recommended where one wasn't viable. Channels correctly treated as having distinct change management processes rather than one shared model. Monitoring plan carries a specific metric, a defined cadence, and thresholds calibrated against real historical data rather than invented round numbers. Escalation authority's actual decision options are stated. The monitoring period has a defined end and an explicit accountability handoff after it.

## Jason's Edited Version

No material corrections to the Claude output. The structural classifications (policy/procedure vs. system, uniform vs. phased) held up cleanly against the real case. The key insight captured in this prompt that was missing in practice: post-launch monitoring had a real mechanism (the fraud thresholds and escalation ladder) for the fraud risk specifically, but no equivalent mechanism existed for the upside benefits, which is covered separately in prompt 13.

## Lessons Learned

- Not every change benefits from a phased pilot. A policy or procedure change that must apply uniformly across all channels to avoid inconsistency or a loophole structurally rules a pilot out, and a change management prompt should check for this before defaulting to "pilot first" as a universal best practice.
- Channels or business units can each have their own distinct change management process. Treating them as one uniform function, or assuming one person owns readiness across all of them the same way, misses how the actual work gets divided between subject matter expertise (facilitation, Q&A) and each channel's own change management support (comms drafting, scheduling).
- Post-launch monitoring is only as strong as its specificity. A defined metric, a time-bound cadence that steps down over time, thresholds calibrated against real historical data, and named escalation authority with actual decision options turn "we'll keep an eye on it" into something that would actually catch a problem and act on it.
- A monitoring plan needs an explicit end point and a clear statement of where accountability lands afterward. Without that, monitoring either continues indefinitely as the initiative owner's problem, or quietly stops with no one having agreed whose job it becomes.

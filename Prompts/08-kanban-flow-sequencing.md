> **Note on this case study:** The worked example below uses a fictional company, Northvale Financial, and an invented scenario (automating a commercial card application workflow) to demonstrate this prompt. Every figure, system, team, and event in it is illustrative and invented. The scenario is deliberately modeled on the kind of complexity found in regulated financial services delivery work, so that the prompt is tested against a realistic problem rather than a trivial one. It does not describe any real organization, and it is not a record of delivered work.

# Prompt 08: Kanban Flow & Work Sequencing

**Stage in JOR AI Product Delivery Framework:** Prioritize

**Job to be done:** Recommend what to work on next in a Kanban environment where there is no reliable velocity or capacity data, story points are not sized relatively, and prioritization is driven by dependency order and leadership judgment rather than a formal estimation framework.

**Organizational context this prompt assumes:** No dedicated Scrum Master authority to shape team structure or ceremonies. The "team" may be a Kanban pod of independently-owning Product Owners with no shared interdependent delivery work, though they may still share valuable business context (market trends, campaigns, escalation patterns) relevant to a Product Owner whose role extends beyond delivery into broader business representation (e.g., acting as the face of a product line to distribution channels). A separate developer department is negotiated with rather than embedded, and that negotiation itself is a common bottleneck. This includes both getting developers' time to review and understand a proposed initiative before committing to build it, and getting that work prioritized against everything else competing for their capacity.

---

## Prompt (v1.0)

```
You are acting as an experienced Product Owner operating in a Kanban
environment (not Scrum sprints) in a regulated financial services
setting. There is no reliable velocity or throughput data — story points,
if used, are not sized relatively and cannot inform capacity planning.
T-shirt sizing may exist at the Feature level only, not the story level.
The Product Owner works largely alone (no dedicated team with shared
interdependent work), negotiating priority with a separate developer
department, often with leadership input that is judgment-based rather
than criteria-based.

Given a backlog of stories (with their Epic groupings and dependencies),
your job is to recommend a pull order — what should be worked on next —
using the following approach, since velocity-based planning is not
available:

1. DEPENDENCY-DRIVEN SEQUENCING
   Identify what must happen first based on logical/technical dependency
   (not effort estimation), and sequence accordingly. Note that advisory
   consultation (e.g., Legal, Compliance) is often an ongoing thread
   rather than a bounded phase — sequencing it "first" may mean starting
   the conversation early, not completing it before other work begins.

2. RISK-INFORMED PRIORITIZATION
   Flag any story that resolves significant uncertainty early (e.g.,
   confirms technical feasibility, confirms a compliance constraint) as a
   candidate to pull earlier, even if not strictly blocking, since
   resolving unknowns early reduces downstream rework risk.

3. STAKEHOLDER/LEADERSHIP SIGNAL
   If I indicate leadership has expressed a preference or priority signal
   that isn't purely dependency-driven, incorporate it, but note clearly
   when a sequencing choice is being driven by leadership preference
   rather than dependency or risk logic, so the reasoning is transparent
   rather than presented as objectively optimal.

4. FLOW HEALTH CHECK
   Identify any signs that stories may sit blocked waiting on an external
   department (e.g., developer department, Compliance) and flag these as
   flow risks to monitor. Be specific about WHY a developer-department
   dependency is a common bottleneck: it typically requires (a) securing
   developer time just to review and understand a proposed initiative
   before any coding begins, and (b) negotiating priority for that work
   against everything else competing for that department's capacity —
   both are separate friction points, not one.

5. CEREMONY VALUE CHECK
   If I describe a recurring ceremony (e.g., standups) as part of the
   process, do not assume it is adding coordination value by default, but
   also do not assume its only possible value is task coordination. Ask
   or note whether the ceremony provides OTHER forms of value even
   without shared interdependent delivery work — for example, shared
   business context, market/campaign intelligence, or escalation
   awareness that is genuinely useful to a Product Owner whose role
   extends beyond pure delivery (e.g., someone who also represents the
   product line to distribution channels, handles escalations, or tracks
   sales trends). Only flag a ceremony as low-value if neither
   coordination value NOR this broader informational value applies.

For the backlog provided, produce:

1. RECOMMENDED PULL ORDER
   Ordered list of stories/tasks with a one-line reason for each
   position (dependency, risk-reduction, or leadership signal — labeled
   explicitly).

2. FLOW RISKS TO MONITOR
   Stories at risk of stalling on external dependencies.

3. PROCESS OBSERVATION (if applicable)
   Any note on ceremonies or process elements, weighing both
   coordination value and broader informational/business value before
   concluding whether they're well-structured for their purpose.

Here is the backlog and context:
"{{BACKLOG_AND_CONTEXT}}"
```

---

## Sample Input

> Backlog: (1) Operations Analyst process-mapping story, (2) Retail Branch Rep intake story, (3) Rewrite acceptance criteria for smartform validation, (4) Duplicate submission handling, (5) Stale pre-populated data handling, (6) Compliance/Legal advisory consultation (ongoing thread, started early), (7) Technical feasibility assessment (Epic 4). Leadership has signaled they want visible progress on the compliance/legal front early, given past scoping history where the project stalled for lack of funding approval.
> Process note: standups run 3x/week; each Product Owner in the pod independently owns a different product with no shared delivery dependencies, but the Product Owner in this case also functions as the face of the product line to distribution channels (handling escalations, presenting campaigns, tracking sales trends), a role that benefits from staying current on what Retail Cards and the Business Cards marketing partner are doing.

---

## Claude Output (v1.0)

**1. Recommended Pull Order**

1. Operations Analyst process-mapping story — *dependency: foundational input for all downstream design and validation work*
2. Retail Branch Rep intake story — *dependency: runs alongside #1, same Epic, no blocking relationship between them*
3. Compliance/Legal advisory consultation (ongoing thread) — *leadership signal + risk-reduction: started early given historical stalling on funding/approval, and because an unfavorable compliance finding could reshape the whole solution; expect this to continue in parallel with later work rather than reaching a single completion point*
4. Technical feasibility assessment (Epic 4) — *dependency: needs input from #1 and directional signals from #3's ongoing consultation, but can start once early direction is available rather than waiting for consultation to formally "finish"*
5. Rewrite acceptance criteria for smartform validation — *dependency: needs feasibility direction from #4 to confirm what's technically validated by the smartform vs. handled elsewhere*
6. Duplicate submission handling — *dependency: refinement of #5, lower urgency*
7. Stale pre-populated data handling — *dependency: refinement of #5, lower urgency*

**2. Flow Risks to Monitor**

- Compliance/Legal consultation (#3) is an ongoing thread with historical funding-related stalling. Monitor closely given leadership's explicit sensitivity to this.
- Technical feasibility (#4) depends on a separate developer department. This is a common two-part bottleneck: first, simply securing developer time to review and understand the proposed initiative before any coding begins; second, negotiating priority for this work against everything else already competing for that department's capacity. Both should be actively managed, not assumed to resolve on their own.

**3. Process Observation**
The 3x/week standups bring together Product Owners who each independently own different products with no shared delivery dependencies, so as pure task coordination, the ceremony has limited value, since no participant can resolve another's delivery blockers. However, this Product Owner's role extends beyond delivery: acting as the face of the product line to distribution channels, handling escalations, and tracking sales trends means staying current on what Retail Cards and the Business Cards marketing partner are doing has real, separate value. This includes shared market intelligence, campaign awareness, and cross-pollination of tactics that support that broader part of the role. The standups likely deliver this second kind of value even without delivering the first, which is worth recognizing rather than dismissing the ceremony outright.

---

## Jason's Edited Version

**On the pull order:** This sequencing works. Legal/Compliance conversations need to be started at some point, and starting them early, while recognizing they're ongoing rather than a single bounded phase, is exactly how I'd approach it.

**On the developer-department flow risk:** This is accurate, and for the two specific reasons captured here. First, it's genuinely hard to even get developers' time just to review and understand what we're trying to do before any coding starts. Second, separately, we need to get our work prioritized against every other initiative competing for their capacity. These are two distinct friction points, not one combined issue, and both need active management.

**On the standup/ceremony observation:** This needed correction, and the revised version is more accurate. While there are no shared delivery dependencies among the Product Owners in the pod, we do gain real shared knowledge: how processes work across products, what's happening with campaigns and marketing. This mattered because I wasn't only delivering change initiatives with Tech. I was also the face of Business Cards to the distribution channels: handling escalations, presenting new campaigns, and speaking to anything helping or hindering card sales, similar to a regional sales manager function. Working with Retail Cards to understand their trends, tactics, and best practices, and with our Business Cards marketing partner to know what national campaigns and targeted offers were happening, was genuinely valuable, just not for the reason a typical Scrum ceremony would be.

---

## Lessons Learned

- Advisory consultation (Legal, Compliance) being "first" in a pull order doesn't mean it finishes before other work starts. It means starting the conversation early, since it runs as an ongoing thread throughout the initiative.
- A developer-department dependency is really two separate bottlenecks, not one: getting their time to review/understand a proposal, and separately negotiating priority against competing demands. Naming both distinctly makes the risk easier to manage.
- Not every low-coordination-value ceremony is actually low-value. The real test is whether it serves a purpose beyond its nominal one. In my case, standups didn't coordinate shared delivery work, but they did support a broader part of my role (business representation to distribution channels, escalation handling, staying current on campaigns) that a narrower "task coordination" lens would have missed entirely.

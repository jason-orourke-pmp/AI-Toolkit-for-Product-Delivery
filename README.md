# AI Toolkit for Product Delivery

A set of reusable AI prompts supporting product and delivery work in regulated, complex environments, designed as the **JOR AI Product Delivery Framework** (JOR = Jason O'Rourke).

## About this repository

I built this toolkit as a self-directed learning and portfolio project while developing AI fluency for product management and delivery roles. Each prompt was designed iteratively: I described how I approach a given task, tested the prompt against a worked scenario, corrected the output where it fell short, and documented what the iteration revealed.

**Important disclosure:** Every worked example in this repository is fictional. They are set at **Northvale Financial**, an invented company, and follow an invented scenario: automating a commercial card application workflow. All figures, systems, teams, timelines, and events in those examples are illustrative and made up. Nothing here describes any real organization's internal processes, data, or decisions, and none of it is a record of delivered work.

The scenario is deliberately built to carry realistic complexity, including advisory and compliance dependencies, competing stakeholders, ownership ambiguity, and scope decisions with real trade-offs. That is the point: a prompt that only works on a trivial example is not worth reusing. The complexity is designed, not borrowed.

## Why this exists

Most job postings for Product Owner/Manager/Delivery roles now mention AI fluency, but they aren't looking for AI engineers. They're looking for people who can identify where AI genuinely helps in product delivery work, direct it effectively, and know when to override it with real judgment. This toolkit is my evidence of that. It goes beyond "I used ChatGPT/Claude" to a documented, repeatable method with visible reasoning at every step.

## The JOR AI Product Delivery Framework

Each prompt below maps to a stage in the product delivery lifecycle.

**Discover → Clarify → Map → Prioritize → Validate → Deliver → Review**

| # | Stage | Prompt | What it does |
| --- | --- | --- | --- |
| 01 | Discover | [Stakeholder Conversation Design Builder](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/01-stakeholder-conversation-design-builder.md) | Decides who belongs in a stakeholder conversation versus who should be approached separately, using a give-or-receive value test. Adds the step of securing a business leader's buy-in before approaching their team directly when no formal project mandate exists. |
| 02 | Discover | [Stakeholder Alignment / RACI Builder](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/02-stakeholder-alignment-raci-builder.md) | Turns informal, referral- and domain-knowledge-based stakeholder discovery into a documented RACI. Distinguishes confirmed decision authority from a late-stage ask backed by leverage, flags stakeholders affected by internal-only impacts invisible to the customer, and runs a completeness check to catch who got missed. |
| 03 | Discover | [Business Case / Executive Presentation Builder](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/03-business-case-executive-presentation-builder.md) | Builds a business case and VP-ready deck from raw Finance and dashboard inputs. Separates verified data from inherited or new assumptions, classifies the case's real justification pattern (visible benefit, foundational/invisible, competitive parity, or strategic dependency), and keeps the sequence of when each pattern became known accurate rather than implied from the outset. |
| 14 | Discover | [Audience-Tailored Artifact Splitter](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/14-audience-tailored-artifact-splitter.md) | Splits a completed business case and/or process map into separate, audience-tailored artifacts instead of one document trying to serve everyone. Gives channel/operational audiences a short, benefit-framed version, treats a technical/delivery audience's process map as its own artifact, and deliberately over-anticipates likely questions for advisory/compliance audiences rather than under-detailing them. |
| 04 | Clarify | [Requirements Clarifier](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/04-requirements-clarifier.md) | Turns a vague stakeholder request into a structured discovery document: business problem, scope boundary, assumptions, open questions, risks, and stakeholders. |
| 05 | Map | [Current State to Future State Process Mapper](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/05-current-state-future-state-process-mapper.md) | Decomposes a process into every real step and decision point per actor, pins the actual technical trigger behind the current-state problem, and tests a proposed future state against whether its ideal integration target is actually stable before committing to it. |
| 06 | Prioritize | [Epic Generator](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/06-epic-generator.md) | Breaks a discovery document into Epics organized by workstream (not solution feature). Distinguishes advisors from actual decision-makers and pre-empts circular approval loops. |
| 07 | Prioritize | [User Story Generator](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/07-user-story-generator.md) | Breaks an Epic into properly-framed User Stories (real stakeholder need, not PO activity) with baked-in acceptance criteria. Separates out PO/delivery tasks that don't belong in story format. |
| 08 | Prioritize | [Kanban Flow & Work Sequencing](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/08-kanban-flow-sequencing.md) | Recommends a pull order for a Kanban backlog with no velocity/capacity data, using dependency order, risk-informed prioritization, and leadership signal. Flags when a ceremony isn't adding coordination value. |
| 09 | Validate | [Edge Case Reviewer](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/09-edge-case-reviewer.md) | Stress-tests a story for missing edge cases. Also checks whether the story itself has gone stale relative to the actual solution design. |
| 10 | Deliver | [Executive/Stakeholder Status Reporting](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/10-executive-stakeholder-status-reporting.md) | Takes one project status and produces audience-calibrated versions for AVP (brief, spoken), VP (high-altitude), peer POD (FYI), and distribution channel (business-impact framing) audiences, without hiding or over-explaining routine blockers. |
| 11 | Deliver | [Risk & Escalation Summary](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/11-risk-escalation-summary.md) | Assesses whether a blocker warrants escalation against a clear threshold, and produces a factual escalation summary and structured risk log entry. |
| 12 | Deliver | [Change Management / Rollout Readiness Builder](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/12-change-management-rollout-readiness.md) | Builds a rollout readiness and change management plan. Identifies when a change structurally requires an all-at-once rollout instead of a phased pilot, and builds risk-specific post-launch monitoring with a real metric, a stepped-down cadence, thresholds calibrated to historical data, and a defined handoff back to standard operations. |
| 15 | Deliver | [Change Request / Issue Log Builder](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/15-change-request-issue-log-builder.md) | Builds a lightweight scope-decision log with version history, not just current state, for initiatives with no formal change-control process. Distinguishes a future vision from the committed increment, identifies whether the real constraint is budget/deadline or negotiated team capacity, and records informal decision authority and its reasoning rather than letting scope become "the new understanding" with no recoverable basis. |
| 13 | Review | [Benefit Realization Tracking Plan Builder](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/13-benefit-realization-tracking-plan-builder.md) | Builds a forward-looking plan for tracking whether a business case's promised benefit actually materialized. Distinguishes benefits with a natural owner from those with none by default, and won't assign a tracking mechanism that isn't real. |
| 16 | Review | [Lessons Learned / Knowledge Capture Builder](https://github.com/jason-orourke-pmp/AI-Toolkit-for-Product-Delivery/blob/main/Prompts/16-lessons-learned-knowledge-capture-builder.md) | Captures recurring organizational knowledge (who to go to, what a team will or won't do, answers to questions that keep getting re-asked) in a form built for discoverability, not just storage. Distinguishes knowledge that decays (routing/contact) from knowledge that's relatively stable (factual/process), and treats capture as a continuous practice, not a one-time project-closure exercise. |

## How each prompt file is structured

Every file in this repo follows the same format.

1. **The prompt itself** — the reusable template, with `{{PLACEHOLDER}}` fields for new inputs
2. **Sample input** — a fictional scenario from the Northvale Financial commercial card automation case study
3. **Claude output** — the AI's response to that input
4. **Jason's edited version** — my own corrections and refinements, in my own voice
5. **Lessons learned** — what the iteration process revealed about the prompt itself

## A note on numbering

File numbers reflect the order prompts were added to the repo, not necessarily their position in the lifecycle. The **Stage** column above is the source of truth for where a prompt actually fits in the workflow. As of file 16, numbering and stage order have diverged in several places (e.g., file 14 is a Discover-stage prompt added after several higher-numbered files). A renumbering pass to bring file order back in line with workflow order may happen once the toolkit's growth slows down, rather than after each individual addition.

## A note on honesty in this toolkit

Several scenarios in this repo are deliberately set in an imperfect delivery environment: no formal risk register, informal estimation, ceremonies that don't always add coordination value, escalation paths that are worked out as they go. That is a design choice, not a complaint about anyone. Most delivery work happens in conditions like these, and a prompt that only holds up inside a textbook process is not much use.

Where a lessons-learned section names a gap, it is describing the fictional scenario's conditions and what a Product Owner should do about them. Recognizing a process gap and knowing how to correct it is a stronger signal of judgment than assuming everything runs by the book.

## About me

Jason O'Rourke, PMP — 17+ years in financial services, with experience across card payments, card acquisition, internal workflow automation, and Agile delivery in regulated environments. Connect with me on LinkedIn at <https://www.linkedin.com/in/jason-orourke-pmp/>.

---
name: spec
description: "Use when the user says /spec or wants to translate their requirements into a technical blueprint — architecture, stack, data flow, and file structure."
---

# /spec — Blueprint Your App

Read `skills/sprint-guide/SKILL.md` for overall behavior, then read `skills/sprint-guide/references/spec-patterns.md` for architecture decision guidance. Follow this command.

You are a technical collaborator. You interview first, propose second. You build the architecture WITH the participant — not for them. They should walk away understanding their app well enough to explain it to someone else.

## Prerequisites

`docs/scope.md` (or `docs/brief.md` for sprint track) and `docs/prd.md` (or the brief) must exist.
`docs/hackathon-brief.md` and `docs/learner-profile.md` must exist.

## Before You Start

- Read everything in `docs/` — every file.
- Read `docs/hackathon-brief.md` carefully: required technologies, allowed platforms, submission format, timeline.
- Read `docs/prd.md` (or brief): note all epic headings and acceptance criteria — the spec must implement these.
- Read `docs/learner-profile.md`: technical experience, known tools, what they want to learn.
- Read `docs/team-profile.md` if it exists: skill sets per team member.
- Append `## /spec` to `process-notes.md`.

## The Core Lesson

A spec detailed enough that any engineer or AI coding agent can build from it without asking questions. This is increasingly how software gets built at speed: sharpen the spec, then delegate the implementation. The spec is the primary artifact — code is downstream of it.

## Flow

### Phase 1 — Mandatory Questions (one at a time)

**Q1. Constraint intake from hackathon brief.**
Before proposing anything, surface hard constraints: "The hackathon requires [required tech/APIs]. Does that affect your stack preferences, or is there flexibility in how you use it?"

If required technologies exist, the stack must accommodate them. Don't propose a stack that ignores mandatory constraints.

**Q2. Participant tech preferences.**
Read from `learner-profile.md` and adapt:
- First-timers: "What have you heard of or tried? Are there any tools you've seen that looked interesting?" Recommend the simplest viable approach.
- Intermediate: "What do you know well? What do you want to stretch into?" Balance comfort and stretch.
- Experienced: "What's your preferred stack? Any strong opinions?" Defer to their choices and focus on tradeoffs.

For teams: "Who on the team is most comfortable with frontend? Backend? Does anyone have experience with [relevant technology]?" Let skill distribution inform the architecture.

**Q3. Research the stack.**
Before proposing anything concrete, use web search to verify:
- Is this library/framework actively maintained?
- What's the current stable version?
- Known issues or recent breaking changes?
- For external APIs: current pricing, rate limits, quickstart docs.

Share findings with the participant. Link to relevant documentation. Do not recommend anything without verifying its current state.

**Q4. Propose architecture.**
Use the decision framework in `spec-patterns.md` to reason through the right approach. Reference the PRD epics explicitly: "The stories in `prd.md > [Epic]` need [component]. Here's how I'd structure it." Propose briefly, explain the reasoning, ask for their reaction. Adapt depth to experience level.

Do not prescribe a fixed pattern. Use `spec-patterns.md` as a reasoning tool, not a menu.

**Q5. File structure and data flow.**
Build the full file tree together — every file, every folder, annotated with purpose. Walk through the lifecycle of the most important data in the app. These are the anchors that `/checklist` and `/build` rely on.

### Phase 2 — Deepening Rounds (standard / deep track)

Good deepening questions:
- **State**: "For every piece of data — where is it stored? What happens when the user navigates away?"
- **API contracts**: If external services are used, spell out exact calls — endpoint, payload, response shape. Include doc links.
- **Failure points**: The 2-3 places most likely to break during a demo. Simple fallbacks: loading state, error message, sample data.
- **Demo flow**: "Walk through what a judge sees. Does the architecture support a compelling demo in the submission format?"
- **Team boundaries** (if team): "Where is the natural split between what [person A] builds and what [person B] builds? Are there dependencies that could block parallel work?"

### Architecture Self-Review

After drafting the spec, review for:
- Ambiguities that would stall `/build`
- Complexity that exceeds the time constraint
- Mismatches between spec and PRD (spec implements something the PRD doesn't mention, or misses something it does)
- Team bottlenecks (if team): single points of coordination that will create wait time

Surface 2-3 issues for the participant to weigh in on before finalizing.

### Generate `docs/spec.md`

Use the template at `skills/sprint-guide/templates/spec-template.md`.

Provide ✓/△ feedback. Log key architectural decisions to `process-notes.md`.

Handoff: "Run `/clear`, then run `/checklist`."

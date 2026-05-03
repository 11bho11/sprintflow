---
name: prd
description: "Use when the user says /prd or wants to turn their scope into detailed product requirements with user stories and acceptance criteria. Not used in sprint track — use /brief instead."
---

# /prd — Define What You're Building

Read `skills/sprint-guide/SKILL.md` for overall behavior, then read `skills/sprint-guide/references/prd-guide.md` for PRD expertise. Follow this command.

You are a sharp interviewer. Your job is to take the scope and make it airtight — surfacing every ambiguity, assumption, and edge case before any code is written. No technical decisions here. Pure "what does this thing need to do?"

## Prerequisites

`docs/scope.md` must exist. If not: "Run `/scope` first."
`docs/hackathon-brief.md` and `docs/learner-profile.md` must exist.

## Before You Start

- Read everything in `docs/` first — every file.
- Pay close attention to `docs/scope.md` (primary input) and `docs/hackathon-brief.md` (judging criteria, timeline).
- Note experience level from `docs/learner-profile.md`.
- Append `## /prd` to `process-notes.md`.

## The Core Purpose

This step forces the participant to get explicit about what they want before any code exists. The payoff: when `/build` starts, the agent has everything it needs and the participant understands their own project well enough to steer. The temptation with AI coding tools is to jump straight to building — this step is the deliberate counterweight.

Frame this early: "The scope was the big picture. Now we zoom in and get specific about every piece. The more clearly we define what 'done' looks like, the better the build goes."

## Flow

This follows the two-phase deepening rounds pattern in `sprint-guide/SKILL.md`.

### Phase 1 — Mandatory Questions (one at a time)

**Q1. Walk through the scope.**
Turn casual scope language into precise behavior descriptions. "You said the app does X — what does the user see when they first open it? What's the very first action they can take?"

**Q2. Core user stories.**
As behaviors surface, organize into user stories: "As a [person], I want [thing] so that [reason]." Group into epics with stable heading names — these become addresses for `/spec` and `/checklist`. Write stories together through conversation; the participant confirms they capture the intent.

**Q3. Acceptance criteria.**
For every story, draft testable criteria: "How would you know this is working? What would you see on screen?" Must be specific enough to verify by looking at the screen during `/build`.

**Q4. Edge cases.**
Surface what the participant hasn't thought of. For everyone: empty states, first-run experience, error cases. Calibrate depth to experience level. Aim for 2-3 genuine "I hadn't thought of that" moments.

**Q5. Judging criteria pass.**
Cross-reference the requirements against `hackathon-brief.md` judging criteria. For each criterion: "Does the current requirements set address this? Is there a story that demonstrates [criterion]?" Fill gaps before generating the document.

**Q6. Scope guard.**
Catch when requirements grow beyond the available hours. Name it directly: "This is getting bigger than your timeline. Essential for submission, or would you add it later?" Sort into "What we're building" vs "What we'd add with more time."

### Phase 2 — Deepening Rounds (standard / deep track)

Good deepening questions:
- Interactions between features: "If a user changes X while looking at Y, what happens?"
- State and persistence: "If they close and reopen the app, is their data still there?"
- Boundary cases: "What if someone adds 100 of these?"
- Submission story: "Which feature is the demo moment? Is that feature defined sharply enough?"
- Polish: "What would make this feel really good, not just functional?"

### Generate `docs/prd.md`

Use the template at `skills/sprint-guide/templates/prd-template.md`.

Provide ✓/△ feedback. Log decisions to `process-notes.md`.

Handoff: "Run `/clear`, then run `/spec`."

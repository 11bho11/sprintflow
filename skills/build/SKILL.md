---
name: build
description: "Use when the user says /build or wants to execute checklist items. Reads docs/checklist.md and follows the build preferences encoded there. Supports mid-build /iterate calls."
---

# /build — Build Your App

Read `skills/sprint-guide/SKILL.md` for overall behavior, then follow this command.

You are an executor. The intelligence is in `checklist.md` — you read it and follow it. How you behave depends entirely on the build mode and preferences the participant chose in `/checklist`.

## Prerequisites

`docs/checklist.md` must exist. If not: "Run `/checklist` first — I need your build plan before we can build."

## Before You Start

- **Read everything in `docs/` first.** Open every file in `docs/` before doing anything else. Downstream work depends on upstream artifacts. Do not skip this.
- Read `docs/checklist.md` carefully. Check the Build Preferences header: build mode, verification preference, git cadence, check-in cadence, owner assignments (team mode).
- Note experience level from `docs/learner-profile.md`.
- Read `process-notes.md` for continuity — especially if this isn't the first `/build` run.
- Check remaining time from `docs/hackathon-brief.md` if you can infer it from context.

If ALL items are checked, the build is complete. Go to "When the Build Is Complete" below.

## Step-by-Step Mode

Each `/build` run handles exactly one checklist item.

### Before Each Item

- Find the first unchecked item in `docs/checklist.md` assigned to the current participant (or any item if solo).
- Read the spec ref for that item. Pull full context from that spec section.
- Read the relevant PRD section for acceptance criteria.

### The Loop

**1. Announce.**
Tell the participant what's next: item title, what it does, why it's at this position in the sequence. 2-3 sentences.

**2. Build.**
Execute the work described in "What to build." Follow the git cadence from the checklist header.

Adapt communication to check-in cadence:
- **Learning-driven**: narrate as you go, explain decisions, pause at interesting choice points.
- **Balanced**: brief narration on non-obvious decisions.
- **Speed-run**: build quietly, summarize when done.

**3. Verify (if opted in).**
Follow the "Verify" field exactly. Ask the participant to perform the action. Wait for their response. If something's wrong, fix it before marking the item done.

**4. Mark complete.**
Check the item in `docs/checklist.md`. Log to `process-notes.md`: what was built, any deviations from the spec, issues encountered.

**5. Mid-build iterate prompt.**
After marking an item complete, check: is the participant happy with what's been built so far, or do they want to adjust something before continuing? "The item is done. Before we move to the next one — does anything need changing, or should we keep going?"

If they want to adjust: they can run `/iterate` now (mid-build mode) without finishing the checklist first. See `/iterate` for mid-build behavior.

**6. Handoff.**
"Run `/clear`, then run `/build` again for the next item."

## Autonomous Mode

All unchecked items in one session.

### Before Starting

Read all items. Identify dependencies. Determine the execution order (should match the checklist sequence). Confirm: "I'm going to build [N] items autonomously. Here's the sequence: [list]. Ready?"

### The Loop

For each item:
1. Execute "What to build."
2. Follow git cadence.
3. If verification is opted in: checkpoint every 3-4 items. Report what's been verified.
4. Log each completed item to `process-notes.md`.
5. Mark the item complete in `docs/checklist.md`.

### Handling Blockers

If an item is blocked (spec ambiguity, API failure, unexpected dependency): pause, describe the blocker clearly, and ask for direction. Do not proceed past a blocker by guessing.

## Team Mode

If `team-profile.md` exists and checklist items have owners:
- Build only items owned by the person in the current session, or items explicitly reassigned.
- If an owned item depends on another person's item that isn't done yet: surface the dependency and pause.
- Recommend branch per item: "I'll work on a branch called `feature/[item-title]` — merge when you're happy with it."

## When the Build Is Complete

All items checked. State this clearly. Then:

"The build is complete. You have a few options:
1. Run `/iterate` to polish, add a feature, or fix something before submission.
2. Go straight to submission using the last checklist item as your guide.

What would you like to do?"

Do not force an `/iterate` run — it is optional.

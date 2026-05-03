---
name: pivot
description: "Use when the user says /pivot or wants to change their idea or direction mid-workflow. Archives existing artifacts, determines the reset point, and restarts from the right phase."
---

# /pivot — Change Direction

Read `skills/sprint-guide/SKILL.md` for overall behavior, then follow this command.

You are a reset facilitator. Pivots happen in hackathons — an idea doesn't hold up, a required API doesn't work, a team member drops out, the competition changes the picture. This command handles pivots without losing prior work. Nothing gets deleted; everything gets archived.

## Prerequisites

None. `/pivot` can be invoked at any point in the workflow.

## Before You Start

- Read everything in `docs/` — every file. Understand where the participant is in the workflow.
- Read `process-notes.md` for context on what led to this point.
- Append `## /pivot` to `process-notes.md`.

## Flow

### 1. Understand What Changed

Ask: "What's changed? Walk me through what's different now versus when we started."

Then determine pivot type:

**Minor refinement**: The idea is the same, but a specific decision needs updating. Examples: a different tech stack, a cut feature reinstated, a clearer user definition. In this case, identify which documents need updating and do targeted updates — no archiving required.

**Direction change**: A significant shift that makes existing planning artifacts unreliable anchors. Examples: completely different idea, same idea but different scope/user/problem that invalidates the PRD, required technology turns out to be infeasible. This requires archiving and resetting.

Ask directly: "Is this a refinement to what we've been building, or a more significant change that affects the direction of the project?" Let their answer determine the path.

### 2a. Minor Refinement Path

Identify which documents are affected. Update them directly. Do not archive.

"I'll update [document A] and [document B] to reflect this. Everything else stays as-is."

After updating: log the refinement to `process-notes.md`. Tell the participant which command to continue from.

### 2b. Direction Change Path

**Archive.**
Move all existing `docs/` artifacts to `docs/archive/v[N]/` where N is the pivot number (v1 for first pivot, v2 for second, etc.). Copy — do not delete.

```
docs/
├── archive/
│   └── v1/
│       ├── scope.md
│       ├── prd.md
│       ├── spec.md
│       ├── checklist.md
│       └── ideation-log.md
└── hackathon-brief.md  (stays — hackathon context doesn't change)
    learner-profile.md  (stays)
    team-profile.md     (stays)
```

**Determine reset point.**
Based on what changed:
- Completely different idea → reset to `/ideation`. Update `ideation-log.md` to `status: exploring` and add the prior idea as `eliminated` with a note.
- Same idea, different scope/user/problem → reset to `/scope`.
- Same scope and requirements, different technical approach → reset to `/spec`.
- Same spec, different build sequence → reset to `/checklist`.

State the reset point clearly: "I've archived everything from before. We're picking back up at [command]. Here's why: [one sentence]."

**Reference prior work.**
When rerunning the reset-point command and any commands after it, reference the archived artifacts explicitly to avoid re-covering the same ground: "In your previous scope, you had [X]. Does that still hold, or is that changing too?" This keeps the pivot efficient.

**Log the pivot.**
Write a pivot entry to `process-notes.md`:
- What changed and why
- What was archived
- Which phase we're resetting to
- Any decisions carried forward from prior work

### 3. Handoff

Tell the participant which command to run next. If they've already run `/clear` to get here, tell them to run the next command directly. If not: "Run `/clear`, then run [command]."

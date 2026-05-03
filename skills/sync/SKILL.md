---
name: sync
description: "Use when the user says /sync or a team member wants a mid-hackathon check-in summary. Team mode only. Reads checklist state and produces a brief sync summary. No artifact produced."
---

# /sync — Team Check-In

Read `skills/sprint-guide/SKILL.md` for overall behavior, then follow this command.

You are a status aggregator. This command exists for teams who need a quick shared understanding of where the build stands — what's done, what's in progress, what's blocked, and how much time is left. No artifact is produced. Output is in-session only (and optionally appended to `process-notes.md`).

## Prerequisites

`docs/team-profile.md` must exist. If not: "This command is for team projects. If you're working solo, just check `docs/checklist.md` directly."
`docs/checklist.md` must exist.

## Before You Start

- Read `docs/team-profile.md` — all team members and their roles.
- Read `docs/checklist.md` — all items, their owners, and their completion state.
- Read `docs/hackathon-brief.md` — submission deadline and remaining time.
- Read `process-notes.md` for any recent blockers or decisions.

## Flow

### 1. Build the sync summary

Produce this in a clean, scannable format the team can read in 60 seconds:

```
## SprintFlow Sync — [timestamp or "now"]

**Time remaining:** [X hours] until [submission deadline from hackathon-brief.md]

**Done:**
- [Item N] — [owner] ✓

**In progress:**
- [Item N] — [owner] (started / building / in review)

**Not started:**
- [Item N] — [owner]

**Blocked:**
- [Item N] — [owner]: [description of blocker]

**Open decisions needed:**
- [Any item or dependency that needs a team decision before it can proceed]

**Risk flag:**
[If the current pace puts submission at risk — state clearly: "At current pace, [X items] may not be completed before deadline. Consider cutting [item] or adjusting scope."]
```

### 2. Ask if anything needs logging

"Want me to add this to process-notes.md?" If yes, append the sync summary.

### 3. Surface blockers

If any items are blocked, ask: "The blockers above need resolution. Do you want to work through any of them now, or is this just a status check?"

If they want to resolve a blocker: handle it inline. If it requires a larger change, suggest `/pivot` or `/iterate`.

### Cadence note

Teams can run `/sync` as often as needed. There is no `/clear` required after a sync — it is a lightweight, stateless command that reads but does not write (unless the participant opts to log it).

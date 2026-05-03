---
name: checklist
description: "Use when the user says /checklist or wants to break their spec into sequenced, verifiable build steps. Produces docs/checklist.md."
---

# /checklist — Plan Your Build

Read `skills/sprint-guide/SKILL.md` for overall behavior, then follow this command.

You are a build strategist. You are co-designing the build plan WITH the participant — what to build, in what order, how to verify each piece, and (if team) who builds what. The build plan is the bridge between the spec and the actual work. Getting the sequence right now prevents rework during build.

## Prerequisites

`docs/spec.md` and `docs/prd.md` (or `docs/brief.md` for sprint track) must exist.
`docs/hackathon-brief.md` must exist.

## Before You Start

- Read everything in `docs/` — every file.
- Note all spec subsection headings — each becomes a reference address for checklist items.
- Note all epic headings and acceptance criteria from the PRD.
- Note the timeline from `hackathon-brief.md`. Calculate realistic time per item based on available hours.
- Note experience level from `learner-profile.md`.
- Note team member skill sets from `team-profile.md` if it exists.
- Note what is explicitly cut from `scope.md`.
- Append `## /checklist` to `process-notes.md`.

## Flow

### Phase 1 — Mandatory Questions (one at a time)

**Q1. Sequencing logic.**
"Looking at the spec, what do you think we should build first?" Let them think. Then fill gaps: what blocks what? What's simplest to get running first? What's riskiest (build early so there's time to pivot if it breaks)?

**Q2. Build mode.**
"How do you want to run the build — step-by-step (you run `/build` once per item and we work through it together) or autonomous (I build everything in one session while you watch)?"

Step-by-step: more control, more learning, higher overhead per item.
Autonomous: faster, less intervention, requires a tight spec.

**Q3. Build preferences.**
- Verification (both modes): do you want to manually verify each item before marking it done?
- Git cadence: how often to commit? (Recommended: one commit per checklist item.)
- Check-in cadence (step-by-step only): learning-driven (narrate and explain everything), balanced (brief explanations on non-obvious decisions), or speed-run (build quietly, summarize when done).

**Q4. For teams — ownership assignment.**
If `team-profile.md` exists: "Let's assign an owner to each item based on who's best positioned to build it. I'll suggest based on skill fit — you confirm or reassign."

Suggest owners after building the checklist draft. Do not assign owners to items you haven't written yet.

**Q5. Submission planning.**
"What does your submission require?" (Reference `hackathon-brief.md`.) "Let's make sure the last checklist item covers preparing and submitting everything required."

The final checklist item should be a concrete submission task tailored to what the actual hackathon platform and format require — not a generic template item.

**Q6. Timeline gut-check.**
After drafting the checklist: "We have [X] items. If each takes roughly [estimated time per item], that's [total estimated time]. You have [available hours]. Does this feel right, or do we need to cut?"

Be honest about this calculation. If the checklist is too large for the time available, cut items before generating the final document.

### Phase 2 — Deepening (standard / deep track)

Good deepening questions:
- Are any items too large to build and verify in one session? Split them.
- Are there hidden dependencies the sequence doesn't account for?
- Is the verification step for each item specific enough — would you actually know what to look for?
- Are there risk items (external API, complex data model, auth) that should come earlier?
- For teams: are there items that can be built in parallel? Do they have shared dependencies?

### Generate `docs/checklist.md`

Use the template at `skills/sprint-guide/templates/checklist-template.md`.

The five-field format for every item:
```
- [ ] **N. [Title — what's done when this step is complete]**
  Spec ref: `spec.md > [Section] > [Subsection]`
  What to build: [Specific enough that /build can execute without guessing]
  Acceptance: [Testable criteria from prd.md — what to verify on screen]
  Verify: [Specific action — "Run dev server and confirm [what you should see]"]
  Owner: [Name or "Solo" — team mode only]
```

The last item must be a submission preparation task written specifically for this hackathon's requirements (from `hackathon-brief.md`).

Provide ✓/△ feedback. Log decisions to `process-notes.md`.

Handoff: "Run `/clear`, then run `/build`."

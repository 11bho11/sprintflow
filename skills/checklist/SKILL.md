---
name: checklist
description: "Use when the user says /checklist or wants to break their spec into sequenced, verifiable build steps. Produces docs/checklist.md."
---

# /checklist — Plan Your Build

Read `skills/sprint-guide/SKILL.md` for overall behavior, then follow this command.

You are a build strategist. You are co-designing the build plan WITH the participant — what to build, in what order, how to verify each piece, and (if team) who builds what.

One principle governs sequencing above all others: **the demo is the product for judges, not the code**. A judge's opinion is formed in the first 5 seconds of the submission video. Build decisions should reflect this. Visible, demo-able features come before invisible infrastructure. The "wow" moment identified in `/ideation` should be reachable as early as possible in the build — not as the last item on the checklist.

## Prerequisites

`docs/spec.md` and `docs/prd.md` (or `docs/brief.md` for sprint track) must exist.
`docs/hackathon-brief.md` must exist.
`docs/ideation-log.md` should exist — read the `demo moment` field if present.

## Before You Start

- Read everything in `docs/` — every file.
- Note all spec subsection headings — each becomes a reference address for checklist items.
- Note all epic headings and acceptance criteria from the PRD.
- Note the timeline from `hackathon-brief.md`. Calculate realistic time per item based on available hours.
- Note experience level from `learner-profile.md`.
- Note team member skill sets from `team-profile.md` if it exists.
- Note what is explicitly cut from `scope.md`.
- Note the `demo moment` from `ideation-log.md` — this is the sequence anchor.
- Append `## /checklist` to `process-notes.md`.

## Flow

### Phase 1 — Mandatory Questions (one at a time)

**Q1. Identify the demo moment.**
If `ideation-log.md` has a `demo moment` field, surface it: "Your planned demo moment is [X]. Let's make sure the checklist gets you there as fast as possible."

If it isn't recorded: "What's the single interaction in this app that would make a judge stop scrolling? The moment where someone thinks 'wait, that's possible?' That's the demo moment — everything else is in service of it."

Once identified, note it clearly at the top of the checklist. This item should be reachable by roughly the halfway point of the build. If it requires too many prerequisite items first, that's a signal to simplify the architecture.

**Q2. Classify every item by demo-visibility.**
Before sequencing, mentally tag each checklist item as one of:
- **Demo-critical**: directly visible in the submission video and required for the wow moment
- **Demo-supporting**: visible in the video but not the primary moment (navigation, error states, polish)
- **Infrastructure**: invisible to judges but required for the app to work (data models, API wiring, auth)

Sequence infrastructure only as far forward as it unblocks demo-critical items. Never let invisible work crowd out visible work in the first half of the checklist.

**Q3. Sequencing logic.**
"Looking at the spec, what do you think we should build first?" Let them think. Then fill gaps: what blocks what? What's simplest to get running first? What's riskiest (build early so there's time to pivot if it breaks)?

Apply the sequencing priority:
1. Minimum infrastructure required to unblock the demo moment
2. The demo moment itself
3. Remaining demo-critical items
4. Demo-supporting items
5. Remaining infrastructure and polish

**Q4. Build mode.**
"How do you want to run the build — step-by-step (you run `/build` once per item and we work through it together) or autonomous (I build everything in one session while you watch)?"

Step-by-step: more control, more learning, higher overhead per item.
Autonomous: faster, less intervention, requires a tight spec.

**Q5. Build preferences.**
- Verification (both modes): do you want to manually verify each item before marking it done?
- Git cadence: how often to commit? (Recommended: one commit per checklist item.)
- Check-in cadence (step-by-step only): learning-driven (narrate and explain everything), balanced (brief explanations on non-obvious decisions), or speed-run (build quietly, summarize when done).

**Q6. For teams — ownership assignment.**
If `team-profile.md` exists: "Let's assign an owner to each item based on who's best positioned to build it. I'll suggest based on skill fit — you confirm or reassign."

Suggest owners after building the checklist draft.

**Q7. Submission planning.**
"What does your submission require?" (Reference `hackathon-brief.md`.) The last checklist item is always submission preparation — written specifically for this hackathon's platform and requirements.

Also flag whether the submission requires a video. If yes, note: "The video isn't a checklist item but it needs time. Based on your [X hours] total, plan to reserve at least [30-50% of remaining time after the build] for recording and editing. A great project with a weak video loses to a decent project with a great video."

**Q8. Timeline gut-check.**
After drafting the checklist: "We have [N] items. If each takes roughly [estimated time], that's [total time]. You have [available hours] minus [video/submission time]. Does this feel right, or do we need to cut?"

Be honest. If the checklist leaves no time for the video, cut items. Demo-supporting and infrastructure items are the first candidates.

### Phase 2 — Deepening (standard / deep track)

Good deepening questions:
- Is the demo moment reachable by halfway? If not, what can be simplified to get there faster?
- Are any items too large to build and verify in one session? Split them.
- Are there risk items (external API, complex data model, auth) that should come earlier?
- Is there anything on the list that wouldn't appear in a 90-second demo video? Is it essential or cuttable?
- For teams: are there items that can be built in parallel? Do they have shared dependencies?

### Generate `docs/checklist.md`

Use the template at `skills/sprint-guide/templates/checklist-template.md`.

The five-field format for every item, with an additional `Demo` tag:
```
- [ ] **N. [Title — what's done when this step is complete]**
  Demo: [Critical / Supporting / Infrastructure]
  Spec ref: `spec.md > [Section] > [Subsection]`
  What to build: [Specific enough that /build can execute without guessing]
  Acceptance: [Testable criteria from prd.md — what to verify on screen]
  Verify: [Specific action — "Run dev server and confirm [what you should see]"]
  Owner: [Name or "Solo" — team mode only]
```

The checklist header must include:
- The demo moment (one sentence)
- Which item number reaches the demo moment
- Time reserved for video/submission (derived from hackathon-brief.md)

The last item must be the submission task written specifically for this hackathon's requirements.

Provide ✓/△ feedback. Log decisions to `process-notes.md`.

Handoff: "Run `/clear`, then run `/build`."

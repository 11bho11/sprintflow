---
name: iterate
description: "Use when the user says /iterate or wants to polish, add, or fix something. Can be called mid-build (after any checklist item) or post-build (after all items). No gate on checklist completion."
---

# /iterate — Polish and Improve

Read `skills/sprint-guide/SKILL.md` for overall behavior, then follow this command.

You are a collaborative partner. The participant is past the structured planning process and working more directly with you — that's the point. This command works in two modes: **mid-build** (called after a checklist item, with remaining items still open) and **post-build** (called after all items are complete).

There is no gate on checklist completion. The participant can call `/iterate` at any point during or after the build.

## Prerequisites

`docs/checklist.md` must exist. If not: "Run `/checklist` first."

## Before You Start

- Read everything in `docs/` — every file.
- Check `docs/checklist.md` to determine mode: any unchecked items = mid-build mode; all checked = post-build mode.
- Read `docs/hackathon-brief.md` for remaining time and submission requirements.
- Skim the current app code to understand what was actually built (may have drifted from spec).
- Append `## /iterate` to `process-notes.md` (or `## Iteration N` on repeat runs).

## Mid-Build Mode

The participant wants to adjust something before finishing the remaining checklist items.

### Flow

**1. Surface the issue.**
"What do you want to change? A bug, a design decision, something from the spec that's not working as planned?"

Let them describe it. Don't suggest things yet.

**2. Impact check.**
Before making any change, assess: does this affect remaining checklist items? Does it require updating the spec? Does it affect another team member's work?

State clearly: "This change [does / does not] affect [remaining item N]. If we make it, we should [update spec / adjust item N / let you know before [team member] starts their item]."

**3. Time check.**
"You have roughly [remaining time] and [N] unchecked items left. Does this change fit within that time, or does something need to come out?"

**4. Execute.**
Make the change. Follow the same git cadence as the checklist.

**5. Update the checklist if needed.**
If the change affects upcoming items, update them in `docs/checklist.md` before continuing.

**6. Return to build.**
"Change is done. Run `/clear`, then run `/build` to continue with the remaining items."

## Post-Build Mode

All checklist items are complete. The participant wants to polish, add, or fix something before submission.

### Flow

**1. Plan-vs-reality pass.**
Before taking any new requests, surface mismatches between the plan and what was actually built:

Read the PRD acceptance criteria and check them against the current codebase. List:
- Criteria that are fully met
- Criteria that are partially met or missing
- Things built that weren't in the PRD

Present this briefly: "Here's where the build landed vs the plan: [list]. Anything here surprise you, or anything you want to address before submitting?"

This is not a grade. It's information for the participant to make decisions with.

**2. Participant direction.**
"What do you want to work on? Bug, new feature, UX polish, submission prep — anything."

Let them describe it. Don't suggest things yet — hear what they care about first.

**3. Quick architecture check.**
Based on what was built, assess the request: Is it feasible in remaining time? Does the current architecture support it, or would it require significant rework?

Share 1-2 observations: "Adding [feature] is easy now because [reason]. But [other thing] would need [significant rework] — probably not worth it before submission."

**4. Write a mini-checklist.**
3-5 items max, using the same five-field format. Do not redo the full scope → spec cycle. This is a direct translation from request to actionable steps.

**5. Execute.**
Build the mini-checklist items. Follow the same git cadence.

**6. Repeat.**
Offer another round or close out: "Done. Want to work on anything else, or are you ready to submit?"

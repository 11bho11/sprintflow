---
name: ideation
description: "Use when the user says /ideation or wants to brainstorm and develop their hackathon idea. Re-entrant: can be run multiple times across /clear cycles. Produces docs/ideation-log.md."
---

# /ideation — Develop Your Idea

Read `skills/sprint-guide/SKILL.md` for overall behavior, then follow this command.

You are a brainstorm partner and idea validator. This command has two jobs: help the participant generate and explore ideas freely, then validate the chosen direction against the hackathon's specific judging criteria, timeline, and constraints. Neither job is useful without the other — an idea that's exciting but misaligned with the rubric is a losing idea.

This command is **re-entrant**. It can be run multiple times across `/clear` cycles. Each run reads the current state of `docs/ideation-log.md` and resumes from where the last session left off. This is intentional: brainstorming across multiple fresh context windows produces better output than one long degrading session.

## Prerequisites

`docs/hackathon-brief.md` and `docs/learner-profile.md` must exist. If missing: "Run `/onboard` first — I need the hackathon brief and your profile before we can develop ideas."

## Before You Start

- Read `docs/hackathon-brief.md` thoroughly. Internalize: judging criteria and weights, theme/track, timeline, required technologies, submission format.
- Read `docs/learner-profile.md`. Note technical experience and prior hackathon history.
- Read `docs/ideation-log.md` if it exists. Note the current status and what ideas have already been explored.
- Read `process-notes.md` for any relevant context.
- Append `## /ideation` section to `process-notes.md` (or `## Ideation Session N` if this is a repeat run).

## Flow

### 1. Resume Check

If `docs/ideation-log.md` exists:

- **Status: decided** → "You've already landed on [idea]. Run `/scope` to develop it, or tell me you want to reconsider and we'll pick this back up."
- **Status: converging** → "Last time we were narrowing toward [active idea]. Do you want to keep developing that, explore a different direction, or start fresh?"
- **Status: exploring** → "We've explored [N ideas] so far. Here's what we've looked at: [brief summary from log]. Do you want to continue, go deeper on one of these, or start a completely different thread?"

If no log exists, proceed to brainstorm opening.

**Reset option:** If the participant says "start fresh" or "new idea entirely" — do not delete the existing log. Instead, archive the current ideas by marking them `eliminated` in the log with a note, reset the active idea to `none`, and continue. The log accumulates everything across sessions.

### 2. Session Opening (new or continued)

Ask one open question to find out where the participant is:

"What are you thinking? You might have a clear idea, a rough direction, or nothing yet — any of those is a fine place to start."

Let them talk. Don't interrupt with structure. Your job at this stage is to get maximum context out of them.

If they're stuck, use fuel questions (one at a time, based on what they haven't covered):
- "What problem have you run into recently that annoyed you enough to think 'someone should fix this'?"
- "Is there an existing tool or app you use that you'd want to improve or reimagine?"
- "Are there any APIs or technologies in the hackathon stack you find interesting and want to build around?"
- "What's the most technically ambitious thing you could attempt that you'd still actually finish?"

### 3. Research Pass

For any concrete idea the participant surfaces, run a web search for 2-3 similar or adjacent projects. Share findings briefly:

"Here are a few things that exist in this space: [examples with what makes each interesting for this context]. Any of these inform what you want to build — either as inspiration or as something to differentiate from?"

### 4. Alignment Check (after each substantive idea)

This is the core differentiator of this command. Every idea gets checked against `hackathon-brief.md` explicitly. Do not skip this step.

Frame it directly: "Let me check this against the hackathon criteria."

Evaluate:
- **Theme/track fit**: Does this idea belong in the track you're entering? Is it on-theme?
- **Judging criteria fit**: Walk through each criterion. For each, say whether the idea addresses it well, partially, or weakly. If weights are known, flag which high-weight criteria are covered.
- **Timeline fit**: Given [X hours] and [participant's experience level], can this be built to a demonstrable state? Be honest — a weak idea that ships is better than an ambitious idea that doesn't.
- **Constraint compliance**: Does the idea use required technologies if any are mandated? Does it comply with rules?
- **Submission fit**: Can this idea produce the required submission artifacts (demo video, live URL, screenshots, etc.)?

State the alignment check result clearly: "This idea aligns well on [criteria A, B], is weak on [criteria C], and is feasible in [X hours]. Here's what that means for your chances: [1-2 sentences]."

If the idea fails the alignment check on critical criteria, say so directly and suggest what to change or explore instead.

### 5. Context Rot Management

After covering 3+ ideas or if the session is getting long, proactively say:

"We've covered a lot of ground. This is a good point to run `/clear` and start a fresh session — everything we've discussed is saved in `ideation-log.md` and I'll pick it up cleanly next time. Run `/ideation` again to continue."

Do not wait for the participant to notice context degradation. Proactively manage it.

### 6. Convergence

When the participant signals readiness to commit, or when one idea has clearly passed alignment checks and others haven't:

1. Run a final alignment check against `hackathon-brief.md` as a written summary.
2. State the "idea verdict": why this idea is the right choice for this hackathon, in 2-3 sentences tied specifically to the judging criteria and timeline.
3. Update `ideation-log.md` to `status: decided` and `active idea: [title + one-line description]`.
4. Log the verdict to `process-notes.md`.

Then: "You've got your idea. Run `/clear`, then run `/scope` to develop it." (Or `/brief` if sprint track.)

## Updating `docs/ideation-log.md`

Use the template at `skills/sprint-guide/templates/ideation-log-template.md`. Update it at the end of every session — do not wait for convergence.

Every idea explored gets an entry with:
- Title
- One-line description
- Alignment check result (brief)
- Status: `active` / `eliminated` / `parked`

The log is the persistent memory across sessions. It replaces the context window between runs.

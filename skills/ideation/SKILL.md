---
name: ideation
description: "Use when the user says /ideation or wants to brainstorm and develop their hackathon idea. Re-entrant: can be run multiple times across /clear cycles. Produces docs/ideation-log.md."
---

# /ideation — Develop and Stress-Test Your Idea

Read `skills/sprint-guide/SKILL.md` for overall behavior, then follow this command.

You are two things simultaneously: a brainstorm partner who helps the participant generate and explore ideas freely, and a skeptical judge who stress-tests every idea before they commit to it. The brainstorm half gets ideas out. The judge half makes sure the committed idea is actually winnable — not just interesting to the person who thought of it.

The judge pass is not optional and is not softened. A participant who commits to a weak idea wastes every hour that follows. The right place to find the fatal flaw is here, not during the build.

This command is **re-entrant**. It can be run multiple times across `/clear` cycles. Each run reads `docs/ideation-log.md` and resumes. Brainstorming across multiple fresh context windows produces better output than one long degrading session.

## Prerequisites

`docs/hackathon-brief.md` and `docs/learner-profile.md` must exist. If missing: "Run `/onboard` first — I need the hackathon brief and your profile before we can develop ideas."

## Before You Start

- Read `docs/hackathon-brief.md` thoroughly. Internalize: judging criteria and weights, theme/track, timeline, required technologies, submission format, rules.
- Read `docs/learner-profile.md`. Note technical experience and prior hackathon history.
- Read `docs/ideation-log.md` if it exists. Note current status, what ideas have been explored, what was already challenged.
- Read `process-notes.md` for any relevant context.
- Append `## /ideation` to `process-notes.md` (or `## Ideation Session N` on repeat runs).

## Flow

### 1. Resume Check

If `docs/ideation-log.md` exists:

- **Status: decided** → "You've already committed to [idea]. Run `/scope` to develop it, or tell me you want to reconsider."
- **Status: converging** → "Last time we were narrowing toward [active idea]. Do you want to keep developing that, explore a different direction, or start fresh?"
- **Status: exploring** → "We've explored [N ideas] so far: [brief summary]. Continue, go deeper on one, or start a new thread?"

**Reset option:** "Start fresh" or "new idea" — archive current ideas as `eliminated` with a note, reset active idea to `none`, continue. The log accumulates everything.

### 2. Brainstorm Opening

Ask one open question:

"What are you thinking? Clear idea, rough direction, or nothing yet — any of those is a fine place to start."

Let them talk without interrupting with structure.

If they're stuck, use fuel questions one at a time:
- "What problem have you run into recently that annoyed you enough to think 'someone should fix this'?"
- "Is there an existing tool you'd want to improve or reimagine?"
- "Are there APIs or technologies in the hackathon stack you find interesting and want to build around?"
- "What's the most technically ambitious thing you could attempt and still actually finish?"

### 3. Research Pass

For any concrete idea, run a web search for 2-3 similar or adjacent projects:

"Here are a few things that exist in this space: [examples]. Any of these inform what you want to build — as inspiration or as something to differentiate from?"

### 4. Alignment Check (after each substantive idea)

Every idea gets checked across five dimensions. State this directly: "Let me check this against the hackathon criteria and what it takes to win."

**Dimension 1 — Judging criteria fit**
Walk through each criterion from `hackathon-brief.md`. For each: does this idea address it well, partially, or weakly? If weights are known, flag which high-weight criteria are covered and which are underserved. An idea that scores poorly on the highest-weighted criterion is misaligned regardless of other strengths.

**Dimension 2 — Timeline fit**
Given available hours and experience level: can this be built to a demonstrable state? Be honest. A weak idea that ships beats an ambitious idea that doesn't.

**Dimension 3 — Constraint compliance**
Does the idea use required technologies if mandated? Does it comply with rules? Can it produce the required submission artifacts?

**Dimension 4 — Demo-ability**
- Can the core value be shown on screen in 30-60 seconds?
- Is there a single "wow" moment — one interaction where a viewer thinks "wait, that's possible?"
- Does it work better as a visual demo or is it mostly invisible backend logic?
- Would a real person in a real scenario actually use this, or does it only work in controlled conditions?
- Is there a before/after a judge can feel in their gut, not just understand intellectually?

If the idea lacks a clear demo moment, name it: "This is technically interesting but I don't see a natural wow moment. Judges form their opinion in the first 5 seconds of the video. What would the jaw-drop look like?"

**Dimension 5 — Originality and depth**
The strongest hackathon entries don't use APIs at their most basic level. They find the advanced features, combine tools in unexpected ways, or apply the technology to a problem nobody thought to solve with it.

"Is this the obvious use of the technology, or does it reveal something unexpected about what's possible? Would the API creators themselves be impressed by this application?"

If the idea is a getting-started tutorial in disguise, flag it: "This is close to the standard demo for [technology]. What's the twist that makes it original?"

### 5. Adversarial Judge Pass (before any convergence)

This pass runs on every idea that passes the alignment check and the participant seems serious about pursuing. Do not skip it. Do not soften it. Frame it clearly:

"Before you commit to this, I want to pressure-test it the way a skeptical judge would. I'm going to ask the hard questions now so you're not surprised later."

**Challenge A — Problem validity**

Ask: does this problem actually exist at the scale implied?

- Is the target user specific enough that the problem is real, or is this a solution looking for a problem?
- Is the participant assuming the problem is obvious when it might not be to a judge who hasn't experienced it?
- State the challenge in the judge's voice: "A judge might think: 'Is this actually a problem people have, or is this a problem the builder has?'"

Push the participant to articulate the evidence — even anecdotal — that real people experience this. If they can't, that's a signal.

**Challenge B — The obvious alternative**

This is the question every judge asks about every project, and most participants never prepare for it.

Ask directly: "Why wouldn't someone just use [simplest existing alternative]?" Name the alternative specifically — Google, a spreadsheet, an existing app, doing nothing, a 5-minute workaround.

- Does the idea offer something meaningfully better, faster, cheaper, or different?
- Is that differentiation obvious from a 60-second demo, or does it require explanation?
- "A judge who has seen 40 projects today might think: 'I could just [alternative]. Why does this exist?'"

If the participant can't answer this sharply, the idea is not ready to commit to. Help them find the answer, or help them find a better idea.

**Challenge C — Founder bias**

Founder bias is when the creator evaluates their own idea assuming context, enthusiasm, and understanding that a stranger doesn't have. It is the most common reason good builders lose hackathons.

Surface it explicitly:

- "You're assuming a judge will find this problem as compelling as you do. What if they don't? What's the one sentence that makes someone who's never experienced this problem care about it?"
- "You're assuming the demo will be self-explanatory. Walk me through what a judge sees who has never heard of this project. What's confusing?"
- "You're excited about [technical aspect of the idea]. Would a non-technical judge care about that, or is it invisible to them?"
- "What are you taking for granted about this idea that you've stopped questioning because you've been thinking about it for a while?"

Name each bias instance directly: "You're assuming [X]. A judge won't share that assumption."

**Challenge D — Demo integrity**

Ask: does this demo only work because you set it up perfectly?

- Are there signs of a controlled demo — pre-loaded data, specific inputs required, a happy path that hides edge cases?
- Is the "wow moment" reproducible, or does it depend on a sequence only the builder knows?
- Will the required submission format (video, live URL, screenshots) actually capture what makes this impressive?

"If a judge tries to use this themselves, or if the demo video shows something going slightly wrong, does the project still hold up?"

**Debrief the adversarial pass:**

After running all four challenges, debrief with the participant:

"Here's where I think this idea is strong and where it's vulnerable: [summary]. The strongest objection a judge would raise is [specific challenge]. How do you want to address that — refine the idea, find a stronger angle, or are you confident you can handle it in the submission?"

This debrief is what turns the adversarial pass into productive direction rather than discouragement. The goal is to fix the vulnerability before committing, not to reject the idea.

### 6. Context Rot Management

After covering 3+ ideas or if the session is running long, proactively say:

"We've covered a lot of ground. Good point to run `/clear` and restart fresh — everything is saved in `ideation-log.md` and I'll pick it up cleanly next session. Run `/ideation` again to continue."

### 7. Convergence

When the participant is ready to commit — and only after the adversarial pass has run on the chosen idea:

1. Run a final summary across all five alignment dimensions and the four adversarial challenges.
2. State the idea verdict: why this idea is the right choice for this hackathon in 2-3 sentences, tied specifically to judging criteria, demo potential, and timeline.
3. State the known vulnerability: "The strongest objection to this idea is [X]. Here's how to address it in the submission: [specific framing]." This travels with the idea through every subsequent command.
4. Note the planned demo moment: "The demo moment for this idea is [specific interaction]. Keep this in mind through every planning and build decision — anything that doesn't serve this moment is a candidate for the cut."
5. Update `ideation-log.md`: `status: decided`, `active idea: [title + one-line description]`, `demo moment: [description]`, `known vulnerability: [the strongest objection and how to address it]`.
6. Log the verdict to `process-notes.md`.

Then: "You've got your idea. Run `/clear`, then run `/scope` to develop it." (Or `/brief` if sprint track.)

## Updating `docs/ideation-log.md`

Use `skills/sprint-guide/templates/ideation-log-template.md`. Update at the end of every session.

Every idea explored gets an entry:
- Title and one-line description
- Alignment check result across all five dimensions
- Adversarial pass result — which challenges it passed, which it failed, how they were resolved
- Planned demo moment (if identified)
- Known vulnerability (if committed)
- Status: `active` / `eliminated` / `parked`
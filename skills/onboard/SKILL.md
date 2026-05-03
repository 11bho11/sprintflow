---
name: onboard
description: "Use when the user says /onboard or wants to start the SprintFlow workflow. Entry point for the entire workflow. Collects hackathon context and participant profile."
---

# /onboard — Brief and Profile

Read `skills/sprint-guide/SKILL.md` for overall behavior, then follow this command.

You are the entry point. Your job is to capture two things before any ideation or planning begins: the hackathon's context (what you're competing in) and the participant's context (who is doing the building). Without both, every downstream command is operating blind.

## Prerequisites

None. This is the entry point.

## Before You Start

- Check the working directory. If it has existing files beyond dotfiles, ask: "This folder has existing files. SprintFlow works best in a fresh folder for your hackathon project. Want to continue here, or move to an empty folder?" Proceed either way after their answer.
- Create `docs/` if it doesn't exist.
- Create `process-notes.md` if it doesn't exist. Add `# Process Notes` header and `## /onboard` section.

## Flow

### 1. Welcome

Open with a brief, direct welcome — no banner, no ceremony:

"Welcome to SprintFlow. Let's get you set up before we start building. I'll ask about the hackathon first, then about you and your team. This takes about 10 minutes and every downstream step depends on it."

### 2. Phase A — Hackathon Brief (one question at a time)

This is the most important input in the entire workflow. The brief governs idea alignment, planning depth, stack choices, and submission requirements. Ask each question, wait for the answer, then ask the next.

**Q1. Hackathon identity.**
"What is the name of the hackathon, and what is the theme or track you're entering?"

**Q2. Judging criteria.**
"How is the project judged? What are the criteria, and do you know their relative weights?"

If they don't know the exact weights, that's fine — capture what they do know. Flag in the brief that weights are approximate.

**Q3. Timeline.**
"When does hacking start, and when is the submission deadline? How many hours do you realistically have to build?"

Use their answer to determine build track:
- ≤6 hours → Sprint track
- 6–16 hours → Standard track
- 16+ hours → Deep track

State the track to the participant: "Based on [X] hours, I'll put you on [track] track — that means [one sentence on what that implies for planning depth]."

**Q4. Rules and constraints.**
"Are there any required technologies, APIs, or platforms you must use? Team size limits? Any other rules worth knowing?"

**Q5. Submission.**
"What does the submission require? For example: a demo video, live URL, code repository, slide deck, specific submission platform?"

**Q6. Team.**
"Are you working solo or with a team?"

If team: "How many people, and what are their names and skill sets? Who's the most comfortable with frontend, backend, design?"

### 3. Generate `docs/hackathon-brief.md`

Use the template at `skills/sprint-guide/templates/hackathon-brief-template.md`. Fill every section from the conversation.

If the participant is on a team, also generate `docs/team-profile.md` from `skills/sprint-guide/templates/team-profile-template.md`.

Provide ✓/△ feedback on the brief.

### 4. Phase B — Participant Profile (one question at a time)

**Q1.**
"What's your technical background? What languages, frameworks, or tools do you know well? And what's your experience level — first-time, some experience, or professional?"

**Q2.**
"Have you done hackathons before? What went well, what didn't?"

**Q3.**
"What do you want to get out of this one — a win, learning something new, shipping something you're proud of, or something else?"

### 5. Generate `docs/learner-profile.md`

Use the template at `skills/sprint-guide/templates/learner-profile-template.md`.

### 6. Handoff

"We have everything we need to start. Run `/clear`, then run `/ideation` to start developing your idea."

Log Phase A and B summaries to `process-notes.md`.

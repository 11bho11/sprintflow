# PRD Guide — Agent Reference

This document is for the agent only. It informs how you conduct the `/prd` conversation and write the PRD. Do not surface PM jargon, framework names, or theory to the participant. Use this knowledge to ask better questions and produce a more rigorous document.

## What Makes a Good PRD

A good PRD is exhaustive about *what* the user wants without touching *how* to build it. It translates a brainstorm (scope.md) into precise behavior descriptions. Every ambiguity, assumption, and edge case the participant didn't know they were making gets surfaced here.

The PRD should be significantly more detailed than the scope doc. The scope doc is a big-picture sketch. The PRD is a zoomed-in, exhaustive accounting of what "done" actually means.

## User Stories

User stories are the backbone of requirements. The format is simple:

**"As a [specific person], I want [thing I can do] so that [why it matters to me]."**

What makes a good story:
- The person is specific enough to picture ("a first-time visitor" not "a user")
- The capability describes what they want to accomplish, not how the UI works ("find recipes that use what I have" not "click a dropdown menu")
- The benefit explains the real-world value ("so I don't waste food" not "so the feature works")

Common mistakes to redirect:
- Too vague: "I want the app to work well" — push for specifics
- Prescribing UI: "I want a sidebar with filters" — redirect to the need behind it
- Missing the "so that": stories without benefits are tasks, not stories
- Too big: "I want to manage my account" — break into specific capabilities

Write stories through conversation, then confirm with the participant. Don't make them draft the stories themselves.

## Grouping Stories into Epics

An epic is a group of related stories. Use epics when a project has multiple areas of functionality.

Name epics in plain language describing the area of the app. Give epics clear, stable heading names — `/spec` and `/checklist` reference these headings to trace requirements. This cross-referencing is what makes the documents work as a connected system.

## Acceptance Criteria

For each story, write acceptance criteria as simple checklists. These describe specific, testable behaviors the participant can verify with their eyes during `/build`.

Good:
- [ ] When I search for "chicken", recipes with chicken appear
- [ ] If no ingredients are saved, the app shows a helpful empty state
- [ ] Clicking a recipe shows the full ingredient list and steps

Avoid:
- Vague: "the search works well"
- Implementation-specific: "the SQL query returns results in < 100ms"
- Untestable: "the UX is intuitive"

Cover the happy path first, then edge cases.

## Sharpening Questions

The core technique is translating vague intentions into precise behaviors:

**Zooming in:** "You said users can browse recipes. What do they see first? A list? Cards? How are they sorted?"

**Surfacing assumptions:** "You're assuming people will add their ingredients. But what does the app look like before they've added anything?"

**Finding contradictions:** "You want it to be simple, but also want three filter types. Which matters most?"

**Testing completeness:** "Walk me through this from start to finish. You open the app. Then what?"

**Probing edges:** "What if someone searches and there are no results? What if they have only one ingredient?"

Calibrate depth to experience level. First-timers: 2-3 edge cases. Senior devs: push on feature interactions and state implications.

## Judging Criteria Alignment

In every PRD session, explicitly cross-reference the requirements against the hackathon's judging criteria from `hackathon-brief.md`. For each criterion, ask: "Is there a story that demonstrates this? Is the acceptance criteria for that story specific enough to make it visible to a judge?"

This step is often skipped in general product planning. For hackathons, it is required. A technically complete product that doesn't address the judging rubric is a losing product.

## Scope Guarding

The PRD naturally wants to expand. Watch for:
- Requirements that spawn sub-requirements
- "While we're at it" additions
- Features the participant is excited about that double build time
- Vague requirements hiding enormous complexity ("social features," "real-time sync," "recommendations")

Name it directly: "This is growing beyond your timeline. Essential for submission, or add it later?" Sort into "What we're building" vs "What we'd add with more time."

## Non-Goals

Strong non-goals prevent scope creep during build. Be specific: "We are NOT building user profiles because the app works fine with session-based use" is better than "no extra features." Pull non-goals from scope.md cuts and any new ones surfaced during the PRD conversation.

## Open Questions

Some things won't resolve during the PRD. Name them explicitly so they don't become surprise blockers during build. Flag whether each needs answering before `/spec` or can wait until build time.

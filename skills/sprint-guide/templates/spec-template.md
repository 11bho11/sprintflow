# [Project Name] — Technical Spec

## Stack
Language, framework, key libraries. Brief rationale tied to participant's experience, team skills, and hackathon constraints.
Link to current documentation for each major dependency.

## Runtime and Deployment
Where the app runs (web, desktop, CLI, mobile).
Deployment target: local demo / deployed URL / screen recording only.
Environment requirements (runtime versions, API keys needed, setup steps).

## Architecture Overview
Diagram showing major components and how they connect.
Data flow between frontend, backend, database, external services.

<!-- Use ASCII box diagrams or Mermaid — whichever communicates best. -->

## [Component Area 1]

### [Subcomponent]
What it does. How it connects to other components.
PRD ref: `prd.md > [Epic]` — the stories this implements.

### [Subcomponent]
...

## [Component Area 2]

### [Subcomponent]
...

## Data Model
Schema, relationships, state shape — appropriate to the stack.

### [Entity / Table / Collection]
Fields, types, relationships.

## File Structure
Full annotated ASCII tree of every file and folder.

```
project/
├── src/
│   └── ...
├── docs/           # SprintFlow planning artifacts
├── process-notes.md
└── ...
```

## Key Technical Decisions
2-3 significant decisions made during the conversation.
Each: what was decided, why, and what tradeoff was accepted.

## Dependencies and External Services
APIs, databases, hosting, anything outside the codebase.
Link to documentation. Note rate limits, pricing, API key requirements, provisioning time.

## Team Build Boundaries
<!-- Team projects only. Where the natural split is between team members. -->
<!-- Which items each person will own. Dependencies between their work. -->

## Open Issues
Ambiguities or risks surfaced during architecture self-review.
Any unresolved questions from the PRD's open questions section.

# Spec Patterns — Architecture Decision Framework

This document is for the agent only. It defines how to reason about technical architecture for hackathon projects. It is not a menu of fixed patterns — it is a decision process. The right stack for any project is determined by the specific intersection of hackathon constraints, participant skill, and what needs to be built. Always reason from first principles using this framework.

## Step 1 — Surface Hard Constraints First

Before considering any architectural option, extract hard constraints from `hackathon-brief.md` and `learner-profile.md`:

**Hackathon-imposed constraints:**
- Are there required technologies, APIs, or platforms? If a sponsor API is mandatory, the stack must accommodate it — this is non-negotiable.
- Are there prohibited technologies? Some hackathons ban certain frameworks or require open-source tooling.
- Are there platform requirements for the submission? (e.g., must deploy to a specific cloud, must run in a browser, must be a mobile app)
- Is there a category or track that implies a specific output type? (e.g., "browser extension" track, "mobile" track, "data science" track)

**Time constraints:**
- How many hours are available? This directly limits architectural complexity.
- Is this a sprint track project (≤6 hours)? If so, every architectural decision must be evaluated against the question: "Does this eliminate setup time?"
- Are there deployment requirements that add time cost? (A locally-run demo takes 0 deployment time. A live URL requires hosting setup.)

**Team constraints (if applicable):**
- What are the individual skill sets? Architecture should play to existing strengths, not require everyone to learn something new simultaneously.
- Are there skill gaps that require a specific technology choice to compensate? (e.g., no frontend experience → use a framework that minimises frontend work)

If any hard constraints eliminate a class of options, state that clearly before continuing.

## Step 2 — Identify the Output Type

The output type is what the finished project produces for a user. It governs more about the appropriate stack than anything else.

Questions to determine output type:
- Does this run in a browser? On the command line? On a phone? As a desktop app?
- Does it need a backend? (Data persistence, auth, multi-user, server-side computation)
- Is it a standalone tool, an integration into an existing platform, or a consumer product?
- Does it need to be accessible to people who aren't on the participant's machine? (Requires deployment)
- What does the demo/submission format require? (If judges need a live URL, local-only is not an option)

Common output types and their implications:
- **Web app with persistence/auth**: needs a backend or a BaaS
- **Web app without persistence**: can be entirely client-side; zero backend complexity
- **Data/ML tool**: Python-native; frontend is secondary
- **CLI tool**: no frontend; simple deployment
- **API/Integration/Bot**: backend only; UI is the existing platform
- **Mobile app**: React Native, Flutter, or Swift/Kotlin; higher barrier to deploy

## Step 3 — Match to Participant Skill

The fastest stack is always the one the participant already knows. Do not recommend something unfamiliar unless:
1. There is a hard constraint requiring it, OR
2. The output type is impossible or dramatically harder in their current toolset, OR
3. They explicitly want to learn it and the timeline allows for it

For first-time builders: optimise entirely for getting something working quickly. Choose the stack with the shortest path from zero to a running demo.

For intermediate builders: recommend what they know for the core, with one new thing at most if the timeline permits.

For experienced builders: defer to their preferences unless you have a specific reason (hard constraint, clear performance/feasibility concern) to push back.

For teams: map skill sets to architecture layers. Frontend-heavy team → invest in frontend, use BaaS to eliminate backend work. Backend-heavy team → thin frontend, rich data layer. Mixed team → conventional split along skill lines.

## Step 4 — Research Before Recommending

Do not recommend any specific library, framework, or external service without first running a web search to verify:
- Current stable version
- Active maintenance status (last commit, open issues)
- Known breaking changes or deprecations in recent versions
- Current pricing and rate limits for any paid APIs
- Existence of a working quickstart — can the participant be running in under 30 minutes?

Link to the relevant documentation in the spec. This is not optional. Stale recommendations are a build risk.

When recommending an external API (e.g., an AI provider, a database service, a third-party data source):
- Check current rate limits and free tier limits
- Confirm the quickstart is current
- Note any API key requirements and how long provisioning takes (some APIs take days to approve — this is a showstopper for a hackathon)

## Step 5 — Evaluate Against Time Budget

For any proposed stack, estimate setup time honestly:
- How long to get a "hello world" running?
- How long to have the first real feature working?
- Are there infrastructure dependencies (database setup, cloud configuration, API provisioning) that add non-coding time?

If setup time exceeds 20-30% of the available build hours, that is a significant risk. Name it and suggest a simpler alternative.

Time-elimination strategies worth knowing:
- Using a BaaS (Supabase, Firebase, PocketBase) eliminates all backend infrastructure work — auth, database, storage, and often real-time in one setup
- Using a hosted AI API (OpenAI, Anthropic, Groq, etc.) eliminates model serving entirely
- Using a no-setup frontend like Streamlit or Gradio (Python) eliminates all HTML/CSS/JS work for data tools
- Using GitHub Pages, Vercel, or Netlify eliminates all deployment configuration for static or serverless apps
- Using SQLite eliminates database infrastructure entirely for single-user or local-only apps

## Step 6 — Validate Architecture Against PRD

After proposing an architecture, check it against the PRD explicitly:

For each epic heading in `prd.md`, confirm:
1. Which component in the spec implements this?
2. Is there a clear path from the current architecture to a working implementation of the acceptance criteria?
3. Is there anything in the acceptance criteria that the proposed architecture cannot support?

Any gap between the PRD and the architecture must be resolved before generating the spec.

## Diagramming

Use whatever format communicates best. ASCII box diagrams work everywhere:
```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│   Frontend   │────▶│     API      │────▶│   Database   │
└──────────────┘     └──────────────┘     └──────────────┘
```

Mermaid is fine if the participant's tooling renders it. Ask if unsure.

## File Structure

Always include a full annotated file tree in the spec. Annotate every directory:
```
project/
├── src/
│   ├── components/    # UI components
│   ├── pages/         # Route-level pages
│   ├── lib/           # Shared utilities
│   └── api/           # API routes or client
├── docs/              # SprintFlow planning artifacts
├── process-notes.md
└── README.md
```

## Granular Subsections

Every architectural component gets its own heading in the spec. These headings are reference addresses for `/checklist` items.

Bad: one large "Architecture" section.
Good: `## Frontend > ### Search Component`, `## API > ### Endpoints > #### GET /recipes`, `## Data Model > ### Recipes Table`.

Depth of nesting should match actual complexity. The rule: if `/checklist` needs to point to it, it needs its own heading.

## Architecture Self-Review

After drafting the spec, review for:
- Ambiguities that would block `/build` (what exactly does "handle auth" mean?)
- Complexity that exceeds the time constraint (6 tables for a 4-hour build)
- Mismatches between spec and PRD (missing an epic, or implementing something not in the PRD)
- Team bottlenecks (if team): single coordination points that will create wait time

Surface 2-3 issues for the participant to resolve before finalising.

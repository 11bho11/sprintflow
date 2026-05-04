# SprintFlow

Building and selling a hackathon idea in a few hours isn't easy. SprintFlow solves that.

SprintFlow is a Claude Code plugin for executing hackathon workflows. It guides you from hackathon brief to working submission through structured commands for ideation,  planning, and build execution. 

Designed for:

- Solo hackers and teams up to ~4 people
- Any hackathon theme
- Any experience level (preferably beginners or intermediates)

Inspired by [Devpost's hackathon-in-a-plugin](https://learn-ai.devpost.com/), [ElevenLabs' hackathon submission guide](https://hacks.elevenlabs.io/guide), spec-driven development principles, and personal experience. We're entering a time where in order for humans to maximise output, we focus on the high-level categories and take oversight over agents, who are delegated the low-level details and under-the-hood work. Here the idea is you work with your agent to design and write a detailed step-by-step hackathon plan of what to do and leave the agent to do it (the way it does best).

### Install

```
/plugin marketplace add 11bho11/sprintflow
/plugin install sprintflow
```

### How it works
SprintFlow is a chain of slash commands. Each command produces a planning artifact in your `docs/` folder — you run `/clear` between commands, and the docs carry the state forward.

| Command | What it does |
|---|---|
| `/onboard` | Captures the hackathon brief, your profile, team composition, and sets the build track |
| `/ideation` | Re-entrant brainstorm session — validates ideas against judging criteria and timeline |
| `/scope` | Sharpens the committed idea into a concrete user, problem, and explicit cuts |
| `/prd` | Turns the scope into user stories, acceptance criteria, and non-goals |
| `/spec` | Builds the technical blueprint — stack, architecture, file structure, data flow |
| `/checklist` | Sequences the build into verifiable steps with time budget and ownership |
| `/build` | Executes the checklist in step-by-step or autonomous mode |
| `/iterate` | Polish and adjust mid-build or post-build before submission |
| `/submit` | Submission readiness check, video guidance, description, and social posting |
| `/pivot` | Archives existing artifacts and resets to the right phase when direction changes |
| `/sync` | Mid-hackathon team status summary — what's done, blocked, and at risk *(team only)* |

### Command Flow

```mermaid
flowchart TD
    ON(["/onboard"]) --> ID(["/ideation"])

    ID -- "standard / deep" --> SC(["/scope"])
    SC --> PR(["/prd"])
    PR --> SP(["/spec"])

    ID -- "sprint track" --> BR(["/brief"])
    BR --> SP

    SP --> CL(["/checklist"])
    CL --> BU(["/build"])
    BU --> IT(["/iterate"])
    IT --> SU(["/submit"])

    BU -. "team only" .-> SY(["/sync"])
    IT -. "team only" .-> SY

    BU -. "change direction" .-> PV(["/pivot"])
    IT -. "change direction" .-> PV

    PV -- "new idea" --> ID
    PV -- "new scope" --> SC
    PV -- "new approach" --> SP
    PV -- "new build plan" --> CL

    style ON fill:#EEEDFE,stroke:#534AB7,color:#3C3489
    style SU fill:#E1F5EE,stroke:#0F6E56,color:#085041
    style PV fill:#FAECE7,stroke:#993C1D,color:#712B13
    style SY fill:#E6F1FB,stroke:#185FA5,color:#0C447C
    style BR fill:#FAEEDA,stroke:#854F0B,color:#633806
```

### What gets produced
By the time you reach `/build`, your `docs/` folder contains:
```
docs/
├── hackathon-brief.md      ← judging criteria, timeline, rules, submission requirements
├── learner-profile.md      ← your background and goals
├── team-profile.md         ← team skills and ownership (team projects)
├── ideation-log.md         ← all ideas explored, alignment checks, final verdict
├── scope.md                ← sharpened idea, user, problem, explicit cuts
├── prd.md                  ← user stories, acceptance criteria, non-goals
├── spec.md                 ← architecture, stack, file structure, data flow
└── checklist.md            ← sequenced build steps with owners and time budget
```
These are the decision records for your project — useful for guiding your hackathon project and your agent on what to build.


### Build tracks

SprintFlow sets a build track during `/onboard` based on your available hacking timeframe:

| Track | Hours | Planning depth |
|-------|-------|----------------|
| Sprint | ≤6h | `/scope` and `/prd` merged into `/brief`; lightweight spec; no deepening rounds |
| Standard | 6–16h | Full command chain; deepening rounds optional |
| Deep | 16h+ | Full chain; deepening rounds actively encouraged |

You can override the track at any point.

---

## Commands

### `/onboard`
Your entry point to the hack. It captures two things before any planning begins:

- **Hackathon brief**: name, theme, judging criteria and weights, timeline, rules and constraints, submission requirements. This governs everything downstream: how deep the planning goes, which ideas are viable, what the build must produce.
- **Participant profile**: technical experience, prior hackathon history, goals for this event. If you're on a team, `/onboard` also captures team composition and skill distribution into `docs/team-profile.md`.


### `/ideation`
Brainstorm partner and adversarial judge in one command. This is the most rigorous command in the chain — every serious idea gets two passes before you're allowed to commit to it.

**Brainstorm pass**: open generation, research into adjacent projects, alignment checks across five dimensions: judging criteria fit, timeline feasibility, constraint compliance, demo-ability (is there a wow moment?), and originality.

**Adversarial judge pass**: runs on every idea you're serious about before commitment. Four challenges, each framed the way a skeptical judge would raise them:

- *Problem validity* — does this problem actually exist at the scale you're implying, or is this a solution looking for a problem?
- *The obvious alternative* — why wouldn't someone just use [spreadsheet / Google / existing app]? If you can't answer this sharply, the idea isn't ready.
- *Founder bias* — you're assuming the judge shares your context, enthusiasm, and understanding of the problem. They don't. What are you taking for granted?
- *Demo integrity* — does this only work because you set it up perfectly? What does a judge see if something goes slightly wrong?

The adversarial pass is not optional and is not softened. Finding the fatal flaw here saves every hour that follows. The output is a committed idea with a recorded demo moment and a known vulnerability — a specific objection and how to address it in the submission.

This command is **re-entrant** — run it multiple times across `/clear` cycles. All ideas and challenge results are preserved in `docs/ideation-log.md`.


### `/scope`
Takes the committed idea and makes it concrete: sharp user definition, specific problem statement, realistic scope given available time, and explicit cuts. 

*Not used in sprint track (≤6 hours) — use `/brief` instead, which merges scope and PRD.*


### `/prd`
Translates the scope into complete product requirements: user stories grouped into epics, testable acceptance criteria, edge cases, and explicit non-goals. Every requirement gets cross-referenced against the hackathon's judging rubric so nothing important gets missed.

*Not used in sprint track.*


### `/spec`
Builds the technical blueprint with you. Stack selection is driven by a decision framework that accounts for hackathon constraints, required technologies, team skill sets, and available time. Every proposed library or API gets verified against current documentation before it appears in the spec.


### `/checklist`
Breaks the spec into sequenced, verifiable build steps. Each item has five fields: spec reference, what to build, acceptance criteria, verification step, and owner (team mode). The last item is always a submission task written specifically for your hackathon's platform and requirements.

Includes a time budget check: estimated hours per item vs available hours, before you start building.


### `/build`
Executes the checklist. Supports two modes:

- **Step-by-step**: one checklist item per `/build` run, with per-item verification
- **Autonomous**: all items in one session

At any point during build you can call `/iterate` without finishing the checklist — you don't need to complete all items first.


### `/iterate`
Iterate on your current build whenever it's useful. Works in two modes:

- **Mid-build**: called after any checklist item to adjust something before continuing. Assesses impact on remaining items and time before making changes.
- **Post-build**: called after all items are complete to polish, add a feature, or fix something before submission. Opens with a plan-vs-reality pass — compares what was built against the original PRD acceptance criteria.


### `/pivot` — utility
Handles direction changes mid-workflow. Nothing gets deleted — prior artifacts are archived to `docs/archive/v1/` and the workflow resets to the appropriate phase.

- Completely different idea → resets to `/ideation`
- Same idea, different scope → resets to `/scope`
- Same scope, different technical approach → resets to `/spec`
- Same spec, different build plan → resets to `/checklist`


### `/sync` — utility, team only
Produces a 60-second team status summary: what's done, in progress, not started, and blocked — with a risk flag if current pace puts submission at risk. No artifact produced. Stateless — no `/clear` needed after running it.

---

## Contributing

Issues and PRs welcome. If you find a command produces a worse result for a specific hackathon type or time constraint, open an issue describing the context — the goal is for the planning depth to be genuinely useful across the full range of hackathon formats.

---

## License

MIT

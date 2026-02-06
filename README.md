# AI Product Team — Orchestration Workflow

## Overview

This repository defines a strict, role-based AI agent team for building digital products (mobile apps, web apps, SaaS). Each agent has a clearly defined scope, responsibilities, and owned documents. Agents must NOT operate outside their scope.

Agents coordinate through **Linear** (issue tracking) and share artifacts through the **`docs/`** folder in the project repository.

## Runtime Architecture

### How Agents Are Invoked

Each agent is a Claude session with a system prompt (the agent's `README.md` + templates).

```
Linear Event (webhook)
  → Framework receives: issue created / updated / comment with @mention
  → Framework determines which agent to invoke (by assignee, label, or mention)
  → Framework starts Claude session with the agent's system prompt
  → Framework passes the webhook context (issue details, comment text) as user message
  → Agent processes the request:
      1. Reads relevant docs/ files for context
      2. Does its work (analysis, writing, planning)
      3. Uses Linear MCP to update issues (comments, sub-issues, status changes)
      4. Returns a final message → posted back to the chat
  → For follow-up messages in the same thread, framework uses `resume`
```

### Trigger Events

| Event | What Happens |
|---|---|
| New issue assigned to agent | Agent picks up the issue, does its work, updates Linear |
| Comment mentioning @agent | Agent reads the comment context, responds via Linear + chat |
| Issue moved to agent's status | Agent picks up work for that phase |
| Sub-issue created for agent | Agent works on the sub-issue within parent context |

## Team Structure

| Agent | Folder | System Prompt | Primary Responsibility |
|---|---|---|---|
| [Product Manager](./product_manager/README.md) | `product_manager/` | `product_manager/README.md` | Vision, PRD, features, backlog, sprint planning |
| [UX Designer](./ux_designer/README.md) | `ux_designer/` | `ux_designer/README.md` | User flows, wireframes, UX documentation |
| [Head of Engineering](./head_of_engineering/README.md) | `head_of_engineering/` | `head_of_engineering/README.md` | Architecture, system design, tech stack, data models |
| [Software Engineer](./software_engineer/README.md) | `software_engineer/` | `software_engineer/README.md` | Code implementation following specs |
| [QA Engineer](./qa_engineer/README.md) | `qa_engineer/` | `qa_engineer/README.md` | Test plans, test cases, bug reports, validation |

## docs/ — Shared Artifact Store

The `docs/` folder in the project repository is the **primary source of truth** for all deliverables. Every agent reads from and writes to `docs/`.

```
docs/
├── prd.md                    # Product Requirements Document (PM)
├── feature_list.md           # Prioritized features (PM)
├── user_personas.md          # Target user definitions (PM)
├── user_stories/             # Individual story files (PM)
│   ├── US-001.md
│   └── ...
├── user_flows.md             # Journey maps (UX)
├── screen_inventory.md       # Screen specs with states (UX)
├── ux_review.md              # Heuristic evaluation results (UX)
├── architecture.md           # System design (HoE)
├── tech_stack.md             # Technology choices (HoE)
├── data_models.md            # Database schema (HoE)
├── api_contracts.md          # API endpoint specs (HoE)
├── technical_standards.md    # Coding conventions (HoE)
├── test_plan.md              # Test strategy (QA)
├── test_cases/               # Individual test case files (QA)
│   ├── TC-001.md
│   └── ...
└── bug_reports/              # Bug report files (QA)
    ├── BUG-001.md
    └── ...
```

**Rules:**
- `docs/` files are git-versioned and always up to date
- Each file is owned by one agent (see agent READMEs for ownership)
- Other agents may read any file but must NOT edit files they don't own
- Linear issue descriptions and comments reference `docs/` files but don't replace them

## Linear Conventions

### Statuses

```
Backlog → Todo → In Progress → In Review → QA → Done
```

| Status | Meaning |
|---|---|
| Backlog | Identified but not yet planned |
| Todo | Planned for current cycle, ready to pick up |
| In Progress | Agent is actively working on it |
| In Review | Work done, waiting for review/approval from another agent |
| QA | Implementation complete, waiting for QA Engineer testing |
| Done | All acceptance criteria verified, QA passed |

### Labels

**Agent labels** (who owns the work):
- `pm` — Product Manager
- `ux` — UX Designer
- `engineering` — Head of Engineering
- `dev` — Software Engineer
- `qa` — QA Engineer

**Type labels**:
- `epic` — High-level feature grouping
- `story` — User story with acceptance criteria
- `task` — Technical or design task
- `bug` — Defect found during QA
- `spike` — Research / investigation

### Issue Hierarchy

```
Project (Linear Project)
  └── Epic issue (feature-level, created by PM)
       ├── Story sub-issue (user story, created by PM)
       │    ├── UX sub-issue (design work, created by PM → assigned to UX)
       │    ├── Engineering sub-issue (architecture, created by PM → assigned to HoE)
       │    │    ├── Dev sub-issue (implementation task, created by HoE → assigned to SE)
       │    │    └── Dev sub-issue (another task, created by HoE → assigned to SE)
       │    └── QA sub-issue (testing, created by PM → assigned to QA)
       └── Bug issue (created by QA → assigned to SE, linked to story)
```

### Cycles

Linear Cycles = Sprints. Product Manager creates cycles and moves issues into them.

## Workflow — How the Team Operates

### Phase 1: Discovery & Planning (Product Manager)

1. **You (Product Owner)** create an issue or message describing your idea.
2. The Product Manager processes the request and produces:
   - `docs/prd.md` — Product Requirements Document
   - `docs/feature_list.md` — Prioritized features
   - `docs/user_personas.md` — Target users
   - `docs/user_stories/US-*.md` — Individual user stories
3. The Product Manager creates **Linear issues**: epic + story sub-issues.
4. The Product Manager creates **sub-issues for UX Designer and Head of Engineering**, assigning them with context.

### Phase 2: UX Design (UX Designer)

5. The UX Designer picks up assigned sub-issues.
6. Reads `docs/prd.md`, `docs/user_stories/`, `docs/user_personas.md` for context.
7. Produces:
   - `docs/user_flows.md`
   - `docs/screen_inventory.md`
   - `docs/ux_review.md`
8. Updates the Linear issue with a summary comment, moves to `In Review`.
9. Product Manager reviews and approves (or requests changes).

### Phase 3: Technical Architecture (Head of Engineering)

10. The Head of Engineering picks up assigned sub-issues.
11. Reads `docs/prd.md`, `docs/user_stories/`, `docs/user_flows.md`, `docs/screen_inventory.md`.
12. Produces:
    - `docs/architecture.md`
    - `docs/tech_stack.md`
    - `docs/data_models.md`
    - `docs/api_contracts.md`
    - `docs/technical_standards.md`
13. Creates **implementation sub-issues** for the Software Engineer in Linear (one per task).
14. Updates the engineering issue with a summary, moves to `Done`.

### Phase 4: Implementation (Software Engineer)

15. The Software Engineer picks up assigned sub-issues from Head of Engineering.
16. Reads `docs/` for full context: user stories, UX specs, architecture, API contracts.
17. Writes code, links branches/PRs to Linear issues.
18. Moves issues to `In Review` when done.
19. If specs are unclear — comments on the issue tagging Head of Engineering.

### Phase 5: Quality Assurance (QA Engineer)

20. Issues move to `QA` status after implementation review.
21. The QA Engineer picks up issues in `QA` status.
22. Reads `docs/` for specs, tests the implementation.
23. Produces:
    - `docs/test_plan.md`
    - `docs/test_cases/TC-*.md`
24. If tests pass → moves issue to `Done`.
25. If tests fail → creates **bug issues** in Linear assigned to Software Engineer, moves story back to `In Progress`.

## Communication via Linear

### How Agents Coordinate

Agents communicate through **Linear issue actions**, not direct messages:

| From | To | How |
|---|---|---|
| Product Manager | UX Designer | Creates sub-issue labeled `ux`, assigns |
| Product Manager | Head of Engineering | Creates sub-issue labeled `engineering`, assigns |
| Product Manager | QA Engineer | Creates sub-issue labeled `qa`, assigns |
| Head of Engineering | Software Engineer | Creates sub-issues labeled `dev`, assigns |
| QA Engineer | Software Engineer | Creates bug issue labeled `bug`, assigns |
| Any agent | Any agent | Comments on shared parent issue |
| Any agent | Product Manager | Comments on epic/story issue with concerns |

### Strictly Forbidden

- Product Owner directly assigning tasks to Software Engineer or QA
- Software Engineer making architecture decisions without Head of Engineering
- UX Designer defining technical implementation details
- QA Engineer modifying code or architecture
- Any agent operating outside their defined scope
- Any agent editing `docs/` files they don't own

## Agent Decision Loop

Every time an agent is invoked, it follows this loop:

```
1. Read the incoming context (issue details, comment, webhook data)
2. Read relevant docs/ files for background
3. Do the work (analysis, writing, planning)
4. Decide: do I need to update Linear?
   → Update issue description or status?
   → Add a comment with results?
   → Create sub-issues for other agents?
   → Create bug reports?
5. Execute Linear MCP actions
6. Return a final message to the chat
```

The final message is always returned to the user/chat — it summarizes what was done and what happens next.

## Document Ownership

Each agent owns specific `docs/` files and templates. Only the owning agent may create or modify their files. Other agents may read and reference them but never edit them.

See each agent's README for their owned documents and templates.

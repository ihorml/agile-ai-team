# AI Product Team — Orchestration Workflow

## Overview

This repository defines a strict, role-based AI agent team for building digital products (mobile apps, web apps, SaaS). Each agent has a clearly defined scope, responsibilities, and owned documents. Agents must NOT operate outside their scope.

## Team Structure

| Agent | Folder | Primary Responsibility |
|---|---|---|
| [Product Manager](./product_manager/README.md) | `product_manager/` | Vision, PRD, features, backlog, sprint planning |
| [UX Designer](./ux_designer/README.md) | `ux_designer/` | User flows, wireframes, UX documentation |
| [Head of Engineering](./head_of_engineering/README.md) | `head_of_engineering/` | Architecture, system design, tech stack, data models |
| [Software Engineer](./software_engineer/README.md) | `software_engineer/` | Code implementation following specs |
| [QA Engineer](./qa_engineer/README.md) | `qa_engineer/` | Test plans, test cases, bug reports, validation |

## Workflow — How the Team Operates

### Phase 1: Discovery & Planning (Product Manager)

1. **You (Product Owner)** communicate your idea or feature request to the **Product Manager**.
2. The Product Manager conducts brainstorming, asks clarifying questions, and produces:
   - Product Requirements Document (PRD)
   - Feature list with priorities
   - User personas
   - Success metrics
3. The Product Manager splits the PRD into **user stories** with acceptance criteria and organizes them into a **backlog**.

### Phase 2: UX Design (UX Designer)

4. The Product Manager hands the PRD and user stories to the **UX Designer**.
5. The UX Designer produces:
   - User flow diagrams (described in text/mermaid)
   - Screen inventory with descriptions
   - Wireframe specifications
   - UX review checklist
6. The Product Manager reviews and approves the UX deliverables before they move forward.

### Phase 3: Technical Architecture (Head of Engineering)

7. The Product Manager hands the approved PRD + UX docs to the **Head of Engineering**.
8. The Head of Engineering produces:
   - System architecture document
   - Tech stack decisions (with rationale)
   - Data models and database schema
   - API contracts
   - Algorithm specifications (if applicable)
   - Implementation plan broken into technical tasks
9. The Head of Engineering does NOT write code. They produce specs that the Software Engineer follows.

### Phase 4: Implementation (Software Engineer)

10. The **Software Engineer** receives:
    - User stories from Product Manager
    - UX specs from UX Designer
    - Technical specs from Head of Engineering
11. The Software Engineer writes code strictly following the provided specs. If the specs are ambiguous or missing, they escalate back to the Head of Engineering — they do NOT make architectural decisions on their own.
12. The Software Engineer maintains implementation guides and common patterns for onboarding.

### Phase 5: Quality Assurance (QA Engineer)

13. The **QA Engineer** receives:
    - User stories with acceptance criteria from Product Manager
    - UX specs from UX Designer
    - Completed implementation from Software Engineer
14. The QA Engineer produces:
    - Test plans per feature/story
    - Test cases (manual and automated specs)
    - Bug reports with reproduction steps
15. Any QA person should be able to pick up a story and start testing using the QA Engineer's documentation — no tribal knowledge.

## Communication Rules

### Allowed Communication Paths

```
Product Owner ──→ Product Manager ──→ UX Designer
                                  ──→ Head of Engineering ──→ Software Engineer
                                  ──→ QA Engineer

UX Designer ────→ Product Manager (review/feedback)
Head of Eng ────→ Product Manager (feasibility/scope concerns)
Software Eng ──→ Head of Engineering (technical questions)
QA Engineer ───→ Product Manager (acceptance failures)
               ──→ Software Engineer (bug reports)
```

### Strictly Forbidden

- Product Owner directly assigning tasks to Software Engineer or QA
- Software Engineer making architecture decisions without Head of Engineering
- UX Designer defining technical implementation details
- QA Engineer modifying code or architecture
- Any agent operating outside their defined scope

## Handoff Protocol

Every handoff between agents must include:

1. **Context**: What has been decided so far
2. **Deliverables**: The documents being handed off (linked)
3. **Expectations**: What the receiving agent is expected to produce
4. **Constraints**: Any limitations, deadlines, or non-negotiables

## Document Ownership

Each agent owns specific documents. Only the owning agent may create or modify their documents. Other agents may read and reference them but never edit them.

See each agent's README for their owned documents and templates.

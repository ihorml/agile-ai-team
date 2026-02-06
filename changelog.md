# Changelog

## 2026-02-06 — Linear MCP Integration Refactor

Refactored the entire agent framework from document-driven handoffs to Linear-based coordination.

### Added
- `team_context.md` — shared team structure file referenced by all agents (DRY)
- `mcp.json` — Linear MCP server configuration
- **Runtime Architecture** section in README (webhook → agent → Linear MCP → response)
- **`docs/` Shared Artifact Store** section with folder structure and ownership rules
- **Linear Conventions** — statuses, labels, issue hierarchy, cycles
- **Agent Decision Loop** — standardized read → work → update Linear → respond pattern
- Per-agent sections: **How You Are Invoked**, **Linear MCP Actions**, **docs/ Files You Own**, **Response Format**

### Changed
- `README.md` — complete rewrite for Linear-centric workflow
- All 5 agent READMEs — refactored with Linear MCP actions, `docs/` ownership, webhook invocation model
- Workflow phases now create/move Linear issues instead of prose handoffs
- Communication rules replaced with concrete Linear coordination table
- Templates remain as reference formats; actual deliverables go to `docs/`
- Team context extracted from duplicated inline blocks to shared `team_context.md`

### Design Decisions
- `docs/` is the primary source of truth (git-versioned, agent-accessible)
- Linear descriptions/comments are secondary coordination sugar
- Each agent README serves as its Claude system prompt
- Framework concatenates `team_context.md` + agent README for full system prompt

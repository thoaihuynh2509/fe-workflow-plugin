# fe-workflow-plugin

> Senior frontend engineer daily workflow plugin for Claude Code.
> React + TypeScript (strict) · Modular Monolith · Azure DevOps · Pro plan optimised.

---

## What it does

Covers the full engineering lifecycle in one plugin:

```
task-runner → planner → coder → reviewer → release-writer
```

Every task goes through: **Plan → Design → Implement → Test → Fix → Review → Docs → Release notes**

---

## Components

### Skills (trigger by phrase)
| Skill | Trigger |
|---|---|
| `fe-standards` | "coding standards", "right pattern?", "Modular Monolith" |
| `review-code` | "review my changes", "check before push" |
| `audit-performance` | "why is this slow", "perf audit" |
| `refactor` | "extract hook", "split component", "clean this up" |
| `release-docs` | "write release notes", "what do I tell users?" |

### Agents (autonomous)
| Agent | Trigger |
|---|---|
| `task-runner` | "work on AB#...", "implement feature", "fix this bug" |
| `refactor-runner` | "migrate all features/ to modules/", "full refactor" |

### Subagents (spawned by task-runner)
| Subagent | Model | Role |
|---|---|---|
| `planner` | opus · medium | Phase 1–2: plan + design |
| `coder` | sonnet · medium | Phase 3–5: implement + test + fix |
| `reviewer` | sonnet · high | Phase 6–7: review + docs + commit |
| `release-writer` | sonnet · medium | Phase 8: user-facing release notes |

---

## Install

### User scope (all projects)
```bash
claude plugin add https://github.com/thoaihuynh2509/fe-workflow-plugin --scope user
```

### Project scope (shared with team)
```bash
claude plugin add https://github.com/thoaihuynh2509/fe-workflow-plugin --scope project
```

### Via TUI
```
/plugin → Marketplaces → Add → https://github.com/thoaihuynh2509/fe-workflow-plugin
```

---

## Daily usage

```bash
# Start a task from a ticket
"Work on AB#1892 — notifications dropdown"

# Fix a bug
"Fix TypeError at UserList.tsx:47"

# Before pushing
"Review my changes"

# Something is slow
"Audit the dashboard for performance issues"

# End of sprint
"Write release notes for this branch"

# Migrate old structure
"Migrate src/features/ to Modular Monolith"
```

---

## Stack assumptions
- React 18 + TypeScript 5 (strict mode)
- Azure DevOps (branches, PRs, AB# work items)
- Modular Monolith architecture (`modules/` → `shared/` → `app/` → `pages/`)
- Quality gates: `npx tsc --noEmit && npm run lint && npm test`

> To adapt to your stack: edit `skills/fe-standards/SKILL.md` and `hooks/hooks.json`.

---

## Structure
```
.claude-plugin/plugin.json
skills/
  fe-standards/       SKILL.md + 4 references
  review-code/        SKILL.md
  audit-performance/  SKILL.md
  refactor/           SKILL.md
  release-docs/       SKILL.md + examples reference
agents/
  task-runner.md
  refactor-runner.md
  subagents/
    planner.md
    coder.md
    reviewer.md
    release-writer.md
    references/       phase-gates.md, claudemd-template.md
hooks/
  hooks.json
```

---

## Version
`v0.7.0` — 5 skills · 2 agents · 4 subagents · 2 hooks · 7 references · ~5,400 tokens

---
name: refactor-runner
description: >
  Large-scale autonomous refactors. Triggers: "migrate all features to modules",
  "refactor entire <module>", "clean up codebase structure".
  For single-file → use refactor skill.

  <example>
  user: "Migrate src/features/ to Modular Monolith"
  assistant: "refactor-runner: analyse → plan → migrate → verify."
  </example>

model: sonnet
effort: medium
color: magenta
tools: ["Read", "Write", "Edit", "Bash", "Grep", "Glob"]
---

Restructure without changing behaviour. Tests break → fix the refactor.

## Phases
1. **Analyse** — `find src -type f \( -name "*.ts" -o -name "*.tsx" \) | sort` + read CLAUDE.md
2. **Plan** — print before touching: goal, create → move → update imports → delete, test count
3. **Execute** — strict order: create stubs → migrate → update imports → fill index.ts → delete old. `npx tsc --noEmit` after each step.
4. **Verify** — `npx tsc --noEmit && npm run lint && npm test`
5. **UI check** — if UI moved: open `https://reactdev.sqreemtech.com/`, confirm no regressions
6. **CLAUDE.md** — update Modules table + Recent Significant Changes

Commit one per logical unit: `refactor(<scope>): <what>`.
Ref: `skills/fe-standards/references/modular-monolith.md`

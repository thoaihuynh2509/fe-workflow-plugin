---
name: refactor
description: >
  Targeted refactoring. Triggers: "refactor", "clean up", "extract hook", "split component",
  "migrate to modules", "file too big". For multi-file autonomous refactors → refactor-runner agent.
metadata:
  version: "0.3.0"
---

**Prime directive**: behaviour must not change. Tests break → fix the refactor, not the tests.

Types: extract hook · split component · migrate to module · remove duplication · strengthen types

## Process
1. Read files + find all consumers: `grep -r "from.*<file>" src -l`
2. Plan: create → modify → update imports → delete (strict order)
3. Execute — never delete before imports updated. `npx tsc --noEmit` after each step.
4. Final: quality gate. Update CLAUDE.md.
5. Commit: `refactor(<scope>): <summary>` — no behaviour change.

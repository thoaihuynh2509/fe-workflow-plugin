# Azure DevOps Workflow

## Branches
`feature/<AB#>-<desc>` · `bugfix/<AB#>-<desc>` · `hotfix/<AB#>-<desc>` · `perf/<desc>` · `refactor/<desc>` · `chore/<desc>`

## Commits (Conventional)
`<type>(<scope>): <summary>` — types: feat, fix, perf, refactor, test, chore, docs, ci
Footer: `AB#<id>` to link Azure Boards.

## PR template
```markdown
## Summary
## Changes
## Work Item — AB#<id>
## Test Plan
- [ ] Unit tests · [ ] Dev tested · [ ] Edge cases
## Screenshots (UI changes)
## Checklist
- [ ] No `any` · [ ] Strict types · [ ] Accessible · [ ] No unused imports
```

## PR size
Small (<200 lines preferred) · Medium (200–500, detailed summary) · Large (>500, split if possible)

## Review etiquette
Prefix: `nit:` minor · `question:` clarification · `blocker:` must fix.

# CLAUDE.md Template

Minimum viable CLAUDE.md for a new project:

```markdown
# <Project Name>

## Stack
- React 18 + TypeScript 5 (strict)
- <state manager> · <styling> · <testing lib>
- Azure DevOps · Node <version>

## Architecture: Modular Monolith
src/modules/ → src/shared/ → src/app/ → src/pages/

## Modules
| Module | Domain | Public exports |
|---|---|---|
| auth | Auth, sessions | useAuth, AuthGuard, User |

## Key Patterns
- All data fetching via React Query — no raw fetch() in components
- <pattern>

## Known Gotchas
- <gotcha>

## Recent Significant Changes
- YYYY-MM-DD AB#<id>: modules/<name> — <one-line summary>

## TODO / Tech Debt
- [ ] <item>
```

## Update rules
- Append to Recent Significant Changes — never rewrite history
- New module → update Modules table
- New pattern → update Key Patterns
- Gotcha found → update Known Gotchas
- Never store secrets, line-by-line code, or content duplicated in README

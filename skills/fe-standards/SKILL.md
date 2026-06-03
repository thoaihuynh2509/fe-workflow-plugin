---
name: fe-standards
description: >
  React + TypeScript coding standards. Triggers: "coding standards", "naming conventions",
  "how should I structure this", "right pattern?", "TypeScript best practices", "React patterns",
  "Modular Monolith". Also referenced by all agents.
metadata:
  version: "0.3.0"
---

Stack: React 18 · TypeScript 5 (strict) · Modular Monolith · Azure DevOps

## Rules (canonical — all agents inherit these)
- No `any` — use `unknown` + narrowing. No `@ts-ignore` without justification.
- Explicit return types on all exports. No `console.log` in committed code.
- `interface` for objects, `type` for unions. `?.` and `??` over `!`.
- Functional components only. Props typed with `interface`.
- Custom hooks for stateful logic (`use` prefix). `useMemo` for derived state, not `useEffect`.
- Error + loading + empty states on every async op. Semantic HTML + `aria-*`.

## Structure: Modular Monolith
```
src/
├── modules/<domain>/   # bounded context: components, hooks, services, types
│   └── index.ts        # PUBLIC API — only import via this
├── shared/             # zero domain knowledge: Button, formatDate, ApiResponse<T>
├── app/                # wiring: router, providers, layouts
└── pages/              # thin route shells
```
Import rule: `import { X } from '@/modules/auth'` ✅ — internal paths ❌
Deps: pages → modules → shared (never reverse)

## Naming
Component: PascalCase · Hook: `use` + camelCase · Type: PascalCase · Constant: UPPER_SNAKE

## Quality gate (run before every commit)
```bash
npx tsc --noEmit && npm run lint && npm test -- --related --passWithNoTests
```

## References (load on demand)
- `references/modular-monolith.md` — zones, dependency rules, module checklist
- `references/component-patterns.md` — compound, refs, event typing
- `references/typescript-patterns.md` — branded types, discriminated unions
- `references/azure-devops-workflow.md` — branches, commits, PR template

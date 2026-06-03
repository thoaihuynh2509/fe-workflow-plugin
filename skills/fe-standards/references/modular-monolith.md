# Modular Monolith

Single deployable app, self-contained domain modules. Each module owns components, hooks, services, types. Communication only via `index.ts` public API.

## Structure
```
src/
├── modules/<domain>/       # bounded context
│   ├── components/         # domain components
│   ├── hooks/              # domain hooks
│   ├── services/           # API calls (no business logic)
│   ├── store/              # module-scoped state
│   ├── types.ts            # create first
│   ├── constants.ts
│   └── index.ts            # PUBLIC API — only export what others need
├── shared/                 # zero domain knowledge: Button, formatDate, ApiResponse<T>
├── app/                    # wiring: router, providers, layouts
└── pages/                  # thin route shells rendering module components
```

## Three zones
**modules/** — bounded contexts. Never import another module's internals.
**shared/** — generic only. No module imports, no domain knowledge.
**app/** — wiring only. No business logic.

## Import rules
```ts
import { useAuth } from '@/modules/auth'                    // ✅ public API
import { useAuth } from '@/modules/auth/hooks/useAuth'      // ❌ internal path
```

## Dependency direction
`pages → modules → shared` — never reverse. `shared` imports nothing internal.

## Module index.ts — public API contract
Export only what other modules actually import. Services, store internals stay private.

## Path aliases (tsconfig)
`@/modules/*`, `@/shared/*`, `@/app/*`, `@/pages/*`

## New module checklist
Start with `types.ts` + `index.ts`. Add `components/`, `hooks/`, `services/` as needed.

## When to split
>15 components, distinct sub-domains, or team boundary. Don't split prematurely.

## Linting
`eslint-plugin-import` with zone rules to catch cross-module internal imports at CI.

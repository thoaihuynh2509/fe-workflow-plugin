---
name: audit-performance
description: >
  Performance audit. Triggers: "audit performance", "why is this slow", "optimise",
  "reduce rerenders", "laggy", "bundle too large", "perf audit".
metadata:
  version: "0.3.0"
---

Audit across: rendering, bundle, network. Scope: file given → that file; else → changed files.

## Checklist
**Rendering**: inline obj/fn props, missing memo (only where justified), context too broad, unvirtualised lists, useEffect infinite loops
**Bundle**: heavy deps (moment→date-fns, full lodash→tree-shaken), missing React.lazy on routes, duplicate packages
**Network**: waterfall requests, missing staleTime, no pagination

## Output
Per file: 🔴 Critical / 🟡 Moderate / 🔵 Minor / ✅ Good — with impact + fix.
Priority by impact÷effort. Branch: `perf/<desc>`.

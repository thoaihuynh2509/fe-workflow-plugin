---
name: review-code
description: >
  Code review. Triggers: "review my code", "review changes", "check before push",
  "review PR", "is this code good?", "self-review".
metadata:
  version: "0.3.0"
---

Review changed files. Scope: file given → that file; no file → `git diff --name-only HEAD`.

## Tiers
🔴 **Blocker** — `any`/`@ts-ignore`, null crashes, XSS, missing a11y, unhandled async
🟡 **Warning** — inline obj/fn props, wrong useEffect deps, >200-line component, missing states
🔵 **Suggestion** — naming, extractable hooks, test gaps
✅ **Positive** — call out good patterns

## Output
Per file: `## <path>` → 🔴/🟡/🔵/✅ with `Line N: issue → fix`.
Verdict: `✅ Ready` / `🟡 Minor fixes` / `🔴 Do not merge`.

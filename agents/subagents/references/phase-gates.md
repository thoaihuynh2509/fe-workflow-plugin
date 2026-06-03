# Phase Gates

| Phase | Agent | Exit |
|---|---|---|
| 1. Plan | planner | Branch exists, checklist → `PLANNER_DONE` |
| 2. Design | planner | Component tree + key types defined |
| 3. Implement | coder | All files written, `tsc --noEmit` clean |
| 4. Test | coder | `tsc + lint + test` all exit 0 |
| 5. Fix loop | coder | Phase 4 green → `CODER_DONE` |
| 6. Review | reviewer | Zero 🔴 blockers |
| 7. Docs | reviewer | CLAUDE.md updated, commit + PR → `REVIEWER_DONE` |
| 8. Release | release-writer | User-facing release notes generated |

Gate: `npx tsc --noEmit && npm run lint && npm test -- --related --passWithNoTests`
Fix loop: never delete tests, never `any`, 3 fails same error → stop.

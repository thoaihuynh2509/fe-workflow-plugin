# Release Notes Examples

## Commit → release note translation

| Raw commit | Release note |
|---|---|
| `feat(notifications): add unread badge with polling` | You can now see unread notification count at a glance |
| `fix(auth): resolve blank screen after OAuth login` | Fixed a blank screen that appeared after signing in with Google |
| `perf(dashboard): virtualise table rows` | Dashboard loads significantly faster with large data sets |
| `refactor(modules): migrate features/ to modules/` | — internal only, omit |
| `chore: update dependencies` | — omit |
| `feat(avatar): upload, crop, preview profile photo` | Upload and crop your profile photo directly in settings |
| `fix(modal): prevent body scroll when open` | Fixed page scrolling in the background when a dialog is open |

## Good vs bad
❌ "Implemented useNotifications hook with React Query polling every 30s"
✅ "Notifications update automatically — no need to refresh"

❌ "Migrated UserTable to modules/users with public API"
✅ (omit — internal refactor)

❌ "Fixed null dereference in UserList.tsx:47"
✅ "Fixed a crash when the user list was empty"

## Tone
- Friendly but professional. No exclamation marks.
- Past tense for fixes ("Fixed…"), present for features ("You can now…").
- Group related commits into one line when possible.

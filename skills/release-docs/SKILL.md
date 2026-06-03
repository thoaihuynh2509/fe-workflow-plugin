---
name: release-docs
description: >
  Generate user-facing release notes. Triggers: "release notes", "write release docs",
  "what changed in this release", "release summary", "what do I tell users?".
metadata:
  version: "0.2.0"
---

Generate release notes from git history. Delegates to the release-writer subagent rules.

## Gather
```bash
git log origin/main...HEAD --oneline
git diff origin/main...HEAD --stat
cat CLAUDE.md 2>/dev/null | head -40 || true
```

## Rules
User language only, benefit-first, no AB#/tickets/tech stack, one line per item, active voice.
Group: ✨ New → ⚡ Improved → 🐛 Fixed. Omit empty sections.
Omit refactors/chores/deps — if internal only: "No user-facing changes in this release."
Past tense for fixes, present for features.

Ref: `references/release-notes-examples.md` for translation examples.

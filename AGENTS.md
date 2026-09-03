# Repository instructions for Codex

This repository is a handoff bridge between ChatGPT on the web and Codex.

## Required completion protocol

- Inspect `HANDOFF.md`, the recent Git history, and the current working tree before making changes.
- Preserve unrelated user changes and never commit secrets, credentials, `.env` files, or machine-specific settings.
- Do task work on a dedicated branch named `codex/<short-task-name>`. Do not work directly on `main` unless the user explicitly requests it.
- Run checks or tests appropriate to the changed files before completion.
- Update `HANDOFF.md` with the current task, result, validation, branch, commit information when known, and the recommended next action.
- Commit only the task's intended changes with a clear message.
- Push the task branch to `origin` and set its upstream. Never force-push unless the user explicitly requests it.
- If pushing is blocked by missing authentication, permissions, or a remote, report the exact blocker and leave the local commit intact.

## Final response format

Always report these fields at the end of a completed task:

- Repository: `OWNER/REPO`
- Branch: `branch-name`
- Commit: `full-or-short-sha`
- Validation: checks run and their result
- Handoff: one concise next action

Keep the final response compact so another ChatGPT or Codex session can resume from the repository state without replaying the full conversation.

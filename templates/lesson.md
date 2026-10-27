# Lesson template

Copy this for any new lesson. Keep it short. One lesson per file, or one section in an existing topic file.

```markdown
# <Topic>: <the rule in a few words>

_Learned <Mon DD, YYYY> on <project> (<stack>)._

## What happened
What broke or cost money, in two or three sentences.

## Root cause
Why it happened.

## The rule
1. The rule, in one line.
2. Any follow-on steps.

## Verify
- How to check that a project follows the rule.

## Reference
<owner/repo>#<PR> or commit SHA, plus the files involved.
```

## When adding a lesson
- Add its one-line rule to `AGENTS.md` and link the file.
- If it applies when starting a project, add a line to `checklists/new-project.md`. If it applies at go-live, add one to `checklists/launch.md`.
- Mark anything not yet confirmed as **Unconfirmed**.

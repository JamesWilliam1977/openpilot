---
name: athenad-feature-or-fix-workflow
description: Workflow command scaffold for athenad-feature-or-fix-workflow in openpilot.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /athenad-feature-or-fix-workflow

Use this workflow when working on **athenad-feature-or-fix-workflow** in `openpilot`.

## Goal

Implements new features or fixes in the Athena daemon, often accompanied by corresponding test updates.

## Common Files

- `openpilot/system/athena/athenad.py`
- `openpilot/system/athena/tests/test_athenad.py`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or extend openpilot/system/athena/athenad.py to implement the feature or fix.
- If applicable, update or add tests in openpilot/system/athena/tests/test_athenad.py.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.
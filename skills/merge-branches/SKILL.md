---
name: merge-branches
description: Merge changes from multiple git worktrees into a single integration branch with conflict resolution, testing, and safe push behavior. Use this skill when the user asks to "MERGE BRANCHES" or asks to combine branch changes one by one from multiple worktrees.
---

# Merge Branches

Follow this workflow exactly.

## Hard Constraints

- Use only the `codex/dev-merge` worktree and `codex/dev-merge` branch.
- Create the `codex/dev-merge` worktree/branch if it does not exist.
- Do not push any branch except `codex/dev-merge`.

## Workflow

1. Checkout `codex/dev-merge`.
2. Make a list of branches that have changes to merge.
3. Process branches one by one in list order.
4. Merge the current branch into `codex/dev-merge`.
5. Resolve all merge conflicts before proceeding.
6. Run project tests after conflict resolution.
7. If tests fail, fix issues and create a patch commit on `codex/dev-merge`.
8. If conflicts are resolved and tests pass, push `codex/dev-merge`.
9. Move to the next branch with unmerged changes.
10. Repeat steps 4-9 until all branches are handled.
11. Write a summary of newly merged features.

## Execution Notes

- Keep merge commits and patch commits scoped to the active branch integration step.
- Do not skip tests between branch merges.
- If a branch is already fully merged, record it and continue to the next branch.

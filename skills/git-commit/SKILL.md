---
name: git-commit
description: Prepare and perform a safe Conventional Commit for the current Git repository. Use when Codex needs to inspect staged and unstaged changes, propose a single English Conventional Commit message, show exactly what would be staged, ask for explicit yes/y approval, and only then run the commit.
---

# Git Commit

Prepare a safe Git commit without changing repository state until the user explicitly approves.

## Workflow

1. Run `git status --short` to inspect the working tree.
2. Run `git diff --staged` to inspect already staged changes.
3. Determine whether any tracked or untracked changes are not currently staged.
4. If unstaged changes exist, run `git diff --stat` and summarize them briefly.
5. Propose exactly one Conventional Commit message in English using this format:

```text
<type>(<scope>): <subject>
```

6. Prefer these types for this repository: `feat`, `fix`, `test`, `build`, `docs`.
7. Use `refactor` only when it is clearly the best fit.
8. Keep the subject imperative, lowercase, and without a trailing period.
9. Before asking for confirmation, show:
   - the proposed commit message
   - the exact commit scope
10. If unstaged changes exist, show the exact unstaged file list that would be added by `git add -A`.
11. Do not list files that are already staged.
12. Ask for confirmation after showing the message and any unstaged file list.

## Approval Rules

- Treat only `yes` and `y` as approval.
- Any other reply means do not make Git changes.
- Approval authorizes staging the unstaged files just shown and committing the full staged result.
- Do not ask for additional confirmation after that approval.

## Execution Rules

- Do not perform any Git write operation before approval.
- Execute Git write operations strictly serially, never in parallel.
- Do not use any parallel tool wrapper for `git add` or `git commit`.
- If unstaged changes exist, perform staging and commit in a single shell invocation so execution remains serial:

```bash
git add -A && git commit -m "<commit message>"
```

- If everything is already staged, run:

```bash
git commit -m "<commit message>"
```

## Stop Conditions

- Stop without changing Git state if the user does not approve.
- Stop and explain the blocker if the repository state prevents a safe commit.

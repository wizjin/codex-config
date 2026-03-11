---
description: Generate and perform a conventional git commit
---

Help me prepare a git commit safely.

1. Run `git status --short` to inspect the working tree.
2. Run `git diff --staged` to inspect already staged changes.
3. If any tracked or untracked changes are not currently staged, run `git diff --stat` and summarize them.
4. Propose one Conventional Commit message in English using this format:
   `<type>(<scope>): <subject>`
   Preferred types for this repository: `feat`, `fix`, `test`, `build`, `docs`
   Optional type when clearly appropriate: `refactor`
   Keep the subject imperative, lowercase, and without a trailing period.
5. Before asking for confirmation, show the proposed commit message and the exact commit scope.
6. If any tracked or untracked changes are not currently staged, show the exact unstaged file list that would be added by `git add -A`. Do not list files that are already staged.
7. Then ask for confirmation. Treat only these replies as approval to continue: `yes`, `y`. This approval authorizes both staging the unstaged files just shown and committing the full staged result. Any other reply means do not make git changes.
8. Only after confirmation:
   - if any tracked or untracked changes are not currently staged, run `git add -A`
   - do not ask for any additional confirmation before staging or committing
   - run `git commit -m "<commit message>"`
9. If the user does not confirm, stop without changing git state.

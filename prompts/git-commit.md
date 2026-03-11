---
description: Generate and perform a conventional git commit
---

Help me prepare a git commit safely.

1. Run `git status --short` to inspect the working tree.
2. Run `git diff --staged` to inspect already staged changes.
3. If nothing is staged, run `git diff --stat` and summarize the unstaged changes.
4. Propose one Conventional Commit message in English using this format:
   `<type>(<scope>): <subject>`
   Preferred types for this repository: `feat`, `fix`, `test`, `build`, `docs`
   Optional type when clearly appropriate: `refactor`
   Keep the subject imperative, lowercase, and without a trailing period.
5. Show the proposed commit message to the user and ask for confirmation. If the user replies exactly `yes`, treat that as approval to continue. Any other reply means do not make git changes.
6. Only after confirmation:
   - if the user asked to include all current changes, run `git add -A`
   - run `git commit -m "<commit message>"`
7. If the user does not confirm, stop without changing git state.

---
name: session-learn
description: Extract reusable rules from the current session and merge them into the current project's AGENTS.md safely. Use when Codex needs to analyze repeated mistakes, avoidable clarification loops, weak assumptions, or tool misuse, propose compact rule changes, respect protected AGENTS.md sections, ask for explicit yes/y approval, and only then edit AGENTS.md.
---

# Session Learn

Extract durable lessons from the current session and update `AGENTS.md` safely without making unrelated edits.

## Workflow

1. Use the current session as the primary source of lessons.
2. Extract reusable lessons from repeated mistakes, avoidable clarification loops, redundant exploration, weak assumptions, tool misuse, and similar workflow friction.
3. Keep only general, actionable rules.
4. Reject anything task-specific, merely descriptive, or already covered by an existing rule with the same intent.
5. Resolve the target file as `AGENTS.md` at the current project root.
6. Read `AGENTS.md` before proposing any changes.
7. If `AGENTS.md` does not exist, stop and tell the user.
8. Prefer rewriting or merging existing rules.
9. Add a new rule only when the lesson cannot be absorbed cleanly into the existing file.
10. Keep the result compact and non-redundant.
11. Write candidate rules as short, imperative instructions for future LLM execution.

## Protected Sections

- Respect any protected sections in `AGENTS.md`.
- If the file requires user confirmation for some sections, do not edit those sections without explicit approval.

## Approval Flow

1. Output a short, scannable modification summary before making edits.
2. Include:
   - rules to rewrite
   - rules to add, if any
   - rules rejected as too specific or redundant
   - one short reason per item
3. Ask for explicit approval after that summary.
4. Treat only `yes` and `y` as approval.
5. Any other reply means stop without changing files.

## Edit Rules

- Edit `AGENTS.md` only after explicit approval.
- Make no unrelated edits.
- Preserve the existing structure where possible.
- After editing, show a concise summary of the applied changes.

---
description: Summarize reusable rules from the current session and merge them into AGENTS.md safely
---

Analyze the current session and extract reusable rules that improve future LLM behavior. Then update the current project's `AGENTS.md` safely.

1. Use the current session as the primary source. Extract lessons from repeated mistakes, avoidable clarification loops, redundant exploration, weak assumptions, tool misuse, and other recurring workflow friction.
2. Keep only general, actionable rules. Reject anything task-specific, descriptive without operational value, or already covered by an existing rule with the same intent.
3. Resolve the target file as `AGENTS.md` at the current project root. Read that file before proposing changes. If it does not exist, stop and tell the user. Prefer rewriting or merging existing rules. Add a new rule only when the lesson cannot be absorbed cleanly. Keep the result compact and non-redundant.
4. Write candidate rules for LLM execution: short, imperative, and easy to apply during generation.
5. Respect protected sections in `AGENTS.md`. If the file requires user confirmation for some sections, do not edit them without explicit approval.
6. First output a short modification summary. Keep it brief and scannable. Do not write long explanations. Include:
   - rules to rewrite
   - rules to add, if any
   - rules rejected as too specific or redundant
   - one short reason per item
7. Then ask for explicit approval. Treat only these replies as approval: `yes`, `y`. Any other reply means stop without changing files.
8. Only after explicit approval, update `AGENTS.md` with no unrelated edits and preserve the existing structure where possible.
9. After editing, show a concise summary of the applied changes.

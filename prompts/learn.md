---
description: Summarize reusable rules from the current session and merge them into AGENTS.md safely
---

Analyze the current session and extract reusable operating rules for future LLM turns. Update the current project's `AGENTS.md` safely.

1. Use the current session conversation as the primary source. Extract patterns from repeated mistakes, repeated clarification loops, redundant exploration, avoidable tool misuse, weak assumptions, and workflow friction.
2. Optimize for future LLM execution, not for human prose. Rules should be:
   - short
   - imperative
   - operational
   - easy to apply during generation
3. Prefer rules that prevent classes of failure. Reject anything that is:
   - specific to a single task
   - merely descriptive instead of actionable
   - already covered by an existing rule with the same intent
4. Read the current project's `AGENTS.md` before proposing anything.
5. Merge before adding:
   - if an existing rule partially covers the intent, rewrite that rule to absorb the new lesson
   - add a new rule only when no existing rule can absorb it cleanly
   - keep the final rule set compact and non-redundant
6. When proposing wording, write candidate rules in a form that is easy for an LLM to follow inside `AGENTS.md`. Prefer direct command-style bullets over explanatory sentences.
7. Respect protected sections in `AGENTS.md`. If the file says some sections require user confirmation to change, do not edit them unless the user explicitly approves.
8. First output a short `Modification Summary` only. It must include:
   - rules to rewrite
   - rules to add, if any
   - rules considered but rejected as too specific or redundant
   - one short reason per item
9. After the summary, ask the user to reply exactly `yes` to approve the `AGENTS.md` edit. Any other reply means stop without changing files.
10. Only after the user replies exactly `yes`:
   - update `AGENTS.md`
   - preserve brevity and existing structure where possible
   - avoid unrelated edits
11. After editing, show a concise summary of the applied changes.

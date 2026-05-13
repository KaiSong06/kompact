---
name: kompact
description: Create a concise handoff.md for continuing the current Claude Code session later.
disable-model-invocation: true
---

# Kompact

Create or replace `handoff.md` for the current work. This is a continuation handoff, not a transcript or archive.

## Workflow

1. Read `${CLAUDE_SKILL_DIR}/references/handoff-template.md` before writing the handoff.
2. Identify the handoff location:
   - Use the git repository root when available.
   - If no git root is available, use the current working directory.
3. Inspect the current work state before writing:
   - Current working directory and git root, when available.
   - Git status and changed file names, when available.
   - Relevant recent conversation context, especially decisions, failed attempts, assumptions, and the current next step.
4. Write `handoff.md` at the chosen location, replacing any existing handoff.
5. After writing, briefly report the handoff path and the next step captured.

## Handoff Rules

- Use the exact section structure from `references/handoff-template.md`.
- Keep the handoff concise. Prefer short bullets over narrative recap.
- Prioritize continuation facts: goal, current state, active files, touched work, failed attempts, assumptions, and next action.
- Use repo-relative paths for active files when possible.
- Do not paste full diffs, logs, or conversation transcripts.
- Mark missing facts as `Unknown` or `None known`; do not invent them.
- If writing fails, report the failure directly and do not claim the handoff exists.

## Output Discipline

The chat response after writing should be short:

- State where `handoff.md` was written.
- State the captured next step.
- Mention any important unknowns only if they affect continuation.

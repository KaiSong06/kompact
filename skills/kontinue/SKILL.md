---
name: kontinue
description: Continue the current Claude Code session from an existing handoff.md.
disable-model-invocation: true
---

# Kontinue

Continue from an existing `handoff.md`. Treat the handoff as the starting context for this session unless the user redirects.

## Workflow

1. Locate `handoff.md`:
   - Prefer the git repository root when available.
   - If no git root is available, check the current working directory.
2. If `handoff.md` does not exist, stop and tell the user no handoff was found. Do not invent continuation context.
3. Read `handoff.md` before taking other action.
4. Check for obvious metadata mismatches:
   - The handoff's working directory differs from the current git root or current working directory.
   - The handoff is missing required sections.
5. If there is an obvious mismatch, surface it briefly and ask whether to proceed from the handoff anyway.
6. If the handoff is usable, continue from the `Next step` section while preserving the rest of the handoff as context.

## Expected Handoff Sections

A valid Kompact handoff should include:

- Goal
- Current state
- Active files being modified
- What was touched this session
- What did not work and why
- Next step

## Continuation Rules

- Do not summarize the handoff back at length.
- Do not modify `handoff.md` unless the user explicitly asks.
- Do not retry failed work listed in the handoff without explaining why it is now appropriate.
- If the `Next step` section is missing or unclear, ask the user for direction instead of guessing.
- If the user redirects, follow the user's latest instruction over the handoff.

## Output Discipline

The first response after reading the handoff should be short:

- Confirm that `handoff.md` was read.
- State the next step you are about to take.
- Surface only blocking mismatches or unknowns.

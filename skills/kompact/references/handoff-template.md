# Kompact Handoff Contract

`handoff.md` is a continuation artifact, not a transcript. Keep it tight enough for a fresh Claude Code session to read quickly while preserving the working facts needed to resume.

## Default Location

Write `handoff.md` at the repository root when a git root can be identified. If no git root is available, write it in the current working directory.

## Required Shape

Use this structure exactly:

```markdown
# Handoff

Generated: <local timestamp or Unknown>
Working directory: <repo root or current working directory>

## Goal

- <The user-visible outcome or task being pursued.>

## Current State

- <What is true now, including completed work and any important constraints.>

## Active Files Being Modified

- `<repo-relative path>`: <why it matters right now>
- Unknown: <only when active files cannot be determined>

## What Was Touched This Session

- <Specific files, docs, commands, decisions, or investigations touched during this session.>

## What Did Not Work And Why

- <Failed attempt>: <why it failed or why it was abandoned>
- None known: <use when no failed attempt is known from available context>
- Unknown: <use when the session context is insufficient>

## Next Step

- <The single best next action for the continuing session.>
```

## Writing Rules

- Prefer bullets over paragraphs.
- Keep each section focused on continuation state.
- Preserve mid-conversation decisions, assumptions, failed attempts, and next actions.
- Include active file paths repo-relative when possible.
- Summarize bulky details instead of pasting full diffs, logs, or transcripts.
- Mark missing facts as `Unknown` or `None known` instead of inventing them.
- Avoid sensitive details when a short description is enough for continuation.
- Do not add archive/history sections in v1.

## Quality Bar

A fresh session should be able to read the handoff and answer:

- What are we trying to accomplish?
- What has already happened?
- Which files are in play?
- What should not be retried?
- What should happen next?

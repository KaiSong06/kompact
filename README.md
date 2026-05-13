# Kompact

Kompact is a Claude Code plugin for concise session handoffs. It provides two namespaced skills:

- `/kompact:kompact` creates or replaces a repo-local `handoff.md`.
- `/kompact:kontinue` reads `handoff.md` and continues from the recorded next step.

The goal is to preserve the working state that often gets lost during `/compact` without carrying a long transcript into the next session.

## Install From Marketplace

After this repository is pushed to GitHub, add the marketplace in Claude Code:

```text
/plugin marketplace add KaiSong06/kompact
/plugin install kompact@kaisong-plugins
```

Then restart or run `/reload-plugins` if Claude Code asks you to reload.

## Install Locally

From the parent directory of this repository:

```sh
claude --plugin-dir ./kompact
```

Inside Claude Code, run `/help` or type `/kompact` in slash-command discovery to filter for the namespaced skills. After editing plugin files during development, run `/reload-plugins`.

## Usage

Run `/kompact:kompact` when a session has useful working context that should survive into a later session. The skill writes `handoff.md` at the repository root when a git root is available, or in the current working directory otherwise.

Run `/kompact:kontinue` in a fresh or later session from the same repository. The skill reads `handoff.md`, treats it as the continuation context, and proceeds from the recorded next step unless you redirect it.

## Handoff Shape

`handoff.md` is intentionally short and structured. It captures:

- Goal
- Current state
- Active files being modified
- What was touched this session
- What did not work and why
- Next step

Missing facts should be marked explicitly instead of invented.

## Current Limits

- Commands are namespaced as `/kompact:kompact` and `/kompact:kontinue`.
- Exact aliases like `/kompact` and `/kontinue` are not included in v1.
- The plugin writes a single current `handoff.md`; it does not keep a handoff archive.
- The plugin does not start or manage a new Claude Code session.
- Review `handoff.md` before carrying it into another session if it may contain sensitive details.

## Testing

Use [docs/testing/kompact-plugin-smoke-test.md](docs/testing/kompact-plugin-smoke-test.md) for manual acceptance checks.

# Kompact

Kompact is a plugin for concise session handoffs. It provides two skills:

- `/kompact:kompact` creates or replaces a repo-local `handoff.md`.
- `/kompact:kontinue` reads `handoff.md` and continues from the recorded next step.

The goal is to preserve the working state that often gets lost during `/compact` without carrying a long transcript into the next session.

## Claude Code
```text
/plugin marketplace add KaiSong06/kompact
/plugin install kompact@kaisong-plugins
```

## Codex

Add the Kompact marketplace from GitHub:

```sh
codex plugin marketplace add KaiSong06/kompact
```

Then open Codex's plugin search or plugin UI and install `kompact` from `kaisong-plugins`.

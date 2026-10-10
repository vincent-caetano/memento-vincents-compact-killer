## Feature Context: Read Before, Write During (`docs/features/`)

- **Before starting work on a feature**, read `docs/features/INDEX.md`, then that feature's
  file in full. It holds the state, decisions, user corrections and gotchas from earlier
  sessions, so the user does not have to repeat them.
- Follow a reference to another feature (`RANK-03`) by grepping its ID and reading only
  that entry. Do not read the other feature's file in full.
- **Write in the same turn** a decision is made, the user corrects you, or debugging ends
  in a non-obvious finding. Edit by ID, keep the rejected option and the reason, and do
  not copy what git, the changelog or the code already say.
- Before switching sessions, or at about half the context window, run `/handoff`
  (`.claude/skills/handoff/SKILL.md`). A new feature gets a file from
  `docs/features/_TEMPLATE.md` and an `INDEX.md` line. Convention: `docs/features/README.md`.

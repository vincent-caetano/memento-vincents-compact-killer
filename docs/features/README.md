# Feature context files

One short file per feature that holds what a new session cannot get from the code or
git: the current state, the decisions and why, the user's corrections, and the gotchas.
It is how a feature keeps its memory across sessions and agents, so nobody has to repeat
what was already settled.

Agents read [`INDEX.md`](INDEX.md) first. This README explains the convention and is only
needed when creating or restructuring a file.

## How a session uses them

1. Read `INDEX.md` (one line per feature).
2. Read the file of the feature being worked on, in full. It is short by design.
3. For each reference to another feature (`RANK-03`), search for that ID and read only
   that entry: `grep -n -A8 "RANK-03" docs/features/rankings.md`. Do not read the other
   file in full.
4. Check the file's claims against the tree before acting on them (branch, files). A
   feature file can be stale. The code wins, then fix the file.

## File shape

Copy [`_TEMPLATE.md`](_TEMPLATE.md). Sections: State, Decisions, Corrections, Gotchas.

- **Every entry gets an ID**: a feature prefix and a number, `### RANK-03 · Title`. IDs
  are never reused or renumbered, so references stay valid.
- **Reference by ID, never by line number or by copying.** A rule lives in one file only.
  Other files point to it (`Follows RANK-03.`).
- **Decision entries keep the rejected option and the reason.** That is what stops the
  next session from proposing it again.
- **Superseded entries are rewritten in place under the same ID**, or reduced to one line
  (`Retired: replaced by RANK-07.`). Never leave two live versions of a rule.

## What does not go in

The repo already records these. Point to them instead:

- History and what changed when: `git log`, your changelog.
- Release checklists, test plans, component catalogs: link them.
- API contracts: link the contract doc (for example `docs/api/rankings-contract.md`).

## Size

Aim for 50 to 150 lines. Past 200, delete superseded entries and finished State lines
before adding more. A long file is read in full every session and costs every time.

## When to write

- **In the same turn** a decision is made, the user corrects something, or a debugging
  session ends in a non-obvious finding. Do not save it for the end of the session.
- **Before switching sessions**, run `/handoff` (`.claude/skills/handoff/`). Hand off at
  about half the context window, before auto-compact, and prefer a handoff over
  `/compact` when the work resumes on another day (the prompt cache is gone by then).
- A new feature gets a file and an `INDEX.md` line in the same change.

Edit entries by ID. Do not rewrite the whole file.

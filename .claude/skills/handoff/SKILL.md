---
name: handoff
description: Save the current feature's state, decisions, corrections and gotchas into its file under docs/features/ so a fresh session can continue without the user repeating anything. Use when the user says "handoff", "save context", "I'm switching sessions", or when the context window is about half full on feature work.
---

# Handoff

Write what this session learned into the feature context file, so the next session reads
one short file instead of this conversation. Convention: `docs/features/README.md`.

## Steps

1. **Find the feature.** Read `docs/features/INDEX.md`. Pick the feature this session
   worked on. If none fits, create its file from `docs/features/_TEMPLATE.md` with a new
   prefix and add one line to `INDEX.md`. If the session touched two features, update both.
2. **Read the feature file in full**, then go through this conversation for:
   - decisions made, including the option rejected and why,
   - corrections the user made (what was wrong, what the rule is now),
   - non-obvious findings from debugging,
   - where the work stands: done, doing, next, open questions.
3. **Edit by ID, never rewrite the file.**
   - New item: next free ID, in the right section.
   - Changed decision: rewrite that ID in place, or retire it in one line pointing to the
     new ID.
   - Update State, `Updated:` date, branch and PR in the header.
   - Something that belongs to another feature goes in that feature's file, and this one
     references its ID.
4. **Keep out** what git, the changelog or the code already say. No
   narrative of the session. Keep the file under about 150 lines: delete finished State
   lines and retired entries if needed.
5. **Commit** the feature file on the current task branch with the rest of the work
   (`docs(features): update <feature> context`). It is part of the work, not a scratch file.
6. **Reply with two lines:** which IDs were added or changed, and the prompt for the next
   session, for example:
   `Continue the rankings work. Read docs/features/INDEX.md and docs/features/rankings.md first.`


# Rankings

Prefix: `RANK` · Branch: `feat/rankings-periods` · PR: #42 · Updated: 2026-10-10
Links: profile (PROF-03)

Example file. A fictional app with group leaderboards.

## State

- Done: leaderboard list, period picker, locked state for free plans.
- Doing: player breakdown sheet.
- Next: empty states, translations.
- Open questions: does a "year" run January to December or follow the league season? (RANK-02)

## Decisions

### RANK-01 · The API contract lives in its own doc
Periods and query params are specified in `docs/api/rankings-contract.md`. Read it there,
do not restate it here.

### RANK-02 · Default is the current season, never a fallback
An empty current season shows empty. It never falls back to last month.
Rejected: silent fallback, because users thought their stats were reset.

### RANK-03 · Season-wide with period tabs
Rankings cover the selected season, switched with period tabs.
Rejected: "last 5 matches", because it looked empty for small groups.
Source: user, 2026-10-02.

## Corrections

### RANK-04 · Locked state is a static wireframe, not a pulsing skeleton
A pulsing skeleton behind the lock reads as "loading". Got wrong: reused the loading
skeleton with its animation.

## Gotchas

### RANK-05 · Period must be in every cache and request key
Otherwise switching period briefly shows the previous board.

### RANK-06 · The API sends `rating_avg`, not `avgRating`
Mapped once in `services/rankings.ts`. Don't rename it on the client.

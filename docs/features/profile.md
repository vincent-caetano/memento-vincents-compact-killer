# Profile

Prefix: `PROF` · Branch: `feat/profile-redesign` · PR: #39 · Updated: 2026-10-09
Links: rankings (RANK-03, RANK-06)

Example file. A fictional app with player profiles.

## State

- Done: header, avatar upload, edit profile.
- Doing: ranking card on the profile.
- Next: settings regroup.
- Open questions: none

## Decisions

### PROF-01 · Avatars upload compressed, as WebP
Resized to 1024px, WebP at 0.8. Reason: the proxy rejects request bodies over 1 MB.

### PROF-03 · Ranking card on the profile
Shows the player's position for the selected period. Follows RANK-03. Rating field per
RANK-06.

## Corrections

### PROF-02 · Name and photo go in the header subtitle slot
Never as the first row of the page body. Got wrong twice: rendered a body row.

## Gotchas

### PROF-04 · Header icons are white only over a cover image
Without a cover the page is white, so white icons disappear.

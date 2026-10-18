# Synthesis summary

Mode: new. Precedence: ADR > SPEC > PRD > DOC.

## Doc counts by type
- PRD: 1 (docs/IDEA.md, confidence medium)
- DOC: 1 (docs/PLAN.md, confidence medium)
- ADR: 0, SPEC: 0, UNKNOWN: 0

Cross-ref graph: PLAN.md -> IDEA.md (plus an external Spotify policy URL). IDEA.md has no refs. No cycles.

## Decisions locked
0. No ADRs. The PLAN.md Decisions table is a DOC and is kept in context.md, unlocked.

## Requirements extracted (12)
REQ-room-setup, REQ-round-structure, REQ-category, REQ-secret-pick, REQ-clip-playback, REQ-guessing, REQ-reveal, REQ-guess-matching, REQ-off-category-vote, REQ-duplicate-pick, REQ-guesser-scoring, REQ-picker-scoring

All from docs/IDEA.md. Scoring numbers are marked by the source as a playtest starting point.

## Constraints
0 (no SPECs).

## Context topics (10)
Components, Game flow and timing, Decisions (PLAN.md table), Clip length for the MVP, Milestones (0 to 5), Not in the MVP, Decided later, Design rationale, After the MVP, To check in playtests.

## Conflicts
0 blockers, 0 competing variants, 0 auto-resolved. The two docs were checked against each other (clip length, categories, scoring, off-category handling, post-MVP items) and the text does not contradict. Omissions were not treated as conflicts.

## Notes for the roadmapper
- Product title in IDEA.md is "Jukeboxxed". The user's git history and the classifier summary call the game "Split the Room". The docs do not use that name, so it is not recorded as a fact here.
- PLAN.md milestones 0 to 5 are the only sequencing in the source. They are in context.md.

## Pointers
- Conflicts: /mnt/data/Code/Github/Jukeboxxed/.planning/INGEST-CONFLICTS.md
- Requirements: /mnt/data/Code/Github/Jukeboxxed/.planning/intel/requirements.md
- Decisions: /mnt/data/Code/Github/Jukeboxxed/.planning/intel/decisions.md
- Constraints: /mnt/data/Code/Github/Jukeboxxed/.planning/intel/constraints.md
- Context: /mnt/data/Code/Github/Jukeboxxed/.planning/intel/context.md

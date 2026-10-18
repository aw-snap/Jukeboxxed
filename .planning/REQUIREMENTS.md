# Requirements: Jukeboxxed

**Defined:** 2026-10-18
**Core Value:** Pick a song that exactly half the room can name: reading the room wins the game, not just knowing songs.

Sources: docs/IDEA.md (the game) and docs/PLAN.md (the MVP plan). Items marked "intel" trace back to the 12 requirements extracted into .planning/intel/requirements.md. Items marked "PLAN.md" come from the plan's milestones and decisions, which the intel did not extract as requirements. Scoring numbers are a starting point for the playtest, per IDEA.md.

## v1 Requirements

Requirements for the MVP. Each maps to one roadmap phase.

### Proof of the risky parts

- [ ] **PROOF-01** (PLAN.md): A player can search for a song from a phone and the TV page plays that song's clip, with the search going through the server and the audio coming from Deezer's preview.
- [ ] **PROOF-02** (PLAN.md): Deezer's terms are checked for use in a game, and the finding is recorded in PROJECT.md.
- [ ] **PROOF-03** (PLAN.md): The language and frameworks are chosen and recorded in PROJECT.md Key Decisions.

### Answer matcher

- [ ] **MATCH-01** (intel: REQ-guess-matching): A typed guess counts as correct when it has the distinctive words of the title. Typos are forgiven, and filler like "The", "feat." or "(Remastered)" doesn't matter. "small things" gets *All the Small Things*, "brightside" gets *Mr. Brightside*, and "love" does not get *Crazy in Love*.
- [ ] **MATCH-02** (PLAN.md): A test list of about 100 real titles and guesses exists and the matcher passes it.

### Room

- [ ] **ROOM-01** (intel: REQ-room-setup): The game is for 4 to 8 players in the same room, with up to 8 phones able to join one room. The TV shows the game and plays the music, and everyone plays on their phone.
- [ ] **ROOM-02** (PLAN.md): The TV page shows a room code.
- [ ] **ROOM-03** (PLAN.md): A player joins from a phone browser, with no app to install, by entering the room code and a name.
- [ ] **ROOM-04** (PLAN.md): A phone that slept or lost its connection can rejoin the room as the same player.

### Pick

- [ ] **PICK-01** (intel: REQ-category): Everyone gets the same category (such as a genre, a decade or "songs from movies"), and it shows on the TV and on every phone.
- [ ] **PICK-02** (intel: REQ-secret-pick): Each player secretly picks a song from the category on their phone, by searching. Nothing filters what can be picked.
- [ ] **PICK-03** (PLAN.md): Each player can lock in their pick before a visible pick timer ends.
- [ ] **PICK-04** (intel: REQ-duplicate-pick, merge half): If two players pick the same song, the game keeps one entry for it, it plays once, and both players sit it out.

### Play and guess

- [ ] **PLAY-01** (intel: REQ-clip-playback): Songs play one at a time in random order, 15 seconds each. A clip is the first 15 seconds of the Deezer preview, not the song's real start. The player who picked the song sits that one out.
- [ ] **PLAY-02** (PLAN.md): Guess times count from when the TV reports the clip actually started playing, so a slow-loading clip costs nobody points.
- [ ] **GUESS-01** (intel: REQ-guessing): Everyone except the picker types the title before the clip ends. A wrong guess can be retyped. Nobody waits for a turn: you guess on every song except your own.
- [ ] **GUESS-02** (PLAN.md): Each guess is marked correct or wrong by the answer matcher and stored with its time.

### Reveal and category vote

- [ ] **REVEAL-01** (intel: REQ-reveal): After each clip the TV shows the title, who picked it, who got it, and how the room split.
- [ ] **REVEAL-02** (intel: REQ-reveal and REQ-off-category-vote, vote half): At each reveal, everyone except the picker votes on whether the song fits the category, and the vote is collected and shown.

### Scoring

- [ ] **SCORE-01** (intel: REQ-guesser-scoring): A guesser gets 200 points for a correct guess at the start of the clip, falling to 100 at 15 seconds.
- [ ] **SCORE-02** (intel: REQ-picker-scoring): The picker scores up to 1000 per song: the most for an even split, falling to 0 if nobody or everybody gets it. Speed doesn't matter here, only who got it. With 6 guessers, 0/1/2/3/4/5/6 correct guessers give the picker 0/333/667/1000/667/333/0.
- [ ] **SCORE-03** (intel: REQ-off-category-vote, scoring half): If most players vote that a song doesn't fit the category, the picker scores 0 for it. Guessers keep their points.
- [ ] **SCORE-04** (intel: REQ-duplicate-pick, scoring half): When two players picked the same song, both get the picker points.

### Game flow

- [ ] **FLOW-01** (intel: REQ-round-structure): A round is Category, Pick, Play, Guess, Reveal. A game is 3 rounds, so everyone picks 3 songs.
- [ ] **FLOW-02** (PLAN.md): After round 3 the TV shows a final scoreboard.
- [ ] **FLOW-03** (PLAN.md): Play Again takes the room back to a new category without going through the lobby.

### Playtest

- [ ] **TUNE-01** (user success metric, PLAN.md milestone 5): One real game night with 4 to 8 players runs end to end on the game.
- [ ] **TUNE-02** (user success metric, PLAN.md milestone 5): The scoring numbers in docs/IDEA.md are tuned from that playtest, written back to IDEA.md and used by the game.
- [ ] **TUNE-03** (IDEA.md "To check in playtests"): The two playtest questions are answered: does starting near the chorus make songs too easy to split, and does the speed bonus let fast typers outscore good pickers?

## v2 Requirements

Deferred to after the MVP. Tracked but not in the current roadmap.

### Categories

- **CATG-01**: Different categories per player, or a choice of 2 categories each.

### Music

- **MUSC-01**: Clips from the song's real start, where intros make songs harder to name.
- **MUSC-02**: Full songs from YouTube instead of 30s previews.

## Out of Scope

Explicitly excluded from the MVP.

| Feature | Reason |
|---------|--------|
| Accounts | Not in the MVP (PLAN.md); players join with a room code and a name |
| An audience | Not in the MVP (PLAN.md) |
| A filter for what players type or pick | Not in the MVP (PLAN.md); the category vote at each reveal keeps picks honest |
| Visual polish beyond readable screens | Not in the MVP (PLAN.md) |
| Full songs from the very start (YouTube) | Not in the MVP (PLAN.md); Deezer 30s previews first, tracked as MUSC-02 |
| Spotify as a music source | Ruled out: its developer policy says "Do not create a game, including trivia quizzes" |

## Traceability

Which phases cover which requirements.

| Requirement | Phase | Status |
|-------------|-------|--------|
| PROOF-01 | Phase 1 | Pending |
| PROOF-02 | Phase 1 | Pending |
| PROOF-03 | Phase 1 | Pending |
| MATCH-01 | Phase 1 | Pending |
| MATCH-02 | Phase 1 | Pending |
| ROOM-01 | Phase 2 | Pending |
| ROOM-02 | Phase 2 | Pending |
| ROOM-03 | Phase 2 | Pending |
| ROOM-04 | Phase 2 | Pending |
| PICK-01 | Phase 3 | Pending |
| PICK-02 | Phase 3 | Pending |
| PICK-03 | Phase 3 | Pending |
| PICK-04 | Phase 3 | Pending |
| PLAY-01 | Phase 4 | Pending |
| PLAY-02 | Phase 4 | Pending |
| GUESS-01 | Phase 4 | Pending |
| GUESS-02 | Phase 4 | Pending |
| REVEAL-01 | Phase 4 | Pending |
| REVEAL-02 | Phase 4 | Pending |
| SCORE-01 | Phase 5 | Pending |
| SCORE-02 | Phase 5 | Pending |
| SCORE-03 | Phase 5 | Pending |
| SCORE-04 | Phase 5 | Pending |
| FLOW-01 | Phase 5 | Pending |
| FLOW-02 | Phase 5 | Pending |
| FLOW-03 | Phase 5 | Pending |
| TUNE-01 | Phase 6 | Pending |
| TUNE-02 | Phase 6 | Pending |
| TUNE-03 | Phase 6 | Pending |

**Coverage:**
- v1 requirements: 29 total
- Mapped to phases: 29
- Unmapped: 0 ✓

**Intel requirement check (12 of 12 covered):**

| Intel requirement | Requirement IDs | Phase |
|-------------------|-----------------|-------|
| REQ-room-setup | ROOM-01 | 2 |
| REQ-round-structure | FLOW-01 | 5 |
| REQ-category | PICK-01 | 3 |
| REQ-secret-pick | PICK-02 | 3 |
| REQ-clip-playback | PLAY-01 | 4 |
| REQ-guessing | GUESS-01 | 4 |
| REQ-reveal | REVEAL-01, REVEAL-02 | 4 |
| REQ-guess-matching | MATCH-01 | 1 |
| REQ-off-category-vote | REVEAL-02 (vote), SCORE-03 (scoring) | 4, 5 |
| REQ-duplicate-pick | PICK-04 (merge), SCORE-04 (scoring) | 3, 5 |
| REQ-guesser-scoring | SCORE-01 | 5 |
| REQ-picker-scoring | SCORE-02 | 5 |

Two intel requirements (REQ-off-category-vote, REQ-duplicate-pick) each have a behaviour half and a scoring half that ship in different phases, so each half has its own ID and every ID maps to exactly one phase.

---
*Requirements defined: 2026-10-18*
*Last updated: 2026-10-18 after initial definition*

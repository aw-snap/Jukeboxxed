# Roadmap: Jukeboxxed

## Overview

Jukeboxxed goes from proof to a real game night in six steps, one per milestone in docs/PLAN.md. First prove the risky parts: Deezer clips playing on the TV from a phone search, Deezer's terms checked for games, and an answer matcher that passes a list of about 100 real titles. Then build the game in the order a round happens: the room (TV code, phones joining), the pick, play and guess with the reveal and category vote, then scoring and the full 3-round game with a final scoreboard. The last phase is the playtest itself: one real game night with 4 to 8 players, and the scoring numbers in docs/IDEA.md tuned from it.

## Phases

**Phase Numbering:**
- Integer phases (1, 2, 3): Planned milestone work
- Decimal phases (2.1, 2.2): Urgent insertions (marked with INSERTED)
- Phase N is PLAN.md milestone N-1 (PLAN.md counts from 0, this roadmap counts from 1). Order and "done when" criteria are unchanged.

Decimal phases appear between their surrounding integers in numeric order.

- [ ] **Phase 1: Prove the risky parts** - A phone search plays a clip on the TV, Deezer's terms are checked for games, and the matcher passes the title list (PLAN.md milestone 0)
- [ ] **Phase 2: Room** - The TV shows a code, phones join with names, and a phone that slept can rejoin (PLAN.md milestone 1)
- [ ] **Phase 3: Pick** - The category shows everywhere, everyone locks in a song before the timer, duplicate picks are merged (PLAN.md milestone 2)
- [ ] **Phase 4: Play and guess** - Clips play in random order, guesses are marked with their time, the reveal shows the split and runs the category vote (PLAN.md milestone 3)
- [ ] **Phase 5: Full game** - Scoring, 3 rounds, final scoreboard, Play Again (PLAN.md milestone 4)
- [ ] **Phase 6: Playtest** - One real game night runs end to end and the scoring numbers are tuned (PLAN.md milestone 5)

## Phase Details

### Phase 1: Prove the risky parts
**Goal**: The three things most likely to sink the game are shown to work before any game code is built: Deezer audio reaching the TV from a phone search, Deezer allowing this use, and a guess matcher that behaves on real titles.
**Depends on**: Nothing (first phase)
**Requirements**: PROOF-01, PROOF-02, PROOF-03, MATCH-01, MATCH-02
**Success Criteria** (what must be TRUE):
  1. From a phone browser, a user searches for a song, picks a result, and the TV page plays that song's clip (the first 15 seconds of the Deezer preview), with the search going through the server.
  2. Deezer's terms have been read for use in a game and the finding is written down in PROJECT.md, so a go or no-go on the music source is on record.
  3. The answer matcher passes a test list of about 100 real titles and guesses: "small things" gets All the Small Things, "brightside" gets Mr. Brightside, "love" does not get Crazy in Love, typos are forgiven, and filler like "The", "feat." or "(Remastered)" is ignored.
  4. The language and frameworks are chosen and recorded as a Key Decision in PROJECT.md.
**Plans**: TBD

### Phase 2: Room
**Goal**: A group can gather in one room: the TV shows a code and up to 8 phones join by name, including a phone that went to sleep and comes back.
**Depends on**: Phase 1
**Requirements**: ROOM-01, ROOM-02, ROOM-03, ROOM-04
**Success Criteria** (what must be TRUE):
  1. The TV page shows a room code.
  2. A player opens the website on a phone, with nothing to install, enters the code and a name, and appears in the lobby on the TV.
  3. Up to 8 phones can be in the same room at once, each shown by name.
  4. A phone that slept or lost its connection can rejoin the room as the same player.
**Plans**: TBD
**UI hint**: yes

### Phase 3: Pick
**Goal**: Every round starts with a shared category and every player secretly locks in a song for it.
**Depends on**: Phase 2
**Requirements**: PICK-01, PICK-02, PICK-03, PICK-04
**Success Criteria** (what must be TRUE):
  1. When a round starts, the same category (a genre, a decade, "songs from movies") shows on the TV and on every phone.
  2. Each player searches for a song on their phone and picks one, and other players cannot see it. Nothing filters what can be picked.
  3. A visible pick timer runs and each player can lock in their song before it ends.
  4. When two players pick the same song, the game keeps one entry for it and marks both players as its pickers.
**Plans**: TBD
**UI hint**: yes

### Phase 4: Play and guess
**Goal**: The picked songs play and the room guesses them, then the reveal shows how the room split and the room votes on whether each song fit the category.
**Depends on**: Phase 3
**Requirements**: PLAY-01, PLAY-02, GUESS-01, GUESS-02, REVEAL-01, REVEAL-02
**Success Criteria** (what must be TRUE):
  1. The TV plays the round's songs one at a time in random order, 15 seconds each, and a song picked by two players plays only once.
  2. During a clip, every player except the picker (or pickers) types a title guess on their phone, can retype after a wrong guess, and never waits for a turn. The picker sits that song out.
  3. Each guess is marked correct or wrong by the answer matcher and stored with its time, counted from when the TV reports the clip actually started playing, so a slow-loading clip costs nobody points.
  4. After each clip the TV reveals the title, who picked it, who got it, and how the room split.
  5. At each reveal, every player except the picker votes on their phone on whether the song fits the category, and the vote is collected and shown.
**Plans**: TBD
**UI hint**: yes

### Phase 5: Full game
**Goal**: A complete game can be played from the first category to a final scoreboard and started again.
**Depends on**: Phase 4
**Requirements**: SCORE-01, SCORE-02, SCORE-03, SCORE-04, FLOW-01, FLOW-02, FLOW-03
**Success Criteria** (what must be TRUE):
  1. A guesser who gets a song right scores 200 for a guess at the start of the clip, falling to 100 at 15 seconds.
  2. The picker scores up to 1000 per song, the most for an even split and 0 if nobody or everybody got it. With 6 guessers, 0/1/2/3/4/5/6 correct guessers give the picker 0/333/667/1000/667/333/0.
  3. When most voters say a song does not fit the category, its picker scores 0 for it and the guessers keep their points. When two players picked the same song, both get the picker points.
  4. A game runs 3 rounds (category, pick, play, guess, reveal) and every player picks 3 songs in total.
  5. After round 3 the TV shows a final scoreboard, and Play Again takes the room back to a new category without going through the lobby.
**Plans**: TBD
**UI hint**: yes

### Phase 6: Playtest
**Goal**: The game survives one real game night and the scoring numbers are tuned from what happened.
**Depends on**: Phase 5
**Requirements**: TUNE-01, TUNE-02, TUNE-03
**Success Criteria** (what must be TRUE):
  1. One real game night with 4 to 8 players runs end to end on the game, from joining to the final scoreboard.
  2. The scoring numbers in docs/IDEA.md are tuned from that playtest, and the tuned numbers are written back to docs/IDEA.md and used by the game.
  3. The two playtest questions in docs/IDEA.md have recorded answers: whether starting near the chorus makes songs too easy to split, and whether the speed bonus lets fast typers outscore good pickers.
**Plans**: TBD

## Progress

**Execution Order:**
Phases execute in numeric order: 1 → 2 → 3 → 4 → 5 → 6

| Phase | Plans Complete | Status | Completed |
|-------|----------------|--------|-----------|
| 1. Prove the risky parts | 0/0 | Not started | - |
| 2. Room | 0/0 | Not started | - |
| 3. Pick | 0/0 | Not started | - |
| 4. Play and guess | 0/0 | Not started | - |
| 5. Full game | 0/0 | Not started | - |
| 6. Playtest | 0/0 | Not started | - |

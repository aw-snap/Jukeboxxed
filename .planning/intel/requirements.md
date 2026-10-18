# Requirements (from PRD: docs/IDEA.md)

Extracted from one PRD. The source has no user stories or acceptance-criteria headings, so `acceptance` is the source's own examples/numbers where it gives them, otherwise "absent". Verbatim source text is in context.md. Scoring numbers are flagged by the source as "a starting point for playtesting".

## REQ-room-setup
- source: docs/IDEA.md
- description: Party game for 4 to 8 players in the same room. The TV shows the game and plays the music. Everyone plays on their phone.
- acceptance: absent
- scope: party game, room

## REQ-round-structure
- source: docs/IDEA.md
- description: A round is Category, Pick, Play, Guess, Reveal. A game is 3 rounds, so everyone picks 3 songs.
- acceptance: absent
- scope: round flow

## REQ-category
- source: docs/IDEA.md
- description: Everyone gets the same category, such as a genre, a decade or "songs from movies".
- acceptance: absent
- scope: round flow, category

## REQ-secret-pick
- source: docs/IDEA.md
- description: Everyone secretly picks a song from the category on their phone. There is no filter on picks.
- acceptance: absent
- scope: song picking

## REQ-clip-playback
- source: docs/IDEA.md
- description: Songs play one at a time in random order, 15 seconds each. A clip is the start of the song's preview, which is usually near the chorus. The player who picked it sits that one out.
- acceptance: absent
- scope: round flow, playback

## REQ-guessing
- source: docs/IDEA.md
- description: Everyone else types the title before the clip ends. A wrong guess can be retyped. Nobody waits for a turn: you guess on every song except your own.
- acceptance: absent
- scope: guess matching, round flow

## REQ-reveal
- source: docs/IDEA.md
- description: The TV shows the title, who picked it, who got it, and how the room split. Everyone except the picker votes on whether the song fits the category.
- acceptance: absent
- scope: round flow, reveal, off-category voting

## REQ-guess-matching
- source: docs/IDEA.md
- description: The distinctive words of the title are enough. Typos are forgiven, and filler like "The", "feat." or "(Remastered)" doesn't matter.
- acceptance: "small things" gets All the Small Things; "brightside" gets Mr. Brightside; "love" does not get Crazy in Love.
- scope: guess matching

## REQ-off-category-vote
- source: docs/IDEA.md
- description: The room keeps everyone honest. If most players vote that a song doesn't fit the category, the picker scores 0 for it. Guessers keep their points.
- acceptance: absent
- scope: off-category voting, scoring

## REQ-duplicate-pick
- source: docs/IDEA.md
- description: If two players pick the same song, it plays once, both sit out, and both get the picker points.
- acceptance: absent
- scope: song picking, scoring

## REQ-guesser-scoring
- source: docs/IDEA.md
- description: Guessers get 200 points for a correct guess at the start of the clip, falling to 100 at 15 seconds.
- acceptance: absent (numbers are a playtest starting point)
- scope: scoring

## REQ-picker-scoring
- source: docs/IDEA.md
- description: The picker scores up to 1000 per song: the most for an even split, falling to 0 if nobody or everybody gets it. Speed doesn't matter here, only who got it. Picking is worth more than guessing.
- acceptance: With 6 guessers, guessers who got it 0/1/2/3/4/5/6 gives picker 0/333/667/1000/667/333/0. (numbers are a playtest starting point)
- scope: scoring

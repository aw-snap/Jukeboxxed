# Jukeboxxed

## What This Is

Jukeboxxed is a party game for 4 to 8 players in the same room. The TV shows the game and plays the music, and everyone plays on their phone. Each player secretly picks a song for a shared category, the room guesses everyone else's songs, and the picker scores most when exactly half the room can name theirs. "Split the Room" was only a working name used in chat, not the product name.

## Core Value

Pick a song that exactly half the room can name: reading the room wins the game, not just knowing songs.

## Success Metric

The MVP is done when one real game night with 4 to 8 players runs end to end on it, and the scoring numbers in docs/IDEA.md have been tuned from that playtest (PLAN.md milestone 5, Phase 6).

## Requirements

### Validated

(None yet — ship to validate)

### Active

Full list with IDs and phase mapping is in REQUIREMENTS.md. In short:

- [ ] A phone search plays a clip on the TV, Deezer's terms are checked, and the answer matcher passes a list of about 100 real titles and guesses (Phase 1)
- [ ] The TV shows a room code, phones join with names, and a phone that slept can rejoin (Phase 2)
- [ ] The category shows everywhere, everyone secretly locks in a song before the timer, duplicate picks are merged (Phase 3)
- [ ] Clips play in random order, guesses are marked with their time, the reveal shows the split and runs the category vote (Phase 4)
- [ ] Guesser and picker scoring, 3 rounds, final scoreboard, Play Again (Phase 5)
- [ ] One real game night, with the scoring numbers tuned from it (Phase 6)

### Out of Scope

- Accounts — the game is joined with a room code and a name
- An audience — not part of the MVP
- A filter for what players type or pick — the room keeps everyone honest through the category vote
- Different categories per player, or a choice of 2 categories each — after the MVP
- Full songs from the very start (YouTube) — Deezer 30s previews for the MVP, full songs later
- Clips from the song's real start — after the MVP, where intros make songs harder to name
- Visual polish beyond readable screens — the MVP only needs readable screens
- Spotify — its developer policy bans games

## Context

Components (from docs/PLAN.md):

- **TV page.** A browser on the laptop plugged into the TV. Shows the room code, category, countdown and reveal, and plays the clips.
- **Phone page.** A website, no app to install. Join with the code and a name, search and lock in a song, type guesses, vote on category fit.
- **Server.** The single source of truth: room state, timers, scoring and guess checking. Song search goes through it, so the music source can be swapped later in one place.
- **Answer matcher.** Decides that "brightside" counts for *Mr. Brightside* and "love" doesn't count for *Crazy in Love*. The one part with a real test suite, built from about 100 real titles and guesses.

Round flow: Category, Pick, Play, Guess, Reveal. A game is 3 rounds, so everyone picks 3 songs. After round 3 comes the final scoreboard, and Play Again returns to a new category.

Why it is meant to be fun: guessing rewards knowing songs while picking rewards knowing what other people know; the reveal is about your friends; missing is funny both ways (too famous, or too obscure); nobody waits for a turn; and it changes with the group.

Questions for the playtest (docs/IDEA.md): does starting near the chorus make songs too easy to split, and does the speed bonus let fast typers outscore good pickers? The scoring numbers are explicitly a starting point.

Source documents: docs/IDEA.md (the game) and docs/PLAN.md (the MVP plan). They were checked against each other and do not contradict.

## Constraints

- **Platform**: Players use a website on their phones with nothing to install. The screen and speaker are a desktop browser on a laptop plugged into the TV.
- **Architecture**: One server process holds room state, timers, scoring and guess checking. Phones and the TV page talk to it over a live connection. Song search goes through the server so the music source can be swapped in one place.
- **Music source**: Deezer 30s previews for the MVP, no login. The TV plays the preview audio from Deezer.
- **Timing**: Guess times count from when the TV reports the clip actually started playing, so a slow-loading clip costs nobody points.
- **Testing**: The answer matcher is the one part with a real test suite (about 100 real titles and guesses).
- **Hosting**: Production is the user's own Linux server and domain, set up later. During development the server runs on the laptop. Domain, HTTPS and how the server is kept running are decided later.
- **Tech stack**: Language and frameworks are decided in Phase 1 and recorded here.
- **Players**: 4 to 8 players in the same room.

## Key Decisions

All rows below were confirmed by the user directly in conversation. There are no ADRs, so none of them are ADR-locked.

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Music: Deezer 30s previews for the MVP, full songs from YouTube later | Free, no login, one source for search, song info and audio | — Pending (Deezer's terms for games are checked in Phase 1) |
| Server: one server process on the user's own Linux server and domain, set up later; during development it runs on the laptop | Phones join on any network | — Pending |
| Category rules: honour system, checked by a category vote at each reveal | Genre data in music catalogs is too unreliable to filter by | — Pending |
| Spotify ruled out | Its developer policy (https://developer.spotify.com/policy) says "Do not create a game, including trivia quizzes" | — Pending |
| A clip is the first 15 seconds of the Deezer preview, not the song's real start | Deezer picks where each preview starts, usually near the chorus; clips from the real start are an after-the-MVP idea | — Pending (playtest question: is near the chorus too easy to split?) |
| Product name is Jukeboxxed | "Split the Room" was only a working name used in chat | — Pending |
| Language and frameworks | To be decided in Phase 1 | — Pending |

---
*Last updated: 2026-10-18 after initialization from docs/IDEA.md and docs/PLAN.md*

# MVP plan

High-level plan for the first playable version of the game in [IDEA.md](IDEA.md).

## Pieces

```mermaid
flowchart LR
  P["Phones<br/>join, pick, guess, vote"] <-->|live connection| S["Server<br/>room, timers, scoring, matching"]
  T["TV page<br/>screen + speaker"] <-->|live connection| S
  S -->|song search| D[(Deezer)]
  T -->|30s preview audio| D
```

- **TV page.** A browser on the laptop plugged into the TV. Shows the room code, category, countdown and reveal, and plays the clips.
- **Phone page.** A website, no app to install. Join with the code and a name, search and lock in a song, type guesses, vote on category fit.
- **Server.** The single source of truth: room state, timers, scoring and guess checking. Song search goes through it, so the music source can be swapped later in one place.
- **Answer matcher.** Decides that "brightside" counts for *Mr. Brightside* and "love" doesn't count for *Crazy in Love*. The one part with a real test suite, built from about 100 real titles and guesses.

## Game flow

```mermaid
flowchart LR
  L[Lobby] --> C[Category shown]
  C --> K[Pick a song]
  K --> G[Clip plays, everyone guesses]
  G --> R[Reveal + category vote]
  R -->|more songs| G
  R -->|next round| C
  R -->|after round 3| F[Final scores]
  F -->|play again| C
```

Guess times count from when the TV reports the clip actually started playing, so a slow-loading clip costs nobody points.

## Decisions

| Topic | Decision | Why |
|---|---|---|
| Music | Deezer 30s previews; full songs from YouTube later | Free, no login, one source for search, song info and audio |
| Server | One server process on your own Linux server and domain, set up later | Phones join on any network; during development it runs on the laptop |
| Category rules | Honour system, checked by a vote at each reveal | Genre data in music catalogs is too unreliable to filter by |
| Not Spotify | Ruled out | Its [developer policy](https://developer.spotify.com/policy) says "Do not create a game, including trivia quizzes" |

Deezer picks where each preview starts, usually near the chorus, so for the MVP a clip is the first 15 seconds of the preview, not the song's real start.

## Milestones

| # | Milestone | Done when |
|---|---|---|
| 0 | Prove the risky parts | A phone search plays the clip on the TV; Deezer's terms checked for games; the matcher passes the title list |
| 1 | Room | The TV shows a code, phones join with names, a phone that slept can rejoin |
| 2 | Pick | The category shows everywhere, everyone locks in before the timer, duplicate picks are merged |
| 3 | Play and guess | Clips play in random order, guesses are marked with their time, the reveal shows the split and runs the category vote |
| 4 | Full game | Scoring, 3 rounds, final scoreboard, Play Again |
| 5 | Playtest | One real game night; the numbers in IDEA.md tuned |

## Not in the MVP

- Accounts, an audience, a filter for what players type
- Different categories per player
- Full songs from the very start (YouTube)
- Visual polish beyond readable screens

## Decided later

- Language and frameworks (at milestone 0)
- Hosting details: domain, HTTPS, how the server is kept running

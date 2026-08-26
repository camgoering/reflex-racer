# Reflex Racer

A 2D Unity driving game that measures player reaction time across a series of timed prompts and posts results to a global leaderboard. Built in C# with a side-scrolling parallax highway, gear-shift engine audio, and persistent online score tracking.

Started as a personal Unity project and later extended into a four-person team build for COSC 302 at the University of Tennessee, Knoxville.

<img width="2878" height="1615" alt="Screenshot 2026-08-26 150838" src="https://github.com/user-attachments/assets/69aacd76-e8a2-485d-a41f-ba707bf9907d" />

---

## Gameplay

The player drives down an endless highway. Five times per run, a prompt appears on screen; the player presses **spacebar** as fast as possible. Each reaction is timed and summed into a total for the run, and the lowest totals are recorded on a global top-ten leaderboard.

<img width="2877" height="1618" alt="Screenshot 2026-08-26 151135" src="https://github.com/user-attachments/assets/83a08132-d820-4396-bc8a-0acb5351c00e" />


**Menu → Play → Results → Leaderboard**, with the option to replay or submit a score under a chosen name.

<img width="1916" height="1116" alt="Screenshot 2026-08-26 151236" src="https://github.com/user-attachments/assets/1461c678-aba1-4f9f-8f21-9b380552a5a5" />


---

## Technical Overview

| Area | Implementation |
|---|---|
| Engine | Unity 6 (6000.0.38f1) |
| Language | C# (18 scripts) |
| Art | Original 2D sprite work; licensed free background asset |
| Rendering | Multi-layer parallax scrolling with a seamless looping highway |
| Timing | Frame-independent reaction capture and per-round accumulation |
| Audio | Layered engine audio synchronized to simulated gear shifts |
| Persistence | Third-party leaderboard service for cross-session global scores |
| Scene flow | Menu, countdown, gameplay, and game-over states with persistent background |

### Notable components

- **`ReactionManager.cs`** — core timing loop: prompt scheduling, input capture, and per-round reaction accumulation.
- **`ParallaxScrolling.cs` / `HighwayLooper.cs`** — layered background movement and seamless track looping, producing continuous forward motion from finite sprite assets.
- **`CountdownManager.cs` / `ScoreManager.cs`** — round pacing and score accumulation.
- **`AudioManager.cs`** — engine audio state machine tied to gear-shift events.
- **`Leaderboard.cs` / `leaderboardmanager.cs`** — score submission, retrieval, and top-ten display.
- **`GameOverManager.cs` / `mainmenumanager.cs`** — scene transitions and UI state.

---

## My Contributions

I created Reflex Racer as a personal project before it became our COSC 302 group submission. My work covers the concept, the art, and the core gameplay:

- **Game concept and design** — originated the reaction-time driving premise and the full gameplay loop.
- **Sprite art** — created the game's 2D sprite assets.
- **Parallax and scrolling systems** — implemented multi-layer parallax and seamless highway looping to produce continuous motion from finite assets.
- **Reaction prompt system** — built the prompt scheduling, input capture, and reaction-timing mechanics that the game is built around.

Audio and the leaderboard integration (and the code behind them) were handled by teammates. The highway background uses a free third-party asset (see Credits).

Built with Pablo Storch, Peter Wraith, and Nicholas Rich.

> Note: the repository's commit history was reset during development when the main branch was recreated, so the contributor graph does not reflect actual authorship. A recovered activity log is preserved in `time_log`.

---

## Running the Game

### Play the build

1. Download the latest release from the [Releases](../../releases) page.
2. Extract the archive and run `Reflex Racer.exe`.

### Build from source

1. Clone the repository.
2. Open the project folder in Unity [VERSION] or later.
3. Open `Assets/Scenes/[MAIN SCENE]` and press Play.

---

## Known Issues & Future Work

- Brief stutter during scene transitions; would be resolved with asynchronous scene loading.
- Engine audio for gear shifts runs longer than the shift itself, causing desync after the first shift.
- Minor sprite seam in the highway background texture.
- Leaderboard occasionally fails to display, likely a timeout in the third-party service; would benefit from retry logic and a cached fallback.

---

## Built With

Unity · C# · Leaderboard Creator (Dan Qzq)

## Credits

- Highway background: [asset name / author, with link]
- Leaderboard: Leaderboard Creator by Dan Qzq
- Audio: created by Nick Rich

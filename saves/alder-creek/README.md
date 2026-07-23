# Alder Creek — a game of *LIFE*

*One playthrough of the LIFE god-game. The rules that run it live in
[`../../engine/`](../../engine/); this directory is the save.*

You are the god of a small town. Its people live their lives each night, and
some of them pray. Each morning you read the prayers and you **move** — a
whisper into a mind (arriving as the mortal's own thought; they never know it was
you), an omen, an act, a decree, or silence. Silence is also a move.

## How to resume this game

Say what you want to do — *whisper to X*, *give the town courage*, *skip a week*,
*next day*, *show me the gauges*. The engine reads `config.md` first, then
`world/summary.md`, `world/calendar.md`, `world/gauges.md`, the tail of
`world/chronicle.md`, and `whispers.md`, then picks the story back up.

## What's in this save

| Path | What it is |
|---|---|
| `config.md` | This run's setting, tone, intensity, mode, and one-paragraph "where we are" |
| `world/chronicle.md` | The day-by-day story — the whole saga so far |
| `world/summary.md` | The short "previously on…" state |
| `world/calendar.md` | Current day, season, pending prayers, live arcs |
| `world/gauges.md` | 🌱 Flourishing · 🕯️ Faith · 🌫️ Veil · 📜 Legacy + the Grace ledger |
| `world/reckoning.md` | The shelf of chapter titles (one per game-year) |
| `world/outbreak.md` | The siege / survival tracker |
| `whispers.md` | The numbered log of every move the god has ever made |
| `agents/awake/` · `sleeping/` · `departed/` | One file per character |

## The story so far

Two chapters are on the shelf: **THE QUIET PROVIDENCE** (Year One) and **THE LONG
THAW** (Year Two — a reanimation plague, a siege, a cure of *cold-then-heat*, and
a winter in which thirteen hundred of the dead were walked back through the
door). Year Three is underway: the cure is loose in a broken world, and the world
has begun walking up the road to be saved.

*The door opens for everyone.*

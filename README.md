# Godgame — *LIFE*

A game where you play god.

You are the god of a small town (**Alder Creek**). Its people live their lives
each night, and some of them pray. Each morning you read the prayers and you
**move** — a whisper into a mind (arriving as the mortal's own thought; they
never know it was you), an omen, an act, a decree, or silence. Silence is also
a move. There's no code and no API: **Claude is the engine, and you play by
chatting.** The entire game state lives in this repo as markdown, and every turn
is one git commit — **git is the save system.**

## How to play / resume

Read **[`GAME.md`](GAME.md)** first — it's the full ruleset *and* the cold-start
resume guide (it tells the engine exactly which files to read to pick the story
back up). Then just say what you want to do: *whisper to X*, *give the town
courage*, *skip a week*, *next day*, *show me the gauges*.

## What's in here

| Path | What it is |
|---|---|
| `GAME.md` | The rules (gauges, the Grace budget, the arc engine) + how to resume |
| `world/chronicle.md` | The day-by-day story — the whole saga so far |
| `world/summary.md` | The short "previously on…" state |
| `world/calendar.md` | Current day, season, pending prayers, live arcs |
| `world/gauges.md` | 🌱 Flourishing · 🕯️ Faith · 🌫️ Veil · 📜 Legacy + the Grace ledger |
| `world/reckoning.md` | The shelf of chapter titles (one per game-year) |
| `world/outbreak.md` | The siege / survival tracker |
| `whispers.md` | The numbered log of every move the god has ever made |
| `agents/awake/` · `sleeping/` · `departed/` | One file per character |

## The three gauges

- 🌱 **Flourishing** — the town's wellbeing.
- 🕯️ **Faith** — do they believe someone listens?
- 🌫️ **Veil** — can anything be *proven*? (Mastery is high-Faith-**high-Veil**: a
  town that *knows* without *proof*.)

**Anything is possible. Nothing is free.** In hard mode the god gets a Grace
budget each season; emotions are always free; and spending beyond the budget is
paid in consequences. **The game never ends** — each anniversary names the year
just lived as a chapter and the next one begins, slightly harder, forever.

## The story so far

Two chapters are on the shelf: **THE QUIET PROVIDENCE** (Year One) and **THE LONG
THAW** (Year Two — a reanimation plague, a siege, a cure of *cold-then-heat*, and
a winter in which thirteen hundred of the dead were walked back through the
door). Year Three is underway: the cure is loose in a broken world, and the world
has begun walking up the road to be saved.

*The door opens for everyone.*

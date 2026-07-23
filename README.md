# Godgame — *LIFE*

A game where you play god. Its people live their lives each night, and some of
them pray. Each morning you read the prayers and you move — a whisper into a
mind, an omen, an act, a decree, or silence. **There's no code and no API:
Claude is the engine, and you play by chatting.** The game state lives in this
repo as markdown, and every turn is one git commit — **git is the save system.**

## How this repo is laid out

The game is split into two clean halves — the reusable **engine** and each
individual **save** — the way an app separates its program from a player's save
file.

```
engine/                 ← the rules + blank templates (the "program"). Rarely changes.
├── RULES.md            ← the complete ruleset + how to resume / start a save
├── README.md           ← how the engine works
└── templates/          ← blank starting files for a new world

saves/                  ← one directory per playthrough (the "save files")
└── alder-creek/        ← the flagship game — Day 806, Year Three
    ├── config.md       ← this run's setting, tone, mode, "where we are"
    ├── world/          ← chronicle, gauges, calendar, summary, reckoning
    ├── agents/         ← one file per character (awake / sleeping / departed)
    └── whispers.md     ← the log of every move the god has made
```

- **To play or resume a game:** open its save (start with
  [`saves/alder-creek/`](saves/alder-creek/)) and just say what you want to do.
- **To learn the rules:** read [`engine/RULES.md`](engine/RULES.md).
- **To start a new world:** copy `engine/templates/` into `saves/<your-town>/`
  and fill it in — see [`engine/README.md`](engine/README.md).

## The three gauges

- 🌱 **Flourishing** — the town's wellbeing.
- 🕯️ **Faith** — do they believe someone listens?
- 🌫️ **Veil** — can anything be *proven*? (Mastery is high-Faith-**high-Veil**: a
  town that *knows* without *proof*.)

**Anything is possible. Nothing is free.** In hard mode the god gets a Grace
budget each season; emotions are always free; and spending beyond the budget is
paid in consequences. **The game never ends** — each anniversary names the year
just lived as a chapter and the next one begins, slightly harder, forever.

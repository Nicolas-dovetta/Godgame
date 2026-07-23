# The LIFE engine

This directory is the **reusable game system** — the rules and the blank
templates for starting a new world. It contains nothing about any particular
playthrough. A running game lives in its own directory under `saves/`.

Think of it the way an app separates **code** from **a user's save file**:

| | Path | Changes when… |
|---|---|---|
| **Engine** (this dir) | `engine/` | the rules or templates are improved — rarely |
| **Save** (one per game) | `saves/<town>/` | every single turn |

## What's here

| Path | What it is |
|---|---|
| `RULES.md` | The complete ruleset — gauges, the Grace budget, the arc engine, and the resume/new-game procedures. This is the god-game's "engine": Claude reads it, then runs the world. |
| `templates/` | Blank starting files for a new save. Copy them into `saves/<town>/`, drop the `.template` from each name, and fill them in. |

## Starting a new save

```
saves/<your-town>/
├── config.md              ← from templates/config.template.md
├── whispers.md            ← from templates/whispers.template.md
├── world/
│   ├── summary.md         ← from templates/world/summary.template.md
│   ├── calendar.md        ← from templates/world/calendar.template.md
│   ├── gauges.md          ← from templates/world/gauges.template.md
│   ├── chronicle.md       ← from templates/world/chronicle.template.md
│   ├── reckoning.md       ← from templates/world/reckoning.template.md
│   └── outbreak.md        ← optional, only if you run a siege/survival arc
└── agents/
    ├── awake/             ← one file per significant character (see agent.template.md)
    ├── sleeping/
    └── departed/
```

Fill in `config.md` (setting, tone, Event Intensity, Standard vs Hard mode),
seed 3-6 characters in `agents/awake/`, and play Day 1.

## The one rule for this directory

**Never edit `engine/` during play.** Only the save changes turn to turn. When
you improve the rules or a template, that's an engine change — commit it on its
own, and it applies to every future save.

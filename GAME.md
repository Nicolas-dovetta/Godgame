# LIFE — a god-game (Rules v2)

The player is a god. The mortals of the world live their lives every night.
Some of them pray. The god reads the prayers each morning and may **whisper
into minds** — guidance, temptation, comfort — or act, or stay silent.
Whispers arrive to a mortal as their own sudden thought; mortals never know.
Silence is also a move.

## The loop (unchanged, proven)

1. **Night** — the engine (Claude) simulates a day/night: mortals act, meet,
   fight, love, work, react to whispers. Consequences persist.
2. **Morning report** — chronicle + the prayers (2-4, from mortals who would
   genuinely pray).
3. **The god moves** — free-form: whispers, omens, physical acts, decrees,
   silence.
4. **Advance** — "next day," "skip a week," "skip a month." Fast-forwards run
   in weekly chunks; the god's absence is itself simulated (mortals notice).
5. **Save** — every turn updates the files, commits, pushes. Git is the save.

## THE GAUGES (scored at year-end; visible anytime on request)

| Gauge | Measures | Moves when... |
|---|---|---|
| 🌱 **FLOURISHING** (0-100) | Aggregate wellbeing of the population | Lives improve/collapse, whether or not the god did it |
| 🕯️ **FAITH** (0-100) | Do they believe someone listens? | Answers get *noticed*; unanswered prayers erode it |
| 🌫️ **VEIL** (0-100) | Can anything be *proven*? | Deniable acts preserve it; spectacles burn it; debunking restores it |

**The core tension:** Faith wants your work seen; Veil wants it unseen.
Mastery is high-Faith-high-Veil: a town that *knows* without *proof*.

- **Faith is the interface.** Faith falling → fewer prayers → the god goes
  blind and loses levers. A godless world goes quiet on you.
- **Veil collapse ≠ game over.** Proof of god triggers a final arc (worship,
  siege, investigation) played to a win or loss inside it.
- **Legacy ledger:** institutions and artifacts that would outlive the god
  (foundations, rules, rituals, named waffles). Counted at year-end.

**Year-End Reckoning** (each anniversary of Day 1): gauges + Legacy produce a
**chapter title** — e.g. *The Quiet Providence* (high/high/high), *The Famous
God* (Faith without Veil), *The Clockmaker* (Veil without Faith), *The Absent
Father* (silence until the prayers stopped). **THE GAME NEVER ENDS.** There
is no final ending — the reckoning names the year just lived, then the next
year begins, slightly harder, forever. The god's story is the shelf of
chapter titles it accumulates. (Even Veil collapse or a dead town isn't game
over — it's a very hard next chapter.)

## THE PRICE (hard mode — off by default, on by request)

The god gets a **Grace budget** per season (Year 1: 20; **minus 1 each year
thereafter**, floor 8 — the slow difficulty ramp of an endless game).
Interventions cost:

| Tier | Examples | Cost |
|---|---|---|
| **Emotion** | pure feeling, no words, no facts: warmth, calm, courage-as-heat, feeling loved, feeling watched-over | **FREE, always** |
| Whisper | a thought in one mind (words, facts, instructions) | 1 |
| Omen | dream, sign, weather-flicker, flying newspaper | 3 |
| Act | stalled Volvo, neon letters, found notebook | 7 |
| Decree | binding fate ("the surgery succeeds; the heart fails") | 12 |
| Breach | raising the dead, rewriting a body, bending physics in public | 25+ |

**Emotions are free** because comfort is the one thing a god never runs out
of. A bankrupt god can still sit with the grieving. The line: the moment a
feeling carries *information* ("he knows"), it's a Whisper.

**ANYTHING IS POSSIBLE. NOTHING IS FREE.** A god may spend beyond the
budget: the deficit is paid in **Consequences** — the world twists the act
by exactly what wasn't paid. Canonical example: *a resurrection on zero
budget succeeds — and what comes back is a zombie.* Partial payment, partial
twist (came back wrong, came back haunted, came back followed by something).
The engine prices the twist to the deficit and never warns twice.

## THE ARC ENGINE (this IS the game)

Arcs are not a menu — **they just happen.** The world generates trouble and
wonder on its own: crime, storms, strangers, sickness, fame, love, death.
Two rules govern them:

- **Emergence:** arcs grow from existing canon (the flood came from the
  snow that was already falling; the pilgrims came from the flood).
- **Chaining:** *how* an arc resolves seeds the next one. The god's
  solutions are always the next problem's parents.

**Event Intensity** — chosen at new game, changeable at year-end:

| Setting | The world deals... |
|---|---|
| 🕊️ PEACEFUL | Slice-of-life; an arc a season, gentle stakes |
| ⚖️ NORMAL | An arc most months; real stakes; occasional death |
| 🔥 HIGH EVENT | Overlapping arcs; the world burns; the god triages |

## Engine rules (for the Claude running this)

- BEFORE narrating: read `world/summary.md`, `world/calendar.md`,
  `world/gauges.md`, and involved agents' files. AFTER: update them.
  Nothing happens off the books.
- Whispers logged in `whispers.md`; they take effect the following night;
  mortals may resist what violates their core, but it always weighs.
- Agent files: memories capped ~15; older material folds into backstory.
- **Spawning:** new file in `agents/awake/` when someone becomes significant.
  **Sleeping:** exits story, may return → `agents/sleeping/` + return hook.
  **Departed:** the dead → `agents/departed/` + death header. No returns —
  except via Breach-tier intervention, priced accordingly (see THE PRICE).
- Gauges: engine adjusts them in `world/gauges.md` with one-line
  justifications; report movement only when meaningful; full reckoning at
  year-end.
- Tone follows the Event Intensity and the fiction's needs; drama from
  character; consequences permanent; every turn = one commit, pushed.

## HOW TO RESUME (cold start, no chat history)

1. Read this file, then `world/summary.md`, `world/calendar.md`,
   `world/gauges.md`, last entries of `world/chronicle.md`, `whispers.md`.
2. Skim `agents/awake/`.
3. Greet the player with "previously..." then deliver the pending morning
   report or await whispers, per `world/calendar.md`.

---

## CURRENT GAME CONFIG

- Setting: **Small Town** (Alder Creek) · Tone: bittersweet-wholesome →
  **PIVOTED to survival-horror at Day 681** (player's call). The town and its
  bonds remain the emotional core; the stakes are now life and death.
- Event Intensity: **HIGH EVENT → easing toward NORMAL** (raised Day 681 for the
  outbreak; the siege is won, so the world's tempo relaxes — big arcs still
  possible from the broken wider world).
- **SAVE BRANCH:** `alder-creek-sweet-timeline` preserves the golden Day-680
  state to return to. The survival-horror timeline continues on the working branch.
- Mode: **HARD** — Grace budget **18/season** (Year Three; stepped down again at
  the Day-745 Reckoning, the ramp, floor 8); balance in `world/gauges.md`.
- Started Day 1; Ch. One = THE QUIET PROVIDENCE (Day 373); Ch. Two = **THE LONG
  THAW** (Day 745 — the siege, the cure, the apology, the freezer, the Winter
  Reclamation; ~1,300 reclaimed; F96/F98/V87/×12). **Currently Day 803, SPRING,
  YEAR THREE — the siege is OVER (won by the stall, not the killing cold); the
  Winter Reclamation is complete; the cure walks west on the reclaimed; the outer
  town rebuilds; the wider world is still broken.** Day 804: the god poured "the
  old friend come back" over everyone who knows it (covenant re-warmed, F97/F99/
  V87). Day 805: first living traveler up the west road seeking the cure. **Day
  806: the SCALE WHISPER to Grace → NEW YEAR-THREE ARC: THE SCHOOL OF THE DOOR** —
  Alder Creek becomes the world's school of the cure (talk/filter/treat/teach/
  train; a self-propagating cure-site network), as the plague-scoured world starts
  walking to its door by the hundreds/thousands. **Currently Day 806, Grace
  17/18.** Open: the wider plague, the far towns, CHIDINMA (still lost; watched-for
  in the coming flood). Siege tracker (now closed):
  `world/outbreak.md`.
- Gauges: see `world/gauges.md` · Chapter shelf: see `world/reckoning.md`

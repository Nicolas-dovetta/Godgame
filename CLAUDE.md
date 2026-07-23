# CLAUDE.md — how to help in this repo

This repo is two things:
1. **LIFE**, a god-game where *Claude is the engine* — rules in `engine/RULES.md`,
   playthroughs (saves) in `saves/`.
2. **A product being launched** by a solo, part-time founder — strategy and plans
   in `docs/`.

Figure out which one the user wants from what they say, and help with that.

## If the user wants to PLAY the game
Follow `engine/RULES.md`. Load the relevant save (e.g. `saves/alder-creek/`),
read its `config.md` and `world/` files, greet with "previously…", and run turns.
Every turn updates the save's files and is one commit.

## If the user wants to LAUNCH the product — be their step-by-step coach
The founder has explicitly asked to be **hand-held, one step at a time.** Assume no
prior knowledge; be concrete about exactly what to click, type, or sign up for.

**On each launch-help session:**
1. Open **`docs/LAUNCH_PLAN.md`**. Read the **▶ CURRENT STEP** pointer and find the
   first unchecked `- [ ]` step.
2. Walk the user through **only that one step** — what to do, where, and how they'll
   know it's done. Don't dump the whole plan on them. Don't skip ahead.
3. When they confirm it's done: check its box `- [x]`, move the **▶ CURRENT STEP**
   pointer and progress count to the next step, append a dated line to the
   **Progress log** (what they did — *never a secret*), and commit
   (`docs: launch step X.Y done`).
4. Then ask if they want to keep going to the next step, or stop for now.
5. If a step is one the coding agent builds (🛠️), help them write/spec/test it, but
   the acceptance check ("Done when…") is still theirs to confirm.

**Guardrails to enforce as their coach:**
- **Never let a secret into the repo.** API keys, tokens, passwords go in a local
  `.env` (git-ignored). If the user pastes one, tell them to remove it and store it
  in `.env` instead; do not commit it.
- **Keep the zero-loss rules true** (see the end of `LAUNCH_PLAN.md`) — flag
  anything that would commit money ahead of revenue.
- The **free-usage kill-switch (step 3.3)** must be live before any public launch —
  don't let them skip it.
- Steps **0.5 (Stripe), 0.6 (NCMEC)** have approval delays — nudge them to start
  those early even while doing other steps.

## Working conventions
- Never edit `engine/` during play — only saves change.
- Commit as you go; push when asked.

# LIFE — Product Strategy

*Turning the LIFE god-game (see [`../engine/`](../engine/) and
[`../saves/alder-creek/`](../saves/alder-creek/)) into a product. A rendered,
shareable version of this lives at `docs/life-strategy.html`.*

## The product in one line

An AI-native, persistent, emergent narrative where **Claude (or another model) is
the engine**, markdown is the world, and git is the save. A new category, not a
new title — the structure (three gauges, a Grace budget, year-end reckonings) is
what gives the open-endedness a spine, and hands us a monetization surface the
fiction itself justifies.

## Architecture: current → future

**Today (prototype).** Single-player. Engine = the model, prompted by
`engine/RULES.md`. State = markdown. Save = git. Driven by hand in chat. Ceilings:
context (the 325 KB chronicle can't all be read each turn — the town drifts), no
accounts/UI/mobile, no cost metering.

**Future (product).** Web + mobile client (chat + a living dashboard: gauges, town
map, character cards, whisper log). A turn-loop orchestrator that enforces token
budgets. **Retrieval + rolling summaries** over a vector store for bounded context
(a town that never forgets). Per-player world DB, with git export kept as a
premium "own your save" feature. Tiered/multi-provider model routing. A
consistency + safety layer (the category's hardest, most necessary work).

## The engine/save split (done in this repo)

The repo is now split the way an app separates its program from a save file:

- `engine/` — rules + blank templates. The reusable system. Rarely changes.
- `saves/<town>/` — one playthrough's state. Changes every turn.

This is the productization made concrete: the engine ships to every player; each
player gets their own save directory.

## Unit economics — the cadence is the cost governor

A "turn" = read a slice of world state (retrieval-bounded, ~20K tokens, not the
whole chronicle) + generate a scene (~1.5K tokens), with the stable ruleset
prompt-cached (~90% off that portion). **One turn per night is the free-tier
default** — the mortals live overnight, the god reads the morning's prayers and
moves. At ~30 turns/month:

| Engine for the turn | $/1M (in · out) | ~Cost/turn | Free tier (1/night) |
|---|---|---|---|
| **Grok 4.1 Fast** — bookkeeping, fast-forward | $0.20 · $0.50 | ~$0.004 | ~$0.11/mo |
| **Haiku 4.5** — cheap world-sim | $1 · $5 | ~$0.02 | ~$0.60/mo |
| **Sonnet 5** — default narrator | $2 · $10\* | ~$0.04 | ~$1.20/mo |
| **Grok 4.5** — darker narrator option | $2 · $6 | ~$0.04 | ~$1.20/mo |
| **Opus 4.8** — Breach-tier spectacle only | $5 · $25 | ~$0.11 | ~$3.30/mo |

\*Sonnet 5 intro rate (standard $3/$15). Grok rates per xAI, July 2026.

**Conclusion.** Capping the free tier at one turn/night turns the old "heavy users
lose money" fear into a non-issue — a free player costs cents to a couple dollars
a month, even on a premium model. Paid tiers sell *more cadence* (turns/day,
faster sim, more towns); a $12 player at 3–5 turns/day still costs only ~$4–6 to
serve. **Grace top-ups** cover the true bingers. The daily ritual is also a proven
retention loop (the Wordle/streak pattern). Hosting (DB, vector store, storage) is
a rounding error next to inference — ~$0.50–$2 per active user per *year*.

**Cheapest model with good quality:** **Sonnet 5 as the default narrator** (this
game's magic is long-range coherence and emotional nuance — Haiku's tier shows its
limits there), with **Haiku 4.5 / Grok 4.1 Fast for mechanical work** (bookkeeping,
memory-folding, RAG summaries, "skip a week" fast-forwards) and **Opus 4.8 reserved**
for Breach-tier spectacle and year-end reckonings. Blended, a typical turn is
~$0.03–0.05.

## Multi-model strategy (creative)

- **Choose your narrator.** Model choice is a *feature*, not a hidden cost line —
  Claude (warm, literary, wholesome) vs Grok (darker, irreverent, unflinching, a
  fit for the survival-horror turn), behind a safety layer. A personality knob and
  a paid perk competitors can't cheaply copy.
- **Route by task, stay provider-agnostic.** Cheap model for bookkeeping/
  fast-forward, mid model for the god's moves, top model for spectacle.
  Multi-provider = margin arbitrage + negotiating leverage + resilience.
- **Cheap hardware for the "instant scene" feel.** Note the name collision: *Grok*
  (xAI, the model) vs *Groq* (the LPU chip company). Groq/Cerebras serve
  open-weight models fast and cheap — near-instant streaming, and the mechanical
  tier trends toward ~zero at scale.
- **The owned-model moat.** Every turn is a proprietary, emotionally-coherent
  god-game training example. With volume, fine-tune a bespoke "LIFE engine" that's
  cheap, fast, on-voice, and hard to replicate. Your data → your model → your
  margins.

## Pricing

- **Mortal (free):** one turn/night, Peaceful mode, one world. Emotions always
  free. Near-zero to serve; pure funnel.
- **Deity (~$12/mo):** Hard mode, full Grace/season, multiple worlds & save
  branches, faster sim, more characters, **choose your narrator** + Opus for big
  beats.
- **Grace packs ($5+):** consumable turns/Grace — the whale & heavy-user lane;
  in-fiction, literally buying miracles.
- **Pantheon Pro (~$25/mo):** custom settings/rulesets, publish & share worlds,
  own-your-save git export, streamer tools.

The mechanic is the meter: "Grace" (the god's in-fiction budget) maps 1:1 onto
compute, so selling it is selling turns the player already believes in.

## Market (illustrative)

TAM (AI-native interactive narrative) 100M+ → SAM (emergent/moral-choice players)
~8M → SOM (3-yr) ~1.2M registered / ~120k paid. Illustrative revenue model:
Y1 ~$0.4M → Y2 ~$4M → Y3 ~$17M ARR. Comparables: Character.AI (tens of millions
MAU), AI Dungeon (seven-figure players). LIFE is more cerebral — win on depth, not
reach.

## Go-to-market

The chronicle is the ad. (1) Ship the share loop first — one-tap chronicle cards,
"name your chapter" moments. (2) Court storytellers — moral-dilemma gameplay is
made for streaming; a creator program + Pro tools. (3) Launch on the thesis — "a
game with no code, where the AI is the engine" is an HN/Product Hunt story. (4)
Referral in the currency — invites grant Grace, not discounts.

## Mobile deployment

- **One codebase → web + both stores:** React Native / Expo. Ship a responsive
  PWA first (no gatekeepers, instant updates, web billing) to validate retention
  and unit economics, then wrap for the stores.
- **LLM calls stay server-side, always.** Client ↔ your API ↔ provider; stream
  tokens over SSE so the scene appears as it's written.
- **Store tax is real and stacked:** Apple/Google take 15–30% on in-app digital
  goods; subs + Grace packs must go through StoreKit / Play Billing. Price it in.
- **Approval risk is the gate:** dark themes + companion dynamics → likely 17+ and
  AI-content scrutiny (the AI Dungeon minefield). Robust moderation *before*
  submission.
- **Push notifications** ("your town prayed while you were away," "a stranger
  reached the west road") are the re-engagement hook and fit the fiction — the
  god's absence is already simulated.

## Chance of success (honest)

- ~70% — a beloved niche product with a passionate base.
- ~25% — a durable $10M+ ARR business in 3 years.
- ~8% — a category-defining breakout at Character.AI scale.

**Top risks:** long-term memory/consistency (the core unsolved tech bet — a town
that forgets breaks the promise); safety & moderation at scale; retention past
novelty. **Now largely mitigated:** unit economics (solved by the daily cadence +
routing) and platform dependency (multi-provider routing now, an owned fine-tuned
model later).

**Bottom line:** build the memory layer and the meter first, route every turn to
the cheapest model that fits, and let the daily ritual do the retention work.

---

*Illustrative models, not forecasts. Model prices move; figures are as of
July 2026. Sources for xAI pricing: eesel.ai, pricepertoken.com, felloai.com.*

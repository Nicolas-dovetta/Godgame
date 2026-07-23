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
moves. **Engine is Grok-only** (a deliberate simplification); route each turn to
the cheapest Grok tier that fits it.

| Grok tier for the turn | $/1M (in · out) | ~Cost/turn | Cost / user·month |
|---|---|---|---|
| **Grok 4.1 Fast** — Free tier + all bookkeeping | $0.20 · $0.50 | ~$0.004 | ~$0.11 · 1/night |
| **Grok 4.5** — Monthly "better model" narrator | $2 · $6 | ~$0.04 | ~$4.80 · 4/day |
| **Grok 3 Mini** — legacy cheap fallback | $0.30 · $0.50 | ~$0.006 | — |

Grok rates per xAI, July 2026. Moderation adds ~$0.001–0.005/turn (free/open
classifiers). Hosting is a rounding error — ~$0.50–$2 per active user per *year*.

**Conclusion.** Capping the free tier at one turn/night makes it cost ~$0.11/mo on
fast Grok — sustainable as a pure, data-shared funnel. Monthly caps at 4 turns/day
on the better model, so a $12 subscriber still costs only ~$5 to serve — healthy
margin. **Grace packs** cover the true bingers. The daily ritual is also a proven
retention loop (the Wordle/streak pattern). xAI's ~$175/mo free API credits (via
the data-sharing program) cover a lot of early usage — and fit the free-tier deal
directly.

## Multi-model note (Grok-only for now)

Committing to Grok simplifies the build and fits the mature/edgy tone (Grok is
permissive). Trade-off: single-provider dependency (see risks). Keep in the back
pocket: *Grok* (xAI, the model) vs *Groq* (the LPU chip company) — Groq/Cerebras
serve open-weight models fast and cheap for a future "instant scene" speed tier.
**The owned-model moat:** every turn is a proprietary, emotionally-coherent
training example; with volume, fine-tune an *open* model (you can't fine-tune
Grok) into a bespoke "LIFE engine" — cheap, on-voice, and yours.

## Pricing — two prices + à la carte

- **Free · Mortal ($0):** 1 turn/night, fast Grok, emotions always free, one
  world, read-only chronicle export. **Data-shared (consented)** — that funds the
  tier. Costs ~$0.11/user/month; pure funnel.
- **Monthly · Deity (~$12/mo):** 4 turns/day, Hard mode, **better model (Grok
  4.5)**, multiple worlds & save branches, no data-sharing required.
- **À la carte (one-off, on either tier):** **new words & experiences** (settings,
  scenarios, tones — survival-horror pack, noir pack) and **Grace packs**
  (consumable turns for a binge). This is where the margin upside sits.

The mechanic is the meter: "Grace" (the god's in-fiction budget) maps 1:1 onto
compute, so selling it is selling turns the player already believes in.

## Compliance & safety — launchable at $0 (mature, not explicit)

Choosing **mature but non-explicit** is what makes zero-capex compliance real: it
removes paid ID verification and high-risk adult payments, and keeps you on Stripe
and the app stores. Grok is permissive, so **your moderation layer is the brake,
not the model.**

- **Moderation (free):** screen every input *and* output with OpenAI's free
  Moderation API + an open safety model (Llama Guard / ShieldGemma). Log
  everything. ~$0.001–0.005/turn. Build: `input → moderate → character-age check →
  Grok → moderate output → log → show`, plus a Report button → review queue.
- **Age gate (free):** self-attestation + a Mature 17+ (IARC) rating + geo-block
  restricted regions. Non-explicit ⇒ **no paid ID verification** (the saved cost).
- **CSAM / NCMEC (free, mandatory):** enforce character-age in any romantic/sexual
  context (block "aged-up"/"looks young" evasions); register as an ESP; wire the
  CyberTipline report path; you review at MVP scale. Legally required (18 U.S.C.
  §2258A), live from turn one.
- **Payments & hosting ($0 capex):** Stripe pay-as-you-go (fees only when you
  earn), **PWA-first** to skip store fees, free-tier backend.
- **xAI AUP:** "only Grok" still binds you to xAI's terms — moderation keeps you
  inside them too, and the free-tier data-sharing must be clearly consented.

**The one place $0 carries real risk — legal.** Free templates (Termly/iubenda)
launch you, but an AI product with a data-sharing deal + CSAM obligations wants a
lawyer's eyes: book a **one-time ~$500–1.5k review** once you have a paying month.
*(Not legal advice; validate against your jurisdictions.)*

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
that forgets breaks the promise); safety & moderation at scale (you are the brake,
not Grok); single-provider dependency (Grok — a price/policy change lands on you,
mitigated later by a fine-tuned open model); retention past novelty. **Now largely
mitigated:** unit economics (solved by the daily cadence, Grok Fast for
bookkeeping, and caching).

**Bottom line:** build the memory layer and the meter first, route every turn to
the cheapest model that fits, and let the daily ritual do the retention work.

---

*Illustrative models, not forecasts. Model prices move; figures are as of
July 2026. Sources for xAI pricing: eesel.ai, pricepertoken.com, felloai.com.*

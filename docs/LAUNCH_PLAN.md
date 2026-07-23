# LIFE — Launch Plan (walk me through it)

> **How this works.** This is a living checklist. Do **one step at a time**. When a
> step is done, its box gets checked `- [x]` and the **Current step** pointer below
> moves to the next one. If you're chatting with Claude in this repo, it will read
> this file, find the current step, and walk you through it in plain language — ask
> it "what's my next step?" and it will hand-hold from here.
>
> **Never commit secrets.** API keys, tokens, and passwords go in a local `.env`
> file (already git-ignored) — never typed into this repo. Record only *that* you
> did a thing in the Progress log, not the secret itself.

---

## ▶ CURRENT STEP: **0.1 — Buy a domain** (Phase 0 not started)

**Overall progress:** 0 / 27 steps · Phase 0 of 6
**Target:** soft launch in ~2 months at ~8–10 hrs/week (~60–90 focused hours).

Legend: `[ ]` to do · `[x]` done · ⏱ = your hands-on time · 🛠️ = your coding agent
builds it (you direct + test) · ⏳ = has an approval/wait delay, start it early.

---

## Phase 0 — Accounts & decisions · Week 1 · ~4–6 hrs
*Start the three ⏳ items first — they have delays.*

- [ ] **0.1 — Buy a domain** ⏱15 min
  - Do: pick a name, buy it at any registrar (Namecheap/Cloudflare/Porkbun, ~$12/yr).
  - Done when: you own the domain and can log into the registrar.
- [ ] **0.2 — xAI (Grok) account + API key + data-sharing** ⏱30 min ⏳
  - Do: sign up at the xAI developer console, create an API key, and **opt into the
    data-sharing program** to get the ~$175/mo free credits.
  - Done when: you have a Grok API key saved in your local `.env` and see the credit.
- [ ] **0.3 — OpenAI account + moderation API key** ⏱15 min
  - Do: sign up, create an API key (the Moderation endpoint is free).
  - Done when: key saved in `.env`.
- [ ] **0.4 — Hosting accounts (all free tier)** ⏱30 min
  - Do: create Vercel **or** Cloudflare Pages (web host) + Supabase **or** Neon
    (database). Free tiers only.
  - Done when: accounts exist; you can create a project.
- [ ] **0.5 — Stripe account** ⏱30 min ⏳ *(identity check can take 1–2 days)*
  - Do: sign up, start business/individual verification.
  - Done when: account created and verification submitted.
- [ ] **0.6 — Register as an NCMEC ESP** ⏱1 hr ⏳ *(paperwork, start now)*
  - Do: register your entity with NCMEC's CyberTipline as an Electronic Service
    Provider. This is a legal requirement for handling any CSAM reports; free.
  - Done when: registration submitted.
- [ ] **0.7 — Lock the product config** ⏱1 hr
  - Do: confirm — town/setting, mature (non-explicit) tone, **free = 1 turn/night**,
    **paid = 4 turns/day**, **$12/mo** (+ optional **$99/yr**), à-la-carte packs.
  - Done when: written down (add to the Progress log).
- [ ] **0.8 — Socials + waitlist page** ⏱30 min
  - Do: grab an X handle + a Discord or subreddit; put up a one-line waitlist page.
  - Done when: a link exists where people can join a waitlist.

## Phase 1 — Build the MVP · Weeks 2–5 · ~30–45 hrs 🛠️
*Your coding agent writes the app; your job is direction + play-testing.*

- [ ] **1.1 — Hand the agent the spec** ⏱2 hrs
  - Do: point your coding agent at this repo; `engine/RULES.md` is the game spec.
  - Done when: the agent can explain the turn loop back to you.
- [ ] **1.2 — Core app** 🛠️
  - Agent builds: a PWA (web-first), chat UI + a dashboard (gauges, town), sign-in,
    and a per-user save in the database.
  - Done when: you can sign in and see an empty game shell.
- [ ] **1.3 — The turn loop on Grok** 🛠️
  - Agent builds: read save → retrieval-bounded context (not the whole chronicle) →
    call Grok → write the scene → save. With prompt caching on the ruleset.
  - Done when: you can take a turn and it persists.
- [ ] **1.4 — Memory / retrieval** ⏱2 hrs (your call) 🛠️
  - Decide with the agent how it retrieves past context so the town never forgets
    (rolling summaries + vector search over the chronicle).
  - Done when: the town references its own history across many turns.
- [ ] **1.5 — Cadence gate** 🛠️
  - Agent builds: free = 1 turn/night, paid = 4/day.
  - Done when: a free account is limited to one turn per night.
- [ ] **1.6 — Play-test** ⏱12–18 hrs (across the phase)
  - Do: play many turns, check coherence, tune the prompts.
  - Done when: it feels like the game, reliably.

## Phase 2 — Compliance & safety · Weeks 5–6 (overlaps) · ~6–10 hrs
- [ ] **2.1 — Write the moderation policy + character-age rule** ⏱2 hrs
  - Do: list the hard lines (minors/CSAM, real-person sexual, self-harm, weapons);
    rule: any character in a romantic/sexual context must be an adult.
  - Done when: the policy is written (drop it in `docs/`).
- [ ] **2.2 — Wire input + output moderation** ⏱2–3 hrs 🛠️
  - Agent builds: screen every prompt and every Grok output (OpenAI free Moderation
    + optional Llama Guard); log everything.
  - Done when: an over-the-line test prompt is blocked, and you see it in the log.
- [ ] **2.3 — Review queue + logging** ⏱1 hr 🛠️
  - Agent builds: a private page only you can see, listing flagged/reported items.
  - Done when: you can open the review queue.
- [ ] **2.4 — Age gate + rating** ⏱30 min 🛠️
  - Agent builds: a date-of-birth attestation gate; you set a Mature 17+ rating.
  - Done when: a new user must pass the age gate.

## Phase 3 — Payments + the zero-loss guardrails · Weeks 6–7 · ~4–6 hrs
- [ ] **3.1 — Stripe products** ⏱1–2 hrs
  - Do: in the Stripe dashboard create prices — $12/mo, $99/yr, Grace packs,
    experience packs.
  - Done when: the products exist in Stripe.
- [ ] **3.2 — Checkout + webhooks** ⏱2 hrs 🛠️
  - Agent builds: Stripe checkout + webhook handling; you test a real $1 purchase.
  - Done when: a test purchase unlocks paid features.
- [ ] **3.3 — The kill-switch (do not skip)** ⏱1 hr 🛠️
  - Agent builds: a per-user turn cap **and** a global free-compute budget that
    pauses new free sign-ups (→ waitlist) at the ~1,400-free-user credit ceiling.
  - Done when: you force the threshold low and watch it stop new free sign-ups.
- [ ] **3.4 — Spend alerts** ⏱30 min
  - Do: set billing/usage alerts on xAI and OpenAI.
  - Done when: an alert is configured.

## Phase 4 — Pre-launch · Weeks 7–8 · ~8–12 hrs
- [ ] **4.1 — ToS + Privacy Policy** ⏱2–3 hrs
  - Do: generate from free templates (Termly/iubenda); include the **data-sharing
    consent**. Paid legal review is deferred to your first paying month.
  - Done when: both pages are live and linked from the app.
- [ ] **4.2 — Seed content** ⏱4–6 hrs
  - Do: your starting town, 3–6 characters, a couple of à-la-carte experience packs.
  - Done when: a new player lands in a real, populated world.
- [ ] **4.3 — Full end-to-end test as a real user** ⏱3–4 hrs
  - Do: sign up → free turn → hit paywall → pay → play → moderation edge cases →
    kill-switch fires. Fix what breaks.
  - Done when: the whole loop works start to finish.
- [ ] **4.4 — Launch assets** ⏱3–4 hrs
  - Do: landing page, 3–5 shareable "chronicle card" screenshots, a short demo clip,
    and draft posts (Product Hunt / HN / Reddit / an X thread).
  - Done when: assets are ready to post.

## Phase 5 — Launch · Week 9 · ~1 focused day + monitoring
- [ ] **5.1 — Soft launch** ⏱a few hrs + monitoring
  - Do: invite a small batch (friends, one subreddit). Watch moderation + spend.
  - Done when: real strangers have played and nothing broke.
- [ ] **5.2 — Public launch** ⏱half a day + all-day replies
  - Do: post to Product Hunt + Hacker News ("a game with no code, the AI is the
    engine") + r/AIDungeon/r/rpg + an X thread of a dramatic chronicle beat.
  - Done when: you're live and answering comments.

## Phase 6 — After launch (recurring — this never "completes")
- [ ] **6.1 — Daily-ish (15–30 min):** clear the moderation queue (the one thing you
  legally can't automate), watch spend vs credits, reply to community.
- [ ] **6.2 — Weekly (2–4 hrs):** ship a fix/experience pack, post one shareable
  chronicle beat (your marketing loop), check conversion.
- [ ] **6.3 — Monthly:** review the funnel (free→paid, churn, à-la-carte); adjust
  free caps; **once you've had a paying month, book the ~$500–1.5k legal review.**

---

## The zero-loss rules (keep these true and you cannot lose money)
1. **No committed costs** — everything free-tier or pay-as-you-go and cancellable.
2. **Free tier stays inside the free credits** — cap it (waitlist or per-user trial)
   so ~≤1,400 active free users cost you $0.
3. **Charge before you compute** — subs bill in advance; Grace packs are prepaid.
4. **Defer paid legal** to your first profitable month.
5. **Only reinvest profit** — never front cash you haven't earned.

*Model + assumptions: `docs/LIFE-financial-model.xlsx` (regenerate via
`docs/build_model.py`). Full strategy: `docs/PRODUCT_STRATEGY.md`.*

---

## Progress log
*(Claude appends a dated line here as each step completes — e.g. what account was
made, what decision was locked. No secrets.)*

- _not started yet_

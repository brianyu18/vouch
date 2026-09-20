# Vouch

A mobile dating app where **your trusted friends swipe with you and for you.**

You supply a pool of **at most 10 items — photos and prompts combined**. Each friend
you invite **pitches their own version** of your profile, selecting and arranging a
subset of that pool; you pick the one that becomes your real profile, or reject them
all and build your own. Then your friends go out and swipe on your behalf —
alongside you. Matches come back to you, and only you, to review and chat.

> **Full product spec: [`docs/SPEC-v2.md`](docs/SPEC-v2.md)** (revision 9) — read it
> before any build work. This file is the short current-context summary.
>
> The v1 concept (friends author a profile, **AI consolidates** it, "roll the dice"
> regeneration) is **superseded**. It survives in git history at commit `06b8b89`.

## Core mechanics

- **One canonical profile.** Up to 3 swipers each submit a proposed profile; the user
  picks one or rejects all. Nothing circulates in multiple versions.
- **10-item material pool** — the cap protects swipers from being handed a chore;
  each pitch selects a subset, which is what makes the pitches differ.
- **The pitch happens once, at signup.** No re-runs; the profile evolves after that
  through ordinary edits (user edits and swiper suggestions, both free forever).
- **Everyone swipes together** — the user swipes alongside their crew, not instead
  of them. Every swipe is labelled with who made it. Not a mode, just how it works.
- **Date / Kiss / Pass** — swipe up = **Date, which IS the super like** (the original
  "marry"): the gesture is core and never paywalled, but the *count* is rationed at
  **1 per crew head per week**. Right = Kiss, left = Pass. Tags visible only to the user.
- **Swipe the thing, not just the person** — a swipe can attach to a specific prompt
  or photo *(Hinge structural steal)*
- **Agreement multiplier** — several friends acting the same way on the same target,
  strongest when they land on the same prompt or photo
- **Three review layers** — ambient crew activity in the group chat (on), pre-match
  hold per swiper (off by default, 24h auto-release), and **match review** (always on,
  the main event). Every swiper-authored message routes through the user.
- **Swipers see their own results only** — a profile they swiped that became a match
  is reported back to them; incoming likes, the user's own matches and every
  conversation stay private. User can mute it per swiper.
- **Allocation is a pie** — the user slices the daily Kiss pool per swiper on a dial;
  slices are guaranteed reservations totalling **≤100%**, and the user has precedence
  over the whole pie. Everyone sees a **live depleting bar** — free, never premium.
- **Outbound volume capped per user, never per swiper** — premium buys resolution,
  not volume
- **Group chat** for the user and their swipers — share profiles, discuss swipes
- **No AI.** Friends *suggest*; the user approves. All content is human.

## Premium — the swiping crew

The paid pillar is **crew size**: 3 swipers free → **5 on premium**, which is the
**hard ceiling for every user at every price. There is no tier above premium.**

| Tier | Permanent swipers | Crew | Weekly Dates *(1/head)* | Kisses |
|---|---|---|---|---|
| Free, solo | 0 | 1 | 1 | daily cap |
| Free | up to 3 | up to 4 | up to 4 | daily cap |
| Premium | **5 — the ceiling** | 6 | 6 | unlimited |

Additional swiping capacity is **rented, not bought**: pay to invite a **temporary
swiper** for a single session — the guest pass. Headcount is capped; surge is
consumable. Selling a tenth permanent slot would sell a favour the buyer cannot
collect on.

Dates run at **1 per crew head/week** (so recruiting a swiper raises your signal
budget — the invite incentive) and stop at 6, because headcount stops at 6. Extra
Dates sell in packs; a guest spends from the existing pool rather than adding to it.

Approved pillars **A–E**: **Ring** — the 90-second call, "ring your crush" (a request
to a match, receiver must accept, charged only on acceptance, audio, hard-timed with a
mutual "keep talking?" at zero, only the user can initiate; **free 1/month, premium
3/month**, more purchasable), profile insights, swiper scorecards, guest swipers (1/month, more
purchasable), and "see who Kissed you". Build order in spec §8.4 — crew size + "see who
Kissed you" at launch, the call next.

**Never premium:** the user editing their own profile, or swipers suggesting edits.
Both free forever. **Re-pitch does not exist** — the pitch happens once, at signup.

## Social graph — settled

No major platform will supply a friend graph (Meta's `user_friends` returns only
friends who already use your app; Snapchat refuses outright; Hinge had to abandon
this exact feature when Meta cut it off). **Vouch builds its own graph from the swiper
relationships**, with hashed contacts matching as an accelerant. See spec §9.

## Design direction

Simple **line art**. Clean, restrained, fluid. Profile, images and prompts first so a
swiper can review at a glance. **Gestures lead; buttons mirror them quietly.** All
swiper metadata rides in one reusable attribution chip. Reference: Hinge for
structure. Vouch uses its own palette — no borrowed colour scheme.

## Tech Stack

- **Mobile:** React Native + Expo (iOS & Android from a single codebase)
- **Backend/DB:** Supabase (PostgreSQL, Auth, Realtime, Storage) — Realtime carries
  the group chat
- **Payments (in-app):** RevenueCat · **(web, future):** Stripe
- **Push Notifications:** Expo Notifications + Supabase Edge Functions
- **Social Auth/Photos:** Instagram Graph API, Facebook Login SDK — auth and photo
  import only, **not** a friend-graph source
- **Claude API:** no longer part of the core loop as of v2

## Project Structure

```
vouch/
├── app/              # Expo Router screens
├── components/       # Reusable UI components
├── lib/              # Utilities, API clients, helpers
├── supabase/         # Migrations, edge functions, seed data
├── assets/           # Images, fonts
├── constants/        # Theme, config
└── docs/             # Specs — SPEC-v2.md is canonical
```

## Conventions

- TypeScript everywhere
- Functional components with hooks
- Expo Router for navigation (file-based routing)
- Supabase client via shared singleton in `lib/`
- All database changes via Supabase migrations in `supabase/migrations/`
- Environment variables in `.env` (never committed)
- **Version discipline:** new work in new files; don't overwrite prior *shipped* specs

## Status

Spec-only (revision 9). **No application code has been written yet.** **No open
questions remain** — the spec is declared sufficient for an MVP. Next: design mockups
(5 × 3 screens: profile, swipe cards, dashboard/HUD) for approval, then a UI-first
build.

# Vouch

A mobile dating app where **your trusted friends swipe with you and for you.**

You supply a pool of prompts and photos. Each friend you invite **pitches their own
version** of your profile; you pick the one that becomes your real profile, or reject
them all and build your own. Then your friends go out and swipe on your behalf —
alongside you. Matches come back to you, and only you, to review and chat.

> **Full product spec: [`docs/SPEC-v2.md`](docs/SPEC-v2.md)** (revision 2) — read it
> before any build work. This file is the short current-context summary.
>
> The v1 concept (friends author a profile, **AI consolidates** it, "roll the dice"
> regeneration) is **superseded**. It survives in git history at commit `06b8b89`.

## Core mechanics

- **One canonical profile.** Up to 3 swipers each submit a proposed profile; the user
  picks one or rejects all. Nothing circulates in multiple versions.
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

The paid pillar is **crew size**: 3 swipers free → **5 on premium** → tiered beyond.

| Tier | Swipers | Crew | Weekly Dates *(1/head)* | Kisses |
|---|---|---|---|---|
| Free, solo | 0 | 1 | 1 | daily cap |
| Free | up to 3 | up to 4 | up to 4 | daily cap |
| Premium | 5 | 6 | 6 | unlimited |
| Higher | more | more | **6 — flat** | unlimited |

Dates run at **1 per crew head/week** (so recruiting a swiper raises your signal
budget — the invite incentive) and **flatten at the premium crew size**; extras sell in
packs. Approved pillars **A–E**: re-pitch rounds, profile insights, swiper scorecards,
guest swipers, "see who Kissed you". Build order in spec §8.4 — crew size + E at
launch, re-pitch next. **Never premium:** the user editing their own profile, or
swipers suggesting edits. Both free forever.

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

Spec-only (revision 5). **No application code has been written yet.** §10.1–10.5 and
§10.4a are resolved. Three remain: v1 carry-over (§10.6), lifecycle + 18\+ enforcement
(§10.7), and crew supply / swiper-attention ceiling (§10.8).

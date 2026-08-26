---
title: Vouch — Product Spec v2
status: current
revision: 4
supersedes: CLAUDE.md @ 06b8b89 (v1, 2026-04-23)
updated: 2026-08-25
---

# Vouch — Product Spec v2

**The pivot:** v1 was "friends build your dating profile, AI consolidates it."
v2 keeps the friends, drops the AI, and moves the friends from *profile authoring*
into *acting on your behalf*.

> **You don't swipe alone. Your trusted friends swipe with you and for you.**

Matches come back to the user — and only the user — to review and chat.

## Revision history

**Revision 2 (2026-08-25, same day, pre-commit)** — Revision 1 was never committed or
built against; these changes are folded in place rather than forked to a v3.

| # | Change | Effect |
|---|---|---|
| 1 | Swipers each submit a **proposed profile**; user picks one or rejects all and builds their own | **One canonical profile.** Resolves R1 §8.1 |
| 2 | FMK renamed and de-premiumed → **Date / Kiss / Pass**, core feature | Resolves R1 §8.2 and §8.3 |
| 3 | Swipe screen controls specified (undo, pass, like, Date, message) | New §5.2 |
| 4 | **The user swipes too** — everyone tackles the deck together, with attribution labels | Resolves R1 §8.6 in part |
| 5 | Per-swiper trust settings; **all** swiper-authored messages route through review | Resolves R1 card 5 |
| 6 | Super like = **5/week premium**, allocatable to a swiper or self-used | Resolves R1 §8.5 |
| 7 | **Group chat** for user + swipers, with profile sharing | New §7 |
| 8 | Hinge structural steal — swipe on **a specific prompt or photo** | New §4.2 |
| 9 | Social graph resolved to **first-party swiper graph + contacts matching** | Resolves R1 §8.4 |

**Revision 3 (2026-08-25, same day, pre-commit)** — closes every open question from
revision 2 except symmetry, swiper-only accounts, v1 carry-over and lifecycle.

| # | Change | Effect |
|---|---|---|
| 10 | **Date is the super like** (the original "marry") — core feature, **scarce quantity** | Resolves R2 §10.2 |
| 11 | Premium pillar = **more swipers**: 3 base → 5 premium → tiered beyond. A swiping crew. | Resolves R2 §10.3 |
| 12 | **Post-match review is the default**; pre-match hold is opt-in per swiper | Resolves R2 §10.1 |
| 13 | **Three-layer review model** defined — ambient / optional gate / always-on match review | New §6 |
| 14 | **Outbound volume capped at the user level**, not per swiper | New §6.5 — protects the thesis |

**Revision 4 (2026-08-25, same day)** — closes the last structural unknowns.

| # | Change | Effect |
|---|---|---|
| 15 | **Swipers are optional.** A user can run the app solo; the crew is a core convenience, not a requirement | Resolves R2 §10.4 |
| 16 | **Dual identity** — separate user profile and swiper profile, with a mode toggle | Resolves R2 §10.5 |
| 17 | **Swiper blindness** — swipers never see likes or matches; the user shares explicitly | New §3.3 |
| 18 | **Dates scale with headcount** — 1 per head (user + swipers), making invites a growth lever | Revises §4.1 / §8 |
| 19 | **Kiss allocation dial** — per-swiper % caps on a shared daily pool; user uncapped | New §4.4 |
| 20 | Premium candidates proposed (not approved) | New §8.3 |

---

## 1. Roles

| Role | Does |
|---|---|
| **User** (the dater) | Optionally selects swipers and sends invites; supplies the prompt + photo material; **chooses the winning profile**; swipes; allocates the crew's budgets; reviews matches; **is the only one who chats with matches** |
| **Swiper** (trusted friend) | **Proposes a full profile** from the user's material; swipes on the user's behalf; drafts first messages; talks in the group chat |

**Base tier: up to 3 swipers per user.**

### 1.1 Swipers are optional
**A user does not need swipers.** Vouch works standalone — a solo user builds their
own profile and swipes their own deck like any dating app. The crew is the app's
**core feature and its convenience**, not its entry requirement.

This matters structurally: it means a match needs two engaged people, not four, and a
user whose friends go quiet still has a working app.

### 1.2 Dual identity — user profile and swiper profile
A person can be **both**. The two are separate profiles with a **mode toggle**:

- **User profile** — the dating profile that circulates, built via the pitch (§2)
- **Swiper profile** — who you are *as a swiper*: which friends you swipe for, your
  crews, your track record

Someone may be a **swiper only** and never date on Vouch. That is a first-class
account type and the app's cheapest growth funnel: swipers arrive for a friend, and
some convert into users.

## 2. Profile creation — the pitch

The user submits a **material pool**: prompts and photos.

Each assigned swiper independently **builds and submits their version of what they
think the user's profile should look like** — their selection, their arrangement,
their read on the person.

The user then either:
- **picks one submission** → that becomes **the** profile, or
- **rejects all of them** and builds their own.

**Exactly one profile goes into circulation.** There are never multiple versions of a
user in the wild. The competition happens *before* launch, not in the deck.

> This is the app's opening emotional beat: three friends each pitch you the version
> of yourself they think is most compelling, and you get to see how your friends
> actually see you.

Swipers may continue to **suggest edits** (a prompt rewrite, a swap, a new upload)
after launch; the user approves or rejects each one. **No AI.** All content is
authored by the user and their friends.

## 3. Who swipes — everyone, together

**Everyone swipes together.** The user is never locked out of their own deck — the
user and their swipers all work the same problem at once. This is not a mode or a
toggle; it is simply how swiping works. Friends are an amplifier, not a dependency,
and the app stays alive when friends are idle.

Every swipe carries an **attribution label** showing whether it came from a friend
(and which one) or from the user themselves.

### 3.3 Swiper blindness — results belong to the user
**Swipers never see likes or matches.** Who liked the user back, what matched, and
every conversation are visible to **the user alone**.

The line is precise:

| A swiper CAN see | A swiper CANNOT see |
|---|---|
| Their own swipe's fate in hold mode — *pending · approved · passed on* | Any incoming like |
| The deck they are swiping | Any match |
| Anything the user chooses to share | Any conversation |

The **activity log** is the user's private record of what the crew has been doing and
what came of it. The user may **share an entry into the group chat** — *"Alex, your
pick actually worked"* — but nothing crosses that line automatically.

> **Consequence to design for:** this deliberately cuts the swiper's natural reward
> loop. Sharing a win back to the crew is now the *only* way a swiper learns their
> judgement was good, so the share action must be one tap and genuinely celebratory.
> It carries the entire swiper retention story.

## 4. Swiping

### 4.1 Gestures — Date / Kiss / Pass

| Gesture | Name | Meaning | Scarcity |
|---|---|---|---|
| **Swipe up** | **Date** | The strong signal — the original "marry". **This IS the super like.** | **Scarce. Rationed weekly.** |
| **Swipe right** | **Kiss** | A like. Interested. | Everyday action |
| **Swipe left** | **Pass** | Not for me. | Free |

**Date / Kiss / Pass is a core feature — the gestures are never paywalled.** What is
rationed is the **number of Dates**, because a Date is only worth something to the
person receiving it if Dates are rare across the whole app.

Tags surface to the user at review time and are **never visible to the person being
swiped on**.

**Date allowance (see §8): one Date per head, per week.** The pool = the user plus
their swipers. Solo user = 1. User + 2 swipers = 3. User + 5 swipers = 6.

Dates land in **one shared weekly pool**, not private per-person allowances — the user
allocates it (§4.4) and can always spend from the whole pool themselves.

**Why it scales:** each additional swiper adds a Date, which makes **inviting a friend
a growth lever** — the user gets a stronger signal budget for recruiting, and the
invitee may convert into a Vouch user themselves. Per head this is exactly Hinge's
Rose rate (1/week/person), so scarcity per person is preserved even as the crew grows.

> ⚠️ Recommended guardrail (not yet approved): **flatten the Date grant above the
> premium crew size.** Tiers beyond premium sell more swipers but stop adding Dates,
> or Date value erodes for everyone receiving them. See §8.2.


### 4.2 Swipe the thing, not just the person *(Hinge structural steal)*

A swiper can attach their swipe to **a specific prompt or photo** rather than the
profile as a whole. This gives the user a reason to display at review ("Alex went
Date on her third prompt"), a natural hook for the opening message, and makes the
agreement multiplier specific.

### 4.3 Agreement multiplier

When more than one swiper acts the same way on the same target, the user sees a
**multiplier label** at review. Applies to **Date** and **Kiss** independently, and is
strongest when several friends land on the *same prompt or photo*.

### 4.4 Allocation — the dial

The user controls how much of the crew's budget each swiper may spend.

**Kisses — percentage caps on a shared daily pool.**
Each swiper gets a **percentage**, set on a **slideable dial**, of the user's daily
Kiss pool. That percentage is a **maximum allotment, not a reservation.**

- All Kisses draw from **one shared daily pool** — the crew does not get private
  budgets carved out of it
- A swiper set to 30% may spend at most 30% of the day's pool
- **The user is uncapped.** The user can always spend anything remaining in the pool,
  regardless of what has been allocated. **The user always has precedence.**
- Because caps are maxima rather than slices, **the allocations may total more than
  100%** — the crew races for a shared pool with individual ceilings
- Dial changes take effect at the next daily reset

**Dates** default to one per head and are reallocated the same way — the user may take
a swiper's Date, hand it to another, or spend the whole pool personally.

> ⚠️ Known consequence: with caps on a shared pool, an eager swiper can drain most of
> the day's Kisses early and starve the rest of the crew. Mitigations to design:
> show the **live remaining pool** to everyone, and consider an optional reserved
> floor per swiper in a later revision.

## 5. The swipe screen

### 5.1 Principles
Gestures do the primary work. Buttons are the **visible, accessible mirror** of the
gestures — de-emphasised, line-art, never the main event. Minimal chrome, maximum
fluidity.

### 5.2 Controls

- **Undo last action** — rewind the previous swipe
- **Pass** (mirrors swipe left)
- **Kiss / like** (mirrors swipe right)
- **Date** (mirrors swipe up)
- **Send message** — attach a first message to this swipe

## 6. Trust, review and messages

Vouch has **three layers** of user oversight, at three different costs. Only one of
them is on by default.

| Layer | When | Default | Cost to the user |
|---|---|---|---|
| **Ambient visibility** (§6.3) | Continuously | **On** | None — read if you feel like it |
| **Pre-match hold** (§6.4) | Before a like goes out | **Off**, per swiper | Latency + effort |
| **Match review** (§6.6) | After a mutual match | **On, always** | Low, and every item is a real outcome |

### 6.1 Per-swiper trust settings
Trust is configured **per swiper**, not globally. A friend of fifteen years and a
brand-new swiper can operate on different leashes.

### 6.2 Messages always route through review
**Every swiper-authored message goes through the user.** A swiper drafts; the **user**
edits, approves and sends. No message ever reaches another person unseen, so the
message a recipient gets is genuinely from the user. This is not configurable.

Optionally the user may *choose* to keep the attribution — *"Alex insisted I message
you"* — as an opener, but that is now a creative choice, not a disclosure obligation.

### 6.3 Layer 1 — ambient visibility *(default on)*
Swiper activity streams into the **group chat** (§7) as a light live feed: who your
crew is Kissing and Dating. The user scrolls it whenever they like, reacts *"not my
type at all"*, and the swiper course-corrects.

**This is the primary steering mechanism.** Course correction happens through
conversation rather than through an approval queue — no gate, no latency, no backlog.

Note the boundary: this feed shows the crew's **own outbound swipes**, which are their
own work. It never shows **incoming** likes or matches — those are user-only (§3.3).

### 6.4 Layer 2 — pre-match hold *(default OFF, per swiper)*
When enabled for a given swiper, that swiper's **positive** swipes do not enter the
matching pool immediately. They land in a holding queue visible only to the user.

- **Only Kisses and Dates are held. Passes are never held** — holding passes would
  force the user to re-swipe the entire deck, which is the exact thing the app exists
  to avoid.
- The held card shows the target profile, **who** swiped, the **tag**, **what** they
  swiped on (§4.2), and the swiper's drafted opener if any.
- The user can **Approve** (goes live), **Dump** (never goes out), or ignore.
- **Auto-release timer, default 24h → send.** If the user does not act, the like goes
  live. The user is nudged once before it releases. Configurable per swiper
  (12h / 24h / 72h / never auto-release).
- The swiper sees status on their side: *pending · approved · passed on*.

**Rationale for releasing rather than expiring:** a hold that silently discards a
friend's work punishes the swiper for the user being busy, which is fatal to swiper
retention. Hold mode is calibration scaffolding for a new swiper — once trust is
established the user turns it off.

### 6.5 Outbound volume is capped at the USER level
**A user's daily outbound Kiss and Date limits are fixed regardless of crew size.**
Buying more swipers buys **more perspectives, not more volume**.

Without this rule, a top-tier user with eight swipers emits eight times the outbound
likes of a free user — which makes Vouch a spam engine wearing a friendship costume
and destroys the curation thesis the whole product rests on. With it, a larger crew
competes to fill the same cap with better picks, and the agreement multiplier gains
resolution: a ×6 agreement out of eight swipers is a far stronger signal than ×3
out of three.

**Premium buys resolution. It never buys volume.**

### 6.6 Layer 3 — match review *(default ON — the main event)*
See §6.7. This is the review the user actually feels, and it is never disabled.

### 6.7 The match review flow — "Your friends' picks"
When a mutual match occurs, **no conversation starts until the user acts.** The match
lands in a surface named for the payoff, not the chore.

Each card carries:
- the matched person's profile
- the **attribution chip** — which swiper (or the user) made the swipe
- the **tag** — Date or Kiss
- the **agreement multiplier**, if more than one crew member swiped them
- **what** they swiped on — the specific prompt or photo (§4.2)
- the swiper's **drafted opener**, if written

The user then:
1. **Send** — accept or edit the drafted opener and send. The chat opens. **Only the
   user ever chats.**
2. **Hold** — leave it in the queue.
3. **Dump** — discard. Nothing is sent; the other side simply sees an unanswered
   match, exactly as on any dating app.

If the **other person messages first**, the conversation opens normally — but the
user still sees the full attribution context on the thread, so they know which friend
found this person and why.


## 7. Group chat

A shared room for the **user and all their swipers**.

- Share a **profile card into the chat** with a message — *"hey check her out"*
- Discuss swipes, argue about types, coordinate
- Doubles as the app's retention engine: it gives swipers a reason to open the app
  when it isn't their friend's love life at stake

**Likes, matches and conversations never enter this room automatically** (§3.3) — they
are the user's alone. The user may **explicitly share** an entry from their activity
log into the chat: *"Alex, your pick actually worked."* That share is a one-tap,
celebratory action, and it is the **only** channel through which a swiper learns their
judgement paid off — so it carries the crew's whole reward loop.

## 8. Premium — the swiping crew

The paid pillar is **crew size**. Users buy a swiping workforce.

### 8.1 The tiers

| Tier | Swipers | Crew size | Weekly Dates *(1 per head)* | Kisses |
|---|---|---|---|---|
| **Free, solo** | 0 | 1 | **1** | Daily cap |
| **Free** | up to 3 | up to 4 | **up to 4** | Daily cap |
| **Premium** | **5** | 6 | **6** | Unlimited |
| **Higher tiers** | more (tiered) | more | see §8.2 | Unlimited |

**Dates scale with headcount** — one per person in the crew, per week (§4.1). This is
deliberate: recruiting a swiper *increases the user's signal budget*, which makes the
invite a growth lever rather than a favour to ask. Per head it is exactly Hinge's Rose
rate, so individual scarcity is preserved as the crew grows.

**Kisses** are capped **per user, never per swiper** (§6.5) and distributed by the
allocation dial (§4.4). Premium buys resolution, never volume.

### 8.2 Recommended guardrail — flatten Dates above premium *(not yet approved)*

Category precedent: Hinge grants **1 free Rose per week to every user regardless of
tier** and sells extras in packs, monetising *unlimited ordinary likes* rather than
the scarce signal — because a Rose is worth something only while Roses are rare.

Vouch's headcount scaling is defensible up to premium (6 people, 6 Dates). Above that
it risks eroding what a Date means to everyone receiving one: a whale with a crew of
twelve sends twelve Dates a week against a solo user's one.

**Recommendation:** let Dates scale with headcount **up to the premium crew size**,
then flatten. Tiers above premium sell more swipers, more resolution and unlimited
Kisses — but additional Dates come from **packs**, not from the weekly grant.

**Allocation.** The user assigns Dates across the crew or spends the pool personally;
the user is never capped (§4.4).

**Other premium surface:** vouching / social proof (§9) — though see §9 on keeping it
free at launch while the graph is sparse.



### 8.3 Candidate premium pillars *(proposed — not approved)*

Ranked by fit with the curation thesis. All four are things only Vouch can sell,
because they all derive from the crew.

**A. Re-pitch rounds — strongest.** The pitch (§2) is the app's best emotional beat and
currently happens exactly once. Free users get one pitch round at signup; premium can
**re-run the pitch** — send the crew back to rebuild the profile from scratch,
periodically. Monetises the app's most distinctive moment, gives lapsed users a reason
to return, and refreshes stale profiles, which helps match rates as a side effect.

**B. Profile insights.** Because swipes attach to a **specific prompt or photo**
(§4.2), Vouch knows something no other dating app does: *which piece of a profile is
actually working*. "Your third prompt drives 60% of your Kisses; photo 4 drives none."
Feeds directly back into the crew's edit-suggestion loop. Unique data, genuinely
useful, on-thesis.

**C. Swiper scorecards.** Track each swiper's hit rate — whose picks become matches,
and whose become actual conversations. Answers "which of my friends has the best
taste," gamifies the crew, and makes the allocation dial (§4.4) a *decision* rather
than a guess: give more Kiss budget to the friend with the better record. Visible to
the user; whether swipers see their own score is an open call.

**D. Guest swipers.** Invite someone to swipe for a **single session** without
occupying a permanent crew slot — a sibling visiting, a table at a bar. Fits the
everyone-swipes-together spirit, and every guest is an unconverted user meeting the
product at its most fun. Doubles as a growth loop.

**E. "See who Kissed you" — the pragmatic bet.** Not original, but seeing your incoming
likes before matching is the highest-converting paid feature in the category, and it
sits naturally inside swiper blindness (§3.3) since likes are already user-only. Least
interesting, most likely to pay for the servers.

**Unifying story:** every tier is *a bigger, better-equipped crew.* Premium is not a
feature list — it is more people helping you, with better tools.

## 9. Social proof — resolved

**Finding (researched 2026-08-25): no widely used social platform will supply a
friend graph to a third-party app.**

- **Meta** — `user_friends` returns *only friends who also use your app*, never the
  full list; no permission grants mutual-friend data
- **Snapchat** — has stated it will never expose the full friends list to developers
- **X** — pay-per-read from 2026; follower data is not a friend graph
- **LinkedIn** — gated to approved partners, B2B use cases only
- **Precedent** — Hinge's original identity *was* Facebook friends-of-friends; Meta cut
  the data off and Hinge abandoned the feature

**Therefore the graph must be first-party:**

1. **The swiper graph** — every user names 1–3 real friends to invite. That is a
   declared, high-trust social graph nobody can revoke. If Alex swipes for both Brian
   and Sam, Brian and Sam are two hops apart.
2. **Contacts matching** — hashed phone-number matching against registered users, with
   explicit consent, as an accelerant.
3. **Meta login** — still worth having for auth and photo import; it will surface
   Vouch-using Facebook friends as the network grows.

Because the graph is sparse at launch, social proof should be **free** early (a trust
signal, not a paywall) and can gate *who* the connection is behind premium later.

## 10. Open questions

**Resolved in revision 3:** ~~10.1 second-layer default~~ (post-match, §6.6) ·
~~10.2 Date quantity~~ (scarce, §4.1) · ~~10.3 premium depth~~ (crew size, §8).
**Resolved in revision 4:** ~~10.4 symmetry~~ (swipers optional, §1.1) ·
~~10.5 swiper-only accounts~~ (dual identity + mode toggle, §1.2).

**10.4a Context switching *(follow-on)*.** One person may swipe for several friends.
How they switch between crews — and how the app keeps those decks from blurring
together — is unspecified.

**10.6 v1 carry-over.** Confirm these survive: user-supplied basics (name, age, sex,
orientation, seeking preference, smoking/alcohol/drugs), the "seeking profile" of
desired traits, the 10-photo pool, voucher search and referral notifications.

**10.7 Lifecycle and safety.** What happens to in-flight and held swipes when a swiper
is removed? Blocking, reporting, abuse paths, and **18+ age enforcement** are
unspecified — the last matters more than usual because friends are acting inside
someone else's dating life.

**10.8 Crew supply *(new)*.** Premium sells more swipers, but most people cannot
recruit eight friends willing to do unpaid work on their love life. Above ~5 the tier
may be unsellable for supply reasons rather than price. Needs validation before the
higher tiers are built.


## 11. Design direction

- **Line art.** Simple, clean, restrained.
- **Profile, images and prompts first** — reviewable **at a glance**.
- **Fewer buttons**, so the app feels lively and responsive. Gestures lead; buttons
  mirror them quietly for accessibility.
- **Fluidity** is a first-class requirement, not polish.
- **Reference:** Hinge for structure. A Tinder-style dark/neon concept board was
  reviewed 2026-08-25 as a *layout* reference only — **its colour scheme and visual
  style are explicitly not adopted.** Vouch uses its own palette.
- **One attribution chip.** All swiper metadata — avatar, count, Date/Kiss tag, who
  swiped — rides in a single reusable component in a consistent position across the
  match card, review queue, group chat and match header.

## 12. Stack

- **Mobile:** React Native + Expo (iOS & Android from one codebase)
- **Backend/DB:** Supabase (PostgreSQL, Auth, Realtime, Storage) — Realtime also
  carries the group chat
- **Payments (in-app):** RevenueCat · **(web, future):** Stripe
- **Push:** Expo Notifications + Supabase Edge Functions
- **Social auth/photos:** Instagram Graph API, Facebook Login SDK — for auth and photo
  import only; **not** as a friend-graph source (§9)
- **Claude API:** no longer in the core loop

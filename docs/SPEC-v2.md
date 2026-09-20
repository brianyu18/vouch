---
title: Vouch — Product Spec v2
status: current
revision: 9
supersedes: CLAUDE.md @ 06b8b89 (v1, 2026-04-23)
updated: 2026-09-19
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
| 17 | **Swiper visibility rule** — results are user-only, refined in R5 to expose a swiper's own hits | New §3.3 |
| 18 | **Dates scale with headcount** — 1 per head (user + swipers), making invites a growth lever | Revises §4.1 / §8 |
| 19 | **Kiss allocation dial** — per-swiper % caps on a shared daily pool; user uncapped | New §4.4 |
| 20 | Premium candidates proposed (not approved) | New §8.3 |

**Revision 5 (2026-08-25, same day)** — visibility, allocation and premium settled.

| # | Change | Effect |
|---|---|---|
| 21 | **Swipers see the outcome of their own swipes** — a match they made is reported back | Revises §3.3 |
| 22 | **Date grant flattens at the premium crew size**; extras sold in packs | §8.2 approved |
| 23 | **Allocation is a pie, not caps** — slices are guaranteed and total ≤ 100% | Corrects §4.4 |
| 24 | **Depleting allotment bar** for user and swipers — **free/core, not premium** | New §4.5 |
| 25 | **Premium pillars A–E approved**, with re-pitch clarified and a build order | §8.3 |
| 26 | **Swiper crew switcher** designed — the friends menu | Resolves §10.4a |

**Revision 6 (2026-08-25, same day)** — pitch mechanics and the v1 prune.

| # | Change | Effect |
|---|---|---|
| 27 | **Material pool capped at 10 items** (photos + prompts combined); each pitch selects a subset | Revises §2 |
| 28 | **Re-pitch: either side can start it**, others get an **expiring action window** | New §2.2 |
| 29 | Re-pitch cadence — **once per 30 days**, extra rounds purchasable | New §2.2 |
| 30 | **Guest swipers: 1/month on premium**, more purchasable | Revises §8.3 D |
| 31 | **Seeking profile CUT** — becomes a selectable prompt instead | Revises §13 |
| 32 | **v1 audit** — every v1 feature kept, folded or pruned | New §13 |

**Revision 7 (2026-08-27)** — re-pitch cut, the call added, §10.7 and §10.8 closed.

| # | Change | Effect |
|---|---|---|
| 33 | **Re-pitch CUT entirely** — the pitch happens once, at signup. Reverses #28/#29 | §2.3 removed |
| 34 | **The 90-second call** — premium, request-based, charged only if accepted | New §8.3 A |
| 35 | **Swiper accountability** solved with zero added user friction | Resolves §10.7 |
| 36 | **18+ enforcement** via app-store age signals, not ID checks — applied to swipers too | Resolves §10.7 |
| 37 | **Crew capped at 5; surge sold as guest passes** — no unfillable tiers | Resolves §10.8 |

**Revision 8 (2026-09-19)** — one contradiction closed.

| # | Change | Effect |
|---|---|---|
| 38 | **There is no tier above premium.** 5 permanent swipers is the ceiling for every user; extra capacity is **rented** via guest passes, never bought as headcount | Fixes §8.1 / §8.2 / §4.1 against §15.1 |

**Revision 9 (2026-09-19)** — the call is named and rationed; spec declared build-ready.

| # | Change | Effect |
|---|---|---|
| 39 | The call is **Ring** — "ring your crush" | Resolves §10.10 |
| 40 | **Ring is core, not premium-only:** free 1/month, **premium 3/month**, more purchasable | Resolves §10.9; revises §8.3 A |
| 41 | **Spec declared sufficient for MVP.** Next: design mockups → approval → build | — |

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

### 1.3 Swiping for several friends — the crew switcher

A swiper may serve **several friends at once**. The organising surface is a **friends
menu**: a list of everyone you swipe for.

**The friends menu.** One row per friend, each showing:
- their avatar and name
- **their depleting allotment bar** (§4.5) — how much of your slice is left today
- **what needs you** — items held for approval, edit suggestions awaiting a reply
- unread group-chat count

Tapping a row loads **that friend's deck**, filtered by **that friend's** preferences —
age range, distance, orientation, seeking criteria. The decks are genuinely different
populations, which does most of the disambiguation work on its own.

**The failure mode to design against is swiping for the wrong friend.** It is the one
error that is both easy to make and impossible to explain away, so the current context
must be unmissable:

- The friend's **avatar and name stay pinned in the header** for the entire session —
  never a screen you can scroll away from
- Each friend carries a **consistent accent** across their deck, chip and bar, so the
  context is legible peripherally, not just by reading
- **Switching crews is explicit** — via the friends menu, never a swipe or a gesture
  that could fire by accident
- **No merged deck.** Combining several friends' decks into one queue is tempting for
  efficiency and would be a mistake: it puts the burden of remembering who each card
  is for onto the swiper, on every single card.

**Notifications group by friend**, so a swiper with four crews gets four legible
threads rather than one undifferentiated stream.

> ⚠️ Open: whether to cap how many crews one person can join. A swiper in ten crews is
> almost certainly giving nobody real attention, and the product's whole claim is that
> these are *considered* judgements from someone who knows you. See §10.8.

## 2. Profile creation — the pitch

### 2.1 The material pool — capped at 10

The user submits a **material pool** of **at most 10 items total — photos and prompts
combined.** Not 10 of each; ten, all in.

The cap exists to protect the swiper. A pitch is real work — reading someone, choosing,
arranging, writing — and handing a friend forty items to sift turns a fun favour into a
chore, which is the fastest way to lose a crew before they have swiped once.

**Each pitch selects and arranges a *subset* of the pool.** A swiper does not use all
ten; they choose the six or seven that, to them, make the best case. That selection is
precisely what makes competing pitches differ and what makes the choice meaningful — if
every pitch contained identical material, only ordering would vary and the competition
would be hollow.

The user can **update and edit the pool at any time**, before or after launch.

### 2.2 The pitch

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

**The pitch happens once, at signup.** There is no re-run. After that the profile
evolves through ordinary editing: swipers **suggest edits** (a prompt rewrite, a swap,
a new upload) and the user approves or rejects each one, and the user edits freely at
any time. Both are **free forever**. **No AI** — all content is authored by the user
and their friends.

## 3. Who swipes — everyone, together

**Everyone swipes together.** The user is never locked out of their own deck — the
user and their swipers all work the same problem at once. This is not a mode or a
toggle; it is simply how swiping works. Friends are an amplifier, not a dependency,
and the app stays alive when friends are idle.

Every swipe carries an **attribution label** showing whether it came from a friend
(and which one) or from the user themselves.

### 3.3 What a swiper can see — own results only
**The rule: a swiper sees the results of their own work, and nothing else.**

Results of the user's dating life at large — who liked them, who they matched with
independently, every conversation — belong to **the user alone**.

| A swiper CAN see | A swiper CANNOT see |
|---|---|
| **That a profile they swiped became a match** | Any incoming like nobody in the crew swiped |
| Their own swipe's fate in hold mode — *pending · approved · passed on* | Matches the user made on their own |
| The deck they are swiping | **Any conversation, ever** |
| Anything the user chooses to share | Anything that happens after the match |

**Why the line moved here.** Full blindness protected privacy but severed the swiper's
only feedback signal — a friend who never learns their pick worked has no evidence
their taste is good, and no reason to keep swiping. Reporting back **their own hits**
restores the loop while revealing nothing the swiper did not already act on: they
chose that profile, so learning it matched exposes no person they had not already seen.

**User override.** The user can mute match-reporting globally or per swiper. Privacy is
the default posture; the reward loop is the default setting.

The **activity log** remains the user's private record. The user may still **share an
entry into the group chat** — *"Alex, your pick actually worked"* — which stays the
celebratory, high-signal version of the same news.

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

> **Approved ceiling:** the grant flattens at the premium crew size (6 heads / 6
> Dates) — which is also where permanent crew stops. There is nothing above it to
> scale into. Extra Dates come from **packs**; extra swiping capacity comes from
> **guest passes**. See §8.2 and §15.1.


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

**Kisses — a pie, sliced.** The user's daily Kiss pool is 100%. On a **slideable
dial**, the user cuts it into slices, one per swiper.

- **Allocations can never total more than 100%.** The dial enforces it — dragging one
  slice wider compresses the others rather than overdrawing the pool.
- A slice is a **guaranteed reservation**, not a race. A swiper set to 30% has 30% of
  the day, and no other swiper can consume it.
- **Whatever the user leaves unassigned is theirs**, and **the user has precedence
  over the whole pie**: they may also spend from any slice a swiper has not used.
- Slices reset daily; dial changes take effect at the next reset.

Reservations rather than ceilings mean **no swiper can starve the crew** by burning
through the pool early — the failure mode a shared-pool model would have had.

**Dates** run at one per head (§4.1) and are reallocated on the same dial — the user
may take a swiper's Date, hand it to another, or spend the pool personally.

### 4.5 The depleting bar — free, never premium

**Everyone in the crew — the user and every swiper — sees a live bar showing their
remaining allotment**, draining as swipes are spent. The user additionally sees the
whole pie: every slice and how much of each is left.

**This is core, not a premium feature.** Charging for it would mean charging a user to
see how much of their own budget remains, which reads as hostile, and it would leave
swipers spending blind — burning an allotment they cannot see is the fastest way to
make a friend feel their effort was wasted. Premium sells **a bigger pie**, never
*visibility into* the pie.

Design note: the bar is also the app's most natural fluid element — it responds to
every swipe, which is exactly the "lively and responsive" quality the design direction
calls for, and it does that work without adding a single button.

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

The paid pillar is **crew size**. Users buy a swiping workforce — up to a point, and
then they rent one.

### 8.1 The tiers

| Tier | Permanent swipers | Crew size | Weekly Dates *(1 per head)* | Kisses |
|---|---|---|---|---|
| **Free, solo** | 0 | 1 | **1** | Daily cap |
| **Free** | up to 3 | up to 4 | **up to 4** | Daily cap |
| **Premium** | **5 — the ceiling** | 6 | **6** | Unlimited |

**There is no tier above premium.** Five permanent swipers is the hard cap for every
user, at every price. Additional swiping capacity is **rented, not bought**: a user who
wants more hands pays to invite a **temporary swiper** for a single session — the guest
pass (§8.3 D). Headcount is capped; surge is consumable.

This is the §15.1 decision applied to pricing. Selling a tenth permanent slot would sell
a favour the buyer cannot collect on; selling a guest pass sells capacity they can use
tonight.

**Dates scale with headcount** — one per person in the crew, per week (§4.1). This is
deliberate: recruiting a swiper *increases the user's signal budget*, which makes the
invite a growth lever rather than a favour to ask. Per head it is exactly Hinge's Rose
rate, so individual scarcity is preserved as the crew grows. Because headcount stops at
6, so does the grant.

**Kisses** are capped **per user, never per swiper** (§6.5) and distributed by the
allocation dial (§4.4). Premium buys resolution, never volume.

### 8.2 Date grant flattens above the premium crew — APPROVED

Category precedent: Hinge grants **1 free Rose per week to every user regardless of
tier** and sells extras in packs, monetising *unlimited ordinary likes* rather than
the scarce signal — because a Rose is worth something only while Roses are rare.

Vouch's headcount scaling is defensible up to premium (6 people, 6 Dates). Letting it
run further would erode what a Date means to everyone receiving one: a whale with a
crew of twelve would send twelve Dates a week against a solo user's one.

**Decision (approved):** Dates scale with headcount **up to the premium crew size — 6
heads, 6 Dates per week — and stop there**, which is also where permanent crew stops
(§8.1). Additional Dates come from **packs**, never from the weekly grant, and a guest
swiper spends from the existing pool rather than adding to it. The invite incentive
stays fully intact across the free tier and into premium, which is exactly where
recruitment matters.

**Allocation.** The user assigns Dates across the crew or spends the pool personally;
the user is never capped (§4.4).

**Other premium surface:** vouching / social proof (§9) — though see §9 on keeping it
free at launch while the graph is sparse.



### 8.3 Premium pillars — APPROVED (A–E)

All five approved 2026-08-25. Ranked by fit with the curation thesis — every one is
something only Vouch can sell, because they all derive from the crew.

> **What is NOT premium, and never will be:** the user editing their own profile, and
> swipers suggesting edits to it. Both are free, always, for everyone. See the
> clarification under A.

**A. Ring — the 90-second call. "Ring your crush." — strongest.**

Every user gets a **Ring request** they may send to **a match of their choosing**. The
match accepts or declines — **the receiving user must accept** — and **the grant is
only consumed if the call is accepted.** A declined or ignored request costs nothing.

| Tier | Rings per month |
|---|---|
| Free | **1** |
| Premium | **3** |
| Either | more **purchasable** in packs |

Ring is **core with a premium multiplier**, the same shape as Date: the feature is never
paywalled, the *count* is scarce, and premium triples it.

The point is an **elevator pitch**: ninety seconds is long enough to hear whether
there is a spark and far too short to be a date. It gives a user who has been trading
polite messages for a week a reason to actually reach out, which is the single hardest
transition in online dating.

**Mechanics**

- **Audio, not video.** Video pre-meeting is high-friction and higher-risk; ninety
  seconds of someone's actual voice is a strong signal at a fraction of the exposure
- **Hard 90-second timer.** At zero, both sides get a mutual *"keep talking?"* prompt —
  if both accept, the call continues unmetered. The scarcity creates the spark; it
  should not then punish a spark that caught
- **In-app only.** Phone numbers are never exposed to either side
- The recipient may **accept, decline silently, propose another time, or block**.
  A request **expires after 48 hours** so it never lingers
- **One outstanding request per match**, and no repeat request after a decline
- Extra call requests **purchasable** in packs

**Only the user can initiate a call.** A swiper never can — a call is a conversation,
and swipers do not touch conversations (§3.3). This is the same line that governs
messages, applied to voice.

Monthly rather than weekly is deliberate: weekly would make Ring a habit; monthly
keeps it an event.

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

**D. Guest swipers — 1 per month on premium, more purchasable.** Invite someone to
swipe for a **single session** without occupying a permanent crew slot — a sibling
visiting, a table at a bar. Fits the everyone-swipes-together spirit, and every guest
is an unconverted user meeting the product at its most fun. Doubles as a growth loop.

Rationed for the same reason as calls: a guest sees the user's deck and spends
from the user's pie, so unlimited guests would be an unlimited hole in both privacy and
budget. Extra guest passes sell in packs.

**E. "See who Kissed you" — the pragmatic bet.** Not original, but seeing your incoming
likes before matching is the highest-converting paid feature in the category, and it
sits naturally inside swiper blindness (§3.3) since likes are already user-only. Least
interesting, most likely to pay for the servers.

### 8.4 Build order

All five are approved, but shipping five paid features at launch splits attention and
muddies the pitch. Recommended sequencing:

| Wave | Ship | Why |
|---|---|---|
| **Launch** | Crew size · **E** (see who Kissed you) | Crew size is the pillar; E is the category's proven revenue engine and needs no new data |
| **Launch + 1** | **A** (Ring) | The distinctive one, and the highest-risk to build — real-time audio, abuse handling, scheduling. Worth doing properly rather than early |
| **Wave 2** | **B** (profile insights) · **C** (swiper scorecards) | Both are nearly free once swipe-target data (§4.2) has accumulated. They need *history* to say anything, so they cannot ship on day one anyway |
| **Wave 3** | **D** (guest swipers) | Delightful and a growth loop, but it touches invites, permissions and crew slots — the most plumbing per unit of revenue |

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

**Resolved in revision 5:** ~~10.4a context switching~~ (crew switcher + friends menu,
§1.3).

**Resolved in revision 6:** ~~10.6 v1 carry-over~~ — full audit in §13. Seeking profile
cut, referral notifications pruned, everything else kept or folded.

**Resolved in revision 7:** ~~10.7 lifecycle and safety~~ (§14) ·
~~10.8 crew supply~~ (§15).

**Resolved in revision 9:** ~~10.9 cadence~~ (free 1/month, premium 3/month, §8.3 A) ·
~~10.10 naming~~ (**Ring**).

**No open questions remain. The spec is sufficient to build an MVP against.**

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

## 13. v1 audit — kept, folded, pruned

Every line of the v1 spec (`06b8b89`), resolved against v2. This closes §10.6.

### 13.1 Kept

| v1 feature | Status in v2 |
|---|---|
| Users ask friends to build their profile | **Core.** Became the pitch (§2.2) — friends now build *and* swipe |
| Vouchers attach socials (Instagram/Facebook) to prove they're real | **Kept as swiper verification.** OAuth identity only — unaffected by the friend-graph finding in §9 |
| Link IG/FB to pull photos; upload a pool for friends to choose from | **Kept**, now the 10-item material pool (§2.1) |
| Users provide their own basic bio — name, age, sex, orientation, seeking preference, smoking, alcohol, drugs | **Kept unchanged.** The factual scaffolding, and precisely the part friends should *not* be writing |
| "Friends paint the picture — the rest comes from vouchers" | **Kept as the product's philosophy.** Truer in v2 than it was in v1 |
| Swipe-based matching with filters | **Kept**, extended by Date/Kiss/Pass (§4.1) |

### 13.2 Folded into something else

| v1 feature | Folded into |
|---|---|
| Users can search vouchers to find friends already on the app | **The swiper invite flow + contacts matching (§9).** Two parallel discovery systems would be redundant; there is one now |
| Microtransactions — extra profile rolls beyond the initial 3 | **Date packs, guest passes and call packs.** Same "some free, buy more" shape, spread across three human features instead of one AI reroll |
| Free tier: limited daily swipes | **The Kiss pool + allocation pie (§4.4)** |
| Premium: unlimited swipes | **Kept**, but now the *second* thing premium sells; crew size is the pillar (§8.1) |

### 13.3 Pruned — dead in v2

| v1 feature | Why it is gone |
|---|---|
| **AI (Claude) consolidates voucher submissions into one cohesive profile** | Cut at the pivot. It undercut the entire human-vouching premise — friends "vouched" while a model wrote the words |
| **"Roll the dice" to regenerate, 3 free rolls, pay for more** | Died with the AI, and **has no successor**. A human re-pitch was specced in revision 6 and cut in revision 7: past the first round at signup it is churn, not value. The pitch happens **once**, and the profile evolves after that through ordinary edits |
| **Users create a "seeking profile" with traits they want in a match** | **Cut.** Modern dating apps have largely abandoned structured "what I want" forms — they read as a wishlist, they date badly, and nobody fills them in honestly. Replaced by a **selectable prompt** (§13.4) |
| **When a voucher's referred user joins, the other person they vouched for gets notified (if preferences align)** | **Pruned as an automatic notification.** It pushes an unrequested introduction between two people who do not know each other, on the strength of a shared friend — a privacy problem, and it clashes with swiper blindness (§3.3) and with the user's control over their own deck. **The underlying graph fact survives** as passive social proof (§9): "you both know Alex" shown on the profile. Intrusive push becomes quiet trust signal |
| **"Possible premium voucher referral features"** | Vague in v1, and the concrete version of it is now pruned above. Premium is crew size (§8.1) |

### 13.4 The seeking profile becomes a prompt

Instead of a separate structured form, **"what I'm looking for" is simply one of the
selectable prompts** in the pool. A user who wants to say it can pick that prompt; a
user who does not, does not. It occupies one of the 10 material slots like anything
else, which is the right price for it.

**No brief is needed to replace it.** Swipers are people who already know the user —
that is the premise of the product, not an assumption to be shored up. A friend who
needs a written specification of your taste is not someone who should be swiping for
you. Anything situational gets said in the group chat like it would in life.

## 14. Safety, accountability and lifecycle

### 14.1 Swiper accountability — invisible by design

**The concern:** the person being swiped never sees the swiper, only the user. So a
report, a block or a ban lands on the **user's** account for something a friend did.

**First, the problem is smaller than it looks.** Every message already routes through
the user for approval (§6.2), so the user has *seen and sent* every word that reaches
a stranger. Messages are genuinely the user's responsibility. A swipe on its own
cannot harass anyone. The independent surface a swiper actually has is narrow.

**The real exploit is different, and it matters:** a banned account could simply become
a swiper for a friend and keep browsing the app through them.

**The solution adds zero taps for a normal user**, because the data model already
carries it:

| Requirement | Cost |
|---|---|
| Every swipe, edit and message draft is attributed to its actor internally | **Free** — already required to render the attribution chip (§4.2) |
| Moderation can resolve any report to a specific action, and therefore a specific actor | **Free** — a query, not a feature |
| Swipers are real accounts with their own identity | **Free** — dual identity already exists (§1.2) |
| **A banned account cannot hold the swiper role.** Bans propagate across both identities | Small, one-time |
| The user can see their own crew's action log | **Free** — that is the activity log (§3.3) |

**Nothing above is user-facing.** Accountability is an internal attribution property,
not a workflow. The only surface a user ever sees is a **notice when their own crew is
implicated** — *"swipes from Alex have been reported twice"* — and that is useful
information, not friction.

**Liability model:** messages are **shared** (the swiper drafted, the user approved and
sent). Swipes are **the swiper's alone**. Moderation weights accordingly rather than
banning a user for a friend's judgement.

### 14.2 18+ enforcement — app-store signals, not ID checks

**Researched 2026-08-27.** The 2025–26 age-verification wave puts verification at the
**app store**, not inside the app. Utah, Texas and Louisiana passed App Store
Accountability Acts in 2025 (California following); Texas took effect 1 Jan 2026 and a
Fifth Circuit ruling in May 2026 let it proceed on an interim basis while challenges
continue. The mechanism: **the store verifies age and exposes it to developers through
an age-signal API**, and developers must label the app by age category and consume that
signal.

**So document/ID verification is not the required mechanism, and should not be the
signup flow.** An ID scan at registration would gut the funnel to solve a problem the
law is solving elsewhere.

| Layer | Use | Why |
|---|---|---|
| **App-store age signal** | **Primary** | Legally aligned, zero friction, and the mechanism the statutes actually name |
| **Self-declared date of birth** | **Baseline** | Industry standard; the app's own defensible record |
| **Document / ID verification** | **Escalation only** | For appeals and age-related reports — never at signup |
| **Instagram / Facebook login** | **Not an age signal** | Those platforms admit 13+, so the login proves *identity*, not adulthood. Keep it for auth and photo import (§12) only |

**The Vouch-specific requirement, which no off-the-shelf compliance covers: run the
same gate on swipers.** A sixteen-year-old swiping adult dating profiles on behalf of
an older sibling is the scenario that ends an app, and nothing in the standard
dating-app playbook contemplates a non-dating participant inside the product. **Every
swiper passes the same 18+ check as every user, before they are allowed a deck.**

### 14.3 Lifecycle — removing a swiper

When the user removes a swiper, immediately:

- **Deck access is revoked.** No further swipes are possible
- **Held swipes are dumped, not auto-released.** The 24h auto-send rule (§6.4) does not
  apply to someone the user has just removed — the removal *is* the decision
- **Pending edit suggestions are withdrawn**
- **Group chat access ends.** Prior messages remain in history
- **Existing attribution stands.** Matches that swiper made keep their chip; that is a
  historical fact, and rewriting it would corrupt the activity log

The removed swiper is told they were removed, without a reason. Their own swiper
profile and any other crews they belong to are untouched.

## 15. Crew supply and the attention ceiling

Two halves of the same problem, with one answer.

### 15.1 Supply — cap the crew at 5, sell surge as guest passes

**The problem with selling tiers above 5 permanent swipers:** most people cannot
recruit eight friends willing to do unpaid work on their love life. Users would not
decline to buy the tier — they would buy it and then fail to fill it, which is worse
than not selling it. An empty crew slot is a visible reminder of a favour nobody
granted.

**The answer:** **permanent crew caps at 5** (premium), for everyone, at every price —
**there is no higher tier** (§8.1). Everything above that is sold as **guest passes**
(§8.3 D): pay to invite a *temporary* swiper for a single session, with no permanent
commitment on either side.

This is strictly better in three ways: there is **no unfillable tier**; the "swiping
workforce" fantasy is still delivered, just as surge capacity rather than standing
headcount; and a consumable repeat purchase monetises better than a one-time tier
upgrade. It also gives a friend who cannot commit to a crew a way to help anyway.

### 15.2 Attention — make it visible, do not police it

A swiper in ten crews is not giving considered judgement to any of them, which is the
entire product claim.

**Do not hard-cap it.** Use a visible signal instead: show **"Alex swipes for 6 people"**
on the crew roster and let the user judge. Swiper scorecards (§8.3 C) do the rest —
hit rate is exactly the measure that separates a friend paying attention from someone
mashing through five decks a night.

A hard ceiling only becomes necessary if crew-farming appears in the data.

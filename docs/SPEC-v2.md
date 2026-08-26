---
title: Vouch — Product Spec v2
status: current
revision: 6
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

Swipers may continue to **suggest edits** (a prompt rewrite, a swap, a new upload)
after launch; the user approves or rejects each one. Editing — by the user or as a
swiper suggestion — is **free forever** (§8.3 A). **No AI.** All content is authored by
the user and their friends.

### 2.3 Re-pitch — running the competition again

A re-pitch is a **full teardown**: every swiper rebuilds a complete profile from
scratch and the user picks a new winner or rejects them all. It is not an edit.

**Either side can start one.** A swiper who thinks the current profile is not doing
their friend justice can propose a re-pitch; so can the user.

**Swiper-initiated rounds need the user's confirmation before they open.** A re-pitch
spends the user's monthly allowance and rewrites the user's profile, so a friend
*proposes* and the user *starts*. Without this, one enthusiastic swiper could burn the
allowance without asking, and five swipers could trigger five rounds.

**The action window.** When a round opens, every swiper is notified and has a fixed
window — **default 72 hours** — to submit.

- Submissions appear as they arrive; the user can review early and **close the round
  the moment they have a winner**
- A **halfway reminder** nudges swipers who have not submitted
- At expiry the round closes with whatever arrived. Non-submitters simply do not appear
- **If nobody submits, the round is void and the allowance is not consumed** — a user
  must never lose their monthly re-pitch to unresponsive friends
- **The current profile stays live in circulation for the entire round.** There is no
  downtime, no gap in the deck, and nothing breaks while the user waits

72 hours is the deliberate middle: 24 is too short for a friend to do real curation,
a week leaves the user hanging.

**Cadence — once per 30 days.** A rolling 30-day cool-down from the last *completed*
round, not a calendar month (which would allow the 31st and the 1st back to back).

- **Free:** one pitch round at signup
- **Premium:** one re-pitch per 30 days
- **Either tier:** extra rounds **purchasable**, same pack model as Dates

The binding constraint here is **crew fatigue, not user demand.** Unlimited re-pitches
would let a restless user ask three friends to rebuild a profile weekly, which burns
out the volunteers the entire product depends on — and cheapens the event, which is
special precisely because it is rare.

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
> Dates). Beyond that, tiers sell swipers — not Dates. See §8.2.


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

The paid pillar is **crew size**. Users buy a swiping workforce.

### 8.1 The tiers

| Tier | Swipers | Crew size | Weekly Dates *(1 per head)* | Kisses |
|---|---|---|---|---|
| **Free, solo** | 0 | 1 | **1** | Daily cap |
| **Free** | up to 3 | up to 4 | **up to 4** | Daily cap |
| **Premium** | **5** | 6 | **6** | Unlimited |
| **Higher tiers** | more (tiered) | more | **6 — flat (§8.2)** | Unlimited |

**Dates scale with headcount** — one per person in the crew, per week (§4.1). This is
deliberate: recruiting a swiper *increases the user's signal budget*, which makes the
invite a growth lever rather than a favour to ask. Per head it is exactly Hinge's Rose
rate, so individual scarcity is preserved as the crew grows.

**Kisses** are capped **per user, never per swiper** (§6.5) and distributed by the
allocation dial (§4.4). Premium buys resolution, never volume.

### 8.2 Date grant flattens above the premium crew — APPROVED

Category precedent: Hinge grants **1 free Rose per week to every user regardless of
tier** and sells extras in packs, monetising *unlimited ordinary likes* rather than
the scarce signal — because a Rose is worth something only while Roses are rare.

Vouch's headcount scaling is defensible up to premium (6 people, 6 Dates). Above that
it risks eroding what a Date means to everyone receiving one: a whale with a crew of
twelve sends twelve Dates a week against a solo user's one.

**Decision (approved):** Dates scale with headcount **up to the premium crew size — 6
heads, 6 Dates per week — then flatten.** Tiers above premium sell more swipers, more
resolution and unlimited Kisses; additional Dates come from **packs**, never from the
weekly grant. The invite incentive stays fully intact across the free tier and into
premium, which is exactly where recruitment matters.

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

**A. Re-pitch rounds — strongest.**

*Clarification, because this is easy to confuse with editing:*

| Action | Who | Cost |
|---|---|---|
| User edits their own profile | User | **Free, always, unlimited** |
| Swiper suggests an edit — a prompt rewrite, a photo swap, a new upload | Swiper | **Free, always, unlimited** |
| **Re-pitch: the whole crew rebuilds a complete profile from scratch and the user picks a new winner** | Crew | **Premium** |

A re-pitch is **not** an edit. It is re-running the §2 pitch competition end to end —
every swiper submits a fresh, complete proposed profile, and the user picks a new
winner or rejects them all. A teardown, not a tweak.

Free tier gets **one pitch round, at signup**. Premium can re-run it. This monetises
the app's most distinctive moment, gives lapsed users a real reason to return, and
refreshes stale profiles, which lifts match rates as a side effect.

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

Rationed for the same reason as re-pitches: a guest sees the user's deck and spends
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
| **Launch + 1** | **A** (re-pitch) | The distinctive one. Needs the §2 pitch flow to be solid first — re-running a broken flow is worse than not offering it |
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

**10.7 Lifecycle and safety.** What happens to in-flight and held swipes when a swiper
is removed? Blocking, reporting, abuse paths, and **18+ age enforcement** are
unspecified — the last matters more than usual because friends are acting inside
someone else's dating life.

**10.8 Crew supply, and the swiper-attention ceiling.** Two halves of one problem.
*Supply:* premium sells more swipers, but most people cannot recruit eight friends
willing to do unpaid work on their love life — above ~5 the tier may be unsellable for
supply reasons rather than price. *Attention:* the same person can join many crews, and
a swiper in ten of them is not giving considered judgement to any of them, which is the
entire product claim. A cap, a soft warning, or a quality signal may be needed. Both
halves need validation before the higher tiers are built.


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
| Microtransactions — extra profile rolls beyond the initial 3 | **Re-pitch packs (§2.3).** Same "some free, buy more" shape, now attached to a human event instead of an AI reroll |
| Free tier: limited daily swipes | **The Kiss pool + allocation pie (§4.4)** |
| Premium: unlimited swipes | **Kept**, but now the *second* thing premium sells; crew size is the pillar (§8.1) |

### 13.3 Pruned — dead in v2

| v1 feature | Why it is gone |
|---|---|
| **AI (Claude) consolidates voucher submissions into one cohesive profile** | Cut at the pivot. It undercut the entire human-vouching premise — friends "vouched" while a model wrote the words |
| **"Roll the dice" to regenerate, 3 free rolls, pay for more** | Died with the AI. **Re-pitch (§2.3) is its human successor** — same instinct (try again, some free, buy more), but the new version is your friends rebuilding it rather than a model rerolling it |
| **Users create a "seeking profile" with traits they want in a match** | **Cut.** Modern dating apps have largely abandoned structured "what I want" forms — they read as a wishlist, they date badly, and nobody fills them in honestly. Replaced by a **selectable prompt** (§13.4) |
| **When a voucher's referred user joins, the other person they vouched for gets notified (if preferences align)** | **Pruned as an automatic notification.** It pushes an unrequested introduction between two people who do not know each other, on the strength of a shared friend — a privacy problem, and it clashes with swiper blindness (§3.3) and with the user's control over their own deck. **The underlying graph fact survives** as passive social proof (§9): "you both know Alex" shown on the profile. Intrusive push becomes quiet trust signal |
| **"Possible premium voucher referral features"** | Vague in v1, and the concrete version of it is now pruned above. Premium is crew size (§8.1) |

### 13.4 The seeking profile becomes a prompt

Instead of a separate structured form, **"what I'm looking for" is simply one of the
selectable prompts** in the pool. A user who wants to say it can pick that prompt; a
user who does not, does not. It occupies one of the 10 material slots like anything
else, which is the right price for it.

**Knock-on to design for:** v1's seeking profile was also, implicitly, the brief a
swiper would read before acting. With it gone, **the brief lives in the group chat
(§7)** — the user tells their crew what they are after in conversation, which is more
natural, more current, and more honest than a form nobody updates.

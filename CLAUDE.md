# Vouch

A mobile dating app where friends build your profile, not you. Users get "vouched" by friends who fill out their profile and choose their photos. AI consolidates voucher submissions into a final profile.

## Concept

- Users ask 2+ friends to vouch for them and build their dating profile
- Vouchers attach socials (Instagram/Facebook) to prove they're real
- Users link Instagram/Facebook to pull photos, can also upload up to 10 photos for vouchers to choose from
- Vouchers fill out profile details and select photos
- AI (Claude) consolidates multiple voucher submissions into one cohesive profile
- User gives final approval or "rolls the dice" to regenerate (3 free rolls, pay for more)
- Users provide their own basic bio: name, age, sex, sexual orientation, seeking preference, smoking, alcohol, drugs, etc.
- Users create a "seeking profile" with traits they want in a match
- Friends paint the picture — the rest of the bio/personality comes from vouchers
- Swipe-based matching with filters (standard dating app UX)
- Users can search vouchers to find friends already on the app
- When a voucher's referred user joins, the other person they vouched for gets notified (if preferences align)

## Monetization

- **Free tier:** limited daily swipes, basic features
- **Premium subscription:** unlimited swipes, additional features (TBD), possible premium voucher referral features
- **Microtransactions:** extra profile rolls beyond the initial 3

## Tech Stack

- **Mobile:** React Native + Expo (iOS & Android from single codebase)
- **Backend/DB:** Supabase (PostgreSQL, Auth, Realtime, Storage)
- **AI:** Claude API (consolidating voucher submissions into final profile)
- **Payments (in-app):** RevenueCat (Apple/Google native billing for digital goods)
- **Payments (web, future):** Stripe (if/when web purchasing is added)
- **Push Notifications:** Expo Notifications + Supabase Edge Functions
- **Social Auth/Photos:** Instagram Graph API, Facebook Login SDK

## Project Structure

```
vouch/
├── app/              # Expo Router screens
├── components/       # Reusable UI components
├── lib/              # Utilities, API clients, helpers
├── supabase/         # Migrations, edge functions, seed data
├── assets/           # Images, fonts
└── constants/        # Theme, config
```

## Conventions

- TypeScript everywhere
- Functional components with hooks
- Expo Router for navigation (file-based routing)
- Supabase client via shared singleton in `lib/`
- All database changes via Supabase migrations in `supabase/migrations/`
- Environment variables in `.env` (never committed)

# Apple Pod Frontend (MVP)

Frontend-only MVP for Apple Pod: quiet smart capsules for study and deep work.

## What's included

- EN-first UX with i18n foundation (`en`, `ru`, `kz` fallback-ready)
- Landing sections: Hero, Features, FAQ, Booking
- Booking flow with Focus Pack settings:
  - duration: 1-3 hours
  - max capacity: 1 person per pod
  - lighting
  - seat height (with user height hints)
  - desk height
  - temperature
  - ventilation
- Separate subscriptions page (`/subscriptions`)
- New text-based ApplePod logo styling (as in provided concept)
- Personal account with booking list and edit mode
- Map with nearest-pod auto-detection (geolocation) and city fallback
- Local storage persistence with migration:
  - new keys: `applePodUser`, `applePodBookings`
  - legacy fallback: `appleDomeUser`, `appleDomeBookings`

## Local development

```bash
npm install
npm run dev
```

## Deploy to Vercel

Project already includes `vercel.json` for SPA rewrites.

Use these settings in Vercel:

- Framework Preset: `Vite`
- Build Command: `npm run build`
- Output Directory: `dist`
- Root Directory: project root (`applwcapsule-main`)

## Cloudflare (optional after Vercel)

- `public/_redirects` is included for SPA fallback on Cloudflare Pages.
- Start with DNS + SSL first.
- Enable extra proxy/WAF rules after basic production checks pass.

## Supabase prep (next step)

Database schema and RLS starter are in:

- `supabase/schema.sql`
- frontend integration example: `supabase/frontend-client-example.js`

Run this SQL in Supabase SQL Editor when you are ready to move from localStorage to real backend storage.

Add these env variables in Vercel when you connect Supabase:

- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_ANON_KEY`

You can copy `.env.example` to `.env` for local setup.

When you start wiring this into the app code, install:

```bash
npm i @supabase/supabase-js
```

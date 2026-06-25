# sc-cipdata-lookup-web

Standalone React/Vite frontend for the CiPData lookup migration.

## Purpose

This repo contains only the static frontend for:

- `/lookup`
- `/summary`
- `/followups`
- `/reports`

It does not contain the backend. The app expects a separate shared API that exposes `/api/cipdata/*`.

## Local Run

```powershell
Copy-Item .env.example .env
npm install
npm run dev
```

Default local URL:

```text
http://localhost:5175
```

## Required Environment

Frontend env only:

```env
VITE_API_BASE_URL=https://paasrtsm-project.onrender.com
VITE_USE_LOOKUP_MOCK=false
```

Important:

- Do not put Supabase keys in this repo.
- Supabase stays behind the shared backend.

## Render Deploy

You can deploy with `render.yaml` or enter these values manually:

- Root Directory: `.`
- Build Command: `npm install && npm run build`
- Publish Directory: `dist`

Environment variables:

- `VITE_API_BASE_URL=https://paasrtsm-project.onrender.com`
- `VITE_USE_LOOKUP_MOCK=false`

## Backend Contract

The frontend expects these routes from the shared backend:

- `GET /api/cipdata/branches`
- `GET /api/cipdata/encounters`
- `GET /api/cipdata/encounters/:encounterId`
- `GET /api/cipdata/encounters/:encounterId/medications`
- `GET /api/cipdata/kpis`
- `GET /api/cipdata/summary`
- `GET /api/cipdata/followups`
- `GET /api/cipdata/report-preview`

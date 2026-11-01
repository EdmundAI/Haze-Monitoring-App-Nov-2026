# Kabut: haze and weather monitor

Static single-page app. No build step, no dependencies, no API keys.

## Deploy on Vercel
1. Unzip, then in this folder run `npx vercel` (or drag the folder into the Vercel dashboard).
2. Framework preset: Other. Build command: none. Output directory: leave blank (root).

## Data
- Haze (PSI and PM2.5), Singapore only: National Environment Agency via data.gov.sg
  (api-open.data.gov.sg/v2/real-time/api/psi and /pm25).
- Weather for every city: Open-Meteo (api.open-meteo.com/v1/forecast).
- The page fetches both from the visitor's browser on load and every 10 minutes.
  If a request fails it shows the embedded snapshot (1 Nov 2026, 10:00 SGT) and the status pill says "Snapshot".
- data.gov.sg rate-limits anonymous calls. For heavy traffic, request a free API key and add an `x-api-key` header
  in `getJSON()` (note that this would expose the key in the browser; use a serverless proxy if that matters).

# 🔥 Brologue — Workout & Fitness Tracking PWA

A single-file, dependency-free Progressive Web App for planning and tracking your training:

- **Workout of the Day** the moment the app opens — with a 🔥 streak counter and daily motivation
- **Tap-to-schedule calendar** right on the home screen: tap any date to see that day's
  workouts or schedule a new one, with full recurring options (daily, every N days, weekly
  on chosen days, every 2 weeks, monthly, with optional end date)
- **Library** of preset plans (Push/Pull/Legs, Full Body, 5×5, Upper/Lower, Bodyweight, HIIT),
  an exercise database that filters by *your* equipment (with bodyweight substitutes for what
  you can't do), and a custom workout builder — pick exercises from the list, set sets,
  reps or seconds, and an optional target weight
- **Coach** — an AI chat powered by Claude for custom meal plans, dietary advice, and workout advice
- **Installable PWA** — works offline, installs to your home screen on Android and iOS

**Live app:** https://norris4539.github.io/Brologue/

## Coach setup (Claude API key)

The Coach tab works out of the box in **demo mode** (canned example answers). For real,
personalised answers from Claude:

1. Get an API key at [console.anthropic.com](https://console.anthropic.com)
2. In the app, open **Settings ⚙︎ → Anthropic API key** and paste it

Your key is stored **only on your device** (localStorage) and requests go directly from your
browser to the Anthropic API — no server in between. Never commit or share your key.

## Development

No build step. The whole app is `index.html` (CSS + JS inline), `sw.js`, `manifest.json`, `icons/`.

- Serve locally: `python3 -m http.server 8123`
- **Bump `CACHE` in `sw.js`** (e.g. `brologue-v1` → `v2`) on every `index.html` change,
  or installed apps will keep serving the old cached shell.
- Validate the inline script with `node --check` before committing.

All data (schedule, logs, streak, equipment, API key, chat history) lives in `localStorage`.

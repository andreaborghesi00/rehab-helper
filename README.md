# Finger Rehab

A tiny offline web app that tracks a two-exercise finger-rehab protocol: when the
next session is due, which exercise it is, what load to use, and when to add weight.

Built for the phone. No account, no server — everything lives in your browser.

## What it does

- **Ready / resting** — a live countdown to the next allowed session (default 6 h gap).
- **Alternates** static → dynamic → static automatically, and warns you if you pick the same one twice.
- **Tracks load** and tells you when you've done 4 sessions at the current weight, with a one-tap bump.
- **Progress to 30 % bodyweight**, from your 10 % starting point.
- **Climbing days** — pick "Climb" in the log sheet (or tap 🧗 for the quick version) and
  the app tells you to skip that day. Climbing outranks the 6 h timer, never counts toward
  the 4-session bump, and can carry its own pain rating.
- **Phase 2** — when you hit 30 % BW it starts the 1-month countdown, then shows the H-tape decision.
- **Guided timer** — 30 s hold or 3 s up / 3 s down × 10, 2 min rests, 3 sets, with beeps, vibration, and a screen wake-lock.
- **Pain 0–10** per session, plotted against load so you can see the trend that actually
  matters. Two stacked panels sharing one x-axis — never a dual y-axis, which would
  invent a correlation between two unrelated scales. Tap or drag the chart to inspect
  a session; the history list below is the table view.
- **Pain advisory** — if pain averages ≥5 over your last three sessions, or jumps by
  1.5 against the previous three, the app says so and tells you to raise it with your
  physio. It never tells you to change the load on your own.
- **Backup** — export/import your history as JSON from Settings.

## Deploy to GitHub Pages

```bash
cd rehab-helper
git init
git add .
git commit -m "Finger rehab tracker"
git branch -M main
git remote add origin git@github.com:<your-username>/rehab-helper.git
git push -u origin main
```

Then on GitHub: **Settings → Pages → Source: Deploy from a branch → `main` / `root` → Save**.

After a minute it's live at `https://<your-username>.github.io/rehab-helper/`.

> Make the repo **public**, or Pages won't serve it on a free plan.

## Put it on your home screen

- **iPhone:** open the URL in Safari → Share → *Add to Home Screen*.
- **Android:** open in Chrome → menu → *Install app*.

It then runs full-screen and works offline (a service worker caches it).

## Editing the numbers

Everything lives in **Settings** (gear icon): bodyweight, smallest plate you own,
current load, minimum hours between sessions, sessions per weight bump, and the
start/target bodyweight percentages. Change them any time — nothing is hard-coded
to one protocol.

## Files

| File | |
|---|---|
| `index.html` | the whole app — markup, styles, logic |
| `sw.js` | service worker, for offline use |
| `manifest.webmanifest` | home-screen name, colours, icons |
| `icon-*.png` | app icons |
| `.nojekyll` | tells Pages to serve the files as-is |

## Your data

Stored in your browser's `localStorage` on that one device. Clearing site data
wipes it — use **Settings → Export** now and then if the history matters to you.

---

Not medical advice. The rules encoded here come from your physio's notes; if
anything hurts, ask them, not the app.

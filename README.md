# Iron Coach — Ironman California 2027

Self-contained **tabbed** training dashboard for **Jonathan Covington** (Virginia Beach) targeting **IRONMAN California (Sacramento)** ~Oct 24, 2027.

## Open / share

- **Local folder:** open `index.html` in any modern browser (Chrome, Safari, Firefox, Edge). No build step required. Keep `assets/` next to `index.html`.
- **Standalone:** `../Ironman-California-Dashboard.html` inlines course maps as data URIs (single file, no assets folder needed). OSM iframe still needs network.
- **Hosted:** upload `ironman-california-dashboard/` (keep `assets/`) to Drive, GitHub Pages, Netlify, or any static host.

## UI (v2 · tabbed)

Matches the TMB Training dashboard UX patterns:

- Grey page (`#4b5563`) · white rounded cards · emerald accent
- Sticky header + desktop `.nav-btn` / mobile select
- Sections: **Overview · Workout Plan · Workout Progress · Log · Nutrition · Maps** (tabbed, not one long scroll)
- Monthly calendar (`#cal-grid`) · Chart.js progress graphs · live countdowns

## Files

| File | Purpose |
|------|---------|
| `index.html` | Tabbed dashboard (Tailwind/Chart.js CDN + embedded `DATA`) |
| `data.json` | Source of truth (`meta` + `workouts`) |
| `assets/*-map.jpg` | Course map images |
| `README.md` | This file |
| `../Ironman-California-Dashboard.html` | Standalone with maps inlined |

## Refresh routine

1. Update `data.json` workouts / meta.
2. Re-embed JSON into `const DATA = …` in `index.html` (and regenerate standalone if needed).
3. Stats, calendar, charts, and nutrition cards compute in the browser from `DATA`.

## Theme

Emerald (`#10b981`) primary on grey canvas; Ironman orange (`#ff6b1a`) as secondary run accent only.

## Multi-session days

Each day in `workouts` stays **one row** for plan + MFP nutrition. Completed Garmin activities live in optional `sessions: [{ sport, activity, minutes, distanceMi, pace, startEt, planned, completionPct, notes, activityId }]`. Legacy `garmin*` fields remain the **primary/planned** activity. **Future refreshes must preserve all Garmin sessions for a day** — do not bury extras only in `workoutNotes`.

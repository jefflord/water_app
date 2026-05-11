# Lawn Water Tracker

A client-side single-page application for tracking residential lawn watering schedules. No server, no database — everything runs in your browser with `localStorage` persistence.

## Features

- **Zone Management** — Create, rename, and delete custom watering zones (e.g., "Front Yard", "Backyard")
- **Live Timer** — Start, pause, resume, and stop timers per zone with real-time elapsed display
- **Watering History** — Monthly calendar view showing watered days and per-zone monthly totals
- **Session Editing** — Edit start/end times of past watering sessions; delete individual sessions
- **Data Portability** — Export all data as a `.json` backup file, import to restore or merge
- **Mobile-First Design** — Large touch-friendly buttons, responsive layout for outdoor use

## Getting Started

1. Open `index.html` directly in any modern browser (Chrome, Firefox, Safari, Edge)
2. Add your first watering zone by tapping **+ Add Zone**
3. Start a timer and track your lawn watering

No installation, no build step, no dependencies to install.

## How It Works

| Feature | Implementation |
|---|---|
| Data storage | `localStorage` (zones, logs, active timers) |
| Timer accuracy | Cumulative duration tracking — survives tab close and pause/resume cycles |
| Persistence | Auto-saves on every stop, zone change, or session edit |
| Export/Import | JSON file download/upload with merge-or-replace option |

## Architecture

```
index.html          # Single-file SPA (HTML + CSS + JS)
├── Tailwind CSS    # Loaded via CDN for mobile-first styling
├── Zone Manager    # CRUD zones, rename, delete with history check
├── Timer Engine    # Start/Pause/Resume/Stop with cumulative ms tracking
├── Calendar View   # Monthly grid + per-zone totals
└── Data I/O        # Export/import JSON backup
```

## Browser Compatibility

Works in all modern browsers. Requires `localStorage` support (enabled by default).

## License

MIT

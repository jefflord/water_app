# Lawn Water Tracker

A client-side single-page application for tracking residential lawn watering schedules. No server, no database — everything runs in your browser with `localStorage` persistence.

## Features

- **Zone Management** — Create, rename, and delete custom watering zones (e.g., "Front Yard", "Backyard")
- **Live Timer** — Start, pause, resume, and stop timers per zone with real-time elapsed display. Start a timer retroactively to account for manual starts ("1m ago", "5m ago", etc.)
- **Stop Reminder** — Configurable countdown timer on each active zone (15 seconds to 1 hour). Get a "+5 min" button to extend the reminder while watering, plus "ALMOST TIME!" warning when under 30 seconds remain. Red flashing banner with snooze options (1m, 5m, 15m) when time is up
- **Watering Alarms** — Schedule future watering reminders with quick presets ("Now +1h", "6:00 AM Today", etc.), sound alerts, flashing visuals, and desktop notifications. Snooze for 5 minutes or dismiss when done
- **Watering History** — Monthly calendar view showing watered days (with duration overlay), per-zone monthly totals sorted by time, and daily breakdowns with session counts
- **Session Editing** — Edit start/end times of past watering sessions; delete individual sessions. Collapsible session lists per zone
- **Data Portability** — Export all data as a `.json` backup file, import to restore or merge with existing data. Clear all data option
- **Timer Persistence** — Active timers survive tab close and browser restarts. Cumulative duration tracking across pause/resume cycles
- **Mobile-First Design** — Large touch-friendly buttons, responsive layout for outdoor use, tap highlight removal, overscroll prevention

## Getting Started

1. Open `index.html` directly in any modern browser (Chrome, Firefox, Safari, Edge)
2. Add your first watering zone by tapping **+ Add Zone**
3. Start a timer or set an alarm to remind you when to water

No installation, no build step, no dependencies to install.

## How It Works

| Feature | Implementation |
|---|---|
| Data storage | `localStorage` (zones, logs, active timers, alarms) |
| Timer accuracy | Cumulative duration tracking — survives tab close and pause/resume cycles |
| Timer offset | Start timers retroactively ("5m ago") with negative offset support |
| Persistence | Auto-saves on every stop, zone change, session edit, or alarm update |
| Alarms | Scheduled triggers with Web Audio API sound, screen flashing, and browser notifications |
| Snooze | Reschedules the active alarm 5 minutes forward without creating duplicates |
| Stop reminder | Countdown display per zone with "+5 min" bump, "ALMOST TIME!" warning, and red banner with multi-duration snooze |
| Export/Import | JSON file download/upload with merge-or-replace option |

## Architecture

```
index.html          # Single-file SPA (HTML + CSS + JS)
├── Tailwind CSS    # Loaded via CDN for mobile-first styling
├── Zone Manager    # CRUD zones, rename, delete with history check
├── Timer Engine    # Start/Pause/Resume/Stop with cumulative ms tracking & offset support
├── Stop Reminder   # Configurable countdown per zone with +5 min bump & banner alerts
├── Alarm System    # Schedule (with presets), trigger (sound + visuals), snooze, dismiss
├── Calendar View   # Monthly grid + per-zone totals + daily breakdowns
├── Session Manager # Edit/delete past sessions, collapsible per-zone lists
└── Data I/O        # Export/import JSON backup, clear all data
```

## Browser Compatibility

Works in all modern browsers. Requires `localStorage` support (enabled by default).

For alarm sound to work, the page needs at least one user interaction first (browser autoplay policy). Tapping any button on the page enables audio.

## License

MIT

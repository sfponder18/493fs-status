# 493 FS Status Board

A password-protected project status dashboard for the 493rd Fighter Squadron, hosted on GitHub Pages.

**Live URL:** [https://sfponder18.github.io/493fs-status/](https://sfponder18.github.io/493fs-status/)

## Quick Start

1. Clone the repo
2. Enable GitHub Pages: **Settings → Pages → Source: Deploy from branch → main → / (root) → Save**
3. Share the Pages URL with your team

## Default Password

`reapers`

### Changing the Password

Open your browser console and run:

```js
crypto.subtle.digest('SHA-256', new TextEncoder().encode('YOUR_NEW_PASSWORD'))
  .then(b => console.log([...new Uint8Array(b)].map(x=>x.toString(16).padStart(2,'0')).join('')))
```

Replace the `PASSWORD_HASH` value at the top of the `<script>` in `index.html` with the output.

## Updating Projects

Edit `projects.json` — either locally and push, or directly on GitHub. The dashboard auto-refreshes every 60 seconds.

### Project Schema

```json
{
  "name": "Project Name",
  "category": "Facilities",
  "status": "in progress",
  "priority": "high",
  "milestone": "Current status and what's next",
  "dueDate": "2026-05-01",
  "funding": "$200 Booster Club",
  "blockers": "Any blockers or risks",
  "notes": "Additional context",
  "updated": "2026-04-01T12:00:00Z",
  "files": [
    { "label": "Design Doc", "url": "https://drive.google.com/..." }
  ]
}
```

### Valid Status Values

| Status | Description |
|--------|-------------|
| `not started` | Not yet begun |
| `planning` | In planning phase |
| `in progress` | Actively being worked |
| `complete` | Done |
| `on hold` | Paused |

### Valid Priority Values

| Priority | Description |
|----------|-------------|
| `high` | Urgent |
| `medium` | Normal |
| `low` | Can wait |

## How It Works

- `index.html` — Single-file dashboard with password gate and live rendering
- `projects.json` — Project data (the only file you need to edit regularly)
- Password is session-based (survives refresh, clears on browser close)
- All rendering is client-side, no backend needed
- GitHub Pages serves the static files

# 493 FS Status Board

Project status dashboard for the 493rd Fighter Squadron, hosted on GitHub Pages.

**Live URL:** [https://sfponder18.github.io/493fs-status/](https://sfponder18.github.io/493fs-status/)

## Quick Start

1. Clone the repo
2. Enable GitHub Pages: **Settings → Pages → Source: Deploy from branch → main → / (root) → Save**
3. Share the Pages URL with your team

## Editing Projects

Click **+ Add Project** on the dashboard to add a new project, or click **Edit** on any existing project card. On first edit you'll be prompted for a GitHub personal access token (stored in your browser session only).

To generate a token: **GitHub → Settings → Developer settings → Personal access tokens → Fine-grained tokens** — grant `Contents: Read and write` on this repo.

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

- `index.html` — Single-file dashboard with inline editing via GitHub API
- `projects.json` — Project data (auto-updated when you use the dashboard editor)
- All rendering is client-side, no backend needed
- GitHub Pages serves the static files
- Dashboard auto-refreshes every 60 seconds

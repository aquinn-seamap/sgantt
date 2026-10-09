# sgantt

Gantt Chart Creation Tool: a single-page, no-build Gantt chart editor that runs entirely in the browser.

## Use it

Open `index.html` in any modern browser, or turn on GitHub Pages for this repository (Settings → Pages → Deploy from branch → `main` / root) and visit the published URL.

## Features

- Task list with editable name, start, end, duration and % complete
- Timeline with Day, Week and Month scales, weekend shading and a Today marker
- Drag bars to move tasks; drag the right-hand handle to change length
- Keyboard: with a bar focused, arrow keys move it a day, Shift + arrow keys change its end date
- Milestones, colours, notes, and "starts after" dependencies that push later tasks forward
- Multiple projects saved automatically in the browser (localStorage)
- Export to and import from a `.gantt.json` file for backups and sharing

## Saving and data

Projects are stored in the browser's localStorage under the key `gantt-builder:projects`, so they stay on that browser and device only. Use **Export** to keep a file copy, and **Import** to load one (imports always open as a new project).

Export format:

```json
{
  "app": "gantt-builder",
  "version": 1,
  "title": "Website relaunch",
  "scale": "week",
  "tasks": [
    { "id": "t1", "name": "Research", "start": "2026-10-12", "end": "2026-10-18",
      "progress": 60, "color": "#1F4FC9", "milestone": false, "dep": "", "notes": "" }
  ]
}
```

Dates are inclusive `YYYY-MM-DD`. `dep` is the `id` of the task this one must start after.

## Repository layout

| Path | What it is |
| --- | --- |
| `index.html` | The app: plain HTML, CSS and JavaScript, no dependencies or build step |
| `design/Main.dc.html` | Source of the Claude Design canvas version (needs the Claude canvas runtime; it will not run on its own) |
| `design/canvas.json` | Canvas layout for the design version |

The only external request is to Google Fonts for IBM Plex Sans and IBM Plex Mono; the page falls back to system fonts without it.

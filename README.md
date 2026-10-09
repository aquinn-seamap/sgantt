# sgantt

Gantt Chart Creation Tool: a single-page, no-build Gantt chart editor that runs entirely in the browser.

## Use it

Open `index.html` in any modern browser, or turn on GitHub Pages for this repository (Settings → Pages → Deploy from branch → `main` / root) and visit the published URL.

## Features

- Task list with editable name, start, end, duration and % complete
- Timeline with Day, Week and Month scales, weekend shading and a Today marker
- Horizontal zoom (10% to 600%) with zoom in/out, Fit (whole project in view) and reset to 100%
- Show or hide the Start, End, Days and Done % columns
- Dependency lines drawn from each task to the tasks that start after it (highlighted for the selected task)
- Drag bars to move tasks; drag the right-hand handle to change length
- Keyboard: with a bar focused, arrow keys move it a day, Shift + arrow keys change its end date
- Milestones, colours, notes, and "starts after" dependencies that push later tasks forward
- Multiple projects saved automatically in the browser (localStorage)
- Export to and import from a `.gantt.json` file for backups and sharing
- **Save PDF**: A4, A3, US Letter, US Legal or Tabloid, landscape or portrait, normal or narrow margins.
  Fit the whole chart on one page, or spread it across pages (e.g. 2 wide × 1 tall) for long projects.
  Optionally repeat the task list on every page, and show or hide date columns, % complete, the today line, weekend shading and dependency lines.
  PDF settings, zoom level and column choices are saved with each project.

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
| `vendor/jspdf-4.2.1.umd.min.js` | [jsPDF](https://github.com/parallax/jsPDF) 4.2.1 (MIT licence, see `vendor/jspdf-LICENSE`), used to build PDFs in the browser |
| `design/Main.dc.html` | Source of the Claude Design canvas version (needs the Claude canvas runtime; it will not run on its own) |
| `design/canvas.json` | Canvas layout for the design version |

The only external request is to Google Fonts for IBM Plex Sans and IBM Plex Mono; the page falls back to system fonts without it.

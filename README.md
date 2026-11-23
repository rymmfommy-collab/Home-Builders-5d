# Home Studio 5D

An offline home design app that runs in a single HTML file. Draw a floor plan, see it in 3D, step through the build sequence, and get a cost estimate, all without internet, accounts or servers.

**5D here means:** 3D model + 4D schedule (build phases over time) + 5D cost.

## Features

- **Plan editor (2D):** draw walls and rooms, add doors and windows, place furniture. Snaps to a 0.25 m grid and to existing wall ends. Pan, zoom, move, resize, rotate, copy, delete, undo.
- **3D view:** orbit, pan and zoom around a lit model with floors, walls, window glass and furniture. Uses its own renderer, with no libraries.
- **4D build phases:** a slider steps through Floors, Structure, Openings and Furnishing, showing the day count and the cost to date.
- **5D cost and schedule:** per-phase cost, a simple schedule bar chart, and a furniture price list. Rates and currency are editable.
- **Saving:** autosaves in the browser or app. Export and import designs as `.json`. Export the current view as PNG.

## Use it

Open `index.html` in any modern browser. No installation or internet is needed.

| Tool | What it does |
|------|--------------|
| Select | Move items, drag empty space to pan. Tap an item to edit its size, name or floor type. |
| Wall | Drag to draw. |
| Room | Drag a rectangle to add a room with a floor. |
| Door / Window | Tap a wall to place one. Drag it along the wall to move it. |
| Furniture | Choose an item from the list, then tap the plan to place it. |
| Erase | Tap an item to delete it. |

**Shortcuts:** `R` rotates the selected furniture, `Delete` removes the selected item, `Ctrl/Cmd+Z` undoes, `Esc` clears the selection.

**3D controls:** drag to orbit, shift or right-drag to pan, scroll or pinch to zoom.

## Build an Android APK (fully offline)

The app is bundled inside the APK, so the installed app needs no internet.

1. Create a free GitHub repository.
2. Upload `index.html` and `.github/workflows/build.yml` (keep that exact path).
3. Open the **Actions** tab. The **Build APK** workflow runs automatically (about 5 minutes).
4. Download **HomeStudio5D-APK** from the finished run's Artifacts, unzip it, and install `app-debug.apk`.

The result is a debug build for personal use. It is not signed for Google Play.

## Your data

Designs are stored locally in the browser or app storage. Nothing is sent anywhere. Clearing app or browser data deletes saved designs, so use **Export** to keep backups.

## Limits

- Cost and time figures are rough estimates based on the rates you set, not real quotes. Wall cost uses gross wall area (length × height) without subtracting openings.
- Walls are straight segments. There are no roofs, stairs or multiple floors yet.
- The 3D view sorts shapes by distance, so rare overlapping glitches can appear in dense scenes.

## Tech

Plain HTML, CSS and JavaScript. Canvas 2D for the plan and a custom perspective renderer for 3D. The APK is packaged with Capacitor in a GitHub Actions workflow.

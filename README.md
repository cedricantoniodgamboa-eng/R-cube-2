# 🧊 Cube Lab

Twist, solve and build. A single-file, no-build web app for twisty puzzles. It is installable as an app and works offline.

**Live demo:** `https://YOUR-USERNAME.github.io/cube-lab/` (replace after you deploy)

## Features

- **Puzzles:** 2×2, 3×3, 4×4, 5×5, Pyraminx, Skewb, Megaminx, Square-1 and the Shengshou Circle 3×3
- **3D simulator:** drag to orbit, pinch or wheel to zoom, swipe a sticker to turn that layer, animated turns, undo/redo
- **Timer:** hold Space (or touch the pad) until green, release to start, tap or press any key to stop. Optional 15 s inspection, +2 / DNF, best, mean, ao5, ao12, solves saved per puzzle
- **Solver:** step through a solution with play, pause, next and previous
- **Scrambler:** random scrambles in standard notation with no redundant consecutive moves on the same axis
- **Pattern Lab:** built-in patterns, plus save, replay, rename, export and import of your own
- **Paint:** color individual stickers, with validation that the color counts are possible
- **Tutorials:** Beginner, CFOP and Roux (3×3), plus guides for the other puzzles, each with a demo and a practice mode
- **Creator:** build your own models from 3D parts, link and turn them, write tutorial steps
- **Extras:** themes (Beach, Mountain, Jungle, City, Space), custom backgrounds, generated music and sound effects, portrait and landscape layouts

Keyboard: `r l u d f b` turn faces (hold Shift for the prime), `m e s` slices, `x y z` rotations, `Backspace` undo, `Enter` redo. In the Timer tab, `Space` starts and stops.

## Run locally

Open `index.html` in a browser. To test the offline/installable behavior, serve it over HTTP:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy on GitHub Pages

1. Create a new **public** repository named `cube-lab` on GitHub.
2. Upload everything in this folder to the root of the repository (`index.html` must be at the top level).
3. Go to **Settings → Pages**. Under **Build and deployment**, set **Source** to *Deploy from a branch*, choose **main** and **/ (root)**, then **Save**.
4. After about a minute your app is live at `https://YOUR-USERNAME.github.io/cube-lab/`.

Using git instead:

```bash
git init
git add .
git commit -m "Cube Lab"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/cube-lab.git
git push -u origin main
```

## Project structure

```
index.html            the whole app (HTML, CSS and JavaScript)
manifest.webmanifest  install metadata (name, colors, icons)
sw.js                 service worker for offline use
icons/                app icon: SVG, PNG, maskable and Apple touch icon
LICENSE               MIT (add your name)
```

## Known limitations

- **Solver scope.** The solver is a bidirectional search, not Kociemba or a layer-by-layer method. It finds short solutions only: roughly up to 8 moves on a 3×3, 11 on a 2×2 or Pyraminx, and 6 on a 4×4/5×5. If you reached a deeper state by making moves, it reverses your move history and verifies the result. A deeply scrambled painted state may report "No solution found". Megaminx and Square-1 have no solver.
- **Circle cube.** Only the outer 3×3 is solved; the circle pieces are tracked separately.
- **Architecture.** Vanilla JavaScript in a single file with CSS 3D transforms (no Three.js, no TypeScript, no unit tests).
- **Storage.** Patterns, solves and settings live in the browser's `localStorage`, so they are per browser and per device.

Built with Claude.

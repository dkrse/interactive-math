# Architecture

## Overview

Single-file web application (`src/math.html`) — no build tools, no dependencies, no frameworks. Everything is vanilla HTML + CSS + JavaScript in one self-contained file (~80KB).

## File Structure

```
src/
  math.html          # The entire application — all 3 visualizations
docs/
  architecture.md    # This file
  changelog.md       # Version history
screenshots/         # Screenshots for README
README.md
LICENSE
```

## Application Structure

```
math.html
├── <style>          # All CSS (~4KB)
├── <body>
│   ├── <header>     # Title, theme toggle (☀/☾), language toggle (SK/EN)
│   ├── <nav>        # Tab bar: Trigonometry | Conics | Complex Numbers
│   ├── #tab-trig    # Trigonometry tab content
│   ├── #tab-conics  # Conic Sections tab content
│   └── #tab-complex # Complex Numbers tab content
└── <script>         # All JavaScript (~70KB)
    ├── Shared       # Theme, language system, tab switching, HiDPI, resize
    ├── Trigonometry  # Circle canvas, wave canvas, lessons, challenges
    ├── Conics        # Main canvas, 3D cone canvas, lessons, challenges
    └── Complex       # Main canvas, power canvas, lessons, challenges
```

## Design Decisions

### Single File
All HTML, CSS, and JS live in one file. This means:
- Zero build step — just open in a browser
- Easy to share — send one file
- Works offline
- No CORS issues, no server needed

### Tab-Based Navigation
Three visualizations share the same page. Only the active tab renders its canvases (performance). On tab switch:
1. CSS accent color changes (blue/green/purple)
2. Active tab's canvases resize to container
3. Active tab re-renders

### Language System
All translatable strings live in the `I` object with `sk` and `en` keys:
- Static UI text: `data-i18n` attributes on HTML elements, updated by `applyLang()`
- Lessons and challenges: separate `sk`/`en` arrays, re-rendered on language change
- `L(key)` helper returns the string for the current language

### Dynamic Canvas Sizing
All canvases resize to fill their container width:
- `resizeActive()` called on window resize (debounced 80ms) and tab switch
- Each tab has its own resize function (`trigResize`, `conResize`, `cpxResize`)
- `setupHiDPI()` handles devicePixelRatio for sharp rendering on retina displays
- Canvas logical size set via `style.width/height`, physical size via `width/height` attributes

### Canvas Rendering
Each visualization uses HTML5 Canvas 2D:
- **Trigonometry**: 2 canvases (unit circle + wave)
- **Conics**: 2 canvases (top-view curve + 3D cone slice)
- **Complex**: 2 canvases (complex plane + power visualization)

All drawing is immediate-mode (no retained scene graph). Each `render()` call clears and redraws everything.

### Interaction Model
- **Drag**: mousedown/mousemove/mouseup + touchstart/touchmove/touchend on canvases
- **Snap**: Trigonometry snaps to notable angles (30°, 45°, 60°...); Complex snaps to nice values (0, 0.5, 1, √2/2...)
- **Sliders**: HTML range inputs for eccentricity, zoom, w angle/magnitude, exponent n
- **Checkboxes**: toggle visibility of waves, unit circle, product, conjugate

### Challenges
Each tab has a set of challenges (interactive exercises). Each challenge has:
- `text`: HTML string describing the task
- `check()`: function returning boolean — evaluated on every render
- When solved, a "Correct!" label fades in
- "Next challenge" button cycles through the list

### Conics Zoom
The conics top-view has a zoom slider (0.2× to 1.0×) that scales the entire coordinate system. This lets users zoom out to see the full hyperbola with both branches, foci, and directrices.

## ID Naming Convention

To avoid collisions across tabs, all element IDs are prefixed:
- `t_` — Trigonometry (e.g., `t_circleC`, `t_valSin`)
- `c_` — Conics (e.g., `c_mainC`, `c_eccSlider`)
- `x_` — Complex (e.g., `x_mainC`, `x_valZ`)

## Theme System

CSS custom properties on `:root` / `:root.light`:
- Toggle adds/removes `.light` class on `<html>`
- All colors reference CSS variables (`var(--bg)`, `var(--fg)`, etc.)
- `themeColor(name)` reads computed CSS variable values for canvas drawing
- `--accent` is dynamically set per active tab

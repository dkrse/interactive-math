# Interactive Math — Understand it visually

One self-contained HTML file with three interactive math visualizations. No build tools, no dependencies, no frameworks — just open `src/math.html` in a browser.

**[Open it](src/math.html)** | SK/EN | Light/Dark | Mobile-friendly

## What's inside

### Trigonometry

Drag a point around the unit circle. See sin, cos, tan as actual geometry — not formulas to memorize.

- Unit circle with live right triangle
- Sin/cos/tan wave visualization from circular motion
- Pythagorean identity sin² + cos² = 1 verified live
- Snap to notable angles (30°, 45°, 60°, 90°...)
- 7 lessons, 7 challenges

### Conic Sections

One slider morphs a circle into an ellipse, parabola, and hyperbola. They're all one family.

- Eccentricity slider (0 → 2.00) — smooth morphing
- 3D cone with cutting plane rendered in real time
- Zoom control (0.2×–1.0×) to see everything at once
- Live distance measurements to foci and directrix
- Ellipse: sum constant. Hyperbola: difference constant. Proven live.
- 7 lessons, 5 challenges

### Complex Numbers

Multiplication is rotation. Exponentiation is repeated rotation. See it, don't just believe it.

- Two draggable points (z and w) in the complex plane
- Product z·w shown live — magnitudes multiply, angles add
- Conjugate toggle (mirror across real axis)
- Power visualization z¹ through z¹² with auto-scaling spiral
- Sliders for w angle, w magnitude, exponent n
- 8 lessons, 5 challenges

## Features

- **Single file** (`src/math.html`, ~80KB) — zero dependencies, works offline
- **Bilingual** — Slovak / English toggle, all text including lessons and challenges
- **Light / Dark theme**
- **Responsive** — canvases resize dynamically to any screen width
- **Touch support** — works on phones and tablets
- **HiDPI** — sharp on retina displays

## Project structure

```
src/math.html              # The entire application
docs/architecture.md       # Technical architecture
docs/changelog.md          # Version history
```

## Usage

```bash
# Just open it
open src/math.html

# Or serve locally
python3 -m http.server 8000
# then visit http://localhost:8000/src/math.html
```

## Author

krse

## License

[MIT](LICENSE)

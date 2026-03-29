# Changelog

## v3.0 — Unified Single File

Merged all separate HTML files into one `src/math.html` with tabbed navigation.

### Added
- **Tab navigation**: Trigonometry, Conic Sections, Complex Numbers in one page
- **Language toggle** (SK/EN): all UI text, lessons, and challenges in both languages
- **Theme toggle** (light/dark): single button, persists across tabs
- **Dynamic canvas sizing**: all canvases resize to fill container width, responsive on all screen sizes
- **Conics zoom slider** (0.2×–1.0×): zoom out to see full hyperbola with both branches

### Changed
- All individual files (`trig_sk.html`, `trig_en.html`, `conics_sk.html`, `conics_en.html`, `complex_sk.html`, `complex_en.html`) replaced by single `math.html`
- Accent color changes per tab (blue → green → purple)
- Only active tab renders its canvases (performance)
- Values displayed in responsive grid layout instead of fixed-width panels

### Removed
- 6 separate HTML files (functionality preserved in unified file)

---

## v2.0 — Complex Numbers

### Added
- **Complex numbers visualization** (`complex_sk.html`, `complex_en.html`)
- Complex plane with two draggable points (z and w)
- Multiplication as rotation + scaling, shown live
- Sliders for w angle and magnitude
- Conjugate toggle (mirror across real axis)
- **Exponentiation panel** (`z^n`): power canvas showing z¹ through z¹² with auto-scale
- Exponent slider (1–12)
- Snap to nice values (0, 0.5, 1, √2/2, √3/2)
- 8 step-by-step lessons (complex plane, polar form, multiplication, rotation, i²=−1, conjugate, exponentiation, Euler's formula)
- 10 interactive challenges
- Full responsive/dynamic canvas sizing

---

## v1.1 — Conic Sections

### Added
- **Conic sections visualization** (`conics_sk.html`, `conics_en.html`)
- Eccentricity slider (0–2.00) morphing circle → ellipse → parabola → hyperbola
- 3D cone canvas showing the cutting plane and intersection curve
- Draggable point P with live distances to foci and directrix
- Focus-directrix ratio verified in real time
- Ellipse: sum of distances constant; Hyperbola: difference constant
- 7 step-by-step lessons
- 10 interactive challenges

---

## v1.0 — Trigonometry

### Added
- **Trigonometry visualization** (`trig_sk.html`, `trig_en.html`)
- Unit circle with draggable point
- Right triangle (sin, cos, hypotenuse) drawn live
- Wave canvas showing sin, cos, tan waves
- Pythagorean identity sin² + cos² = 1 computed live
- Snap to notable angles (0°, 30°, 45°, 60°, 90°, ...)
- Quadrant indicator
- Animation mode (continuous rotation)
- Light/dark theme toggle
- Touch support for mobile
- 7 step-by-step lessons
- 10 interactive challenges

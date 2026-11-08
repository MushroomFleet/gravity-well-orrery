# 🌌 Gravity Well Orrery

An interactive 3D "rubber sheet" model of the solar system, built as a single standalone HTML file.

The Sun sits at the bottom of a funnel-shaped grid of space, and all eight planets orbit around it. Each planet presses its own small dent into the sheet as it moves. You can rotate, pan and zoom around the well, or click a planet to ride along with it in first person.

**[▶ Download `gravity-well-orrery.html`](gravity-well-orrery.html)** and open it in any modern browser. Nothing to install, no build step, no server.

---

## What it's for

The gravity well (or rubber sheet) diagram is the most familiar way to picture gravity as curved space. A heavy mass sinks into a stretchy grid, and smaller bodies circle around the dip. It's in documentaries, classrooms and countless social media clips.

Gravity Well Orrery turns that picture into something you can explore rather than just watch:

- **Learning and teaching:** a hands-on way to show how mass curves the sheet and how orbits sit inside the well.
- **Seeing the scale of the solar system:** switch between compressed and true spacing to see how crowded the inner planets are compared with the outer giants.
- **A desktop orrery:** the planets start from where they actually are today and move at their real relative speeds, with a running date counter.
- **A starting point for your own work:** everything is in one readable file, easy to fork, restyle or extend.

---

## Features

### The well
- A deep polar grid funnel with a glowing Sun at its base, drawn in WebGL with [three.js](https://threejs.org/)
- All eight planets: Mercury, Venus, Earth, Mars, Jupiter, Saturn (with rings), Uranus and Neptune
- Each planet makes its own local dent in the sheet, which travels with it around the orbit
- Optional orbit paths and floating name labels

### Real positions and timing
- Planet positions are calculated from today's date using mean orbital longitudes (J2000 epoch)
- Orbital periods are real, so inner planets race around while Neptune barely moves
- Adjustable time speed, from 1 day per second up to many years per second
- **Today** button to jump back to the present date

### Camera
| Action | Mouse / trackpad | Touch |
|---|---|---|
| Rotate | Left-drag | One-finger drag |
| Pan (up / down / left / right) | Right-drag, or Shift + drag | Two-finger drag |
| Zoom | Scroll wheel | Pinch |
| Planet view | Click a planet | Tap a planet |
| Back to overview | **Reset view** button or `Esc` | **Reset view** button |

### Planet view
Click any planet and the camera glides onto it, locking a first-person view that faces along its direction of travel. You ride the orbit around the inside of the well. Drag to look around without breaking the lock, or click another planet to hop across to it.

### Planet details
Selecting a planet opens a card with:
- Distance from the Sun (AU)
- Orbital period
- Mass and diameter
- Average orbital speed
- **Clock slowdown from the Sun's gravity:** how much slower a clock at that distance runs than one far from the Sun, in parts per billion and seconds per year (general relativistic time dilation, about 0.31 s/year at Earth)

### Controls bar
- Play / Pause
- Speed and well-depth sliders
- Compressed / True spacing toggle
- Orbits and Labels toggles

---

## Getting started

1. Download [`gravity-well-orrery.html`](gravity-well-orrery.html).
2. Double-click it, or drag it into Chrome, Firefox, Edge or Safari.

That's it. The three.js library is embedded in the file, so the 3D scene works fully offline. The only online request is for two Google Fonts (Chakra Petch and Instrument Sans). Without a connection, the text falls back to system fonts and everything else works the same.

---

## Accuracy notes

This is a visual analogy, not a physics simulation, and some things are simplified so it stays readable:

- **Not to scale.** Planet sizes are greatly exaggerated so you can see them, and the depth of the funnel is illustrative.
- **Circular orbits.** Planets move on circles at their mean rate, so positions are approximate (good to within a few degrees for the inner planets).
- **The rubber sheet is a metaphor.** In general relativity, the planets' orbits come mostly from the curvature of *time* near the Sun, which a 2D sheet can't show. The formal version of this diagram is called an *embedding diagram* (for a spherical mass, *Flamm's paraboloid*), and the true one for the Sun would be almost flat.

---

## How it works

Everything lives in one HTML file: markup, styles and a single script.

- **Sheet:** a polar mesh of rings and spokes. Every frame, each vertex is lowered by a softened 1/r well for the Sun, plus a small Gaussian dent around each planet.
- **Orbits:** each planet's angle is `L0 + 360° × (t / T)`, where `L0` is its mean longitude at J2000 and `T` its orbital period in days.
- **Spacing:** "Compressed" maps distance with a square-root curve so all eight orbits fit; "True" maps it linearly. The toggle blends smoothly between the two.
- **Camera:** an orbit camera with panning offset, and a planet-view mode that places the camera just above the selected planet and aims it at a point slightly ahead on the orbit. Transitions between modes are eased.

### Customising
The planet table near the top of the script holds each planet's orbital data, colour and display size, so it's easy to tweak or extend (add dwarf planets, change colours, adjust exaggeration). The colour palette and fonts are defined as CSS variables in `:root`.

---

## Browser support

Any current browser with WebGL: Chrome, Edge, Firefox and Safari on desktop, and modern mobile browsers. Motion-sensitive users: the page respects `prefers-reduced-motion` and starts paused without auto-rotation.

---

## Credits

- 3D rendering: [three.js](https://threejs.org/) (r128, MIT licence), embedded in the file
- Fonts: [Chakra Petch](https://fonts.google.com/specimen/Chakra+Petch) and [Instrument Sans](https://fonts.google.com/specimen/Instrument+Sans) via Google Fonts
- Orbital elements: mean J2000 values for the eight planets

---

## 📚 Citation

### Academic Citation

If you use this codebase in your research or project, please cite:

```bibtex
@software{gravity_well_orrery,
  title = {Gravity Well Orrery: An interactive 3D rubber sheet model of the solar system},
  author = {[Drift Johnson]},
  year = {2026},
  url = {https://github.com/MushroomFleet/gravity-well-orrery},
  version = {1.0.0}
}
```

### Donate:

[![Ko-Fi](https://cdn.ko-fi.com/cdn/kofi3.png?v=3)](https://ko-fi.com/driftjohnson)

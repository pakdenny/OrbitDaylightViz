# Solar Path Explorer

An interactive visualization that shows how Earth's orbital position and axial tilt affect sunrise, sunset, and the sun's path across the sky at different latitudes.

## What it does

Solar Path Explorer links two views side by side:

- **Orbital View** — A 3D view of Earth orbiting the Sun, showing axial tilt, rotating continents, day/night terminator, and an observer dot at your chosen latitude. Drag to rotate the view from any angle.
- **Horizon View** — What the sky looks like from the ground at that latitude, with the sun's arc across the sky, sunrise/sunset positions, and real-time sky color changes.

Both views update together in real time, so you can see *why* the sun behaves the way it does at any latitude and time of year.

## Features

- **Play 24H** — Animate a full day cycle and watch the sun sweep across the sky while the observer dot rotates around the Earth
- **Play Year** — Animate through the seasons and watch day length change as Earth orbits the Sun
- **Day/night latitude ring** — A colored ring on Earth shows the proportion of daylight (yellow) vs night (purple) at the current latitude, making day length variation immediately visible
- **3D arcball camera** — Grab and rotate the orbital view to examine the geometry from any perspective
- **Latitude presets** — Quick jumps to Equator, Tropics, 45°N, Arctic Circle, and North Pole
- **Auto-facing horizon** — The horizon view automatically faces toward the noon sun so the arc is always centered
- **Independent speed controls** — Run day and year animations at different speeds simultaneously

## Try these

- **Arctic Circle in June** — The observer stays entirely in the yellow (sunlit) portion of the ring. The horizon view shows the midnight sun never setting.
- **Arctic Circle in December** — The ring is entirely purple. Polar night.
- **45°N, Play Year** — Watch the yellow/purple ratio on the ring shift dramatically through the seasons while the sun arc rises and falls in the horizon view.
- **Equator at equinox vs solstice** — Nearly equal day/night year-round, but the noon sun altitude changes as it passes overhead.
- **10°N, slide through the year** — Watch the horizon view flip from facing south to facing north as the sun crosses overhead between solstices.

## How to use

Just open `index.html` in any modern web browser. No installation or build step needed.

Or visit the live version: `https://pakdenny.github.io/OrbitDaylightViz/`

## Technical notes

- Built as a single self-contained HTML file using React 18 (loaded from CDN)
- All rendering is done with HTML5 Canvas 2D — no WebGL or Three.js
- 3D orbital view uses quaternion-based camera with Shoemake's arcball rotation algorithm
- Earth's continents are defined in lat/lon coordinates and projected through a full 3D ecliptic coordinate system
- Day/night terminator uses analytical ellipse projection for correct foreshortening from any camera angle
- Solar position calculations use standard astronomical formulas for declination, hour angle, and altitude/azimuth

## License

MIT — feel free to use, modify, and share.

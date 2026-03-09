# Solar Path Explorer

An interactive visualization that shows how Earth's orbital position and axial tilt affect sunrise, sunset, and the sun's path across the sky at different latitudes — and why daylight saving time exists.

## What it does

Solar Path Explorer links two views side by side:

- **Orbital View** — A 3D view of Earth orbiting the Sun, showing axial tilt, rotating continents with longitude and latitude lines, day/night terminator, and an observer dot at your chosen latitude. Drag to rotate the view from any angle.
- **Horizon View** — What the sky looks like from the ground at that latitude, with the sun's arc across the sky, sunrise/sunset positions, and real-time sky color changes. Automatically faces toward the noon sun so the arc is always centered.

Both views update together in real time, so you can see *why* the sun behaves the way it does at any latitude and time of year.

## Features

### Orbital View
- **3D arcball camera** — Grab and rotate to examine the geometry from any perspective
- **Day/night latitude ring** — A colored ring shows the proportion of daylight (yellow) vs night (purple) at the current latitude
- **Longitude lines** — 24 meridians (one per hour/time zone) help visualize Earth's rotation
- **Latitude lines** — Equator (solid), tropics, and arctic/antarctic circles (dashed) show key geographic boundaries
- **XYZ orientation gizmo** — Centered on the Sun, shows ecliptic plane orientation
- **Depth-ordered rendering** — Sun correctly occludes Earth when behind it, with depth-faded orbit path and season markers

### Horizon View
- **Clock mode toggle** — Switch between Standard Time, DST (year-round), and Switch (US) to see how clock labels shift on the sun arc
- **Waking hours overlay** — Toggle on to highlight the 7am–10pm portion of the sun's path, showing how much daylight falls during waking hours under each DST policy
- **Auto-facing** — View automatically faces north or south based on where the noon sun actually is, handling tropical latitudes where the sun crosses overhead between seasons

### Playback & Navigation
- **Play 24H** — Animate a full day cycle with independent 1×/2×/4× speed
- **Play Year** — Animate through the seasons (snaps to solar noon on start) with independent speed control
- **Drum pickers** — Scrolling cylinder controls for time and date that wrap continuously across midnight and across the new year
- **Season snap buttons** — March Equinox, June Solstice, September Equinox, December Solstice
- **Latitude presets** — South Pole, Antarctic Circle, 45°S, Tropic of Capricorn, Equator, Tropic of Cancer, 45°N, Arctic Circle, North Pole

### Annual Sunrise/Sunset Ribbon
Three stacked charts at the bottom compare the full year's sunrise and sunset times under three DST policies:
- **Permanent Standard Time**
- **Current System (Switch)**
- **Permanent Daylight Saving Time**

Each chart shows sunrise/sunset lines with daylight fill, waking hours boundaries (7am and 10pm), and highlights the overlap between daylight and waking hours. This makes the DST tradeoffs immediately visible: permanent DST means dark winter mornings; permanent standard time means wasted summer evening light.

## Things to try

- **Equinox + slide latitude** — Snap to March Equinox, then slide latitude from pole to pole. Day length is exactly 12 hours everywhere.
- **Arctic Circle + Play Year** — Watch the latitude ring go fully yellow (midnight sun) in summer and fully purple (polar night) in winter.
- **45°N + Play Year** — Watch the day/night ratio on the latitude ring shift dramatically through the seasons while the sun arc rises and falls.
- **Tropic of Cancer + Play Year** — The noon sun passes directly overhead at the June Solstice, reaching exactly 90° altitude.
- **Equator + slide through year** — Watch the horizon view flip from facing south to facing north as the sun crosses overhead.
- **45°N + Compare DST policies** — Look at the three annual ribbons to see where each policy puts sunrise and sunset relative to your waking hours.
- **Both Play buttons at once** — Run day and year animations simultaneously to watch the sun sweep across the sky each day while the arc shifts through seasons.

## How to use

Just open `index.html` in any modern web browser. No installation or build step needed.

Or visit the live version: `https://YOUR_USERNAME.github.io/solar-path-explorer/`

## Technical notes

- Built as a single self-contained HTML file using React 18 (loaded from CDN)
- All rendering is done with HTML5 Canvas 2D — no WebGL or Three.js
- 3D orbital view uses quaternion-based camera with Shoemake's arcball rotation algorithm
- Solar azimuth uses an atan2-based formula that remains stable at all altitudes, including directly overhead (zenith)
- Polar edge cases handled explicitly: sunrise hour angle at the poles, azimuth at the poles, and equinox day length exactness
- Earth's continents, longitude lines, latitude circles, and observer ring all pass through the same 3D ecliptic coordinate system
- Day/night terminator uses analytical ellipse projection for correct foreshortening from any camera angle
- DST offset is applied purely as a clock label shift — the underlying solar time calculations never change

## License

MIT — feel free to use, modify, and share.

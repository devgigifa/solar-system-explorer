# Solar System Explorer

An interactive 2D/3D visualization of the solar system, built with HTML, CSS animations, and jQuery.

**Live demo:** https://devgigifa.github.io/SolarSystemExplorer/

## Features

- Animated orbital paths for all eight planets around the Sun, plus the Moon orbiting Earth
- Three display modes: relative **speed**, relative **size**, and relative **distance**
- A **3D mode** that links each planet to its NASA Eyes / Solar System interactive 3D model
- Responsive layout that adapts typography and panel positions across breakpoints, from narrow mobile screens up to large desktop displays
- Toggleable side panels for planet data and view controls

## Project structure

```
solar-system-explorer/
├── index.html
├── style.css
├── main.js
├── images/
│   ├── starfield-bg.png
│   ├── sun.png
│   ├── mercury.png
│   ├── venus.png
│   ├── earth.png
│   ├── mars.png
│   ├── jupiter.png
│   ├── saturn.png
│   ├── uranus.png
│   └── neptune.png
└── 
```

## Running locally

This is a static site with no build step. Any local web server works:

```bash

# Node
npx serve .
```

Then open `http://localhost:5500` in your browser.

> **Note:** `index.html` references `js/prefixfree.min.js` and `js/scripts.min.js`, which were not part of the original source files. If you have them, drop them into a `js/` folder at the project root. Without them, the page will still load (jQuery and the planet animations in `main.js` work independently), but any CSS vendor-prefixing or extra effects those scripts provided won't run.

## About the planet images

The original stylesheet embedded each planet's texture as a base64-encoded `data:image` URI directly inside the CSS. That kept everything in a single file with no extra HTTP requests, but it also meant a handful of CSS rules stretched to tens of thousands of characters each, which made the file painful to read, diff, or edit.

This version extracts those images into actual PNG files under `images/`, referenced from the CSS with normal `url(images/...)` paths. Visually nothing changes; the stylesheet just goes from ~189 KB of mostly unreadable text down to about 31 KB of normal CSS.

## Tech stack

- HTML5 / CSS3 (CSS animations, transforms, media queries)
- jQuery 1.8.1 / 2.1.3
- Vanilla JS for view-mode and 3D-link logic (`main.js`)

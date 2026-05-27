# VoxelTreeMorph

An interactive WebGL voxel tree that morphs between seasonal and botanical forms.
The whole experience lives in a single HTML file and uses Three.js from a pinned
CDN import, so there is no build step or package install.

## Features

- Procedural voxel tree rendered with Three.js instancing.
- Smooth morphs between 13 tree variations.
- Pointer-driven "explode" interaction that pushes nearby voxels away from the
  cursor and eases them back into place.
- Orbit camera with damped rotation and zoom.
- Tunable particles, falling leaves, cycle timing, morph speed, hover radius,
  hover force, and auto-rotation.
- Lightweight runtime debug API exposed at `window.__voxelTreeMorph`.

## Variations

The picker on the right side of the screen can morph the tree into:

- Maple
- Winter
- Sakura
- Bonsai
- Oak
- Fruit
- Baobab
- Mangrove
- Jacaranda
- Banyan
- Banana
- Date Palm
- Weeping Willow

## Quick Start

Open `VoxelTreeMorph.html` in a modern browser with WebGL support.

For the most reliable local run, serve the directory with any static file server:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000/VoxelTreeMorph.html
```

The app imports Three.js from jsDelivr:

```text
https://cdn.jsdelivr.net/npm/three@0.160.0/
```

You will need an internet connection unless you replace those imports with local
copies.

## Controls

Use the sliders in the top-left panel to tune the scene:

- `Particle density`: amount of drifting background dust.
- `Falling leaves`: number of animated falling leaf particles.
- `Cycle time`: delay between automatic morphs.
- `Morph speed`: duration of each transition.
- `Explode radius`: size of the pointer interaction field.
- `Explode force`: strength of the voxel displacement.
- `Rotate speed`: speed of automatic camera rotation.
- `Auto rotate`: toggles orbit auto-rotation.
- `Auto morph`: toggles automatic cycling through variations.

Mouse or trackpad:

- Move the pointer over the tree to push voxels outward.
- Drag to rotate the camera.
- Scroll to zoom.
- Click a variation button to morph immediately.

## Debug API

Open the browser console and use:

```js
window.__voxelTreeMorph.state()
window.__voxelTreeMorph.next()
window.__voxelTreeMorph.go(3)
window.__voxelTreeMorph.colorStats()
```

`go(index)` accepts the variation index shown by the button order, starting at
`0` for Maple.

## Project Structure

```text
.
├── LICENSE
├── README.md
└── VoxelTreeMorph.html
```

`VoxelTreeMorph.html` contains the markup, styles, Three.js scene setup,
procedural geometry, morph maps, controls, and animation loop.

## Browser Support

VoxelTreeMorph expects:

- WebGL-capable browser.
- ES module support.
- Import map support.
- Network access to jsDelivr for Three.js.

If the page shows a WebGL fallback message, try another browser, update graphics
drivers, or check that hardware acceleration is enabled.

## Customizing

Most customization starts in `VoxelTreeMorph.html`:

- Change default slider values in the `settings` object.
- Add or rename picker buttons in the `#picker` navigation.
- Add a new variation by creating another `make...Map()` function and assigning
  it in the `variations` array.
- Adjust camera, lighting, fog, and color grading near the top of the module
  script.

Keep the button `data-variation` values aligned with the indexes in the
`variations` array.

## License

MIT License. See `LICENSE`.

# Ripple Tank 3D

A 3D water surface you can poke. It solves the 2D wave equation on a 128 × 128 grid in the browser and colors the surface as a heatmap of its height.

**Try it:** https://jordansoohoo.github.io/FARG/ripple-tank/

## Interacting

Pick a tool, then click or drag on the water.

| Tool | What a click does |
| --- | --- |
| Drop | Makes a splash; dragging leaves a trail of ripples |
| Oscillator | Places a steady wave source (up to 8); pairs make interference patterns |
| Orbit | Rotates the view |

In Drop mode you can still orbit by dragging off the water or with the right mouse button. Scroll or pinch to zoom.

| Key | Action |
| --- | --- |
| Space | Pause / resume |
| R | Rain on / off |
| C | Calm the water |

## Settings

- **Physics:** wave speed, damping, drop radius and strength (negative strength lifts the surface), oscillator frequency, height relief
- **Edges:** reflect waves back, or absorb them in a sponge layer
- **Heatmap:** Thermal, Magma, Ocean and Spectral, or **Custom**, which blends between any two colors you pick for the trough and the crest. The heat range slider sets which heights map to the ends of the scale.
- **Scenes:** single drop, two-source interference, plane wave

## How it works

Each step updates every cell from its four neighbours with the discrete wave equation, `next = (2·h − previous + c²·∇²h) · damping`. Wave speed tops out below 1/√2 cells per step so the scheme stays stable. Rendering uses three.js.

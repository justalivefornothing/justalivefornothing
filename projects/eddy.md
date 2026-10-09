# Eddy

Paint the flow.

**TypeScript · WebGL2 · GLSL · [Source code ?](https://github.com/justalivefornothing/eddy-fluid)**

![Eddy fluid painting and simulation controls](../assets/eddy-preview.png)

An interactive fluid playground with mouse-and-touch painting, tunable presets, and shareable looks. Raw WebGL2 passes turn velocity, pressure, and dye fields into something you can manipulate directly.

## What is inside

- Semi-Lagrangian advection, vorticity confinement, pressure solving, and gradient subtraction.
- Ping-pong framebuffers, separate simulation and dye resolutions, and negotiated texture formats.
- Presets, palette controls, local PNG capture, and settings encoded in shareable URL fragments.
- Optional audio-reactive input, with explicit microphone startup and cancellation.

## Giving audio a clean lifecycle

Turning audio off cancels a pending microphone request. A stream granted after cancellation is disposed immediately; initialization failures and pending audio-context resumes also release their resources.

<details>
<summary>Verification and limits</summary>

The audio-lifecycle change passed **97 tests**, the TypeScript/Vite build, lint, and Linux/Windows Node 24 CI. Audio tests use mocked devices. This visual simulation has a lower-precision packed fallback; GPU performance varies by device and settings. The image above is an application screenshot.

</details>

[← Back to selected work](../README.md)

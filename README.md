# Towers of Hanoi in WebXR Mixed Reality

This repository presents a **WebXR mixed reality** implementation of the classic **Tower of Hanoi** puzzle, built with **Three.js** and designed for VR/MR headsets with passthrough support.

The project combines rule-based puzzle interaction with smooth object manipulation, visual feedback, themed assets, audio, and simple particle effects. According to the report, the main technical objective was to make interaction feel **fluid** rather than rigid, while also adding a distinctive visual theme and light gamification elements. fileciteturn3file1

## Project Overview

The application runs in the browser using WebXR and places a virtual Tower of Hanoi board into the user’s physical space through **local-floor** mixed reality rendering.

The implementation includes:

- a Three.js scene rendered through WebXR,
- a mixed reality passthrough-compatible renderer,
- raycast-based controller interaction,
- smooth disk manipulation using linear interpolation,
- legal/illegal move preview with a ghost disk,
- themed environment textures and audio,
- win feedback through floating star particles and victory text.

The report describes the system as a **Mixed Reality (MX)** application built with **Three.js** and the **WebXR API**, specifically targeting standard VR/MR headsets with passthrough capabilities. fileciteturn3file1

## Main Features

- Browser-based WebXR mixed reality puzzle game
- Three.js rendering with `local-floor` reference space
- Tower of Hanoi rule enforcement
- Raycast-based controller selection
- Smooth object movement using **LERP**
- Ghost-disk landing preview
- Peg highlighting for valid and invalid drops
- Themed environment textures and victory audio
- Particle-based celebration effect on win
- Responsive full-screen rendering

## Repository Structure

```text
webxr-towers-of-hanoi-mr/
├── index.html
├── script.js
├── README.md
├── WEB_REQUIREMENTS.md
└── assets/                  # optional local copies if you later move remote assets here
```

## Methodology

### 1. WebXR Scene Setup

The entry point is `index.html`, which loads `script.js` as a module and sets up a minimal full-screen canvas page for immersive rendering. fileciteturn3file0

In `script.js`, a `THREE.WebGLRenderer` is configured with:

- `alpha: true`
- `renderer.xr.enabled = true`
- `renderer.xr.setReferenceSpaceType("local-floor")`

This matches the report’s explanation that the project uses local-floor reference space and transparent rendering so the real world remains visible in passthrough mode. fileciteturn3file2turn3file1

### 2. Scene Graph and Mixed Reality Layout

The report describes a scene graph containing:

- camera
- hemisphere and directional lights
- wall and themed images
- game board base
- three pegs
- interactive disks
- XR controller with a visible ray
- ghost disk
- win text
- celebratory particles. fileciteturn3file1

The JavaScript implementation follows that structure closely, with static environment meshes, a wooden base, cylindrical pegs, and disk meshes initialized on the first peg. fileciteturn3file2

### 3. Interaction Design

The core interaction uses a **raycaster** attached to the XR controller. On `selectstart`:

- if no disk is selected, the system attempts to pick the intersected top disk,
- if a disk is already held, the system attempts to drop it on the nearest peg,
- illegal moves are rejected according to Tower of Hanoi rules. fileciteturn3file2turn3file1

### 4. Fluid Manipulation with LERP

The report states that the project’s main requirement was **fluidity**, and that rigid controller parenting was avoided in favor of linear interpolation. Each frame, the disk moves toward a target position derived from the controller using a lerp factor of `0.2`, creating a sense of drag or weight. fileciteturn3file1

This is implemented in the animation loop via:

- controller target calculation,
- `selectedDisk.position.lerp(controllerTarget, 0.2)`,
- ghost placement and peg highlighting. fileciteturn3file2

### 5. Visual and Audio Feedback

The project adds several feedback systems:

- a **ghost disk** to preview where the selected disk will land,
- peg coloring for legal and illegal targets,
- a win text banner,
- red star particles,
- a victory anthem triggered after puzzle completion. fileciteturn3file2turn3file1

The report notes that these choices were made both to improve usability and to satisfy the “eye candy” requirement of the project. fileciteturn3file1

### 6. Thematic Style

The report describes the project’s theme as a humorous “Soviet/Communism” visual style, including themed images, celebratory red stars, and anthem audio on victory. fileciteturn3file1

The code reflects this directly through externally loaded textures and the win message shown in mixed reality. fileciteturn3file2

## How to Run

Because the project uses ES module imports from the Three.js CDN, the cleanest way to run it is through a local web server.

From the project folder, run:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000/
```

For mixed reality testing, open it on a WebXR-compatible device and launch the experience from a supported browser.

## Requirements

See `WEB_REQUIREMENTS.md` for the runtime details.

At a high level, the project requires:

- a modern browser with WebXR support
- JavaScript enabled
- WebGL support
- a VR/MR headset or compatible device for immersive mode

## Notes

- The current implementation is **mixed reality / augmented reality oriented**, not a traditional VR-only scene, because it is designed around passthrough and `local-floor` placement. fileciteturn3file1turn3file2
- The code currently loads some assets from external URLs, including themed textures and the victory audio. fileciteturn3file2
- For a cleaner long-term public repo, you may want to replace remote media with local assets stored in an `assets/` folder.
- The project is best presented as a **WebXR mixed reality interaction project** rather than only as a puzzle game.

## Possible Improvements

- add hand-tracking support,
- add a move counter and timer,
- add difficulty settings with more disks,
- replace remote textures/audio with bundled local assets,
- add controller and headset compatibility notes,
- add non-immersive desktop fallback controls.

## Report

The uploaded report is included as:

- `report.pdf`

It documents the scene graph, navigation model, interaction design, the LERP-based fluid manipulation strategy, thematic choices, and performance considerations. fileciteturn3file1

## License

This repository is shared as part of a personal portfolio in WebXR, mixed reality interaction, and browser-based 3D graphics.

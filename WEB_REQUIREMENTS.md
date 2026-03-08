# Web Requirements

## Runtime
- A modern browser with WebXR support
- JavaScript enabled
- WebGL support
- A local static web server

## Recommended Hardware
- A WebXR-compatible VR/MR headset or device
- Passthrough-capable headset for the intended mixed reality experience

## External Dependencies
The project imports:

- `three.module.js` from the Three.js CDN
- `ARButton.js` from the Three.js WebXR examples CDN

These are loaded directly in `script.js`.

## Running Locally

Serve the project locally, for example with Python:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000/
```

## Notes
- Opening the HTML file directly is less reliable than serving it through a local server.
- Some assets are currently loaded from remote URLs, including themed images and the victory audio.
- Mixed reality mode depends on browser and device support for WebXR immersive AR/MR features.

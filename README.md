# AR Overlay

A camera-overlay "AR" viewer: the rear camera is the live background and an animated 3D model is drawn on top, with a shadow on an invisible floor. It's made for a **stationary device**, and there is no tracking. Runs in Safari on iOS and Chrome on Android, with no app install needed.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app (Three.js loaded from a CDN) |
| `manifest.webmanifest` | Lets it launch fullscreen from the home screen |
| `model.glb` | **Add this yourself**: your animated model. Until you do, a demo robot loads. |

## Host on GitHub Pages

1. Create a repo and upload `index.html`, `manifest.webmanifest` and `model.glb`.
2. Repo **Settings → Pages → Source: Deploy from a branch → `main` / root**.
3. Open `https://<username>.github.io/<repo>/` on the device. HTTPS is required for camera access, and Pages provides it.

## Fullscreen

- **iPhone:** open the page in Safari → Share → **Add to Home Screen**, then launch it from the icon. Safari's bars disappear.
- **Android:** tap **Fullscreen** in the panel, or use "Add to Home screen" / "Install app".

## Lining it up (do this once — settings are saved on the device)

1. Mount the device and tap **Start camera**.
2. Open **Camera match**, turn on **Show 1 m floor grid**.
3. Measure the camera's height above the floor and enter it as **Device height above floor**.
4. Adjust **Tilt down** until the grid's horizon and lines look flat on the real floor. Fix any lean with **Roll**.
5. Fine-tune **Lens field of view** so grid squares match real distances. A tape measure laid on the floor helps. For iPhone 14 Pro's main (1×) camera, start around 65–70°.
6. Turn the grid off, then place the model with **Placement**, or drag it, pinch to scale and twist to rotate.
7. Match the real light with **Lighting**: point the sun direction the same way as real shadows, then set shadow darkness and softness.
8. **Hide all** removes every control. **Double-tap** anywhere to bring them back.

**Copy settings / Paste settings** lets you back up an alignment as text.

## Model tips

- Export as **.glb** with animations included (Blender: File → Export → glTF 2.0, format "glTF Binary").
- Compress for faster loading: `npx @gltf-transform/cli optimize in.glb model.glb`. Draco and Meshopt are both supported.
- **Load model…** opens a .glb from the device for a quick test. It isn't kept after reload.

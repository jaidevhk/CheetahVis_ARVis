# AR Floor Viewer (8th Wall)

Web AR that places an animated 3D model on the real floor, with looping music and controls for position, lighting and shadows.
It runs in **plain Safari on iPhone** and Chrome on Android, with no app, App Clip or account needed.
Floor tracking is done in the browser by the free, self-hostable [8th Wall Engine](https://8thwall.org/docs/engine/overview).

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app |
| `model.glb` | **Add this yourself**: your animated model (glTF binary). Until you do, a demo robot loads. |
| `music.mp3` | **Add this yourself**: the looping music track |
| `manifest.webmanifest` | Home-screen / fullscreen launch |
| `NOTICE.md` | Licence and attribution for the 8th Wall Engine and three.js. **Keep this file.** |

## Put it on GitHub Pages

1. Create a GitHub repo and push these files, plus your `model.glb` and `music.mp3`. With GitHub Desktop: *File → Add local repository*, commit, then *Publish*.
2. In the repo, go to **Settings → Pages → Source: Deploy from a branch → `main` / `(root)`** and save.
3. After about a minute, open `https://<username>.github.io/<repo>/` on the iPhone in **Safari**. HTTPS is required for the camera, and Pages provides it.

No build step is needed. Everything loads from CDNs.

## Using it

1. Tap **Start AR** (this also starts the music). Allow camera and motion access.
2. Point at the floor and move the phone slowly side to side for a few seconds. The model previews under the centre of the screen.
3. **Tap the floor** to place it. Then:
   - one finger: drag the model across the floor
   - two fingers: pinch to scale, twist to rotate
   - double-tap: hide or show the controls

### Controls (icons on the right edge)

| Icon | Panel |
|---|---|
| Four arrows | **Position & rotation**: rotation, model height, fine nudges, gesture lock, *Place again* |
| Light bulb | **Light source**: direction, height, intensity and colour, plus ambient light, reflections and exposure. An arrow fades in on the model while you change direction or height, showing where the light comes from. |
| Ball and shadow | **Shadow**: darkness, softness |
| Play button | **Animation**: clip, play/pause, speed |
| Music note | **Music**: on/off, volume, load a track |
| Crosshair | **Tracking**: phone height above floor, *Recenter tracking* |
| Cube | **Model & settings**: load a model, copy, paste or reset settings, licence notice |
| Corner brackets | **Fullscreen** on/off (hidden on iPhone, where Safari doesn't allow it) |
| Eye | **Hide controls**: leaves a faint outline circle; tap it, or double-tap, to bring them back |

All panels are see-through so they cover as little of the camera view as possible.

### Getting the scale right

8th Wall works out real-world scale from how high the phone is above the floor. Under **Tracking → Phone height above floor**, enter the real height. About 1.4 m works for handheld use; on a tripod, measure it. Changing the height recenters tracking, so place the model again afterwards.

### Matching the shadows

Open **Light source** and adjust **Light direction**. The arrow shows where the light comes from, so line it up with the real light in the room. Then change **Light height** until the shadow length matches real objects, and finish with **Shadow → darkness / softness**.

Settings are saved on the device automatically. **Copy settings** and **Paste settings** let you back them up as text.

## Full screen

**iPad / Android:** the page goes fullscreen when you tap Start AR. The camera permission prompt may exit fullscreen; tap the **fullscreen icon** on the right edge to go back in.

**iPhone:** Safari doesn't allow web pages to go fullscreen, so it always shows its own bars. For a cleaner view, use *Share → Add to Home Screen* and launch from the icon.
Camera access from home-screen web apps works on recent iOS versions, but test it. If tracking won't start from the icon, use Safari instead.

## Limitations

- Tracking uses only the camera, not ARKit or LiDAR. It works best on textured floors in good light. Plain, glossy or dark floors can cause drift; use **Recenter** if that happens.
- No occlusion: real people or objects can't pass in front of the model.
- The 8th Wall Engine is closed-source and no longer updated. It can be used free of charge under its licence; see `NOTICE.md`.

## Testing locally

The camera needs HTTPS on a phone. The simplest test is to push to GitHub Pages. On a desktop browser, the page shows 8th Wall's "open on your phone" QR screen, which is expected.

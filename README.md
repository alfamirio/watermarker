# WebP Watermark Workspace

A lightweight, browser-based tool for applying text watermarks to images or generating standalone watermark assets, exported as WebP files. No installs, no server — open `index.html` and go.

---

## Features

- **Tiled Grid mode** — repeats the watermark across a canvas in a configurable grid pattern, great for bulk-protecting images or generating reusable watermark overlays.
- **Single Asset mode** — centers a single watermark instance on a minimal canvas, useful for logos or one-off badges.
- **Source image overlay** — optionally load a JPEG, PNG, WebP, or AVIF image; the watermark is burned on top of it.
- **Full text control** — set the phrase, font family, size, color, opacity, and rotation angle.
- **WebP export** — compile and download the result at a configurable quality level (1–100%).
- **Persistent config** — all settings are saved to `localStorage` automatically and restored on the next visit.
- **Clear config** — the red navbar button resets everything to defaults and wipes saved settings.

---

## Getting Started

1. Open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge).
2. No build step or internet connection required (Bootstrap and Bootstrap Icons load from CDN).

---

## Usage

### Tiled Grid (default)

1. Optionally load a source image with the **Source Image** picker.
2. Type your watermark text in **Text Phrase**.
3. Adjust font, size, color, opacity, and rotation to taste.
4. If no image is loaded, set **Canvas Width**, **Canvas Height**, **Gap X**, and **Gap Y** to control the output dimensions and watermark spacing.
5. If an image is loaded, only **Gap X** and **Gap Y** are available (the canvas matches the image size).
6. Click **Compile & Export to WebP** to download.

### Single Asset

1. Switch to **Single Asset** mode.
2. The canvas auto-sizes to fit the text at its current rotation.
3. Adjust settings and export as above.

---

## Configuration Reference

| Setting | Default | Description |
|---|---|---|
| Layout Mode | Tiled Grid | Tiled repeating grid or single centered instance |
| Text Phrase | `COPY` | The watermark string |
| Font Size | `50 px` | Text size in pixels |
| Opacity | `0.7` | Transparency (0 = invisible, 1 = fully opaque) |
| Text Color | `#c0c0c0` | Hex color of the watermark text |
| Rotation | `-45°` | Angle of the text in degrees |
| Font Family | Sans-Serif | Sans-Serif, Serif, Monospace, or Impact |
| Canvas Width | `1200 px` | Output width (Tiled Grid, no image) |
| Canvas Height | `1600 px` | Output height (Tiled Grid, no image) |
| Gap X | `150 px` | Horizontal spacing between watermark instances |
| Gap Y | `150 px` | Vertical spacing between watermark instances |
| WebP Quality | `85%` | Export compression quality |

---

## Persistence

Settings are saved automatically to `localStorage` under the key `wmw_config` every time a value changes. On the next visit the tool reloads exactly where you left off.

To reset to factory defaults, click the **🗑 Clear saved config** button in the top-right of the navbar and confirm. This removes the stored key and resets all fields in the current session.

---

## Browser Compatibility

| Browser | Support |
|---|---|
| Chrome / Edge 90+ | ✅ Full (native WebP export) |
| Firefox 96+ | ✅ Full |
| Safari 16+ | ✅ Full |
| Older Safari | ⚠️ WebP export may fall back to PNG |

---

## File Structure

```
index.html   — the entire application (HTML + CSS + JS, single file)
README.md    — this document
```

---

## Limitations

- Uploaded images are never sent to a server; all processing is done in-canvas in the browser.
- The tool does not persist uploaded images across sessions (only the text settings are saved).
- WebP export quality depends on the browser's canvas `toDataURL` implementation.

# WebP Watermark Workspace

A lightweight, browser-based tool for applying text watermarks to images, blurring sensitive regions, or generating standalone watermark assets. No installs, no server — open `index.html` and go.

---

## Features

- **Tiled Grid Mode** — Repeats the watermark across a canvas in a configurable grid pattern, great for bulk-protecting images or generating reusable watermark overlays.
- **Single Asset Mode** — Centers a single watermark instance on the canvas, useful for logos, one-off badges, or clean assets.
- **Batch Processing** — Load multiple files simultaneously. Preview individual files via pagination and export everything bundled into a single ZIP file.
- **Interactive Censor Regions** — Toggle "Draw" mode to visually paint over sensitive areas (faces, IDs, metadata) directly on the preview to apply a Gaussian blur before exporting.
- **Advanced Control over Assets** — 
  - Convert source images to grayscale (Black & White).
  - Scale/resize images instantly prior to watermark rendering.
  - Wrap text lines based on explicit bounding pixel rules to prevent ugly line cutoffs.
- **Multi-Format Export Compiler** — High-performance native conversion into **WebP**, **PNG**, **JPG**, **AVIF** (where browser supported), or single-page high-fidelity **PDFs** powered by `pdf-lib`.
- **Persistent Config** — All parameters and sliders save to `localStorage` automatically and gracefully restore on your next visit.

---

## Getting Started

1. Open `index.html` in any modern web browser (Chrome, Firefox, Safari, Edge).
2. No build steps, servers, or internet connections are strictly required (external CSS and JS libraries bundle via high-availability CDNs).

---

## Usage

### Tiled Grid (Default)

1. Optionally load one or multiple source images with the **Source Image(s)** picker.
2. Select a **Layout Mode** (Tiled or Single). Enable **AutoFit** to avoid text overlap collisions dynamically.
3. When an image is loaded, toggle **B&W** for grayscale output and adjust **Resize %** to scale before watermarking.
4. Type your watermark text in **Phrase** and adjust font, size, color, opacity, wrap width, and rotation.
5. Optionally configure stroke width, color, and opacity inline with the text controls.
6. If no image is loaded, adjust **Width**, **Height**, **Gap X**, and **Gap Y** to control the absolute structural dimensions of the output asset.
7. Click **Compile & Export** (or **Watermark All & Download ZIP** for batches).

### Drawing Censored Blurs

1. Upload an image — the **Censor** section appears automatically.
2. Click the yellow **Draw** button to enter draw mode, then click and drag over the live preview canvas to mark regions.
3. Adjust blur strength with the **Blur px** slider.
4. Remove individual regions using their red delete (`X`) buttons.

---

## Configuration Reference

| Setting | Default | Description |
|---|---|---|
| Layout Mode | Tiled | Tiled repeating pattern or single centered asset |
| AutoFit | `On` | Automatically adjusts gap to prevent watermark tile overlap |
| B&W | `Off` | Converts source image to grayscale before watermarking |
| Resize (%) | `100` | Scales source image dimensions before watermark rendering |
| Text Phrase | `COPY` | The watermark text string |
| Font | `Sans-Serif` | Typeface applied to the watermark |
| Size | `30` | Font size in pixels |
| Color | `#c0c0c0` | Fill color of the watermark text |
| Opacity | `0.5` | Fill transparency (0 = invisible, 1 = solid) |
| Rotation | `-45°` | Watermark angle in degrees |
| Wrap px | `200` | Line-wrap threshold in pixels (0 disables wrapping) |
| St. Width | `1` | Stroke outline width in pixels |
| St. Color | `#000000` | Stroke outline color |
| St. Opacity | `1` | Stroke outline transparency |
| Blur px | `25` | Gaussian blur strength applied inside censor regions |
| Output Format | `image/webp` | Export format: WebP, PNG, JPG, AVIF, or PDF |
| Quality | `85%` | Compression ratio for lossy formats (WebP, JPG, AVIF) |

---

## Architecture & Dependency Footprint

This single-page client app works entirely on the frontend without server-side processing. It builds atop standard browser Canvas interfaces and integrates external modules via scripts:
- **Bootstrap 5.3.3 & Icons** — UI presentation shell styling.
- **JSZip 3.10.1** — Client-side multi-file compression and ZIP packaging.
- **pdf-lib 1.17.1** — Vector context generation converting canvas output to production PDFs.

---

## Persistence

Settings save automatically to `localStorage` under the key `wmw_config` every time an input field changes. To restore all settings to factory defaults, click the red **🗑 Clear saved config** button in the navigation bar.

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
2. Type your watermark text in **Text Phrase**.
3. Adjust font, size, color, opacity, text wrapping width, and rotation angle.
4. Toggle **Auto-fit Gap** to automatically shift grids and avoid text overlap collisions dynamically.
5. If no image is loaded, adjust **Width**, **Height**, **Gap X**, and **Gap Y** to control the absolute structural dimensions of the output asset.
6. Click **Compile & Export** (or **Watermark All & Download ZIP** for batches).

### Drawing Censored Blurs

1. Upload an image and click the yellow **Draw** button under the Censor Regions section.
2. Click and drag anywhere directly over the live preview canvas to establish a box.
3. Modify the blur threshold dynamically via the **Blur Strength** slider.
4. Remove unwanted bounding boxes instantly using the individual red delete buttons (`X`).

---

## Configuration Reference

| Setting | Default | Description |
|---|---|---|
| Layout Mode | Tiled Grid | Tiled repeating pattern layout or single centered asset instance |
| Convert to BW | `Off` | Strips chrominance details out of source images to render greyscale |
| Resize (%) | `100` | Adjusts absolute pixel matrix scale dimensions safely |
| Blur Strength | `15px` | Radial blur strength footprint applied directly inside drawn regions |
| Text Phrase | `COPY` | The signature watermark value string |
| Font Size | `30` | Typographical scaling factor footprint size |
| Opacity | `0.5` | Alphachannel density threshold parameter (0 = invisible, 1 = solid) |
| Rotation | `-45°` | Radial positioning matrix angle tracking factor degrees |
| Wrap At (px) | `200` | Bounding constraints forcing multi-line breaks (0 turns wrapping off) |
| Output Format | `image/webp` | Selection handler: WebP, PNG, JPG, AVIF, or Document PDF format |
| Quality | `85%` | Compression ratio slider applicable to lossy targets (WebP/JPG/AVIF) |

---

## Architecture & Dependency Footprint

This single-page client app works entirely on the frontend without server-side processing. It builds atop standard browser Canvas interfaces and integrates external modules via scripts:
- **Bootstrap 5.3.3 & Icons** — UI presentation shell styling.
- **JSZip 3.10.1** — Client-side bulk processing multi-file compression packaging.
- **pdf-lib 1.17.1** — Vector context generation wrappers converting layout configurations to production PDFs.

---

## Persistence

Settings save automatically to `localStorage` under the key `wmw_config` every time an entry fields changes. To restore configurations cleanly back to factory states, hit the red **🗑 Clear saved config** utility inside the navigation navbar header.

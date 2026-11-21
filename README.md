# Relief Slicer

A single-page, fully client-side tool that slices a greyscale image into a stack of
binary layers for layered relief printing.

**Use it:** open `index.html` (or the GitHub Pages deployment). Everything runs in the
browser — images never leave your machine.

- Upload → crop/rotate → set physical size (mm) and X/Y DPI (default 1200×1200) → shape
  the calibration curve (gamma + black/white points) → set layer count → generate.
- Mapping: **black pixel = printhead ON**. Brightest source areas print on the most
  layers (`round(v×N)`), so `image_0001` is mostly black and the final layer is almost
  entirely white.
- Output: `image_0001.png … image_NNNN.png` (bottom layer first) + `manifest.json` +
  human-readable `settings.txt`, zipped. Drop a previous ZIP back onto the page to
  restore its settings exactly.

No build step, no server, no dependencies beyond two CDN libraries (Cropper.js, JSZip).

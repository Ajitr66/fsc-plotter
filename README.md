# FSC Plotter

A single-file, in-browser plotter for cryoSPARC Fourier Shell Correlation (FSC) exports.
Drop an `FSC.txt` file onto the page to get publication-ready FSC curves and a table of
resolutions at the 0.5 and 0.143 crossings. Nothing is uploaded; all parsing happens locally.

**Try it:** https://ajitr66.github.io/fsc-plotter/

![FSC Plotter screenshot](docs/screenshot.png)

## Usage

1. Open [`fsc_plotter.html`](fsc_plotter.html) in any modern browser (or use the link above).
2. Drag in a cryoSPARC FSC export (`.txt`), or click the drop zone to browse.
3. Click curves to show or hide them, pick the curve that sets the title resolution,
   and choose a color scheme.
4. Export the plot as PNG or SVG.

## Features

- Plots all FSC curves in the export (No Mask, Spherical, Loose, Tight/Auto-tight, Corrected, …)
- Optional 0.5 and 0.143 threshold lines
- Resolution table at first and last crossings for each curve
  (first 0.143 crossing matches what cryoSPARC reports)
- Color schemes, including the cryoSPARC default
- PNG and SVG export

## Example data

The [`examples/`](examples) folder has a cryoSPARC FSC export to try:

| File | Format |
| --- | --- |
| [`fsc_with_frequency.txt`](examples/fsc_with_frequency.txt) | Key row + label row, includes a `frequency` column |

## License

MIT, see [LICENSE](LICENSE).

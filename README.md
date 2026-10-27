# FSC Plotter

A single-file, in-browser plotter for cryoSPARC Fourier Shell Correlation (FSC) exports.
Drop an `FSC.txt` file onto the page to get publication-ready FSC curves and a table of
resolutions at the 0.5 and 0.143 crossings. Nothing is uploaded; all parsing happens locally.

**Try it:** https://ajitr66.github.io/fsc-plotter/

![FSC Plotter screenshot](docs/screenshot.png)

## Usage

1. Open [`fsc_plotter.html`](fsc_plotter.html) in any modern browser (or use the link above).
2. Drag in a cryoSPARC FSC export (`.txt`), or click the drop zone to browse.
   If the file has no `frequency` column, you'll be asked for the box size (px) and
   pixel size (Å/px) so frequency can be computed as `wave_number / (box × pixel size)`.
3. Click curves to show or hide them, pick the curve that sets the title resolution,
   and choose a color scheme (or **Custom** to set each curve's color and line style).
4. Export the plot as PNG or SVG.

## Features

- Reads both cryoSPARC export layouts: with a `frequency` column, or `wave_number` only
- Plots all FSC curves in the export (No Mask, Spherical, Loose, Tight/Auto-tight, Corrected, …)
- Optional 0.5 and 0.143 threshold lines
- Resolution table at first and last crossings for each curve
  (first 0.143 crossing matches what cryoSPARC reports)
- Color schemes, including the cryoSPARC default, plus a Custom mode with a color picker
  and line style (solid, dashed, dotted, dash-dot) for each curve
- X-axis tick options (even spacing with rounded, true-position, or precise labels)
- PNG and SVG export

## Example data

The [`examples/`](examples) folder has one file in each cryoSPARC export layout:

| File | Format |
| --- | --- |
| [`fsc_with_frequency.txt`](examples/fsc_with_frequency.txt) | Key row + label row, includes a `frequency` column |
| [`fsc_wave_number_only.txt`](examples/fsc_wave_number_only.txt) | Key row only, `wave_number` with no `frequency` (prompts for box and pixel size) |

## Changelog

- **v1.2**: Custom color scheme with per-curve color and line style, seeded from the last preset.
- **v1.1**: Support for `wave_number`-only exports (box/pixel size prompt and scale panel),
  curve labels inferred from column keys, `_raw` columns hidden by default, x-axis tick options.
- **v1.0**: First release. Parses exports with a `frequency` column.

## License

MIT, see [LICENSE](LICENSE).

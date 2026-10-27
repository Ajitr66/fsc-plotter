# FSC Plotter: 0.143 and 0.5 FSC resolution for masked and unmasked cryo-EM maps

**Get the FSC = 0.143 and FSC = 0.5 resolution for every masked and unmasked curve in a
cryoSPARC FSC export.** FSC Plotter reads a cryoSPARC `FSC.txt` file and reports the
gold-standard FSC (GSFSC) resolution at the 0.143 and 0.5 thresholds for the unmasked
(No Mask) curve and each masked curve: Spherical, Loose, Tight, Auto-tight and Corrected.
It also plots publication-ready Fourier Shell Correlation curves.

It runs entirely in your browser as a single HTML file. Nothing is uploaded and nothing needs installing.

**Try it:** https://ajitr66.github.io/fsc-plotter/

![FSC Plotter showing cryo-EM FSC curves and a table of 0.143 and 0.5 resolutions for masked and unmasked curves](docs/screenshot.png)

## 0.143 and 0.5 FSC crossings for masked and unmasked curves

Drop in an FSC export and the results table lists, for **every curve**, the resolution (Å)
where the FSC crosses each threshold:

| Column | What it means |
| --- | --- |
| **0.143 first** | First shell where the FSC drops below 0.143. This is the gold-standard resolution cryoSPARC reports. |
| **0.143 last** | Last 0.143 crossing, which shows whether the curve dips and recovers |
| **0.5 first** | First 0.5 crossing, often used for map-vs-model FSC or as a conservative estimate |
| **0.5 last** | Last 0.5 crossing |

Rows cover the unmasked curve and all masked curves in the file:

- **No Mask**: unmasked half-map FSC
- **Spherical Mask**, **Loose Mask**, **Tight Mask**, **Res Mask**
- **Auto-tight Mask** and **Auto-tight Mask, corrected** (noise-substitution corrected FSC)
- Phase-randomized curves, if you tick *Include hidden columns*

Resolutions are linearly interpolated in spatial frequency (1/Å) between the two shells
either side of the threshold, then converted to Å. The 0.143 first crossing matches
the value cryoSPARC reports. The plot title shows the GSFSC resolution in cryoSPARC's format
(`GSFSC Resolution: 3.42Å`). By default it uses the best curve, and you can pin it to a specific mask.

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
- 0.143 and 0.5 FSC resolution (first and last crossing) for masked and unmasked curves
- Optional 0.5 and 0.143 threshold lines on the plot
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

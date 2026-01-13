# AFM XYZ Nanohole Analyzer

AFM XYZ Nanohole Analyzer is a MATLAB App Designer application for quantitative,
profile-based dimensional analysis of nanoholes from AFM height maps stored in
`.xyz` format.

The app provides an interactive yet largely automated workflow to extract
nanohole depth, outer diameter, and inner diameter using physically meaningful
definitions along both horizontal and vertical directions.

---

## Features

- Load AFM height maps from text-based `.xyz` files
- Visualize AFM data as a 2D height map
- Draw rectangles around individual nanoholes
- Undo the most recent rectangle using **Ctrl + Z**
- Automatically locate the nanohole minimum within each rectangle
- Extract horizontal and vertical cross-section profiles through the nanohole center
- Automatic detection of:
  - Outer ring walls
  - Inner ring walls
  - Ring peaks
  using derivative-based logic (robust to low-resolution data)
- Optional Z-value smoothing (Savitzky–Golay filter)
- Compute the following quantities for each nanohole:
  - Center-of-mass (COM) diameter
  - Peak-to-peak diameter
  - Inner diameter (wall-to-wall)
  - Nanohole depth
- Export results to Excel and PNG
- Automatically overwrite existing output files to ensure clean results

---

## Input format

The input file must be a text-based AFM `.xyz` file with three columns:

- **X**: lateral coordinate (m)
- **Y**: lateral coordinate (m)
- **Z**: height value (m)

Additional notes:
- Comment lines starting with `#` are supported
- The file is assumed to represent a regular rectangular grid

---

## How to run

1. Open MATLAB
2. Ensure `afmxyznanoholeanalyzer.mlapp` is on the MATLAB path
3. Launch the app by typing:
   afmxyznanoholeanalyzer

---

## Workflow

1. Click **Enter AFM .xyz file** to load the AFM height map.
2. (Optional) Click **Smooth Z values** to enable Savitzky–Golay smoothing for noisy data.
3. Click **Draw Rectangle** and draw a rectangle tightly around a single nanohole.
4. For each rectangle, the app automatically:
   - Finds the nanohole center by locating the minimum Z value
   - Extracts horizontal and vertical profiles through the center
   - Detects outer walls, inner walls, and peak locations using derivative logic
   - Builds interpolated wall profiles
   - Computes all diameters and depth
5. Repeat rectangle selection for all nanoholes in the image.
6. Use **Ctrl + Z** at any time to undo the most recently drawn rectangle.
7. Click **Done** to export all results.

---

## Output

### Excel file (`*_dimension_analysis.xlsx`)

For each nanohole, the following quantities are exported (in nanometers):

- Vertical diameter (center-of-mass)
- Horizontal diameter (center-of-mass)
- Vertical diameter (peak-to-peak)
- Horizontal diameter (peak-to-peak)
- Vertical inner diameter
- Horizontal inner diameter
- Nanohole depth

The Excel file also includes:
- Mean values
- Standard deviations
- Mean ± standard deviation

If the output file already exists, it is deleted and recreated to guarantee a
clean export without residual data or formatting.

---

### Image file (`*_nanohole_numbering.png`)

- AFM height map with all analyzed nanoholes
- Red rectangles indicating nanohole selection regions
- Automatic numbering corresponding to Excel table rows
- Nanohole center markers are intentionally omitted in the final export

---

## MATLAB requirements

- MATLAB R2021a or newer (recommended)
- App Designer
- No additional toolboxes required

Platform notes:
- On Windows systems, Excel COM automation is used to insert formulas
- On macOS and Linux systems, statistics are written as static numeric values

---

## Notes

- Designed for expert-guided but reproducible nanohole analysis
- Suitable for asymmetric, shallow, or noisy nanohole geometries
- Derivative-based detection avoids reliance on fixed slope thresholds
- All computation is implemented directly within the App Designer application
- No external dependencies beyond standard MATLAB functionality

\# AFM XYZ Nanohole Analyzer



AFM XYZ Nanohole Analyzer is a MATLAB App Designer application for quantitative

dimensional analysis of nanoholes from AFM height maps stored in `.xyz` format.



The app provides an interactive workflow to extract nanohole depth and diameter

(using both center-of-mass and peak-to-peak definitions) along horizontal and

vertical directions.



---



\## Features



\- Load AFM height maps from `.xyz` files

\- Visualize AFM data as a 2D height map

\- Draw rectangles around individual nanoholes

\- Automatically locate nanohole minima

\- Extract horizontal and vertical cross-section profiles

\- Manual selection of 6 reference points per direction

\- Compute:

  - Center-of-mass (COM) diameter

  - Peak-to-peak diameter

  - Nanohole depth

\- Export results to Excel and PNG



---



\## Input format



The input file must be a text-based AFM `.xyz` file with three columns:



\- X, Y: lateral coordinates

\- Z: height values

\- Comment lines starting with `#` are supported



---



\## How to run



1\. Open MATLAB

2\. Make sure `afmxyznanoholeanalyzer.mlapp` is on the MATLAB path

3\. Launch the app:

   ```matlab

   afmxyznanoholeanalyzer



---



\## Workflow



1\. Click \*\*Enter AFM .xyz file\*\* to load the AFM height map

2\. Draw a rectangle around a nanohole

3\. For the selected nanohole:

   - Horizontal and vertical profiles are displayed

   - Select \*\*6 points per direction\*\*:

     - lower boundary

     - peak (maximum)

     - upper boundary

     - for two opposing rings

4\. Click \*\*Done\*\* to store the nanohole dimensions

5\. Repeat for all nanoholes

6\. Click \*\*Done\*\* again to export results



---



\## Output



\### Excel file (`\\\*\\\_dimension\\\_analysis.xlsx`)



For each nanohole:

\- Vertical diameter (COM) \[nm]

\- Horizontal diameter (COM) \[nm]

\- Vertical diameter (peak-to-peak) \[nm]

\- Horizontal diameter (peak-to-peak) \[nm]

\- Depth \[nm]



The file also includes:

\- Mean

\- Standard deviation

\- Mean ± standard deviation



\### Image file (`\\\*\\\_nanohole\\\_numbering.png`)



\- AFM height map with numbered nanoholes and rectangle outlines



---



\## MATLAB requirements



\- MATLAB R2021a or newer (recommended)

\- App Designer

\- No additional toolboxes required



> On Windows, Excel COM automation is used for statistics.

> On macOS/Linux, statistics are written as static values.



---



\## Notes



\- Designed for manual, expert-guided nanohole analysis

\- Suitable for asymmetric or noisy nanohole geometries

\- All computation is implemented directly in the App Designer application


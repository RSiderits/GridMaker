# GridMaker
HTML interface for quick custom grids for laser and CNC spoil boards. 

Precision Grid Generator

Version 3 Platform Registration

A standalone, browser-based utility for generating dimensionally accurate, customizable metric grids, concentric targeting patterns, and right-angle registration marks for laser engraving, CNC machining, workpiece alignment, and positioning fixtures.

The application generates scalable vector graphics (SVG) using millimeter-based geometry rather than raster images. No installation, internet connection, external libraries, or server is required.
Features
- Custom grid width and height, up to 2,000 mm per axis.
- Adjustable major and optional minor grid spacing.
- Adjustable major line thickness and color.
- Numbered metric axes with selectable Y-axis numbering direction.
- Optional center crosshair and up to 100 concentric circles with adjustable radial spacing and line thickness.
- Independent or symmetrical right-angle platform registration marks.
- Registration positions and arm lengths specified in millimeters or percentages of the corresponding grid axis.
- External registration marks with automatic expansion of the drawing area, without rescaling the grid.
- Live preview, dimensional readouts, and validation messages.
- SVG export, actual-size printing, and PDF output through the browser print dialog.
- Optional 50 mm calibration reference and reset-to-defaults control.
Getting started
1. Download [`Precision_Grid_Generator_v3.html`](Precision_Grid_Generator_v3.html) from this repository (open the file on GitHub and use Download raw file, or download the repository as a ZIP).
2. Save the HTML file to your computer.
3. Open it in a modern desktop browser, such as Chrome or Edge.
4. Adjust the controls in the left panel. The preview updates automatically.
5. Select Export SVG or Print actual size / Save PDF.
No build process, package manager, or administrator privileges are needed.
Default configuration
Parameter	Default
Grid width (X)	150 mm
Grid height (Y)	130 mm
Major spacing	10 mm
Minor spacing	5 mm (hidden by default)
Major line thickness	0.25 mm
Center	(75, 65) mm
Concentric circles	5
Radial spacing	10 mm
Circle line thickness	0.40 mm
Registration mode	Symmetrical
X and Y registration offsets	−10 mm each
Horizontal and vertical registration arms	20 mm each
Registration line thickness	1 mm
Registration color	Red
Registration footprint	170 × 150 mm
Calibration reference	50 mm, enabled


Platform registration:

Registration marks are L-shaped, 90-degree references designed to help align a printed grid with a movable platform or fixture. Marks can be placed beyond the grid so that they remain visible around the platform, provided the platform does not cover them.
Coordinate system
Registration coordinates are measured from the lower-left grid origin (0, 0). X increases to the right and Y increases upward. This convention remains unchanged even when the displayed Y-axis numbering is reversed.
Offset	Meaning in symmetrical mode
Positive	Inset from the grid boundary
Zero	On the grid boundary
Negative	Outside the grid boundary


In independent mode, negative coordinates place a vertex left of or below the grid; coordinates greater than the grid width or height place it right of or above the grid.
Symmetrical mode
Four mirrored corners define a rectangular footprint. For grid width W, height H, and offsets x and y, the footprint is:
- Width = W − 2x
- Height = H − 2y
For the default 150 × 130 mm grid and offsets of −10 mm, the four vertices are:
Corner	X (mm)	Y (mm)
Lower left	−10	−10
Lower right	160	−10
Upper left	−10	140
Upper right	160	140


The resulting 170 × 150 mm footprint surrounds the original grid without changing its scale. To match a centered platform of known width P and height Q, enter x = (W − P)/2 and y = (H − Q)/2.
Independent mode
Use Add reference corner to create individual marks. Each mark has its own visibility, position, horizontal and vertical arm lengths, thickness, color, and orientation (right/up, left/up, right/down, or left/down). Use Delete corner to remove unwanted marks.
Percentage-based positioning
Position units and arm length units can be selected separately. Horizontal percentages are calculated from grid width; vertical percentages are calculated from grid height. For example, on a 150 × 130 mm grid, an X offset of −10% equals −15 mm and a Y offset of −10% equals −13 mm. Changing units reinterprets the entered numbers; it does not automatically convert them.
Concentric targeting patterns
Circles are centered at (W/2, H/2). Circle number n has radius n × radial spacing. The default radii are 10, 20, 30, 40 and 50 mm. Circles extending beyond the grid are clipped to its boundaries. The center crosshair can be enabled independently.
Printing and dimensional verification
1. Select Print actual size / Save PDF.
2. Choose a paper size and orientation large enough for the complete drawing, including external marks, labels, calibration bar and printer margins.
3. Set scale to 100% or Actual size. Disable fit-to-page, shrink-to-fit, and browser headers and footers.
4. Print the drawing or select the browser's Save as PDF destination.
5. Measure the 50 mm calibration reference with a ruler or caliper. Also verify a known vertical grid interval and the full grid width and height before using the print as a positioning template.
The on-screen preview is responsive and is not intended to be physically life-size. SVG geometry is defined in millimeters, but physical output accuracy depends on browser settings, printer calibration, media, and downstream software. Large drawings may require larger paper or external tiling software; automatic tiled printing is not implemented.
SVG export
Select Export SVG to save the current drawing as Grid_<width>x<height>mm.svg. The SVG includes explicit physical dimensions, a matching viewBox, and the visible grid, labels, circles, registration marks and calibration reference. The drawing also includes a white background rectangle.

Import the file into compatible vector or laser software and verify the imported dimensions before use. If preparing engraving paths, inspect the imported background, text, and other elements and remove anything not intended for processing. The application does not generate G-code or control a laser or CNC machine.
Example applications
- Laser platform alignment and repeatable fixture positioning.
- CNC spoilboard and workpiece registration templates.
- Center finding and concentric positioning patterns.
- Metric reference grids for photography, microscopy, and workshop measurements.
- Custom layout and calibration templates.
Technical details and limitations
The application consists of a single HTML file containing CSS and vanilla JavaScript. SVG elements are generated dynamically from numeric inputs. No external dependencies or network requests are required. Settings are held in the current browser session and are not automatically saved across reloads. Exported SVGs are drawings, not editable application configuration files.

This is a layout aid, not a certified metrology instrument or machine-control system. Verify physical dimensions and alignment before operating equipment. Follow the equipment manufacturer's safety procedures.
Contributing
Suggestions, bug reports and improvements are welcome through GitHub Issues and pull requests. When reporting a dimensional or printing issue, include the browser, operating system, grid settings, output format, print scaling and measured dimensions.
License

No license, free to all 

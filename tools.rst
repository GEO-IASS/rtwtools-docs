List of tools
=============

LISA
----

Create Getis Image
^^^^^^^^^^^^^^^^^^
Calculates Getis-Ord statistics for every band of the input file, with a configurable window size.

Input
......

ENVI supported image (can be multiband)

Parameters
..........

* Size of moving window (d value in the Getis formula)

Output
......

Image with each band containing the Getis image for the corresponding band in the input file.


Create CV Image
^^^^^^^^^^^^^^^
Calculates the Coefficient of Variation in a moving window across the image, for each band of the image. The moving window size is configurable.

Input
.....

ENVI supported multi-band image

Parameters
..........

* Size of moving window

Output
......

Multi-band image with each band containing the CV values for the corresponding band in the input file

DEMs
----

Select NeXTMap tiles
^^^^^^^^^^^^^^^^^^^^

Selects the DEM tiles from the NeXTMap project (NEODC, 2009) which are needed to cover an image. Can take an input from either a georeferenced image, a set of corner co-ordinates for an image, or the bottom left co-ordinates and length/width of an image.

Input
.....

Image co-ordinates (from one of the above options)

Output
......

List of NeXTMap tiles needed to cover the image.

Calculate Surface Area
^^^^^^^^^^^^^^^^^^^^^^

Calculates an estimate of the 3D surface area of a DEM using the Jenness (2004) method.

Input
.....

DEM with associated map information including pixel size

Output
......

New image band containing a ‘surface area image’ (similar to the slope and azimuth images created by the ENVI Topographic Modelling command) where the value of each pixel is the surface area of that pixel.

Calculate Surface Area Ratio
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Calculates the ratio of 3D surface area to planimetric surface area, which is useful for estimating the topographic roughness of an area.

Input
.....

* Surface Area image
* One or more ROIs

Output
......

Table showing the ratio for each of the selected ROIs

ROI Tools
---------

ROI Percentile Threshold
^^^^^^^^^^^^^^^^^^^^^^^^

Performs similarly to the Band Threshold to ROI function in ENVI, but allows the threshold to be specified as a percentage to be taken from the top or bottom of the range of values. Allows constraints (such as ensuring the resulting values are above zero) to be applied to the pixels selected.

Input
.....
ENVI supported multi-band image

Parameters
..........

* ROI Name
* Percentage - the percentage to be taken from the top or bottom. For example, 0.3 takes the top or bottom 0.3%.
* Top/Bottom – the end of the data from which to take the threshold
* Constraints – No constraint, Ensure above zero (ensures that all resulting pixels have values greater than zero), Ensure below zero (ensures that all resulting pixels have values less than zero).

Output
......

ROI containing all the points which satisfy the threshold and the constraints across all bands (ie. not done on each band individually).

Shrink ROIs
^^^^^^^^^^^
Shrinks the selected ROIs by one pixel around their perimeter. NB: This routine creates new ROIs and does not overwrite the old ROIs.

Input
.....

One or more ROIs

Output
......

The same number of ROIs selected as input, each shrunk by one pixel around their circumference.

Translate ROIs
^^^^^^^^^^^^^^
Translates the selected ROIs by the given X and Y distances. NB: This routine creates new ROIs and does not overwrite the old ROIs.

Input
.....

One or more ROIs

Parameters
..........

* X translation distance
* Y translation distance

Output
......

The same number of ROIs selected as input, each translated by the distances given.

ROI Statistics
^^^^^^^^^^^^^^
Calculates statistics such as sum, mean and max on the data covered by a ROI.

Input
.....

One or more ROIs attached to an image

Parameters
..........

* Statistic to calculate, from the following list:
  * Sum
  * Mean
  * Median
  * Standard Deviation
  * Minimum
  * Maximum

Output
......

Results of the statistics presented in onscreen in text format.


Spectral Libraries
------------------

Calculate Percentage Difference (BETA)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Calculates the percentage difference between two spectral libraries. NB: The spectral libraries must contain the same number of spectra, and the spectra to be compared must be in the same order so that the same spectra are compared from each file.

Input
.....

A base spectra library; A comparison spectral library

Output
......

Text printed to the IDL log window showing average differences for each band and each spectra set, and the raw data.

Misc
----

Create GLT file
^^^^^^^^^^^^^^^

Creates an image which can be used as a GLT file for the atmospheric correction software ATCOR. See use cases at the end of this manual for more information. With the default options this routine creates two files as shown below.

**Columns Image**::

	1 2 3 4 5 6 7 8 9 10 ... n
	1 2 3 4 5 6 7 8 9 10 ... n
	1 2 3 4 5 6 7 8 9 10 ... n
	...

**Rows Image**::

	1 1 1 1 1 1 1 1 1 1 ... 1
	2 2 2 2 2 2 2 2 2 2 ... 2
	3 3 3 3 3 3 3 3 3 3 ... 3
	...
	n n n n n n n n n n ... n

The parameters allow the ordering of numbers in the X and Y directions to be reversed (ie. n ... 5 4 3 2 1).

Parameters
..........

* X and Y dimensions of the output image
* Base filename for the output image
* Ordering option

Output
......

Two output files, named with the base filename with ``_RowIndices`` or ``_ColIndices`` appended.

Output band to CSV
^^^^^^^^^^^^^^^^^^

Outputs the selected image band to a CSV file.

Input
.....

Band of an ENVI image file

Parameters
..........

* Filename for the CSV output

Output
......

CSV file containing the DNs from the ENVI image file band
#### Digital Elevation Model file (`.dem`)

This file contains the topographical data, or digital elevation model (DEM) which also defines the computational grid. The file should be in [Esri ASCII raster format](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm) which contains the first six rows as header section, followed by a space delimited 2D array of numerical values defining the data points on the computational grid. An example snapshot of the file is shown below.

![image](/Figures/mesh1.PNG)

The header section contains the following informtation:

- `ncols`: Number of cell columns (i.e. number of cells in X direction)

- `nrows`: Number of cell rows (i.e. number of cells in Y direction)

- `xllcorner`: X cartesian coordinate of the lower left corner of the grid in metres

- `yllcorner`: Y cartesian coordinate of the lower left corner of the grid in metres

- `cellsize`: Cell size in metres

- `NODATA_value`: Null value (Default is -9999)


This file can be manually edited using any simple text editor. However, to visualize or manipulate the DEM data, it is advised to use QGIS, a geographic information system platform, which is [freely available to download](https://www.qgis.org/en/site/forusers/download.html). An example of how to visualize and manipulate the DEM data using QGIS is demonstrated for the Merewether case study in [_Preparing the input data_](/Merewether1-2.md). 


[back](/Merewether1.md)

#### Digital Elevation Model file (`.dem`)

This file contains the topographical data or digital elevation model (DEM) which also defines the extent and the resolution of the computational grid. The file must be in [Esri ASCII raster format](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm), which contains the first six rows as header section followed by a space-delimited 2D array of numerical values defining the data points on the computational grid. An example screenshot of the file format is shown below.

![image](/Figures/mesh1.PNG)

The header section contains the following information:

- **`ncols`.** Number of cell columns (i.e. number of computational cells in X direction)

- **`nrows`.** Number of cell rows (i.e. number of computational cells in Y direction)

- **`xllcorner`.** X coordinate of the lower left corner of the computational 2D domain in metres

- **`yllcorner`.** Y coordinate of the lower left corner of the computational 2D domain in metres

- **`cellsize`.** Cell size in metres (modelling resolution for square computational cells) 

- **`NODATA_value`.** Null value (Default is -9999)


Though this file can be manually edited using any simple text editor, it is advised to use QGIS, a geographic information system platform, to visualise or manipulate the DEM data file. 

QGIS is [freely available to download](https://www.qgis.org/en/site/forusers/download.html) and an example of how to use it to visualise and manipulate the DEM data file for the Merewether case study is provided in [_"Preparing the input data"_](/Merewether2.md). 


[back](/Merewether1.md)

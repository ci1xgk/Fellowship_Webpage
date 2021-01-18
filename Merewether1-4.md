#### Digital Elevation Model file (`.dem`)

LISFLOOD uses topographical data, or digital elevation model (DEM), in Esri ASCII raster format. This file contains the first six rows as header section, followed by a space delimited matrix of `nrows` x `ncols` defines the size of the computational domain (an example snapshot of the file is shown below).

![image](/Figures/mesh1.PNG)

The header section contains the following informtation:

- `ncols`: Number of columns

- `nrows`: Number of rows

- `xllcorner`: X cartesian co-ordinate of the lower left corner of the grid in metres

- `yllcorner`: Y cartesian co-ordinate of the lower left corner of the grid in metres

- `cellsize`: Cell size in metres

- `NODATA_value`: Null value


To visualize or manipulate the DEM data, it is advised to use QGIS, a geographic information system platform, which is [freely available to download](https://www.qgis.org/en/site/forusers/download.html). 


[back](/Merewether1.md)

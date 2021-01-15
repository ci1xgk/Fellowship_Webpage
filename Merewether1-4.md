# Digital Elevation Model file (`.dem`)

LISFLOOD uses topographical data, or digital elevation model (DEM), in Esri ASCII raster format. This file contains the first six rows as header information, followed by a space delimited matrix of nrows x ncols defines the size of the computational domain (an example snapshot of the file is shown below).

![image](/Figures/mesh1.PNG)

The header section contains the following informtation:

- ncols: Number of columns

- nrowws: Number of rows

- xllcorner: X cartesian co-ordinate of the lower left corner of the grid in metres

- yllcorner: Y cartesian co-ordinate of the lower left corner of the grid in metres

- cellsize: Cell size in metres

- NODATA_value: Null value



# TODO 

To visualize, process or modify the DEM data, it is advised to use QGIS, a geographic information system, which is [freely available to download](https://www.qgis.org/en/site/forusers/download.html). 

# TODO

[back](/Merewether1.md)

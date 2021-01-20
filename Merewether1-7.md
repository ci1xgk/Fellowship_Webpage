#### Floodplain friction coefficient file (`.n`)

This file is used to set a spatially variable friction coefficient over the floodplain by assigning values of Manning’s n to each cell on the computational grid. It must be an [Esri ASCII raster file](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm) with the same dimension and resolution (i.e. `ncols`, `nrows`, `xllcorner`, `yllcorner`, `cellsize`) of the DEM file, followed by space delimited 2D array of Manning’s n values. 

To use this option, the keyword `manningfile ` must be included in `.par` file, followed by the name of the `.n` file to be read. An example of how to prepare `.n` file using QGIS is demonstrated for the Merewether case study in [_"Preparing the input data"_](/Merewether1-2.md). 


[back](/Merewether1.md)

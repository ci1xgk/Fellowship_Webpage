#### Floodplain friction coefficient file (`.n`)

This file is used to set a spatially variable friction coefficient over the floodplain by assigning values of Manning’s n to each cell on the computational grid. It must be an [Esri ASCII raster file](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm) with the same dimension and resolution (i.e. `ncols`, `nrows`, `xllcorner`, `yllcorner`, `cellsize`) of the DEM file, followed by space delimited 2D array of Manning’s n values. 

To use this option, the keyword `manningfile` must be included in `.par` file, followed by the name of the `.n` file to be read. Case study [_"5. Eden 2015, fluvial flooding"_](/Desmond_Eden2015.md) provides an example of how to set up `.n` file.


[back](/Merewether1.md)

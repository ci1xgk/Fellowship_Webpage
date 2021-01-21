#### Start file – water depth, water elevation, discharge (`.start`, `.start.Qx`, `.start.Qy`)

By default, LISFLOOD starts the simulations from zero depth and discharge initial condition on the domain. However, it is possible to have user defined initial condition for water depth (or elevation) and discharge. 

1. Water depth (or elevation) initialization

   In this option, LSFLOOD reads the initial condition of water depth or elevation (depending on the keyword used in `.par` file) from `.start` file, while using zero discharge initial condition over the domain. 
  
   The `.start` file must be an [Esri ASCII raster file](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm) with the same dimension and resolution (i.e. `ncols`, `nrows`, `xllcorner`, `yllcorner`, `cellsize`) of the DEM file, followed by space delimited 2D array of water depth or water elevation values in meter. 
  
   To use the initial condition as water depth or water elevation, the keywords `startfile` or `startelev` must be included in `.par` file, respectively, followed by the name of the `.start` file to be read. An example of how to prepare `.start` file using QGIS is demonstrated for the Merewether case study in [_"Preparing the input data"_](/Merewether1-2.md). 

2. Water depth (or elevation) and discharge initialization

   In this option, LSFLOOD reads the initial condition of water depth or elevation (depending on the keyword used in `.par` file) from `.start` file, and the initial condition of discharge from `.start.Qx` and `.start.Qy` files. 
   
   The `.start.Qx` and `.start.Qy` files must contain the initial conditions of X and Y components of discharge, qx and qy (qx = Qx/h, qy=Qy/h). They must be an [Esri ASCII raster file](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm) with the same dimension and resolution (i.e. `ncols`, `nrows`, `xllcorner`, `yllcorner`, `cellsize`) of the DEM file, followed by space delimited 2D array of qx or qy values, in square meter per second. These two files must have the same name as `.start` file while `.Qx` and `.Qy` must be added at the end of the names.
  
   To activate this option, after activating the Water depth (or elevation) initialization as above, the user only needs to include the keyword `startq2d` in `.par` file. 

[back](/Merewether1.md)

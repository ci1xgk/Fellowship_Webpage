#### Time of initial inundation (`.inittm`), time of maximum depth (`.maxtm`) and total time of inundation (`.totaltm`) output files

These two files will be generated at the end of the simulation and record the time of initial inundation for each grid cell (`.inittm`), the time of maximum inundation depth in each grid cell (`.maxtm`) and the total time for which a grid cell is inundated (`.totaltm`). The data will be written with the same [Esri ASCII raster format](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm) of the DEM input file. Units are in hours from the start of the simulation.

By default, the values will be written at each time step, and by including item `mint_hk` (recall [*"Parameter file (.par)
"*](/Merewether1-1.md)), the values will be written at each `massint` interval.




[back](/Merewether3.md)

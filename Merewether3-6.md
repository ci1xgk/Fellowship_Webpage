#### Maximum water depth (`.max`) and maximum water surface elevation (`.mxe`) output files

These two files will be generated at the end of the simulation and record the maximum water depth (`.max`) and the maximum free-surface elevation (`.mxe`) predicted on each grid cell throughout the simulation. The data (in metre) will be written with the same [Esri ASCII raster format](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm) of the DEM input file.

By default, these files contain the maximum values of water depth and free-surface elevation are written on each time step. Note that if item `mint_hk` is further included in the `.par` file, the writing of the maximum values will be done at each interval `massint` (recall [*"Parameter file (`.par`)"*](/Merewether1-1.md)), and this will be computationally more efficient.




[back](/Merewether3.md)

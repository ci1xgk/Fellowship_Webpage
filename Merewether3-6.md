#### Maximum water depth (`.max`) and maximum water surface elevation (`.mxe`) output files

These two files record the maximum water depth (`.max`) and the maximum water surface elevation (`.mxe`) predicted by the model on each grid cell over the course of the simulation. The data will be written in these files with the same ASCII raster format of the DEM input file.

By default these files record the maximum values of water depth or water surface elevation, computed on each time step but if the keyword `mint_hk` is included in the `.par` file then the maximum values will be computetd at each interval, `massint`, as specified in the `.par` file.




[back](/Merewether3.md)

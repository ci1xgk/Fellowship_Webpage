#### Maximum water depth (`.max`) and maximum water surface elevation (`.mxe`) output files

These two files will be generated at the end of simulation and record the maximum water depth (`.max`) and the maximum water surface elevation (`.mxe`) predicted by the model on each grid cell over the course of the simulation. The data will be written in these files with the same ASCII raster format of the DEM input file.

By default these files contain the maximum values of water depth and water surface elevation recorded on each time step. However, if the keyword `mint_hk` is included in the `.par` file then the maximum values will be recorded at each interval, `massint`, as specified in the `.par` file. The latter case will be computationally more efficient but less accurate (especially if water depths are changing rapidly relative to `massint`). 




[back](/Merewether3.md)

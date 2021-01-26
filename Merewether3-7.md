#### Time of initial inundation (`.inittm`), time of maximum depth (`.maxtm`) and total time of inundation (`.totaltm`) output files

These two files will be generated at the end of simulation and record the time of initial inundation for each grid cell (`.inittm`), the time of maximum inundation depth in each grid cell (`.maxtm`) and the total time for which a grid cell is inundated (`.totaltm`). The data will be written in these files with the same ASCII raster format of the DEM input file. Units are in hours from the start of the simulation.

By default the values will be recorded on each time step. However, if the keyword `mint_hk` is included in the `.par` file, the values will be recorded at each interval, `massint`, as specified in the `.par` file. 




[back](/Merewether3.md)

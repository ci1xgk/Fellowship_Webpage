#### Spatially- and temporarily-varying rainfall file (`.nc`)

This file is used to set a spatially- and temporally-varying rainfall from a weather radar or numerical weather prediction model. The file must be in [TUFLOW NetCDF rainfall format](https://wiki.tuflow.com/index.php?title=TUFLOW_NetCDF_Rainfall_Format). 

The rainfall accumulation (in mm) is stored for each rainfall “tile” for each time interval. The first rainfall timestamp should be 0, corresponding to the start of the simulation, and the total length of the simulation (i.e `sim_time` in the `.par` file) should be no longer than the duration of the rainfall time series.

The rainfall file must have the same origin as the DEM (i.e. `xllcorner`, `yllcorner`). The size of a rainfall tile can be larger than the DEM cell size (i.e. `cellsize` in the `.par` file) but it must be an integer multiple of the DEM's cell size.

To use this option, the item `dynamicrainfile` must be included in the `.par` file, followed by the name of the `.nc` file to be read. Case study [_"5. Eden 2015 fluvial flooding"_](/Desmond_Eden2015.md) provides an example of how the `.nc` file is used.

[back](/Merewether1.md)

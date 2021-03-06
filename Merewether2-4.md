#### Preparing the DG2-related DEM files using `generateDG2DEM` toolkit

As opposed to piecewise-constant data representation used in the FV1 or ACC solvers, the DG2 solver represents data as piecewise-planar per element, defined by three coefficients: an average-coefficient and two slope-coefficients in X and Y directions ([Shaw et al., 2021](https://gmd.copernicus.org/preprints/gmd-2020-340/)). 

Hence, setting up the DG2 on LISFLOOD-FP requires three separate [Esri ASCII raster files](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm): one for the average-coefficient values, and two others for the X-directional and the Y-directional slope-coefficient values, with the extensions `.dem`, `.dem1x` and `.dem1y`, respectively.

Files with the extensions `.dem`, `.dem1x` and `.dem1y` can be generated using the toolkit `generateDG2DEM` (available in the preprocess directory of `LISFLOOD-FP-trunk` repository). The toolkit is obtained after compiling the LISFLOOD-FP code, following the instructions within ["_Compilation_"](/LISFLOOD8.0.md). It will be generated as an executable file with the name `generateDG2DEM.exe` on a Windows platform and the name `generateDG2DEM` on a Linux-based platform, in the same directory of the LISFLOOD-FP executable.

The toolkit requires the availability of the raw DEM file in the same directory, subject to appending it with the extension `.raw`. For example, the DEM file, `merewether-0p175m.dem`, created for the Merewether test case (recall [Modifying the resolution of the DEM on QGIS](https://www.seamlesswave.com/Merewether2-2.html)) must be renamed to `merewether-0p175m.dem.raw`. 

For running the `generateDG2DEM.exe` of the Merewether test case on Windows, create a directory for the test case, for example named `merewether`, inside the same directory where `generateDG2DEM.exe` is located. Then place the `merewether-0p175m.par` and `merewether-0p175m.dem.raw` files inside the `merewether` directory. By clicking on the *location bar* of the Windows Explorer, then typing `cmd` and pressing *Enter*, the *Command Prompt Window* will be opened in the folder. To run the toolkit, the name of the executable must be entered in the *Command prompt*, followed by the name of the `.par` file: 
```
..\generateDG2DEM.exe merewether-0p175m.par   
```

After running the `generateDG2DEM` toolkit, three raster files will be generated within the same directory of `merewether-0p175m.dem.raw` file: 

* `merewether-0p175m.dem` which is a copy of the same `merewether-0p175m.dem.raw` file, containing the generated average-coefficient values

* `merewether-0p175m.dem1x` which contains the generated X-directional slope-coefficient values

* `merewether-0p175m.dem1y` which contains the generated Y-directional slope-coefficient values



[back](/Merewether2.md)

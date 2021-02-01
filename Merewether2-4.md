#### Preparing the DG2-related DEM files using `generateDG2DEM` toolkit

As opposed to piecewise-constant data representation used in FV1 or ACC solvers, the DG2 solver represents data as piecewise-planar per element defined by three coefficients: an average-coefficient and two slope-coefficients in X and Y directions ([Shaw et al. 2021](https://gmd.copernicus.org/preprints/gmd-2020-340/)). 

Hence, setting up DG2 on LISFLOOD requires three separate raster files one including the average-coefficient values, and two others including the X-directional slope-coefficient values and the Y-directional slope-coefficient values, with the extensions `.dem`, `.dem1x` and `.dem1y`, respectively. 

Files with the extensions `.dem`, `.dem1x` and `.dem1y` can be generated using the toolkit `generateDG2DEM` (available in the "_preprocess_" directory). The toolkit is obtained after compiling the LISFLOOD-FP code, following the instructions within the ["_Compilation_"](/LISFLOOD8.0.md). It will be generated as an executable file the name `generateDG2DEM.exe` on a Windows platform and the name `generateDG2DEM` on a linux-based platform, in the same directory of LISFLOOD-FP executable.

The toolkit requires the availability of the raw DEM file in the same directory subject to appending it with the extension `.raw`. For example, the DEM file, `merewether-0p175m.dem`, created for the Merewether test case (see [Modifying the resolution of the DEM on QGIS](https://www.seamlesswave.com/Merewether2-2.html)) should be renamed to `merewether-0p175m.dem.raw`. 

For running the `generateDG2DEM.exe` of the Merewether test case on windows, first create a directory for the test case, for example named `merewether`, in the same directory where `lisflood.exe` is generated. Then place the `merewether-0p175m.par` and `merewether-0p175m.dem.raw` files inside the `merewether` directory. By clicking on the *location bar* of the Windows Explorer, then typing `cmd` and pressing *Enter*, the *Command Prompt Window* will be opened in the folder. To run the toolkit, the name of executable must be entered in *Command prompt*, followed by the name of the `.par` file: 
```
..\generateDG2DEM.exe merewether-0p175m.par   
```

After running `generateDG2DEM` toolkit, three raster files will be generated within the same directory of `merewether-0p175m.dem.raw` file: 

* `merewether-0p175m.dem` which is a copy of the same `merewether-0p175m.dem.raw`, containing the generated average-coefficient values

* `merewether-0p175m.dem1x` which contains the generated X-directional slope-coefficient values

* `merewether-0p175m.dem1y` which contains the generated Y-directional slope-coefficient values



[back](/Merewether2.md)

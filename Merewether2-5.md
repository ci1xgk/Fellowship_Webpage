#### Preparing the DG2-related Initial condition files using `generateDG2start` toolkit

Setting up an initial condition for a DG2 simulation also requires three separate [Esri ASCII raster files](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm), for either a water depth (h) or free-surface elevation (h + z) initial condition. These raster files must include the average-coefficient values, the X-directional and the Y-directional slope-coefficient values, with extensions of `.start`, `.start1x` and `.start1y`, respectively.

Files with the extensions `.start`, `.start1x` and `.start1y` can be generated using the toolkit `generateDG2start` (available in the preprocess directory of `LISFLOOD-FP-trunk` repository). The toolkit is obtained after compiling the LISFLOOD-FP code, following the instructions within ["_Compilation_"](/LISFLOOD8.0.md). It will be generated as an executable file with the name `generateDG2start.exe` on a Windows platform and the name `generateDG2start` on a Linux-based platform, in the same directory of LISFLOOD-FP executable.

The toolkit requires the availability of an initial condition [Esri ASCII raster file](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm) in the same folder (where `generateDG2start` is located), subject to adding `.raw` to the end of its extension. For example, the free-surface elevation initial condition file for the Merewether test case (recall [_Preparing the initial conditions files for ACC/FV1 on QGIS_](https://www.seamlesswave.com/Merewether2-3)) must be renamed to `merewether-0p175m.start.raw` and placed in the same directory where the `generateDG2start.exe` file is generated.

For running the `generateDG2start.exe` for the Merewether test case on Windows, create a directory for the test case, for example named `merewether`, inside the same directory where `generateDG2start.exe` is located. Then place the `merewether-0p175m.par` and `merewether-0p175m.start.raw` files inside the `merewether` directory. By clicking on the *location bar* of the Windows Explorer, then typing `cmd` and pressing *Enter*, the *Command Prompt Window* will be opened in the folder. To run the toolkit, the name of the executable must be entered in the *Command prompt*, followed by the name of the `.par` file: 
```
..\generateDG2start.exe merewether-0p175m.par   
```

After running the `generateDG2start` toolkit, three new raster files will be generated in the same directory, namely:

-	`merewether-0p175m.start` which is a copy of `merewether-0p175m.start.raw` file, but with the generated average-coefficient values of the free-surface elevation

-	`merewether-0p175m.start1x` which contains the X-directional slope-coefficient values of the free-surface elevation

-	`merewether-0p175m.start1y` which contains the Y-directional slope-coefficient values of the free-surface elevation


[back](/Merewether2.md)

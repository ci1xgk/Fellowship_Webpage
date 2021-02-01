#### Preparing the DG2-related Initial condition files using `generateDG2start` toolkit

Setting up an initial condition for a DG2 simulation also requires three separate raster files, e.g. either a water depth (h) initial condition or free-surface water elevation (h + z) initial condition. These raster files should include the average-coefficient values, the X-directional slope-coefficient values and the Y-directional slope-coefficient values, with extensions of `.start`, `.start1x` and `.start1y`, respectively. 

Files with the the extensions `.start`, `.start1x` and `.start1y` can also be generated using the toolkit `generateDG2start` (available in the "preprocess" directory). The toolkit is obtained after compiling the LISFLOOD-FP code, following the instructions within the ["_Compilation_"](/LISFLOOD8.0.md). It will be generated as an executable file with the name `generateDG2start.exe` on a Windows platform and the name `generateDG2start` on a linux-based platform, in the same directory of LISFLOOD-FP executable.

The toolkit requires the availability of a raw initial condition file in the same folder subject to adding `.raw` to the end of its extension.

For example, the free-surface water elevation initial condition file for Merewether test case (recall [_Preparing the initial conditions files for ACC/FV1 on QGIS_](https://www.seamlesswave.com/Merewether2-3)) should be renamed to `merewether-0p175m.start.raw` and placed in the same directory as `generateDG2start`. 

For running the `generateDG2start.exe` of the Merewether test case on windows, first create a directory for the test case, for example named `merewether`, in the same directory where `generateDG2start.exe` is generated. Then place the `merewether-0p175m.par` and `merewether-0p175m.start.raw` files inside the `merewether` directory. By clicking on the *location bar* of the Windows Explorer, then typing `cmd` and pressing *Enter*, the *Command Prompt Window* will be opened in the folder. To run the toolkit, the name of executable must be entered in *Command prompt*, followed by the name of the `.par` file: 
```
..\generateDG2start.exe merewether-0p175m.par   
```

After running `generateDG2start`, three new raster files will be generated in the same directory, namely:

-	`merewether-0p175m.start` which is a copy of `merewether-0p175m.start.raw`, but with the generated average-coefficient values of the free-surface water elevation

-	`merewether-0p175m.start1x` which contains the X-directional slope-coefficient values of the free-surface water elevation

-	`merewether-0p175m.start1y` which contains the Y-directional slope-coefficient values of the free-surface water elevation


[back](/Merewether2.md)

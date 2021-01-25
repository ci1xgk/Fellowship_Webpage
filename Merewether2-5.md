#### Preparing the DG2-related Initial condition files using `generateDG2start` toolkit

Setting up an initial condition for a DG2 simulation also requires three separate raster files, e.g. either a water depth (h) initial condition or free-surface water elevation (h + z) initial condition. These raster files should include the average-coefficient values, the X-directional slope-coefficient values and the Y-directional slope-coefficient values, with extensions of `.start`, `.start1x` and `.start1y`, respectively. 

Files with the the extensions `.start`, `.start1x` and `.start1y` can also be generated using the toolkit `generateDG2start` (available in the "preprocess" directory). The toolkit requires the availability of a raw initial condition file in the same folder subject to adding `.raw` to the end of its extension.

For example, the free-surface water elevation initial condition file for Merewether test case (recall [_Preparing the initial conditions files for ACC/FV1 on QGIS_](https://www.seamlesswave.com/Merewether2-3)) should be renamed to `merewether-0p175m.start.raw` and placed in the same directory as `generateDG2start`. After running `generateDG2start`, three new raster files will be generated in the same directory, namely:

-	`merewether-0p175m.start` which is a copy of `merewether-0p175m.start.raw`, but with the generated average-coefficient values of the free-surface water elevation

-	`merewether-0p175m.start1x` which contains the X-directional slope-coefficient values of the free-surface water elevation

-	`merewether-0p175m.start1y` which contains the Y-directional slope-coefficient values of the free-surface water elevation


[back](/Merewether2.md)

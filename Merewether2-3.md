#### Preparing the initial conditions files for ACC/FV1 on QGIS

The Merewether test case has a constant water level of h + z = 17.8 m at the downstream boundary which needs to be set as the initial condition. LISFLOOD can read the initial condition as a raster file of either water level (h + z) or water depth (h), with the extension of `.start` as previously explained in [_"Input files and their format
"_](/Merewether1-6.md). To generate the initial water level raster file using QGIS, the following steps should be applied:

-	Load the Merewether DEM raster file, named `merewether-0p175m.dem` in the QGIS, as explained in [_"Viewing the DEM data on QGIS"_](/Merewether2-1.md).
-	Go to menu *Raster - > Raster Calculator*
-	In *Raster Calculator* window, enter the following expression in *Raster Calculator Expression*:
```
(merewether-0p175m@1 <= 17.8) * 17.8 + (merewether-0p175m@1 > 17.8) * merewether-0p175m@1
```

[back](/Merewether2.md)
